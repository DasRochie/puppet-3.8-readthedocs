---
layout: default
title: "SSL Configuration: CSR Attributes and Certificate Extensions"
canonical: "/puppet/latest/reference/ssl_attributes_extensions.html"
---

[cert_request]: ./subsystem_agent_master_comm.html#check-for-keys-and-certificates
[csr_attributes]: ./configuration.html#csrattributes
[confdir]: ./configuration.html#confdir
[autosign_policy]: ./ssl_autosign.html#policy-based-autosigning
[autosign_basic]: ./ssl_autosign.html#basic-autosigning-autosignconf
[puppet_oids]: #puppet-specific-registered-ids
[trusted_hash]: ./lang_facts_and_builtin_vars.html#trusted-facts
[enable_trusted]: ./config_important_settings.html#getting-new-features-early

Summary
-----

When Puppet agent nodes request their certificates, the certificate signing request (CSR) usually just contains their certname and the necessary cryptographic information. However, agents can also embed more data in their CSR. This extra data can be useful for [policy-based autosigning][autosign_policy] and for adding new [trusted facts.][trusted_hash]

### Status as of Early 2014

In this version of Puppet, embedding additional data into CSRs is mostly useful in deployments where:

* Large numbers of nodes are regularly created and destroyed as part of an elastic scaling system.
* You are willing to build custom tooling to make certificate autosigning more secure and useful.

It may also be useful in deployments where:

* Puppet is used to deploy private keys or other sensitive information, and you want extra control over which nodes receive this data.

If your deployment doesn't match one of these descriptions, you may not need this feature.

> ### Version Note
>
> CSR attributes and certificate extensions are only available in Puppet 3.4 and newer. Access to extensions in the `$trusted` hash is available in 3.5 and newer.


Timing: When Data Can be Added to CSRs / Certificates
-----

When Puppet agent starts the process of requesting a catalog, it first checks whether it has a valid signed certificate. If it does not, it will generate a key pair, craft a CSR, and submit it to the certificate authority (CA) Puppet master. The steps are [covered in more detail in the reference page about agent/master HTTPS traffic][cert_request].

Once a certificate is signed, it is, for all practical purposes, locked and immutable. Thus, for any data to persist in the certificate, it has to be added to the CSR before the CA signs the certificate.

This means **any desired extra data must be present before Puppet agent attempts to request its catalog for the first time.**

