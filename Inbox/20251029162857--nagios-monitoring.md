---
id: 20251029162857--nagios-monitoring
aliases:
  - Nagios Monitoring
tags:
  - area
  - joyent
area:
  - joyent
date: Wednesday October 29th 2025
---

# Nagios Monitoring

## Links

### Documentation

- [MAIN Wiki Page](https://wiki-joyent.atlassian.net/wiki/spaces/sysops/pages/31821695/Nagios)
- [State types  (HARD SOFT)](https://assets.nagios.com/downloads/nagioscore/docs/nagioscore/4/en/statetypes.html)
- [Host and Service Check Scheduling](https://assets.nagios.com/downloads/nagioscore/docs/nagioscore/4/en/checkscheduling.html)
- [Event Handlers](https://assets.nagios.com/downloads/nagioscore/docs/nagioscore/4/en/eventhandlers.html)
- [Core API via env external command](https://assets.nagios.com/downloads/nagioscore/docs/externalcmds/)
- [Plugin Dev Guidelines](https://nagios-plugins.org/doc/guidelines.html)
- [Macros Documentation](https://assets.nagios.com/downloads/nagioscore/docs/nagioscore/4/en/macrolist.html)
- [Custom object Variables](https://assets.nagios.com/downloads/nagioscore/docs/nagioscore/3/en/customobjectvars.html)
- [[id:88390c7d-d073-4e48-87bc-8253f5788d51][NCPA Agent]]
- [Nagios Playbook Confluence Link](https://wiki-joyent.atlassian.net/wiki/spaces/sysops/pages/146244914/Ansible+playbook+nagios.yml)
- [[id:022be17c-6f75-4b2d-90bf-98517474776f][NCPA Agent]]

- [[id:dced0aad-d053-4ff9-b49f-c538d35f3846][Zabbix rules to address with migration]]

### Service Definition

[Documentation Link Nagios](https://assets.nagios.com/downloads/nagioscore/docs/nagioscore/4/en/objectdefinitions.html#service)

# Service Group Definition

A service group definition is used to group one or more services together for simplifying configuration with object tricks or display purposes in the CGIs.

## Definition Format

\Note: Directives in red are required, while those in black are optional.

``` text
define servicegroup{
servicegroup_name servicegroup_name
alias alias
members services
servicegroup_members servicegroups
notes note_string
notes_url url
action_url url
   }
```

## Example Definition

``` text
define servicegroup{
  servicegroup_name  dbservices
  alias              Database Services
  members            ms1,SQL Server,ms1,SQL Server Agent,ms1,SQL DTC
}

```

## Directive Descriptions

- *servicegroup_name:* This directive is used to define a short name used to identify the service group.
- *alias*:  This directive is used to define is a longer name or description used to identify the service group. It is provided in order to allow you to more easily identify a particular service group.
- *members*: This is a list of the descriptions of services (and the names of their corresponding hosts) that should be included in this group. Host and service names should be separated by commas. This directive may be used as an alternative to the servicegroups directive in service definitions. The format of the member directive is as follows (note that a host name must precede a service name/description):
         members=<host1>,<service1>,<host2>,<service2>,...,<hostn>,<servicen>

- *servicegroup_members:*  This optional directive can be used to include services from other "sub" service groups in this service group. Specify a comma-delimited list of short names of other service groups whose members should be included in this group.
- *notes*: This directive is used to define an optional string of notes pertaining to the service group. If you specify a note here, you will see the it in the extended information CGI (when you are viewing information about the specified service group).
- *notes_url:*  This directive is used to define an optional URL that can be used to provide more information about the service group. If you specify an URL, you will see a red folder icon in the CGIs (when you are viewing service group information) that links to the URL you specify here. Any valid URL can be used. If you plan on using relative paths, the base path will the the same as what is used to access the CGIs (i.e. /cgi-bin/nagios/). This can be very useful if you want to make detailed information on the service group, emergency contact methods, etc. available to other support staff.
- *action_url:*  This directive is used to define an optional URL that can be used to provide more actions to be performed on the service group. If you specify an URL, you will see a red "splat" icon in the CGIs (when you are viewing service group information) that links to the URL you specify here. Any valid URL can be used. If you plan on using relative paths, the base path will the the same as what is used to access the CGIs (i.e. /cgi-bin/nagios/).
