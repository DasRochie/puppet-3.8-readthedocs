---
layout: default
built_from_commit: c0673af42427fbe0b22ff97c8e5fa3244715eeae
title: 'Resource Type: nagios_service'
canonical: /puppet/latest/reference/types/nagios_service.html
---

> **NOTE:** This page was generated from the Puppet source code on 2016-01-15 16:31:56 +0100

nagios_service
-----

* [Attributes](#nagios_service-attributes)
* [Providers](#nagios_service-providers)

<h3 id="nagios_service-description">Description</h3>

The Nagios type service.  This resource type is autogenerated using the
model developed in Naginator, and all of the Nagios types are generated using the
same code and the same library.

This type generates Nagios configuration statements in Nagios-parseable configuration
files.  By default, the statements will be added to `/etc/nagios/nagios_service.cfg`, but
you can send them to a different file by setting their `target` attribute.

You can purge Nagios resources using the `resources` type, but *only*
in the default file locations.  This is an architectural limitation.

<h3 id="nagios_service-attributes">Attributes</h3>

<pre><code>nagios_service { 'resource title':
  <a href="#nagios_service-attribute-_naginator_name">_naginator_name</a>              =&gt; <em># <strong>(namevar)</strong> The name of this nagios_service...</em>
  <a href="#nagios_service-attribute-ensure">ensure</a>                       =&gt; <em># The basic property that the resource should be...</em>
  <a href="#nagios_service-attribute-action_url">action_url</a>                   =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-active_checks_enabled">active_checks_enabled</a>        =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-business_impact">business_impact</a>              =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-check_command">check_command</a>                =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-check_freshness">check_freshness</a>              =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-check_interval">check_interval</a>               =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-check_period">check_period</a>                 =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-contact_groups">contact_groups</a>               =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-contacts">contacts</a>                     =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-display_name">display_name</a>                 =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-event_handler">event_handler</a>                =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-event_handler_enabled">event_handler_enabled</a>        =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-failure_prediction_enabled">failure_prediction_enabled</a>   =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-first_notification_delay">first_notification_delay</a>     =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-flap_detection_enabled">flap_detection_enabled</a>       =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-flap_detection_options">flap_detection_options</a>       =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-freshness_threshold">freshness_threshold</a>          =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-group">group</a>                        =&gt; <em># The desired group of the config file for this...</em>
  <a href="#nagios_service-attribute-high_flap_threshold">high_flap_threshold</a>          =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-host_name">host_name</a>                    =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-hostgroup_name">hostgroup_name</a>               =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-icon_image">icon_image</a>                   =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-icon_image_alt">icon_image_alt</a>               =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-initial_state">initial_state</a>                =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-is_volatile">is_volatile</a>                  =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-low_flap_threshold">low_flap_threshold</a>           =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-max_check_attempts">max_check_attempts</a>           =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-mode">mode</a>                         =&gt; <em># The desired mode of the config file for this...</em>
  <a href="#nagios_service-attribute-normal_check_interval">normal_check_interval</a>        =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-notes">notes</a>                        =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-notes_url">notes_url</a>                    =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-notification_interval">notification_interval</a>        =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-notification_options">notification_options</a>         =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-notification_period">notification_period</a>          =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-notifications_enabled">notifications_enabled</a>        =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-obsess_over_service">obsess_over_service</a>          =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-owner">owner</a>                        =&gt; <em># The desired owner of the config file for this...</em>
  <a href="#nagios_service-attribute-parallelize_check">parallelize_check</a>            =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-passive_checks_enabled">passive_checks_enabled</a>       =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-poller_tag">poller_tag</a>                   =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-process_perf_data">process_perf_data</a>            =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-provider">provider</a>                     =&gt; <em># The specific backend to use for this...</em>
  <a href="#nagios_service-attribute-register">register</a>                     =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-retain_nonstatus_information">retain_nonstatus_information</a> =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-retain_status_information">retain_status_information</a>    =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-retry_check_interval">retry_check_interval</a>         =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-retry_interval">retry_interval</a>               =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-service_description">service_description</a>          =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-servicegroups">servicegroups</a>                =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-stalking_options">stalking_options</a>             =&gt; <em># Nagios configuration file...</em>
  <a href="#nagios_service-attribute-target">target</a>                       =&gt; <em># The...</em>
  <a href="#nagios_service-attribute-use">use</a>                          =&gt; <em># Nagios configuration file...</em>
  # ...plus any applicable <a href="./metaparameter.html">metaparameters</a>.
}</code></pre>

<h4 id="nagios_service-attribute-_naginator_name">_naginator_name</h4>

_(**Namevar:** If omitted, this attribute's value defaults to the resource's title.)_

The name of this nagios_service resource.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-ensure">ensure</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

The basic property that the resource should be in.

Valid values are `present`, `absent`.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-action_url">action_url</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-active_checks_enabled">active_checks_enabled</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-business_impact">business_impact</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-check_command">check_command</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-check_freshness">check_freshness</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-check_interval">check_interval</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-check_period">check_period</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-contact_groups">contact_groups</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-contacts">contacts</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-display_name">display_name</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-event_handler">event_handler</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-event_handler_enabled">event_handler_enabled</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-failure_prediction_enabled">failure_prediction_enabled</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-first_notification_delay">first_notification_delay</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-flap_detection_enabled">flap_detection_enabled</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-flap_detection_options">flap_detection_options</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-freshness_threshold">freshness_threshold</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-group">group</h4>

The desired group of the config file for this nagios_service resource.

NOTE: If the target file is explicitly managed by a file resource in your manifest,
this parameter has no effect. If a parent directory of the target is managed by
a recursive file resource, this limitation does not apply (i.e., this parameter
takes precedence, and if purge is used, the target file is exempt).

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-high_flap_threshold">high_flap_threshold</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-host_name">host_name</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-hostgroup_name">hostgroup_name</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-icon_image">icon_image</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-icon_image_alt">icon_image_alt</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-initial_state">initial_state</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-is_volatile">is_volatile</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-low_flap_threshold">low_flap_threshold</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-max_check_attempts">max_check_attempts</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-mode">mode</h4>

The desired mode of the config file for this nagios_service resource.

NOTE: If the target file is explicitly managed by a file resource in your manifest,
this parameter has no effect. If a parent directory of the target is managed by
a recursive file resource, this limitation does not apply (i.e., this parameter
takes precedence, and if purge is used, the target file is exempt).

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-normal_check_interval">normal_check_interval</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-notes">notes</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-notes_url">notes_url</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-notification_interval">notification_interval</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-notification_options">notification_options</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-notification_period">notification_period</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-notifications_enabled">notifications_enabled</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-obsess_over_service">obsess_over_service</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-owner">owner</h4>

The desired owner of the config file for this nagios_service resource.

NOTE: If the target file is explicitly managed by a file resource in your manifest,
this parameter has no effect. If a parent directory of the target is managed by
a recursive file resource, this limitation does not apply (i.e., this parameter
takes precedence, and if purge is used, the target file is exempt).

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-parallelize_check">parallelize_check</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-passive_checks_enabled">passive_checks_enabled</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-poller_tag">poller_tag</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-process_perf_data">process_perf_data</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-provider">provider</h4>

The specific backend to use for this `nagios_service`
resource. You will seldom need to specify this --- Puppet will usually
discover the appropriate provider for your platform.

Available providers are:

* [`naginator`](#nagios_service-provider-naginator)

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-register">register</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-retain_nonstatus_information">retain_nonstatus_information</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-retain_status_information">retain_status_information</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-retry_check_interval">retry_check_interval</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-retry_interval">retry_interval</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-service_description">service_description</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-servicegroups">servicegroups</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-stalking_options">stalking_options</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-target">target</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

The target.

([??? Back to nagios_service attributes](#nagios_service-attributes))

<h4 id="nagios_service-attribute-use">use</h4>

_(**Property:** This attribute represents concrete state on the target system.)_

Nagios configuration file parameter.

([??? Back to nagios_service attributes](#nagios_service-attributes))


<h3 id="nagios_service-providers">Providers</h3>

<h4 id="nagios_service-provider-naginator">naginator</h4>






> **NOTE:** This page was generated from the Puppet source code on 2016-01-15 16:31:56 +0100