Practically speaking, you should populate any extra data when provisioning the node. If you mess up, see [Recovering From Failed Data Embedding](#recovering-from-failed-data-embedding) below.

Data Location and Format
-----

Extra data for the CSR is read from the `csr_attributes.yaml` file in Puppet's [`confdir`][confdir]. (The location of this file can be changed with [the `csr_attributes` setting][csr_attributes].)

The `csr_attributes` file must be a YAML hash containing one or both of the following keys:

* `custom_attributes`
* `extension_requests`

The value of each key must also be a hash, where:

* Each key is a valid [object identifier (OID)](http://en.wikipedia.org/wiki/Object_identifier) --- [Puppet-specific OIDs][puppet_oids] may optionally be referenced by short name instead of by numeric ID.
* Each value is an object that can be cast to a string (that is, numbers are allowed but arrays are not).

See the respective sections below for information about how each hash is used and recommended OIDs for each hash.

Custom Attributes (Transient CSR Data)
-----

**Custom Attributes** are pieces of data that are _only_ embedded into the CSR. They can be used by the CA when deciding whether or not to sign the certificate, but they are discarded after that and will not be transferred to the final certificate.

### Default Behavior

By default, Puppet's CA tools don't do anything with custom attributes. The `puppet cert list` command will not display custom attributes for any pending CSRs, and [basic autosigning (autosign.conf)][autosign_basic] will not check them before signing.

### Configurable Behavior

If you are using [policy-based autosigning][autosign_policy], your policy executable receives the complete CSR in PEM format. The executable can extract and inspect the custom attributes, and it can use them when deciding whether to sign the certificate.

The simplest use is to embed a pre-shared key of some kind in the custom attributes. A policy executable can compare it to a list of known keys and autosign certificates for any pre-authorized nodes.

A more complex use might be to embed an instance-specific ID, and write a policy executable that can check it against a list of your recently requested instances on a public cloud like EC2 or GCE.

### Manually Checking For Custom Attributes in CSRs

You can check for custom attributes by using OpenSSL to dump a PEM-format CSR to text format. Do this by running:

    $ openssl req -noout -text -in <name>.pem

In the output, look for a section called "Attributes," which generally appears below the "Subject Public Key Info" block:

    Attributes:
        challengePassword        :342thbjkt82094y0uthhor289jnqthpc2290

### Recommended OIDs for Attributes

Custom attributes can use any public or site-specific OID, **with the exception of the OIDs used for core X.509 functionality.** This means you can't re-use existing OIDs for things like subject alternative names.

One useful OID is the "challengePassword" attribute --- `1.2.840.113549.1.9.7`. This is a rarely-used corner of X.509 which can easily be repurposed to hold a pre-shared key. The benefit of using this instead of an arbitrary OID is that it will appear by name when using OpenSSL to dump the CSR to text; OIDs that `openssl req` can't recognize will be displayed as numerical strings.

You can also use the Puppet-specific OIDs [referenced below][puppet_oids] in the section on extension requests.

Extension Requests (Permanent Certificate Data)
-----

**Extension requests** are pieces of data that will be _transferred to the final certificate_ (as **extensions**) when the CA signs the CSR. They will persist as trusted, immutable data, which cannot be altered after the certificate has been signed.

They may also be used by the CA when deciding whether or not to sign the certificate.

### Default Behavior

When signing a certificate, Puppet's CA tools will transfer any extension requests into the final certificate.

If [trusted facts are enabled][enable_trusted], any cert extensions can be accessed in manifests as `$trusted[extensions][<EXTENSION OID>]`. Any OIDs in the ppRegCertExt range ([see below][puppet_oids]) will appear using their short names, and other OIDs will appear as plain dotted numbers. See [the page on facts and special variables][trusted_hash] for more information about `$trusted`.

Visibility of extensions is somewhat limited:

* The `puppet cert list` command _will not_ display custom attributes for any pending CSRs, and [basic autosigning (autosign.conf)][autosign_basic] will not check them before signing. You'll need to either use [policy-based autosigning][autosign_policy] or inspect CSRs manually with the `openssl` command (see below).
* The `puppet cert print` command _will_ display any extensions in a signed certificate, under the "X509v3 extensions" section.

Puppet's authorization system (auth.conf) does not use certificate extensions for anything.

### Configurable Behavior

If you are using [policy-based autosigning][autosign_policy], your policy executable receives the complete CSR in PEM format. The executable can extract and inspect the extension requests, and it can use them when deciding whether to sign the certificate.

### Manually Checking For Extensions in CSRs and Certificates

You can check for extension requests in a CSR by using OpenSSL to dump a PEM-format CSR to text format. Do this by running:

    $ openssl req -noout -text -in <name>.pem

In the output, look for a section called "Requested Extensions," which generally appears below the "Subject Public Key Info" and "Attributes" blocks:

    Requested Extensions:
        1.3.6.1.4.1.34380.1.1.4:
            342thbjkt82094y0uthhor289jnqthpc2290
        1.3.6.1.4.1.34380.1.1.3:
            my_ami_image
        1.3.6.1.4.1.34380.1.1.1:
            ED803750-E3C7-44F5-BB08-41A04433FE2E

Any Puppet-specific OIDs (see below) will appear as numeric strings when using OpenSSL.

You can check for extensions in a signed certificate by running `puppet cert print <name>`. In the output, look for the "X509v3 extensions" section. Any of the Puppet-specific registered OIDs (see below) will appear as their descriptive names:

        X509v3 extensions:
            Netscape Comment:
                Puppet Ruby/OpenSSL Internal Certificate
            X509v3 Subject Key Identifier:
                47:BC:D5:14:33:F2:ED:85:B9:52:FD:A2:EA:E4:CC:00:7F:7F:19:7E
            Puppet Node UUID:
                ED803750-E3C7-44F5-BB08-41A04433FE2E
            X509v3 Extended Key Usage: critical
                TLS Web Server Authentication, TLS Web Client Authentication
            X509v3 Basic Constraints: critical
                CA:FALSE
            Puppet Node Preshared Key:
                342thbjkt82094y0uthhor289jnqthpc2290
            X509v3 Key Usage: critical
                Digital Signature, Key Encipherment
            Puppet Node Image Name:
                my_ami_image

### Recommended OIDs for Extensions

Extension request OIDs **must** be under the "ppRegCertExt" (`1.3.6.1.4.1.34380.1.1`) or "ppPrivCertExt" (`1.3.6.1.4.1.34380.1.2`) OID arcs.

Puppet Labs provides several registered OIDs (under "ppRegCertExt") for the most common kinds of extension information, as well as a private OID range ("ppPrivCertExt") for site-specific extension information. The benefits of using the registered OIDs are:

* They can be referenced in `csr_attributes.yaml` using their short names instead of their numeric IDs.
* When using Puppet tools to print certificate info, they will appear using their descriptive names instead of their numeric IDs.

The private range is available for any information you want to embed into a certificate that isn't already in wide use elsewhere. It is completely unregulated, and its contents are expected to be different in every Puppet deployment.

#### Puppet-Specific Registered IDs

The "ppRegCertExt" OID range contains the following OIDs:

Numeric ID              | Short Name         | Descriptive Name
------------------------|--------------------|--------------------------
1.3.6.1.4.1.34380.1.1.1 | `pp_uuid`          | Puppet Node UUID
1.3.6.1.4.1.34380.1.1.2 | `pp_instance_id`   | Puppet Node Instance ID
1.3.6.1.4.1.34380.1.1.3 | `pp_image_name`    | Puppet Node Image Name
1.3.6.1.4.1.34380.1.1.4 | `pp_preshared_key` | Puppet Node Preshared Key


AWS Attributes and Extensions Population Example
-----

Generally, you will want to use an automated script (possibly using cloud-init or a similar tool) to populate the `csr_attributes.yaml` file at the time a node is provisioned.

As an example, you could enter the following script into the "Configure Instance Details ???> Advanced Details" section when provisioning a new node from the AWS EC2 dashboard:

    #!/bin/sh
    if [ ! -d /etc/puppet ]; then
       mkdir /etc/puppet
    fi
    erb > /etc/puppet/csr_attributes.yaml <<END
    custom_attributes:
      1.2.840.113549.1.9.7: mySuperAwesomePassword
    extension_requests:
      pp_instance_id: <%= %x{/opt/aws/bin/ec2-metadata -i}.sub(/instance-id: (.*)/,'\1').chomp %>
      pp_image_name:  <%= %x{/opt/aws/bin/ec2-metadata -a}.sub(/ami-id: (.*)/,'\1').chomp %>
    END

Assuming your image had the `erb` binary available, this would populate the attributes file with the AWS instance ID, image name, and a pre-shared key to use with policy-based autosigning.


Troubleshooting
-----

### Recovering From Failed Data Embedding

When first testing this feature, you might fail to embed the right information in a CSR or certificate and want to start over for your test node(s). (This is not really a problem once your provisioning system is changed to populate the data, but it can happen pretty easily when doing things manually.)

In order to start over, you'll need to do the following:

**On the test node:**

* Turn off Puppet agent, if it's running.
* Check whether a CSR is present; it will be at `$ssldir/certificate_requests/<name>.pem`. If it exists, delete it.
* Check whether a certificate is present; it will be at `$ssldir/certs/<name>.pem`. If it exists, delete it.

**On the CA Puppet master:**

* Check whether a signed certificate exists; use `puppet cert list --all` to see the complete list. If it exists, revoke and delete it with `puppet cert clean <name>`.
* Check whether a CSR for the node exists; it will be in `$ssldir/ca/requests/<name>.pem`. If it exists, delete it.

After you've done that, you can start over.

