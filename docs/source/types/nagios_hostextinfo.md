---
layout: default
built_from_commit: c0673af42427fbe0b22ff97c8e5fa3244715eeae
title: 'Resource Type: nagios_hostextinfo'
canonical: /puppet/latest/reference/types/nagios_hostextinfo.html
---

> **NOTE:** This page was generated from the Puppet source code on 2016-01-15 16:31:56 +0100

nagios_hostextinfo
-----

* [Attributes](#nagios_hostextinfo-attributes)
* [Providers](#nagios_hostextinfo-providers)

<h3 id="nagios_hostextinfo-description">Description</h3>

The Nagios type hostextinfo.  This resource type is autogenerated using the
model developed in Naginator, and all of the Nagios types are generated using the
same code and the same library.

This type generates Nagios configuration statements in Nagios-parseable configuration
files.  By default, the statements will be added to `/etc/nagios/nagios_hostextinfo.cfg`, but
you can send them to a different file by setting their `target` attribute.

You can purge Nagios resources using the `resources` type, but *only*
in the default file locations.  This is an architectural limitation.

<h3 id="nagios_hostextinfo-attributes">Attributes</h3>

<pre><code>nagios_hostextinfo { 'resource title':
  <a href="#nagios_hostextinfo-attribute-host_name">host_name</a>       =&gt; <em># <strong>(namevar)</strong> The name of this nagios_hostextinfo...</em>
  <a href="#nagios_hostextinfo-attribute-ensure">ensure</a>          =&gt; <em># The basic property that the resource should be...</em>
  <a href="#nagios_hostextinfo-attribute-group">group</a>           =&gt; <em># The desired group of the config file for this...</em>
  <a href="#nagios_hostextinfo-attribute-icon_image">icon_image</a>      =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_hostextinfo-attribute-icon_image_alt">icon_image_alt</a>  =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_hostextinfo-attribute-mode">mode</a>            =&gt; <em># The desired mode of the config file for this...</em>
  <a href="#nagios_hostextinfo-attribute-notes">notes</a>           =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_hostextinfo-attribute-notes_url">notes_url</a>       =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_hostextinfo-attribute-owner">owner</a>           =&gt; <em># The desired owner of the config file for this...</em>
  <a href="#nagios_hostextinfo-attribute-provider">provider</a>        =&gt; <em># The specific backend to use for this...</em>
  <a href="#nagios_hostextinfo-attribute-register">register</a>        =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_hostextinfo-attribute-statusmap_image">statusmap_image</a> =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_hostextinfo-attribute-target">target</a>          =&gt; <em># The...</em>
  <a href="#nagios_hostextinfo-attribute-use">use</a>             =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_hostextinfo-attribute-vrml_image">vrml_image</a>      =&gt; <em># Nagios configuration file...</em>
  # ...plus any applicable <a href="./metaparameter.html">metaparameters</a>.
}</code></pre>

<h4 id="nagios_hostextinfo-attribute-host_name">host_name</h4>

_(**Namevar:** If omitted, this attribute's value defaults to the resource's title.)_

The name of this nagios_hostextinfo resource.

([??? Back to nagios_hostextinfo attributes](#nagios_hostextinfo-attributes))

<h4 id="nagios_hostextinfo-attribute-ensure">ensure</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

The basic property that the resource should be in.

Valid values are `present`, `absent`.

([??? Back to nagios_hostextinfo attributes](#nagios_hostextinfo-attributes))

<h4 id="nagios_hostextinfo-attribute-group">group</h4>

The desired group of the config file for this nagios_hostextinfo resource.

NOTE: If the target file is explicitly managed by a file resource in your manifest,
this parameter has no effect. If a parent directory of the target is managed by
a recursive file resource, this limitation does not apply (i.e., this parameter
takes precedence, and if purge is used, the target file is exempt).

([??? Back to nagios_hostextinfo attributes](#nagios_hostextinfo-attributes))

<h4 id="nagios_hostextinfo-attribute-icon_image">icon_image</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_hostextinfo attributes](#nagios_hostextinfo-attributes))

<h4 id="nagios_hostextinfo-attribute-icon_image_alt">icon_image_alt</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_hostextinfo attributes](#nagios_hostextinfo-attributes))

<h4 id="nagios_hostextinfo-attribute-mode">mode</h4>

The desired mode of the config file for this nagios_hostextinfo resource.

NOTE: If the target file is explicitly managed by a file resource in your manifest,
this parameter has no effect. If a parent directory of the target is managed by
a recursive file resource, this limitation does not apply (i.e., this parameter
takes precedence, and if purge is used, the target file is exempt).

([??? Back to nagios_hostextinfo attributes](#nagios_hostextinfo-attributes))

<h4 id="nagios_hostextinfo-attribute-notes">notes</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_hostextinfo attributes](#nagios_hostextinfo-attributes))

<h4 id="nagios_hostextinfo-attribute-notes_url">notes_url</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_hostextinfo attributes](#nagios_hostextinfo-attributes))

<h4 id="nagios_hostextinfo-attribute-owner">owner</h4>

The desired owner of the config file for this nagios_hostextinfo resource.

NOTE: If the target file is explicitly managed by a file resource in your manifest,
this parameter has no effect. If a parent directory of the target is managed by
a recursive file resource, this limitation does not apply (i.e., this parameter
takes precedence, and if purge is used, the target file is exempt).

([??? Back to nagios_hostextinfo attributes](#nagios_hostextinfo-attributes))

<h4 id="nagios_hostextinfo-attribute-provider">provider</h4>

The specific backend to use for this `nagios_hostextinfo`
resource. You will seldom need to specify this --- Puppet will usually
discover the appropriate provider for your platform.

Available providers are:

* [`naginator`](#nagios_hostextinfo-provider-naginator)

([??? Back to nagios_hostextinfo attributes](#nagios_hostextinfo-attributes))

<h4 id="nagios_hostextinfo-attribute-register">register</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_hostextinfo attributes](#nagios_hostextinfo-attributes))

<h4 id="nagios_hostextinfo-attribute-statusmap_image">statusmap_image</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_hostextinfo attributes](#nagios_hostextinfo-attributes))

<h4 id="nagios_hostextinfo-attribute-target">target</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

The target.

([??? Back to nagios_hostextinfo attributes](#nagios_hostextinfo-attributes))

<h4 id="nagios_hostextinfo-attribute-use">use</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_hostextinfo attributes](#nagios_hostextinfo-attributes))

<h4 id="nagios_hostextinfo-attribute-vrml_image">vrml_image</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_hostextinfo attributes](#nagios_hostextinfo-attributes))


<h3 id="nagios_hostextinfo-providers">Providers</h3>

<h4 id="nagios_hostextinfo-provider-naginator">naginator</h4>






> **NOTE:** This page was generated from the Puppet source code on 2016-01-15 16:31:56 +0100