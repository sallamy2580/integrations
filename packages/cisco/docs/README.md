# Cisco Integration (Deprecated)

> Warning: This integration is deprecated. Please use one of the other Cisco integrations
> that are specific to a Cisco product.

This integration is for [Cisco network devices](https://developer.cisco.com/docs/) logs. It includes the following datasets for receiving logs over syslog or read from a file:

- `asa` dataset: supports Cisco ASA firewall logs.
- `ftd` dataset: supports Cisco Firepower Threat Defense logs.
- `ios` dataset: supports Cisco IOS router and switch logs.
- `nexus` fileset: supports Cisco Nexus switch logs.
- `meraki` dataset: supports Cisco Meraki logs.

## Compatibility

## Logs

### ASA

The `asa` dataset collects the Cisco firewall logs.

An example event for `asa` looks as following:

```json
{
    "@timestamp": "2018-10-10T12:34:56.000Z",
    "agent": {
        "ephemeral_id": "a548620b-0623-4130-b586-fe233f00e6e5",
        "hostname": "docker-fleet-agent",
        "id": "3c803d12-46a2-48a4-a206-8fd3630cc2a9",
        "name": "docker-fleet-agent",
        "type": "filebeat",
        "version": "7.14.0"
    },
    "cisco": {
        "asa": {
            "destination_interface": "outside",
            "source_interface": "inside"
        }
    },
    "data_stream": {
        "dataset": "cisco.asa",
        "namespace": "ep",
        "type": "logs"
    },
    "destination": {
        "address": "100.66.98.44",
        "ip": "100.66.98.44",
        "port": 8256
    },
    "ecs": {
        "version": "1.10.0"
    },
    "elastic_agent": {
        "id": "3c803d12-46a2-48a4-a206-8fd3630cc2a9",
        "snapshot": true,
        "version": "7.14.0"
    },
    "event": {
        "action": "firewall-rule",
        "agent_id_status": "verified",
        "category": [
            "network"
        ],
        "code": "305011",
        "dataset": "cisco.asa",
        "ingested": "2021-07-19T08:54:36.436846422Z",
        "kind": "event",
        "original": "Oct 10 2018 12:34:56 localhost CiscoASA[999]: %ASA-6-305011: Built dynamic TCP translation from inside:172.31.98.44/1772 to outside:100.66.98.44/8256\n",
        "severity": 6,
        "timezone": "+00:00",
        "type": [
            "info"
        ]
    },
    "host": {
        "hostname": "localhost",
        "name": "docker-fleet-agent"
    },
    "input": {
        "type": "udp"
    },
    "log": {
        "level": "informational",
        "source": {
            "address": "172.23.0.4:59451"
        }
    },
    "network": {
        "iana_number": "6",
        "transport": "tcp"
    },
    "observer": {
        "egress": {
            "interface": {
                "name": "outside"
            }
        },
        "hostname": "localhost",
        "ingress": {
            "interface": {
                "name": "inside"
            }
        },
        "product": "asa",
        "type": "firewall",
        "vendor": "Cisco"
    },
    "process": {
        "name": "CiscoASA",
        "pid": 999
    },
    "related": {
        "hosts": [
            "localhost"
        ],
        "ip": [
            "172.31.98.44",
            "100.66.98.44"
        ]
    },
    "source": {
        "address": "172.31.98.44",
        "ip": "172.31.98.44",
        "port": 1772
    },
    "tags": [
        "preserve_original_event",
        "cisco-asa",
        "forwarded"
    ]
}
```

**Exported fields**

| Field | Description | Type |
|---|---|---|
| @timestamp | Event timestamp. | date |
| cisco.asa.assigned_ip | The IP address assigned to a VPN client successfully connecting | ip |
| cisco.asa.burst.avg_rate | The current average burst rate seen | keyword |
| cisco.asa.burst.configured_avg_rate | The current configured average burst rate allowed | keyword |
| cisco.asa.burst.configured_rate | The current configured burst rate | keyword |
| cisco.asa.burst.cumulative_count | The total count of burst rate hits since the object was created or cleared | keyword |
| cisco.asa.burst.current_rate | The current burst rate seen | keyword |
| cisco.asa.burst.id | The related rate ID for burst warnings | keyword |
| cisco.asa.burst.object | The related object for burst warnings | keyword |
| cisco.asa.command_line_arguments | The command line arguments logged by the local audit log | keyword |
| cisco.asa.connection_id | Unique identifier for a flow. | keyword |
| cisco.asa.connection_type | The VPN connection type | keyword |
| cisco.asa.dap_records | The assigned DAP records | keyword |
| cisco.asa.destination_interface | Destination interface for the flow or event. | keyword |
| cisco.asa.destination_username | Name of the user that is the destination for this event. | keyword |
| cisco.asa.icmp_code | ICMP code. | short |
| cisco.asa.icmp_type | ICMP type. | short |
| cisco.asa.mapped_destination_host |  | keyword |
| cisco.asa.mapped_destination_ip | The translated destination IP address. | ip |
| cisco.asa.mapped_destination_port | The translated destination port. | long |
| cisco.asa.mapped_source_host |  | keyword |
| cisco.asa.mapped_source_ip | The translated source IP address. | ip |
| cisco.asa.mapped_source_port | The translated source port. | long |
| cisco.asa.message_id | The Cisco ASA message identifier. | keyword |
| cisco.asa.privilege.new | When a users privilege is changed this is the new value | keyword |
| cisco.asa.privilege.old | When a users privilege is changed this is the old value | keyword |
| cisco.asa.rule_name | Name of the Access Control List rule that matched this event. | keyword |
| cisco.asa.security | Cisco FTD security event fields. | flattened |
| cisco.asa.source_interface | Source interface for the flow or event. | keyword |
| cisco.asa.source_username | Name of the user that is the source for this event. | keyword |
| cisco.asa.suffix | Optional suffix after %ASA identifier. | keyword |
| cisco.asa.termination_user | AAA name of user requesting termination | keyword |
| cisco.asa.threat_category | Category for the malware / botnet traffic. For example: virus, botnet, trojan, etc. | keyword |
| cisco.asa.threat_level | Threat level for malware / botnet traffic. One of very-low, low, moderate, high or very-high. | keyword |
| cisco.asa.username |  | keyword |
| cisco.asa.webvpn.group_name | The WebVPN group name the user belongs to | keyword |
| client.address | Some event client addresses are defined ambiguously. The event will sometimes list an IP, a domain or a unix socket.  You should always store the raw address in the `.address` field. Then it should be duplicated to `.ip` or `.domain`, depending on which one it is. | keyword |
| client.domain | The domain name of the client system. This value may be a host name, a fully qualified domain name, or another host naming format. The value may derive from the original event or be added from enrichment. | keyword |
| client.ip | IP address of the client (IPv4 or IPv6). | ip |
| client.port | Port of the client. | long |
| client.user.name | Short name or login of the user. | keyword |
| client.user.name.text | Multi-field of `client.user.name`. | match_only_text |
| cloud.account.id | The cloud account or organization id used to identify different entities in a multi-tenant environment. Examples: AWS account id, Google Cloud ORG Id, or other unique identifier. | keyword |
| cloud.availability_zone | Availability zone in which this host is running. | keyword |
| cloud.image.id | Image ID for the cloud instance. | keyword |
| cloud.instance.id | Instance ID of the host machine. | keyword |
| cloud.instance.name | Instance name of the host machine. | keyword |
| cloud.machine.type | Machine type of the host machine. | keyword |
| cloud.project.id | Name of the project in Google Cloud. | keyword |
| cloud.provider | Name of the cloud provider. Example values are aws, azure, gcp, or digitalocean. | keyword |
| cloud.region | Region in which this host is running. | keyword |
| container.id | Unique container id. | keyword |
| container.image.name | Name of the image the container was built on. | keyword |
| container.labels | Image labels. | object |
| container.name | Container name. | keyword |
| data_stream.dataset | Data stream dataset. | constant_keyword |
| data_stream.namespace | Data stream namespace. | constant_keyword |
| data_stream.type | Data stream type. | constant_keyword |
| destination.address | Some event destination addresses are defined ambiguously. The event will sometimes list an IP, a domain or a unix socket.  You should always store the raw address in the `.address` field. Then it should be duplicated to `.ip` or `.domain`, depending on which one it is. | keyword |
| destination.as.number | Unique number allocated to the autonomous system. The autonomous system number (ASN) uniquely identifies each network on the Internet. | long |
| destination.as.organization.name | Organization name. | keyword |
| destination.as.organization.name.text | Multi-field of `destination.as.organization.name`. | match_only_text |
| destination.bytes | Bytes sent from the destination to the source. | long |
| destination.domain | The domain name of the destination system. This value may be a host name, a fully qualified domain name, or another host naming format. The value may derive from the original event or be added from enrichment. | keyword |
| destination.geo.city_name | City name. | keyword |
| destination.geo.continent_name | Name of the continent. | keyword |
| destination.geo.country_iso_code | Country ISO code. | keyword |
| destination.geo.country_name | Country name. | keyword |
| destination.geo.location | Longitude and latitude. | geo_point |
| destination.geo.region_iso_code | Region ISO code. | keyword |
| destination.geo.region_name | Region name. | keyword |
| destination.ip | IP address of the destination (IPv4 or IPv6). | ip |
| destination.nat.ip | Translated ip of destination based NAT sessions (e.g. internet to private DMZ) Typically used with load balancers, firewalls, or routers. | ip |
| destination.nat.port | Port the source session is translated to by NAT Device. Typically used with load balancers, firewalls, or routers. | long |
| destination.port | Port of the destination. | long |
| destination.user.name | Short name or login of the user. | keyword |
| destination.user.name.text | Multi-field of `destination.user.name`. | match_only_text |
| ecs.version | ECS version this event conforms to. `ecs.version` is a required field and must exist in all events. When querying across multiple indices -- which may conform to slightly different ECS versions -- this field lets integrations adjust to the schema version of the events. | keyword |
| error.message | Error message. | match_only_text |
| event.category | This is one of four ECS Categorization Fields, and indicates the second level in the ECS category hierarchy. `event.category` represents the "big buckets" of ECS categories. For example, filtering on `event.category:process` yields all events relating to process activity. This field is closely related to `event.type`, which is used as a subcategory. This field is an array. This will allow proper categorization of some events that fall in multiple categories. | keyword |
| event.code | Identification code for this event, if one exists. Some event sources use event codes to identify messages unambiguously, regardless of message language or wording adjustments over time. An example of this is the Windows Event ID. | keyword |
| event.created | event.created contains the date/time when the event was first read by an agent, or by your pipeline. This field is distinct from @timestamp in that @timestamp typically contain the time extracted from the original event. In most situations, these two timestamps will be slightly different. The difference can be used to calculate the delay between your source generating an event, and the time when your agent first processed it. This can be used to monitor your agent's or pipeline's ability to keep up with your event source. In case the two timestamps are identical, @timestamp should be used. | date |
| event.dataset | Event dataset | constant_keyword |
| event.duration | Duration of the event in nanoseconds. If event.start and event.end are known this value should be the difference between the end and start time. | long |
| event.end | event.end contains the date when the event ended or when the activity was last observed. | date |
| event.ingested | Timestamp when an event arrived in the central data store. This is different from `@timestamp`, which is when the event originally occurred.  It's also different from `event.created`, which is meant to capture the first time an agent saw the event. In normal conditions, assuming no tampering, the timestamps should chronologically look like this: `@timestamp` \< `event.created` \< `event.ingested`. | date |
| event.kind | This is one of four ECS Categorization Fields, and indicates the highest level in the ECS category hierarchy. `event.kind` gives high-level information about what type of information the event contains, without being specific to the contents of the event. For example, values of this field distinguish alert events from metric events. The value of this field can be used to inform how these kinds of events should be handled. They may warrant different retention, different access control, it may also help understand whether the data coming in at a regular interval or not. | keyword |
| event.module | Event module | constant_keyword |
| event.provider | Source of the event. Event transports such as Syslog or the Windows Event Log typically mention the source of an event. It can be the name of the software that generated the event (e.g. Sysmon, httpd), or of a subsystem of the operating system (kernel, Microsoft-Windows-Security-Auditing). | keyword |
| event.severity | The numeric severity of the event according to your event source. What the different severity values mean can be different between sources and use cases. It's up to the implementer to make sure severities are consistent across events from the same source. The Syslog severity belongs in `log.syslog.severity.code`. `event.severity` is meant to represent the severity according to the event source (e.g. firewall, IDS). If the event source does not publish its own severity, you may optionally copy the `log.syslog.severity.code` to `event.severity`. | long |
| event.start | event.start contains the date when the event started or when the activity was first observed. | date |
| event.timezone | This field should be populated when the event's timestamp does not include timezone information already (e.g. default Syslog timestamps). It's optional otherwise. Acceptable timezone formats are: a canonical ID (e.g. "Europe/Amsterdam"), abbreviated (e.g. "EST") or an HH:mm differential (e.g. "-05:00"). | keyword |
| event.type | This is one of four ECS Categorization Fields, and indicates the third level in the ECS category hierarchy. `event.type` represents a categorization "sub-bucket" that, when used along with the `event.category` field values, enables filtering events down to a level appropriate for single visualization. This field is an array. This will allow proper categorization of some events that fall in multiple event types. | keyword |
| file.path | Full path to the file, including the file name. It should include the drive letter, when appropriate. | keyword |
| file.path.text | Multi-field of `file.path`. | match_only_text |
| host.architecture | Operating system architecture. | keyword |
| host.containerized | If the host is a container. | boolean |
| host.domain | Name of the domain of which the host is a member. For example, on Windows this could be the host's Active Directory domain or NetBIOS domain name. For Linux this could be the domain of the host's LDAP provider. | keyword |
| host.hostname | Hostname of the host. It normally contains what the `hostname` command returns on the host machine. | keyword |
| host.id | Unique host id. As hostname is not always unique, use values that are meaningful in your environment. Example: The current usage of `beat.name`. | keyword |
| host.ip | Host ip addresses. | ip |
| host.mac | Host mac addresses. | keyword |
| host.name | Name of the host. It can contain what `hostname` returns on Unix systems, the fully qualified domain name, or a name specified by the user. The sender decides which value to use. | keyword |
| host.os.build | OS build information. | keyword |
| host.os.codename | OS codename, if any. | keyword |
| host.os.family | OS family (such as redhat, debian, freebsd, windows). | keyword |
| host.os.kernel | Operating system kernel version as a raw string. | keyword |
| host.os.name | Operating system name, without the version. | keyword |
| host.os.name.text | Multi-field of `host.os.name`. | text |
| host.os.platform | Operating system platform (such centos, ubuntu, windows). | keyword |
| host.os.version | Operating system version as a raw string. | keyword |
| host.type | Type of host. For Cloud providers this can be the machine type like `t2.medium`. If vm, this could be the container, for example, or other information meaningful in your environment. | keyword |
| input.type | Input type. | keyword |
| labels | Custom key/value pairs. Can be used to add meta information to events. Should not contain nested objects. All values are stored as keyword. Example: `docker` and `k8s` labels. | object |
| log.file.path | Full path to the log file this event came from, including the file name. It should include the drive letter, when appropriate. If the event wasn't read from a log file, do not populate this field. | keyword |
| log.level | Original log level of the log event. If the source of the event provides a log level or textual severity, this is the one that goes in `log.level`. If your source doesn't specify one, you may put your event transport's severity here (e.g. Syslog severity). Some examples are `warn`, `err`, `i`, `informational`. | keyword |
| log.offset | Offset of the entry in the log file. | long |
| log.source.address | Source address from which the log event was read / sent from. | keyword |
| message | For log events the message field contains the log message, optimized for viewing in a log viewer. For structured logs without an original message field, other fields can be concatenated to form a human-readable summary of the event. If multiple messages exist, they can be combined into one message. | match_only_text |
| network.bytes | Total bytes transferred in both directions. If `source.bytes` and `destination.bytes` are known, `network.bytes` is their sum. | long |
| network.direction | Direction of the network traffic. Recommended values are:   \* ingress   \* egress   \* inbound   \* outbound   \* internal   \* external   \* unknown  When mapping events from a host-based monitoring context, populate this field from the host's point of view, using the values "ingress" or "egress". When mapping events from a network or perimeter-based monitoring context, populate this field from the point of view of the network perimeter, using the values "inbound", "outbound", "internal" or "external". Note that "internal" is not crossing perimeter boundaries, and is meant to describe communication between two hosts within the perimeter. Note also that "external" is meant to describe traffic between two hosts that are external to the perimeter. This could for example be useful for ISPs or VPN service providers. | keyword |
| network.iana_number | IANA Protocol Number (https://www.iana.org/assignments/protocol-numbers/protocol-numbers.xhtml). Standardized list of protocols. This aligns well with NetFlow and sFlow related logs which use the IANA Protocol Number. | keyword |
| network.inner | Network.inner fields are added in addition to network.vlan fields to describe the innermost VLAN when q-in-q VLAN tagging is present. Allowed fields include vlan.id and vlan.name. Inner vlan fields are typically used when sending traffic with multiple 802.1q encapsulations to a network sensor (e.g. Zeek, Wireshark.) | object |
| network.inner.vlan.id | VLAN ID as reported by the observer. | keyword |
| network.inner.vlan.name | Optional VLAN name as reported by the observer. | keyword |
| network.protocol | In the OSI Model this would be the Application Layer protocol. For example, `http`, `dns`, or `ssh`. The field value must be normalized to lowercase for querying. | keyword |
| network.transport | Same as network.iana_number, but instead using the Keyword name of the transport layer (udp, tcp, ipv6-icmp, etc.) The field value must be normalized to lowercase for querying. | keyword |
| network.type | In the OSI Model this would be the Network Layer. ipv4, ipv6, ipsec, pim, etc The field value must be normalized to lowercase for querying. | keyword |
| observer.egress.interface.name | Interface name as reported by the system. | keyword |
| observer.egress.zone | Network zone of outbound traffic as reported by the observer to categorize the destination area of egress traffic, e.g. Internal, External, DMZ, HR, Legal, etc. | keyword |
| observer.hostname | Hostname of the observer. | keyword |
| observer.ingress.interface.name | Interface name as reported by the system. | keyword |
| observer.ingress.zone | Network zone of incoming traffic as reported by the observer to categorize the source area of ingress traffic. e.g. internal, External, DMZ, HR, Legal, etc. | keyword |
| observer.ip | IP addresses of the observer. | ip |
| observer.name | Custom name of the observer. This is a name that can be given to an observer. This can be helpful for example if multiple firewalls of the same model are used in an organization. If no custom name is needed, the field can be left empty. | keyword |
| observer.product | The product name of the observer. | keyword |
| observer.type | The type of the observer the data is coming from. There is no predefined list of observer types. Some examples are `forwarder`, `firewall`, `ids`, `ips`, `proxy`, `poller`, `sensor`, `APM server`. | keyword |
| observer.vendor | Vendor name of the observer. | keyword |
| observer.version | Observer version. | keyword |
| process.name | Process name. Sometimes called program name or similar. | keyword |
| process.name.text | Multi-field of `process.name`. | match_only_text |
| process.pid | Process id. | long |
| related.hosts | All hostnames or other host identifiers seen on your event. Example identifiers include FQDNs, domain names, workstation names, or aliases. | keyword |
| related.ip | All of the IPs seen on your event. | ip |
| related.user | All the user names or other user identifiers seen on the event. | keyword |
| server.address | Some event server addresses are defined ambiguously. The event will sometimes list an IP, a domain or a unix socket.  You should always store the raw address in the `.address` field. Then it should be duplicated to `.ip` or `.domain`, depending on which one it is. | keyword |
| server.domain | The domain name of the server system. This value may be a host name, a fully qualified domain name, or another host naming format. The value may derive from the original event or be added from enrichment. | keyword |
| server.ip | IP address of the server (IPv4 or IPv6). | ip |
| server.port | Port of the server. | long |
| source.address | Some event source addresses are defined ambiguously. The event will sometimes list an IP, a domain or a unix socket.  You should always store the raw address in the `.address` field. Then it should be duplicated to `.ip` or `.domain`, depending on which one it is. | keyword |
| source.as.number | Unique number allocated to the autonomous system. The autonomous system number (ASN) uniquely identifies each network on the Internet. | long |
| source.as.organization.name | Organization name. | keyword |
| source.as.organization.name.text | Multi-field of `source.as.organization.name`. | match_only_text |
| source.bytes | Bytes sent from the source to the destination. | long |
| source.domain | The domain name of the source system. This value may be a host name, a fully qualified domain name, or another host naming format. The value may derive from the original event or be added from enrichment. | keyword |
| source.geo.city_name | City name. | keyword |
| source.geo.continent_name | Name of the continent. | keyword |
| source.geo.country_iso_code | Country ISO code. | keyword |
| source.geo.country_name | Country name. | keyword |
| source.geo.location | Longitude and latitude. | geo_point |
| source.geo.region_iso_code | Region ISO code. | keyword |
| source.geo.region_name | Region name. | keyword |
| source.ip | IP address of the source (IPv4 or IPv6). | ip |
| source.nat.ip | Translated ip of source based NAT sessions (e.g. internal client to internet) Typically connections traversing load balancers, firewalls, or routers. | ip |
| source.nat.port | Translated port of source based NAT sessions. (e.g. internal client to internet) Typically used with load balancers, firewalls, or routers. | long |
| source.port | Port of the source. | long |
| source.user.name | Short name or login of the user. | keyword |
| source.user.name.text | Multi-field of `source.user.name`. | match_only_text |
| syslog.facility.code | Syslog numeric facility of the event. | long |
| syslog.priority | Syslog priority of the event. | long |
| tags | List of keywords used to tag each event. | keyword |
| url.domain | Domain of the url, such as "www.elastic.co". In some cases a URL may refer to an IP and/or port directly, without a domain name. In this case, the IP address would go to the `domain` field. If the URL contains a literal IPv6 address enclosed by `[` and `]` (IETF RFC 2732), the `[` and `]` characters should also be captured in the `domain` field. | keyword |
| url.extension | The field contains the file extension from the original request url, excluding the leading dot. The file extension is only set if it exists, as not every url has a file extension. The leading period must not be included. For example, the value must be "png", not ".png". Note that when the file name has multiple extensions (example.tar.gz), only the last one should be captured ("gz", not "tar.gz"). | keyword |
| url.fragment | Portion of the url after the `#`, such as "top". The `#` is not part of the fragment. | keyword |
| url.full | If full URLs are important to your use case, they should be stored in `url.full`, whether this field is reconstructed or present in the event source. | wildcard |
| url.full.text | Multi-field of `url.full`. | match_only_text |
| url.original | Unmodified original url as seen in the event source. Note that in network monitoring, the observed URL may be a full URL, whereas in access logs, the URL is often just represented as a path. This field is meant to represent the URL as it was observed, complete or not. | wildcard |
| url.original.text | Multi-field of `url.original`. | match_only_text |
| url.password | Password of the request. | keyword |
| url.path | Path of the request, such as "/search". | wildcard |
| url.port | Port of the request, such as 443. | long |
| url.query | The query field describes the query string of the request, such as "q=elasticsearch". The `?` is excluded from the query string. If a URL contains no `?`, there is no query field. If there is a `?` but no query, the query field exists with an empty string. The `exists` query can be used to differentiate between the two cases. | keyword |
| url.registered_domain | The highest registered url domain, stripped of the subdomain. For example, the registered domain for "foo.example.com" is "example.com". This value can be determined precisely with a list like the public suffix list (http://publicsuffix.org). Trying to approximate this by simply taking the last two labels will not work well for TLDs such as "co.uk". | keyword |
| url.scheme | Scheme of the request, such as "https". Note: The `:` is not part of the scheme. | keyword |
| url.subdomain | The subdomain portion of a fully qualified domain name includes all of the names except the host name under the registered_domain.  In a partially qualified domain, or if the the qualification level of the full name cannot be determined, subdomain contains all of the names below the registered domain. For example the subdomain portion of "www.east.mydomain.co.uk" is "east". If the domain has multiple levels of subdomain, such as "sub2.sub1.example.com", the subdomain field should contain "sub2.sub1", with no trailing period. | keyword |
| url.top_level_domain | The effective top level domain (eTLD), also known as the domain suffix, is the last part of the domain name. For example, the top level domain for example.com is "com". This value can be determined precisely with a list like the public suffix list (http://publicsuffix.org). Trying to approximate this by simply taking the last label will not work well for effective TLDs such as "co.uk". | keyword |
| url.username | Username of the request. | keyword |
| user.email | User email address. | keyword |
| user.name | Short name or login of the user. | keyword |
| user.name.text | Multi-field of `user.name`. | match_only_text |


### FTD

The `ftd` dataset collects the Firepower Threat Defense logs.

An example event for `ftd` looks as following:

```json
{
    "@timestamp": "2019-08-16T09:39:03.000Z",
    "agent": {
        "ephemeral_id": "915b9d78-907c-4615-90f8-e2997777f537",
        "hostname": "docker-fleet-agent",
        "id": "3c803d12-46a2-48a4-a206-8fd3630cc2a9",
        "name": "docker-fleet-agent",
        "type": "filebeat",
        "version": "7.14.0"
    },
    "cisco": {
        "ftd": {
            "rule_name": "malware-and-file-policy",
            "security": {
                "application_protocol": "HTTP",
                "client": "cURL",
                "dst_ip": "213.211.198.62",
                "dst_port": "80",
                "file_action": "Malware Cloud Lookup",
                "file_direction": "Download",
                "file_name": "eicar_com.zip",
                "file_policy": "malware-and-file-policy",
                "file_sandbox_status": "File Size Is Too Small",
                "file_sha256": "2546dcffc5ad854d4ddc64fbf056871cd5a00f2471cb7a5bfd4ac23b6e9eedad",
                "file_size": "184",
                "file_storage_status": "Not Stored (Disposition Was Pending)",
                "file_type": "ZIP",
                "first_packet_second": "2019-08-16T09:39:02Z",
                "protocol": "tcp",
                "sha_disposition": "Unavailable",
                "spero_disposition": "Spero detection not performed on file",
                "src_ip": "10.0.1.20",
                "src_port": "46004",
                "threat_name": "Win.Ransomware.Eicar::95.sbx.tg",
                "uri": "http://www.eicar.org/download/eicar_com.zip",
                "user": "No Authentication Required"
            },
            "threat_category": "Win.Ransomware.Eicar::95.sbx.tg"
        }
    },
    "data_stream": {
        "dataset": "cisco.ftd",
        "namespace": "ep",
        "type": "logs"
    },
    "destination": {
        "address": "213.211.198.62",
        "as": {
            "number": 43341,
            "organization": {
                "name": "MDlink online service center GmbH"
            }
        },
        "geo": {
            "city_name": "Magdeburg",
            "continent_name": "Europe",
            "country_iso_code": "DE",
            "country_name": "Germany",
            "location": {
                "lat": 52.1333,
                "lon": 11.6167
            },
            "region_iso_code": "DE-ST",
            "region_name": "Saxony-Anhalt"
        },
        "ip": "213.211.198.62",
        "port": 80
    },
    "ecs": {
        "version": "1.10.0"
    },
    "elastic_agent": {
        "id": "3c803d12-46a2-48a4-a206-8fd3630cc2a9",
        "snapshot": true,
        "version": "7.14.0"
    },
    "event": {
        "action": "malware-detected",
        "agent_id_status": "verified",
        "category": [
            "malware"
        ],
        "code": "430005",
        "dataset": "cisco.ftd",
        "ingested": "2021-07-19T08:56:32.448763106Z",
        "kind": "alert",
        "original": "2019-08-16T09:39:03Z firepower  %FTD-1-430005: SrcIP: 10.0.1.20, DstIP: 213.211.198.62, SrcPort: 46004, DstPort: 80, Protocol: tcp, FileDirection: Download, FileAction: Malware Cloud Lookup, FileSHA256: 2546dcffc5ad854d4ddc64fbf056871cd5a00f2471cb7a5bfd4ac23b6e9eedad, SHA_Disposition: Unavailable, SperoDisposition: Spero detection not performed on file, ThreatName: Win.Ransomware.Eicar::95.sbx.tg, FileName: eicar_com.zip, FileType: ZIP, FileSize: 184, ApplicationProtocol: HTTP, Client: cURL, User: No Authentication Required, FirstPacketSecond: 2019-08-16T09:39:02Z, FilePolicy: malware-and-file-policy, FileStorageStatus: Not Stored (Disposition Was Pending), FileSandboxStatus: File Size Is Too Small, URI: http://www.eicar.org/download/eicar_com.zip\n",
        "severity": 1,
        "start": "2019-08-16T09:39:02Z",
        "timezone": "+00:00",
        "type": [
            "info"
        ]
    },
    "file": {
        "hash": {
            "sha256": "2546dcffc5ad854d4ddc64fbf056871cd5a00f2471cb7a5bfd4ac23b6e9eedad"
        },
        "name": "eicar_com.zip",
        "size": 184
    },
    "host": {
        "hostname": "firepower",
        "name": "docker-fleet-agent"
    },
    "input": {
        "type": "udp"
    },
    "log": {
        "level": "alert",
        "source": {
            "address": "172.23.0.4:41328"
        }
    },
    "network": {
        "application": "curl",
        "iana_number": "6",
        "protocol": "http",
        "transport": "tcp"
    },
    "observer": {
        "hostname": "firepower",
        "product": "asa",
        "type": "firewall",
        "vendor": "Cisco"
    },
    "related": {
        "hash": [
            "2546dcffc5ad854d4ddc64fbf056871cd5a00f2471cb7a5bfd4ac23b6e9eedad"
        ],
        "hosts": [
            "firepower"
        ],
        "ip": [
            "10.0.1.20",
            "213.211.198.62"
        ],
        "user": [
            "No Authentication Required"
        ]
    },
    "source": {
        "address": "10.0.1.20",
        "ip": "10.0.1.20",
        "port": 46004
    },
    "tags": [
        "preserve_original_event",
        "cisco-ftd",
        "forwarded"
    ],
    "url": {
        "domain": "www.eicar.org",
        "extension": "zip",
        "original": "http://www.eicar.org/download/eicar_com.zip",
        "path": "/download/eicar_com.zip",
        "scheme": "http"
    },
    "user": {
        "id": "No Authentication Required",
        "name": "No Authentication Required"
    }
}
```

**Exported fields**

| Field | Description | Type |
|---|---|---|
| @timestamp | Event timestamp. | date |
| cisco.ftd.assigned_ip | The IP address assigned to a VPN client successfully connecting | ip |
| cisco.ftd.burst.avg_rate | The current average burst rate seen | keyword |
| cisco.ftd.burst.configured_avg_rate | The current configured average burst rate allowed | keyword |
| cisco.ftd.burst.configured_rate | The current configured burst rate | keyword |
| cisco.ftd.burst.cumulative_count | The total count of burst rate hits since the object was created or cleared | keyword |
| cisco.ftd.burst.current_rate | The current burst rate seen | keyword |
| cisco.ftd.burst.id | The related rate ID for burst warnings | keyword |
| cisco.ftd.burst.object | The related object for burst warnings | keyword |
| cisco.ftd.command_line_arguments | The command line arguments logged by the local audit log | keyword |
| cisco.ftd.connection_id | Unique identifier for a flow. | keyword |
| cisco.ftd.connection_type | The VPN connection type | keyword |
| cisco.ftd.dap_records | The assigned DAP records | keyword |
| cisco.ftd.destination_interface | Destination interface for the flow or event. | keyword |
| cisco.ftd.destination_username | Name of the user that is the destination for this event. | keyword |
| cisco.ftd.icmp_code | ICMP code. | short |
| cisco.ftd.icmp_type | ICMP type. | short |
| cisco.ftd.mapped_destination_host |  | keyword |
| cisco.ftd.mapped_destination_ip | The translated destination IP address. | ip |
| cisco.ftd.mapped_destination_port | The translated destination port. | long |
| cisco.ftd.mapped_source_host |  | keyword |
| cisco.ftd.mapped_source_ip | The translated source IP address. | ip |
| cisco.ftd.mapped_source_port | The translated source port. | long |
| cisco.ftd.message_id | The Cisco FTD message identifier. | keyword |
| cisco.ftd.privilege.new | When a users privilege is changed this is the new value | keyword |
| cisco.ftd.privilege.old | When a users privilege is changed this is the old value | keyword |
| cisco.ftd.rule_name | Name of the Access Control List rule that matched this event. | keyword |
| cisco.ftd.security | Cisco FTD security event fields. | flattened |
| cisco.ftd.source_interface | Source interface for the flow or event. | keyword |
| cisco.ftd.source_username | Name of the user that is the source for this event. | keyword |
| cisco.ftd.suffix | Optional suffix after %FTD identifier. | keyword |
| cisco.ftd.termination_user | AAA name of user requesting termination | keyword |
| cisco.ftd.threat_category | Category for the malware / botnet traffic. For example: virus, botnet, trojan, etc. | keyword |
| cisco.ftd.threat_level | Threat level for malware / botnet traffic. One of very-low, low, moderate, high or very-high. | keyword |
| cisco.ftd.username |  | keyword |
| cisco.ftd.webvpn.group_name | The WebVPN group name the user belongs to | keyword |
| client.address | Some event client addresses are defined ambiguously. The event will sometimes list an IP, a domain or a unix socket.  You should always store the raw address in the `.address` field. Then it should be duplicated to `.ip` or `.domain`, depending on which one it is. | keyword |
| client.domain | The domain name of the client system. This value may be a host name, a fully qualified domain name, or another host naming format. The value may derive from the original event or be added from enrichment. | keyword |
| client.ip | IP address of the client (IPv4 or IPv6). | ip |
| client.port | Port of the client. | long |
| client.user.name | Short name or login of the user. | keyword |
| client.user.name.text | Multi-field of `client.user.name`. | match_only_text |
| cloud.account.id | The cloud account or organization id used to identify different entities in a multi-tenant environment. Examples: AWS account id, Google Cloud ORG Id, or other unique identifier. | keyword |
| cloud.availability_zone | Availability zone in which this host is running. | keyword |
| cloud.image.id | Image ID for the cloud instance. | keyword |
| cloud.instance.id | Instance ID of the host machine. | keyword |
| cloud.instance.name | Instance name of the host machine. | keyword |
| cloud.machine.type | Machine type of the host machine. | keyword |
| cloud.project.id | Name of the project in Google Cloud. | keyword |
| cloud.provider | Name of the cloud provider. Example values are aws, azure, gcp, or digitalocean. | keyword |
| cloud.region | Region in which this host is running. | keyword |
| container.id | Unique container id. | keyword |
| container.image.name | Name of the image the container was built on. | keyword |
| container.labels | Image labels. | object |
| container.name | Container name. | keyword |
| data_stream.dataset | Data stream dataset. | constant_keyword |
| data_stream.namespace | Data stream namespace. | constant_keyword |
| data_stream.type | Data stream type. | constant_keyword |
| destination.address | Some event destination addresses are defined ambiguously. The event will sometimes list an IP, a domain or a unix socket.  You should always store the raw address in the `.address` field. Then it should be duplicated to `.ip` or `.domain`, depending on which one it is. | keyword |
| destination.as.number | Unique number allocated to the autonomous system. The autonomous system number (ASN) uniquely identifies each network on the Internet. | long |
| destination.as.organization.name | Organization name. | keyword |
| destination.as.organization.name.text | Multi-field of `destination.as.organization.name`. | match_only_text |
| destination.bytes | Bytes sent from the destination to the source. | long |
| destination.domain | The domain name of the destination system. This value may be a host name, a fully qualified domain name, or another host naming format. The value may derive from the original event or be added from enrichment. | keyword |
| destination.geo.city_name | City name. | keyword |
| destination.geo.continent_name | Name of the continent. | keyword |
| destination.geo.country_iso_code | Country ISO code. | keyword |
| destination.geo.country_name | Country name. | keyword |
| destination.geo.location | Longitude and latitude. | geo_point |
| destination.geo.region_iso_code | Region ISO code. | keyword |
| destination.geo.region_name | Region name. | keyword |
| destination.ip | IP address of the destination (IPv4 or IPv6). | ip |
| destination.nat.ip | Translated ip of destination based NAT sessions (e.g. internet to private DMZ) Typically used with load balancers, firewalls, or routers. | ip |
| destination.nat.port | Port the source session is translated to by NAT Device. Typically used with load balancers, firewalls, or routers. | long |
| destination.packets | Packets sent from the destination to the source. | long |
| destination.port | Port of the destination. | long |
| destination.user.name | Short name or login of the user. | keyword |
| destination.user.name.text | Multi-field of `destination.user.name`. | match_only_text |
| dns.question.name | The name being queried. If the name field contains non-printable characters (below 32 or above 126), those characters should be represented as escaped base 10 integers (\DDD). Back slashes and quotes should be escaped. Tabs, carriage returns, and line feeds should be converted to \t, \r, and \n respectively. | keyword |
| dns.question.type | The type of record being queried. | keyword |
| dns.response_code | The DNS response code. | keyword |
| ecs.version | ECS version this event conforms to. `ecs.version` is a required field and must exist in all events. When querying across multiple indices -- which may conform to slightly different ECS versions -- this field lets integrations adjust to the schema version of the events. | keyword |
| error.message | Error message. | match_only_text |
| event.category | This is one of four ECS Categorization Fields, and indicates the second level in the ECS category hierarchy. `event.category` represents the "big buckets" of ECS categories. For example, filtering on `event.category:process` yields all events relating to process activity. This field is closely related to `event.type`, which is used as a subcategory. This field is an array. This will allow proper categorization of some events that fall in multiple categories. | keyword |
| event.code | Identification code for this event, if one exists. Some event sources use event codes to identify messages unambiguously, regardless of message language or wording adjustments over time. An example of this is the Windows Event ID. | keyword |
| event.created | event.created contains the date/time when the event was first read by an agent, or by your pipeline. This field is distinct from @timestamp in that @timestamp typically contain the time extracted from the original event. In most situations, these two timestamps will be slightly different. The difference can be used to calculate the delay between your source generating an event, and the time when your agent first processed it. This can be used to monitor your agent's or pipeline's ability to keep up with your event source. In case the two timestamps are identical, @timestamp should be used. | date |
| event.dataset | Event dataset | constant_keyword |
| event.duration | Duration of the event in nanoseconds. If event.start and event.end are known this value should be the difference between the end and start time. | long |
| event.end | event.end contains the date when the event ended or when the activity was last observed. | date |
| event.ingested | Timestamp when an event arrived in the central data store. This is different from `@timestamp`, which is when the event originally occurred.  It's also different from `event.created`, which is meant to capture the first time an agent saw the event. In normal conditions, assuming no tampering, the timestamps should chronologically look like this: `@timestamp` \< `event.created` \< `event.ingested`. | date |
| event.kind | This is one of four ECS Categorization Fields, and indicates the highest level in the ECS category hierarchy. `event.kind` gives high-level information about what type of information the event contains, without being specific to the contents of the event. For example, values of this field distinguish alert events from metric events. The value of this field can be used to inform how these kinds of events should be handled. They may warrant different retention, different access control, it may also help understand whether the data coming in at a regular interval or not. | keyword |
| event.module | Event module | constant_keyword |
| event.provider | Source of the event. Event transports such as Syslog or the Windows Event Log typically mention the source of an event. It can be the name of the software that generated the event (e.g. Sysmon, httpd), or of a subsystem of the operating system (kernel, Microsoft-Windows-Security-Auditing). | keyword |
| event.severity | The numeric severity of the event according to your event source. What the different severity values mean can be different between sources and use cases. It's up to the implementer to make sure severities are consistent across events from the same source. The Syslog severity belongs in `log.syslog.severity.code`. `event.severity` is meant to represent the severity according to the event source (e.g. firewall, IDS). If the event source does not publish its own severity, you may optionally copy the `log.syslog.severity.code` to `event.severity`. | long |
| event.start | event.start contains the date when the event started or when the activity was first observed. | date |
| event.timezone | This field should be populated when the event's timestamp does not include timezone information already (e.g. default Syslog timestamps). It's optional otherwise. Acceptable timezone formats are: a canonical ID (e.g. "Europe/Amsterdam"), abbreviated (e.g. "EST") or an HH:mm differential (e.g. "-05:00"). | keyword |
| event.type | This is one of four ECS Categorization Fields, and indicates the third level in the ECS category hierarchy. `event.type` represents a categorization "sub-bucket" that, when used along with the `event.category` field values, enables filtering events down to a level appropriate for single visualization. This field is an array. This will allow proper categorization of some events that fall in multiple event types. | keyword |
| file.hash.sha256 | SHA256 hash. | keyword |
| file.name | Name of the file including the extension, without the directory. | keyword |
| file.path | Full path to the file, including the file name. It should include the drive letter, when appropriate. | keyword |
| file.path.text | Multi-field of `file.path`. | match_only_text |
| file.size | File size in bytes. Only relevant when `file.type` is "file". | long |
| host.architecture | Operating system architecture. | keyword |
| host.containerized | If the host is a container. | boolean |
| host.domain | Name of the domain of which the host is a member. For example, on Windows this could be the host's Active Directory domain or NetBIOS domain name. For Linux this could be the domain of the host's LDAP provider. | keyword |
| host.hostname | Hostname of the host. It normally contains what the `hostname` command returns on the host machine. | keyword |
| host.id | Unique host id. As hostname is not always unique, use values that are meaningful in your environment. Example: The current usage of `beat.name`. | keyword |
| host.ip | Host ip addresses. | ip |
| host.mac | Host mac addresses. | keyword |
| host.name | Name of the host. It can contain what `hostname` returns on Unix systems, the fully qualified domain name, or a name specified by the user. The sender decides which value to use. | keyword |
| host.os.build | OS build information. | keyword |
| host.os.codename | OS codename, if any. | keyword |
| host.os.family | OS family (such as redhat, debian, freebsd, windows). | keyword |
| host.os.kernel | Operating system kernel version as a raw string. | keyword |
| host.os.name | Operating system name, without the version. | keyword |
| host.os.name.text | Multi-field of `host.os.name`. | text |
| host.os.platform | Operating system platform (such centos, ubuntu, windows). | keyword |
| host.os.version | Operating system version as a raw string. | keyword |
| host.type | Type of host. For Cloud providers this can be the machine type like `t2.medium`. If vm, this could be the container, for example, or other information meaningful in your environment. | keyword |
| http.request.referrer | Referrer for this HTTP request. | keyword |
| http.response.status_code | HTTP response status code. | long |
| input.type | Input type. | keyword |
| labels | Custom key/value pairs. Can be used to add meta information to events. Should not contain nested objects. All values are stored as keyword. Example: `docker` and `k8s` labels. | object |
| log.file.path | Full path to the log file this event came from, including the file name. It should include the drive letter, when appropriate. If the event wasn't read from a log file, do not populate this field. | keyword |
| log.level | Original log level of the log event. If the source of the event provides a log level or textual severity, this is the one that goes in `log.level`. If your source doesn't specify one, you may put your event transport's severity here (e.g. Syslog severity). Some examples are `warn`, `err`, `i`, `informational`. | keyword |
| log.offset | Offset of the entry in the log file. | long |
| log.source.address | Source address from which the log event was read / sent from. | keyword |
| message | For log events the message field contains the log message, optimized for viewing in a log viewer. For structured logs without an original message field, other fields can be concatenated to form a human-readable summary of the event. If multiple messages exist, they can be combined into one message. | match_only_text |
| network.application | When a specific application or service is identified from network connection details (source/dest IPs, ports, certificates, or wire format), this field captures the application's or service's name. For example, the original event identifies the network connection being from a specific web service in a `https` network connection, like `facebook` or `twitter`. The field value must be normalized to lowercase for querying. | keyword |
| network.bytes | Total bytes transferred in both directions. If `source.bytes` and `destination.bytes` are known, `network.bytes` is their sum. | long |
| network.direction | Direction of the network traffic. Recommended values are:   \* ingress   \* egress   \* inbound   \* outbound   \* internal   \* external   \* unknown  When mapping events from a host-based monitoring context, populate this field from the host's point of view, using the values "ingress" or "egress". When mapping events from a network or perimeter-based monitoring context, populate this field from the point of view of the network perimeter, using the values "inbound", "outbound", "internal" or "external". Note that "internal" is not crossing perimeter boundaries, and is meant to describe communication between two hosts within the perimeter. Note also that "external" is meant to describe traffic between two hosts that are external to the perimeter. This could for example be useful for ISPs or VPN service providers. | keyword |
| network.iana_number | IANA Protocol Number (https://www.iana.org/assignments/protocol-numbers/protocol-numbers.xhtml). Standardized list of protocols. This aligns well with NetFlow and sFlow related logs which use the IANA Protocol Number. | keyword |
| network.inner | Network.inner fields are added in addition to network.vlan fields to describe the innermost VLAN when q-in-q VLAN tagging is present. Allowed fields include vlan.id and vlan.name. Inner vlan fields are typically used when sending traffic with multiple 802.1q encapsulations to a network sensor (e.g. Zeek, Wireshark.) | object |
| network.inner.vlan.id | VLAN ID as reported by the observer. | keyword |
| network.inner.vlan.name | Optional VLAN name as reported by the observer. | keyword |
| network.protocol | In the OSI Model this would be the Application Layer protocol. For example, `http`, `dns`, or `ssh`. The field value must be normalized to lowercase for querying. | keyword |
| network.transport | Same as network.iana_number, but instead using the Keyword name of the transport layer (udp, tcp, ipv6-icmp, etc.) The field value must be normalized to lowercase for querying. | keyword |
| network.type | In the OSI Model this would be the Network Layer. ipv4, ipv6, ipsec, pim, etc The field value must be normalized to lowercase for querying. | keyword |
| observer.egress.interface.name | Interface name as reported by the system. | keyword |
| observer.egress.zone | Network zone of outbound traffic as reported by the observer to categorize the destination area of egress traffic, e.g. Internal, External, DMZ, HR, Legal, etc. | keyword |
| observer.hostname | Hostname of the observer. | keyword |
| observer.ingress.interface.name | Interface name as reported by the system. | keyword |
| observer.ingress.zone | Network zone of incoming traffic as reported by the observer to categorize the source area of ingress traffic. e.g. internal, External, DMZ, HR, Legal, etc. | keyword |
| observer.ip | IP addresses of the observer. | ip |
| observer.name | Custom name of the observer. This is a name that can be given to an observer. This can be helpful for example if multiple firewalls of the same model are used in an organization. If no custom name is needed, the field can be left empty. | keyword |
| observer.product | The product name of the observer. | keyword |
| observer.type | The type of the observer the data is coming from. There is no predefined list of observer types. Some examples are `forwarder`, `firewall`, `ids`, `ips`, `proxy`, `poller`, `sensor`, `APM server`. | keyword |
| observer.vendor | Vendor name of the observer. | keyword |
| observer.version | Observer version. | keyword |
| process.name | Process name. Sometimes called program name or similar. | keyword |
| process.name.text | Multi-field of `process.name`. | match_only_text |
| process.pid | Process id. | long |
| related.hash | All the hashes seen on your event. Populating this field, then using it to search for hashes can help in situations where you're unsure what the hash algorithm is (and therefore which key name to search). | keyword |
| related.hosts | All hostnames or other host identifiers seen on your event. Example identifiers include FQDNs, domain names, workstation names, or aliases. | keyword |
| related.ip | All of the IPs seen on your event. | ip |
| related.user | All the user names or other user identifiers seen on the event. | keyword |
| server.address | Some event server addresses are defined ambiguously. The event will sometimes list an IP, a domain or a unix socket.  You should always store the raw address in the `.address` field. Then it should be duplicated to `.ip` or `.domain`, depending on which one it is. | keyword |
| server.domain | The domain name of the server system. This value may be a host name, a fully qualified domain name, or another host naming format. The value may derive from the original event or be added from enrichment. | keyword |
| server.ip | IP address of the server (IPv4 or IPv6). | ip |
| server.port | Port of the server. | long |
| service.id | Unique identifier of the running service. If the service is comprised of many nodes, the `service.id` should be the same for all nodes. This id should uniquely identify the service. This makes it possible to correlate logs and metrics for one specific service, no matter which particular node emitted the event. Note that if you need to see the events from one specific host of the service, you should filter on that `host.name` or `host.id` instead. | keyword |
| source.address | Some event source addresses are defined ambiguously. The event will sometimes list an IP, a domain or a unix socket.  You should always store the raw address in the `.address` field. Then it should be duplicated to `.ip` or `.domain`, depending on which one it is. | keyword |
| source.as.number | Unique number allocated to the autonomous system. The autonomous system number (ASN) uniquely identifies each network on the Internet. | long |
| source.as.organization.name | Organization name. | keyword |
| source.as.organization.name.text | Multi-field of `source.as.organization.name`. | match_only_text |
| source.bytes | Bytes sent from the source to the destination. | long |
| source.domain | The domain name of the source system. This value may be a host name, a fully qualified domain name, or another host naming format. The value may derive from the original event or be added from enrichment. | keyword |
| source.geo.city_name | City name. | keyword |
| source.geo.continent_name | Name of the continent. | keyword |
| source.geo.country_iso_code | Country ISO code. | keyword |
| source.geo.country_name | Country name. | keyword |
| source.geo.location | Longitude and latitude. | geo_point |
| source.geo.region_iso_code | Region ISO code. | keyword |
| source.geo.region_name | Region name. | keyword |
| source.ip | IP address of the source (IPv4 or IPv6). | ip |
| source.nat.ip | Translated ip of source based NAT sessions (e.g. internal client to internet) Typically connections traversing load balancers, firewalls, or routers. | ip |
| source.nat.port | Translated port of source based NAT sessions. (e.g. internal client to internet) Typically used with load balancers, firewalls, or routers. | long |
| source.packets | Packets sent from the source to the destination. | long |
| source.port | Port of the source. | long |
| source.user.name | Short name or login of the user. | keyword |
| source.user.name.text | Multi-field of `source.user.name`. | match_only_text |
| syslog.facility.code | Syslog numeric facility of the event. | long |
| syslog.priority | Syslog priority of the event. | long |
| tags | List of keywords used to tag each event. | keyword |
| url.domain | Domain of the url, such as "www.elastic.co". In some cases a URL may refer to an IP and/or port directly, without a domain name. In this case, the IP address would go to the `domain` field. If the URL contains a literal IPv6 address enclosed by `[` and `]` (IETF RFC 2732), the `[` and `]` characters should also be captured in the `domain` field. | keyword |
| url.extension | The field contains the file extension from the original request url, excluding the leading dot. The file extension is only set if it exists, as not every url has a file extension. The leading period must not be included. For example, the value must be "png", not ".png". Note that when the file name has multiple extensions (example.tar.gz), only the last one should be captured ("gz", not "tar.gz"). | keyword |
| url.fragment | Portion of the url after the `#`, such as "top". The `#` is not part of the fragment. | keyword |
| url.full | If full URLs are important to your use case, they should be stored in `url.full`, whether this field is reconstructed or present in the event source. | wildcard |
| url.full.text | Multi-field of `url.full`. | match_only_text |
| url.original | Unmodified original url as seen in the event source. Note that in network monitoring, the observed URL may be a full URL, whereas in access logs, the URL is often just represented as a path. This field is meant to represent the URL as it was observed, complete or not. | wildcard |
| url.original.text | Multi-field of `url.original`. | match_only_text |
| url.password | Password of the request. | keyword |
| url.path | Path of the request, such as "/search". | wildcard |
| url.port | Port of the request, such as 443. | long |
| url.query | The query field describes the query string of the request, such as "q=elasticsearch". The `?` is excluded from the query string. If a URL contains no `?`, there is no query field. If there is a `?` but no query, the query field exists with an empty string. The `exists` query can be used to differentiate between the two cases. | keyword |
| url.registered_domain | The highest registered url domain, stripped of the subdomain. For example, the registered domain for "foo.example.com" is "example.com". This value can be determined precisely with a list like the public suffix list (http://publicsuffix.org). Trying to approximate this by simply taking the last two labels will not work well for TLDs such as "co.uk". | keyword |
| url.scheme | Scheme of the request, such as "https". Note: The `:` is not part of the scheme. | keyword |
| url.subdomain | The subdomain portion of a fully qualified domain name includes all of the names except the host name under the registered_domain.  In a partially qualified domain, or if the the qualification level of the full name cannot be determined, subdomain contains all of the names below the registered domain. For example the subdomain portion of "www.east.mydomain.co.uk" is "east". If the domain has multiple levels of subdomain, such as "sub2.sub1.example.com", the subdomain field should contain "sub2.sub1", with no trailing period. | keyword |
| url.top_level_domain | The effective top level domain (eTLD), also known as the domain suffix, is the last part of the domain name. For example, the top level domain for example.com is "com". This value can be determined precisely with a list like the public suffix list (http://publicsuffix.org). Trying to approximate this by simply taking the last label will not work well for effective TLDs such as "co.uk". | keyword |
| url.username | Username of the request. | keyword |
| user.email | User email address. | keyword |
| user.id | Unique identifier of the user. | keyword |
| user.name | Short name or login of the user. | keyword |
| user.name.text | Multi-field of `user.name`. | match_only_text |
| user_agent.original | Unparsed user_agent string. | keyword |
| user_agent.original.text | Multi-field of `user_agent.original`. | match_only_text |


### IOS

The `ios` dataset collects the Cisco IOS router and switch logs.

An example event for `ios` looks as following:

```json
{
    "@timestamp": "2021-07-19T08:58:29.370Z",
    "agent": {
        "ephemeral_id": "7e9d4c95-b972-479d-bc6c-2ac0d05f3eb1",
        "hostname": "docker-fleet-agent",
        "id": "3c803d12-46a2-48a4-a206-8fd3630cc2a9",
        "name": "docker-fleet-agent",
        "type": "filebeat",
        "version": "7.14.0"
    },
    "cisco": {
        "ios": {
            "access_list": "177",
            "facility": "SEC"
        }
    },
    "data_stream": {
        "dataset": "cisco.ios",
        "namespace": "ep",
        "type": "logs"
    },
    "destination": {
        "address": "224.0.0.22",
        "ip": "224.0.0.22"
    },
    "ecs": {
        "version": "1.10.0"
    },
    "elastic_agent": {
        "id": "3c803d12-46a2-48a4-a206-8fd3630cc2a9",
        "snapshot": true,
        "version": "7.14.0"
    },
    "event": {
        "action": "deny",
        "agent_id_status": "verified",
        "category": "network",
        "code": "IPACCESSLOGRP",
        "dataset": "cisco.ios",
        "ingested": "2021-07-19T08:58:30.397370366Z",
        "original": "Feb  8 04:00:48 198.51.100.2 585917: Feb  8 04:00:47.272: %SEC-6-IPACCESSLOGRP: list 177 denied igmp 198.51.100.197 -\u003e 224.0.0.22, 1 packet\n",
        "provider": "firewall",
        "sequence": 585917,
        "severity": 6,
        "timezone": "+00:00",
        "type": "denied"
    },
    "host": {
        "name": "docker-fleet-agent"
    },
    "input": {
        "type": "udp"
    },
    "log": {
        "level": "informational",
        "source": {
            "address": "198.51.100.2"
        }
    },
    "message": "list 177 denied igmp 198.51.100.197 -\u003e 224.0.0.22, 1 packet",
    "network": {
        "community_id": "1:Rt5RGlrNED3cg8Wokm4+KGsDz+4=",
        "packets": 1,
        "transport": "igmp",
        "type": "ipv4"
    },
    "related": {
        "ip": [
            "198.51.100.197",
            "224.0.0.22"
        ]
    },
    "source": {
        "address": "198.51.100.197",
        "ip": "198.51.100.197",
        "packets": 1
    },
    "tags": [
        "preserve_original_event",
        "cisco-ios",
        "forwarded"
    ]
}
```

**Exported fields**

| Field | Description | Type |
|---|---|---|
| @timestamp | Event timestamp. | date |
| cisco.ios.access_list | Name of the IP access list. | keyword |
| cisco.ios.action | Action taken by the device | keyword |
| cisco.ios.facility | The facility to which the message refers (for example, SNMP, SYS, and so forth). A facility can be a hardware device, a protocol, or a module of the system software. It denotes the source or the cause of the system message. | keyword |
| cisco.ios.outcome | The result of the event | keyword |
| cisco.ios.pim.group.ip | Multicast group IP | ip |
| cisco.ios.pim.source.ip | Multicast source IP | ip |
| cisco.ios.session.number | Session ID | integer |
| cisco.ios.session.type | Session type | keyword |
| cloud.account.id | The cloud account or organization id used to identify different entities in a multi-tenant environment. Examples: AWS account id, Google Cloud ORG Id, or other unique identifier. | keyword |
| cloud.availability_zone | Availability zone in which this host is running. | keyword |
| cloud.image.id | Image ID for the cloud instance. | keyword |
| cloud.instance.id | Instance ID of the host machine. | keyword |
| cloud.instance.name | Instance name of the host machine. | keyword |
| cloud.machine.type | Machine type of the host machine. | keyword |
| cloud.project.id | Name of the project in Google Cloud. | keyword |
| cloud.provider | Name of the cloud provider. Example values are aws, azure, gcp, or digitalocean. | keyword |
| cloud.region | Region in which this host is running. | keyword |
| container.id | Unique container id. | keyword |
| container.image.name | Name of the image the container was built on. | keyword |
| container.labels | Image labels. | object |
| container.name | Container name. | keyword |
| data_stream.dataset | Data stream dataset. | constant_keyword |
| data_stream.namespace | Data stream namespace. | constant_keyword |
| data_stream.type | Data stream type. | constant_keyword |
| destination.address | Some event destination addresses are defined ambiguously. The event will sometimes list an IP, a domain or a unix socket.  You should always store the raw address in the `.address` field. Then it should be duplicated to `.ip` or `.domain`, depending on which one it is. | keyword |
| destination.as.number | Unique number allocated to the autonomous system. The autonomous system number (ASN) uniquely identifies each network on the Internet. | long |
| destination.as.organization.name | Organization name. | keyword |
| destination.as.organization.name.text | Multi-field of `destination.as.organization.name`. | match_only_text |
| destination.geo.city_name | City name. | keyword |
| destination.geo.continent_name | Name of the continent. | keyword |
| destination.geo.country_iso_code | Country ISO code. | keyword |
| destination.geo.country_name | Country name. | keyword |
| destination.geo.location | Longitude and latitude. | geo_point |
| destination.geo.region_iso_code | Region ISO code. | keyword |
| destination.geo.region_name | Region name. | keyword |
| destination.ip | IP address of the destination (IPv4 or IPv6). | ip |
| destination.port | Port of the destination. | long |
| ecs.version | ECS version this event conforms to. `ecs.version` is a required field and must exist in all events. When querying across multiple indices -- which may conform to slightly different ECS versions -- this field lets integrations adjust to the schema version of the events. | keyword |
| elastic.agent.id |  | keyword |
| elastic.agent.snapshot |  | boolean |
| elastic.agent.version |  | keyword |
| error.message | Error message. | match_only_text |
| event.category | This is one of four ECS Categorization Fields, and indicates the second level in the ECS category hierarchy. `event.category` represents the "big buckets" of ECS categories. For example, filtering on `event.category:process` yields all events relating to process activity. This field is closely related to `event.type`, which is used as a subcategory. This field is an array. This will allow proper categorization of some events that fall in multiple categories. | keyword |
| event.code | Identification code for this event, if one exists. Some event sources use event codes to identify messages unambiguously, regardless of message language or wording adjustments over time. An example of this is the Windows Event ID. | keyword |
| event.created | event.created contains the date/time when the event was first read by an agent, or by your pipeline. This field is distinct from @timestamp in that @timestamp typically contain the time extracted from the original event. In most situations, these two timestamps will be slightly different. The difference can be used to calculate the delay between your source generating an event, and the time when your agent first processed it. This can be used to monitor your agent's or pipeline's ability to keep up with your event source. In case the two timestamps are identical, @timestamp should be used. | date |
| event.dataset | Event dataset | constant_keyword |
| event.duration | Duration of the event in nanoseconds. If event.start and event.end are known this value should be the difference between the end and start time. | long |
| event.end | event.end contains the date when the event ended or when the activity was last observed. | date |
| event.ingested | Timestamp when an event arrived in the central data store. This is different from `@timestamp`, which is when the event originally occurred.  It's also different from `event.created`, which is meant to capture the first time an agent saw the event. In normal conditions, assuming no tampering, the timestamps should chronologically look like this: `@timestamp` \< `event.created` \< `event.ingested`. | date |
| event.kind | This is one of four ECS Categorization Fields, and indicates the highest level in the ECS category hierarchy. `event.kind` gives high-level information about what type of information the event contains, without being specific to the contents of the event. For example, values of this field distinguish alert events from metric events. The value of this field can be used to inform how these kinds of events should be handled. They may warrant different retention, different access control, it may also help understand whether the data coming in at a regular interval or not. | keyword |
| event.module | Event module | constant_keyword |
| event.provider | Source of the event. Event transports such as Syslog or the Windows Event Log typically mention the source of an event. It can be the name of the software that generated the event (e.g. Sysmon, httpd), or of a subsystem of the operating system (kernel, Microsoft-Windows-Security-Auditing). | keyword |
| event.severity | The numeric severity of the event according to your event source. What the different severity values mean can be different between sources and use cases. It's up to the implementer to make sure severities are consistent across events from the same source. The Syslog severity belongs in `log.syslog.severity.code`. `event.severity` is meant to represent the severity according to the event source (e.g. firewall, IDS). If the event source does not publish its own severity, you may optionally copy the `log.syslog.severity.code` to `event.severity`. | long |
| event.start | event.start contains the date when the event started or when the activity was first observed. | date |
| event.timezone | This field should be populated when the event's timestamp does not include timezone information already (e.g. default Syslog timestamps). It's optional otherwise. Acceptable timezone formats are: a canonical ID (e.g. "Europe/Amsterdam"), abbreviated (e.g. "EST") or an HH:mm differential (e.g. "-05:00"). | keyword |
| event.type | This is one of four ECS Categorization Fields, and indicates the third level in the ECS category hierarchy. `event.type` represents a categorization "sub-bucket" that, when used along with the `event.category` field values, enables filtering events down to a level appropriate for single visualization. This field is an array. This will allow proper categorization of some events that fall in multiple event types. | keyword |
| host.architecture | Operating system architecture. | keyword |
| host.containerized | If the host is a container. | boolean |
| host.domain | Name of the domain of which the host is a member. For example, on Windows this could be the host's Active Directory domain or NetBIOS domain name. For Linux this could be the domain of the host's LDAP provider. | keyword |
| host.hostname | Hostname of the host. It normally contains what the `hostname` command returns on the host machine. | keyword |
| host.id | Unique host id. As hostname is not always unique, use values that are meaningful in your environment. Example: The current usage of `beat.name`. | keyword |
| host.ip | Host ip addresses. | ip |
| host.mac | Host mac addresses. | keyword |
| host.name | Name of the host. It can contain what `hostname` returns on Unix systems, the fully qualified domain name, or a name specified by the user. The sender decides which value to use. | keyword |
| host.os.build | OS build information. | keyword |
| host.os.codename | OS codename, if any. | keyword |
| host.os.family | OS family (such as redhat, debian, freebsd, windows). | keyword |
| host.os.kernel | Operating system kernel version as a raw string. | keyword |
| host.os.name | Operating system name, without the version. | keyword |
| host.os.name.text | Multi-field of `host.os.name`. | text |
| host.os.platform | Operating system platform (such centos, ubuntu, windows). | keyword |
| host.os.version | Operating system version as a raw string. | keyword |
| host.type | Type of host. For Cloud providers this can be the machine type like `t2.medium`. If vm, this could be the container, for example, or other information meaningful in your environment. | keyword |
| hostname | Hostname from syslog header. | keyword |
| icmp.code | ICMP code. | keyword |
| icmp.type | ICMP type. | keyword |
| igmp.type | IGMP type. | keyword |
| input.type |  | keyword |
| labels | Custom key/value pairs. Can be used to add meta information to events. Should not contain nested objects. All values are stored as keyword. Example: `docker` and `k8s` labels. | object |
| log.file.path | Full path to the log file this event came from, including the file name. It should include the drive letter, when appropriate. If the event wasn't read from a log file, do not populate this field. | keyword |
| log.level | Original log level of the log event. If the source of the event provides a log level or textual severity, this is the one that goes in `log.level`. If your source doesn't specify one, you may put your event transport's severity here (e.g. Syslog severity). Some examples are `warn`, `err`, `i`, `informational`. | keyword |
| log.offset |  | long |
| log.source.address |  | keyword |
| message | For log events the message field contains the log message, optimized for viewing in a log viewer. For structured logs without an original message field, other fields can be concatenated to form a human-readable summary of the event. If multiple messages exist, they can be combined into one message. | match_only_text |
| network.community_id | A hash of source and destination IPs and ports, as well as the protocol used in a communication. This is a tool-agnostic standard to identify flows. Learn more at https://github.com/corelight/community-id-spec. | keyword |
| network.iana_number | IANA Protocol Number (https://www.iana.org/assignments/protocol-numbers/protocol-numbers.xhtml). Standardized list of protocols. This aligns well with NetFlow and sFlow related logs which use the IANA Protocol Number. | keyword |
| network.packets | Total packets transferred in both directions. If `source.packets` and `destination.packets` are known, `network.packets` is their sum. | long |
| network.transport | Same as network.iana_number, but instead using the Keyword name of the transport layer (udp, tcp, ipv6-icmp, etc.) The field value must be normalized to lowercase for querying. | keyword |
| network.type | In the OSI Model this would be the Network Layer. ipv4, ipv6, ipsec, pim, etc The field value must be normalized to lowercase for querying. | keyword |
| process.program | Process from syslog header. | keyword |
| related.ip | All of the IPs seen on your event. | ip |
| related.user | All the user names or other user identifiers seen on the event. | keyword |
| source.address | Some event source addresses are defined ambiguously. The event will sometimes list an IP, a domain or a unix socket.  You should always store the raw address in the `.address` field. Then it should be duplicated to `.ip` or `.domain`, depending on which one it is. | keyword |
| source.as.number | Unique number allocated to the autonomous system. The autonomous system number (ASN) uniquely identifies each network on the Internet. | long |
| source.as.organization.name | Organization name. | keyword |
| source.as.organization.name.text | Multi-field of `source.as.organization.name`. | match_only_text |
| source.geo.city_name | City name. | keyword |
| source.geo.continent_name | Name of the continent. | keyword |
| source.geo.country_iso_code | Country ISO code. | keyword |
| source.geo.country_name | Country name. | keyword |
| source.geo.location | Longitude and latitude. | geo_point |
| source.geo.region_iso_code | Region ISO code. | keyword |
| source.geo.region_name | Region name. | keyword |
| source.ip | IP address of the source (IPv4 or IPv6). | ip |
| source.packets | Packets sent from the source to the destination. | long |
| source.port | Port of the source. | long |
| source.user.name | Short name or login of the user. | keyword |
| source.user.name.text | Multi-field of `source.user.name`. | match_only_text |
| tags | List of keywords used to tag each event. | keyword |


### Nexus

The `nexus` dataset collects Cisco Nexus logs.

An example event for `nexus` looks as following:

```json
{
    "@timestamp": "2022-01-25T08:47:14.944Z",
    "agent": {
        "ephemeral_id": "091f3442-1209-4033-8434-e8c731c8a092",
        "hostname": "docker-fleet-agent",
        "id": "0a0be70a-90aa-494d-8be3-b06a8a05e08c",
        "name": "docker-fleet-agent",
        "type": "filebeat",
        "version": "7.16.2"
    },
    "data_stream": {
        "dataset": "cisco.nexus",
        "namespace": "ep",
        "type": "logs"
    },
    "ecs": {
        "version": "1.12.0"
    },
    "elastic_agent": {
        "id": "0a0be70a-90aa-494d-8be3-b06a8a05e08c",
        "snapshot": false,
        "version": "7.16.2"
    },
    "event": {
        "agent_id_status": "verified",
        "code": "pam_aaa",
        "dataset": "cisco.nexus",
        "ingested": "2022-01-25T08:47:15Z",
        "original": "2012 Dec 18 14:51:08 Nexus5010-B %AUTHPRIV-3-SYSTEM_MSG: pam_aaa:Authentication failed for user en from 2.2.2.1 - login\n",
        "timezone": "+00:00"
    },
    "input": {
        "type": "udp"
    },
    "log": {
        "source": {
            "address": "172.19.0.4:54372"
        }
    },
    "observer": {
        "product": "Nexus",
        "type": "Switches",
        "vendor": "Cisco"
    },
    "rsa": {
        "internal": {
            "messageid": "pam_aaa"
        },
        "time": {
            "timezone": "Nexus5010-B %AUTHPRIV-3-SYSTEM_MSG"
        }
    },
    "tags": [
        "preserve_original_event",
        "cisco-nexus",
        "forwarded"
    ]
}
```

**Exported fields**

| Field | Description | Type |
|---|---|---|
| @timestamp | Date/time when the event originated. This is the date/time extracted from the event, typically representing when the event was generated by the source. If the event source has no original timestamp, this value is typically populated by the first time the event was received by the pipeline. Required field for all events. | date |
| client.domain | The domain name of the client system. This value may be a host name, a fully qualified domain name, or another host naming format. The value may derive from the original event or be added from enrichment. | keyword |
| client.registered_domain | The highest registered client domain, stripped of the subdomain. For example, the registered domain for "foo.example.com" is "example.com". This value can be determined precisely with a list like the public suffix list (http://publicsuffix.org). Trying to approximate this by simply taking the last two labels will not work well for TLDs such as "co.uk". | keyword |
| client.subdomain | The subdomain portion of a fully qualified domain name includes all of the names except the host name under the registered_domain.  In a partially qualified domain, or if the the qualification level of the full name cannot be determined, subdomain contains all of the names below the registered domain. For example the subdomain portion of "www.east.mydomain.co.uk" is "east". If the domain has multiple levels of subdomain, such as "sub2.sub1.example.com", the subdomain field should contain "sub2.sub1", with no trailing period. | keyword |
| client.top_level_domain | The effective top level domain (eTLD), also known as the domain suffix, is the last part of the domain name. For example, the top level domain for example.com is "com". This value can be determined precisely with a list like the public suffix list (http://publicsuffix.org). Trying to approximate this by simply taking the last label will not work well for effective TLDs such as "co.uk". | keyword |
| cloud.account.id | The cloud account or organization id used to identify different entities in a multi-tenant environment. Examples: AWS account id, Google Cloud ORG Id, or other unique identifier. | keyword |
| cloud.availability_zone | Availability zone in which this host is running. | keyword |
| cloud.image.id | Image ID for the cloud instance. | keyword |
| cloud.instance.id | Instance ID of the host machine. | keyword |
| cloud.instance.name | Instance name of the host machine. | keyword |
| cloud.machine.type | Machine type of the host machine. | keyword |
| cloud.project.id | Name of the project in Google Cloud. | keyword |
| cloud.provider | Name of the cloud provider. Example values are aws, azure, gcp, or digitalocean. | keyword |
| cloud.region | Region in which this host is running. | keyword |
| container.id | Unique container id. | keyword |
| container.image.name | Name of the image the container was built on. | keyword |
| container.labels | Image labels. | object |
| container.name | Container name. | keyword |
| data_stream.dataset | Data stream dataset. | constant_keyword |
| data_stream.namespace | Data stream namespace. | constant_keyword |
| data_stream.type | Data stream type. | constant_keyword |
| destination.address | Some event destination addresses are defined ambiguously. The event will sometimes list an IP, a domain or a unix socket.  You should always store the raw address in the `.address` field. Then it should be duplicated to `.ip` or `.domain`, depending on which one it is. | keyword |
| destination.as.number | Unique number allocated to the autonomous system. The autonomous system number (ASN) uniquely identifies each network on the Internet. | long |
| destination.as.organization.name | Organization name. | keyword |
| destination.as.organization.name.text | Multi-field of `destination.as.organization.name`. | match_only_text |
| destination.bytes | Bytes sent from the destination to the source. | long |
| destination.domain | The domain name of the destination system. This value may be a host name, a fully qualified domain name, or another host naming format. The value may derive from the original event or be added from enrichment. | keyword |
| destination.geo.city_name | City name. | keyword |
| destination.geo.country_name | Country name. | keyword |
| destination.geo.location | Longitude and latitude. | geo_point |
| destination.ip | IP address of the destination (IPv4 or IPv6). | ip |
| destination.mac | MAC address of the destination. The notation format from RFC 7042 is suggested: Each octet (that is, 8-bit byte) is represented by two [uppercase] hexadecimal digits giving the value of the octet as an unsigned integer. Successive octets are separated by a hyphen. | keyword |
| destination.nat.ip | Translated ip of destination based NAT sessions (e.g. internet to private DMZ) Typically used with load balancers, firewalls, or routers. | ip |
| destination.nat.port | Port the source session is translated to by NAT Device. Typically used with load balancers, firewalls, or routers. | long |
| destination.port | Port of the destination. | long |
| destination.registered_domain | The highest registered destination domain, stripped of the subdomain. For example, the registered domain for "foo.example.com" is "example.com". This value can be determined precisely with a list like the public suffix list (http://publicsuffix.org). Trying to approximate this by simply taking the last two labels will not work well for TLDs such as "co.uk". | keyword |
| destination.subdomain | The subdomain portion of a fully qualified domain name includes all of the names except the host name under the registered_domain.  In a partially qualified domain, or if the the qualification level of the full name cannot be determined, subdomain contains all of the names below the registered domain. For example the subdomain portion of "www.east.mydomain.co.uk" is "east". If the domain has multiple levels of subdomain, such as "sub2.sub1.example.com", the subdomain field should contain "sub2.sub1", with no trailing period. | keyword |
| destination.top_level_domain | The effective top level domain (eTLD), also known as the domain suffix, is the last part of the domain name. For example, the top level domain for example.com is "com". This value can be determined precisely with a list like the public suffix list (http://publicsuffix.org). Trying to approximate this by simply taking the last label will not work well for effective TLDs such as "co.uk". | keyword |
| dns.answers.name | The domain name to which this resource record pertains. If a chain of CNAME is being resolved, each answer's `name` should be the one that corresponds with the answer's `data`. It should not simply be the original `question.name` repeated. | keyword |
| dns.answers.type | The type of data contained in this resource record. | keyword |
| dns.question.domain | Server domain. | keyword |
| dns.question.registered_domain | The highest registered domain, stripped of the subdomain. For example, the registered domain for "foo.example.com" is "example.com". This value can be determined precisely with a list like the public suffix list (http://publicsuffix.org). Trying to approximate this by simply taking the last two labels will not work well for TLDs such as "co.uk". | keyword |
| dns.question.subdomain | The subdomain is all of the labels under the registered_domain. If the domain has multiple levels of subdomain, such as "sub2.sub1.example.com", the subdomain field should contain "sub2.sub1", with no trailing period. | keyword |
| dns.question.top_level_domain | The effective top level domain (eTLD), also known as the domain suffix, is the last part of the domain name. For example, the top level domain for example.com is "com". This value can be determined precisely with a list like the public suffix list (http://publicsuffix.org). Trying to approximate this by simply taking the last label will not work well for effective TLDs such as "co.uk". | keyword |
| dns.question.type | The type of record being queried. | keyword |
| ecs.version | ECS version this event conforms to. `ecs.version` is a required field and must exist in all events. When querying across multiple indices -- which may conform to slightly different ECS versions -- this field lets integrations adjust to the schema version of the events. | keyword |
| error.message | Error message. | match_only_text |
| event.action | The action captured by the event. This describes the information in the event. It is more specific than `event.category`. Examples are `group-add`, `process-started`, `file-created`. The value is normally defined by the implementer. | keyword |
| event.code | Identification code for this event, if one exists. Some event sources use event codes to identify messages unambiguously, regardless of message language or wording adjustments over time. An example of this is the Windows Event ID. | keyword |
| event.dataset | Event dataset | constant_keyword |
| event.ingested | Timestamp when an event arrived in the central data store. This is different from `@timestamp`, which is when the event originally occurred.  It's also different from `event.created`, which is meant to capture the first time an agent saw the event. In normal conditions, assuming no tampering, the timestamps should chronologically look like this: `@timestamp` \< `event.created` \< `event.ingested`. | date |
| event.module | Event module | constant_keyword |
| event.original | Raw text message of entire event. Used to demonstrate log integrity or where the full log message (before splitting it up in multiple parts) may be required, e.g. for reindex. This field is not indexed and doc_values are disabled. It cannot be searched, but it can be retrieved from `_source`. If users wish to override this and index this field, please see `Field data types` in the `Elasticsearch Reference`. | keyword |
| event.outcome | This is one of four ECS Categorization Fields, and indicates the lowest level in the ECS category hierarchy. `event.outcome` simply denotes whether the event represents a success or a failure from the perspective of the entity that produced the event. Note that when a single transaction is described in multiple events, each event may populate different values of `event.outcome`, according to their perspective. Also note that in the case of a compound event (a single event that contains multiple logical events), this field should be populated with the value that best captures the overall success or failure from the perspective of the event producer. Further note that not all events will have an associated outcome. For example, this field is generally not populated for metric events, events with `event.type:info`, or any events for which an outcome does not make logical sense. | keyword |
| event.timezone | This field should be populated when the event's timestamp does not include timezone information already (e.g. default Syslog timestamps). It's optional otherwise. Acceptable timezone formats are: a canonical ID (e.g. "Europe/Amsterdam"), abbreviated (e.g. "EST") or an HH:mm differential (e.g. "-05:00"). | keyword |
| file.attributes | Array of file attributes. Attributes names will vary by platform. Here's a non-exhaustive list of values that are expected in this field: archive, compressed, directory, encrypted, execute, hidden, read, readonly, system, write. | keyword |
| file.directory | Directory where the file is located. It should include the drive letter, when appropriate. | keyword |
| file.extension | File extension, excluding the leading dot. Note that when the file name has multiple extensions (example.tar.gz), only the last one should be captured ("gz", not "tar.gz"). | keyword |
| file.name | Name of the file including the extension, without the directory. | keyword |
| file.path | Full path to the file, including the file name. It should include the drive letter, when appropriate. | keyword |
| file.path.text | Multi-field of `file.path`. | match_only_text |
| file.size | File size in bytes. Only relevant when `file.type` is "file". | long |
| file.type | File type (file, dir, or symlink). | keyword |
| geo.city_name | City name. | keyword |
| geo.country_name | Country name. | keyword |
| geo.name | User-defined description of a location, at the level of granularity they care about. Could be the name of their data centers, the floor number, if this describes a local physical entity, city names. Not typically used in automated geolocation. | keyword |
| geo.region_name | Region name. | keyword |
| group.id | Unique identifier for the group on the system/platform. | keyword |
| group.name | Name of the group. | keyword |
| host.architecture | Operating system architecture. | keyword |
| host.containerized | If the host is a container. | boolean |
| host.domain | Name of the domain of which the host is a member. For example, on Windows this could be the host's Active Directory domain or NetBIOS domain name. For Linux this could be the domain of the host's LDAP provider. | keyword |
| host.hostname | Hostname of the host. It normally contains what the `hostname` command returns on the host machine. | keyword |
| host.id | Unique host id. As hostname is not always unique, use values that are meaningful in your environment. Example: The current usage of `beat.name`. | keyword |
| host.ip | Host ip addresses. | ip |
| host.mac | Host MAC addresses. The notation format from RFC 7042 is suggested: Each octet (that is, 8-bit byte) is represented by two [uppercase] hexadecimal digits giving the value of the octet as an unsigned integer. Successive octets are separated by a hyphen. | keyword |
| host.name | Name of the host. It can contain what `hostname` returns on Unix systems, the fully qualified domain name, or a name specified by the user. The sender decides which value to use. | keyword |
| host.os.build | OS build information. | keyword |
| host.os.codename | OS codename, if any. | keyword |
| host.os.family | OS family (such as redhat, debian, freebsd, windows). | keyword |
| host.os.kernel | Operating system kernel version as a raw string. | keyword |
| host.os.name | Operating system name, without the version. | keyword |
| host.os.name.text | Multi-field of `host.os.name`. | text |
| host.os.platform | Operating system platform (such centos, ubuntu, windows). | keyword |
| host.os.version | Operating system version as a raw string. | keyword |
| host.type | Type of host. For Cloud providers this can be the machine type like `t2.medium`. If vm, this could be the container, for example, or other information meaningful in your environment. | keyword |
| http.request.method | HTTP request method. The value should retain its casing from the original event. For example, `GET`, `get`, and `GeT` are all considered valid values for this field. | keyword |
| http.request.referrer | Referrer for this HTTP request. | keyword |
| input.type | Type of Filebeat input. | keyword |
| log.file.path | Full path to the log file this event came from. | keyword |
| log.flags | Flags for the log file. | keyword |
| log.level | Original log level of the log event. If the source of the event provides a log level or textual severity, this is the one that goes in `log.level`. If your source doesn't specify one, you may put your event transport's severity here (e.g. Syslog severity). Some examples are `warn`, `err`, `i`, `informational`. | keyword |
| log.offset | Offset of the entry in the log file. | long |
| log.source.address | Source address from which the log event was read / sent from. | keyword |
| log.syslog.facility.code | The Syslog numeric facility of the log event, if available. According to RFCs 5424 and 3164, this value should be an integer between 0 and 23. | long |
| log.syslog.priority | Syslog numeric priority of the event, if available. According to RFCs 5424 and 3164, the priority is 8 \* facility + severity. This number is therefore expected to contain a value between 0 and 191. | long |
| log.syslog.severity.code | The Syslog numeric severity of the log event, if available. If the event source publishing via Syslog provides a different numeric severity value (e.g. firewall, IDS), your source's numeric severity should go to `event.severity`. If the event source does not specify a distinct severity, you can optionally copy the Syslog severity to `event.severity`. | long |
| message | For log events the message field contains the log message, optimized for viewing in a log viewer. For structured logs without an original message field, other fields can be concatenated to form a human-readable summary of the event. If multiple messages exist, they can be combined into one message. | match_only_text |
| network.application | When a specific application or service is identified from network connection details (source/dest IPs, ports, certificates, or wire format), this field captures the application's or service's name. For example, the original event identifies the network connection being from a specific web service in a `https` network connection, like `facebook` or `twitter`. The field value must be normalized to lowercase for querying. | keyword |
| network.bytes | Total bytes transferred in both directions. If `source.bytes` and `destination.bytes` are known, `network.bytes` is their sum. | long |
| network.direction | Direction of the network traffic. Recommended values are:   \* ingress   \* egress   \* inbound   \* outbound   \* internal   \* external   \* unknown  When mapping events from a host-based monitoring context, populate this field from the host's point of view, using the values "ingress" or "egress". When mapping events from a network or perimeter-based monitoring context, populate this field from the point of view of the network perimeter, using the values "inbound", "outbound", "internal" or "external". Note that "internal" is not crossing perimeter boundaries, and is meant to describe communication between two hosts within the perimeter. Note also that "external" is meant to describe traffic between two hosts that are external to the perimeter. This could for example be useful for ISPs or VPN service providers. | keyword |
| network.forwarded_ip | Host IP address when the source IP address is the proxy. | ip |
| network.interface.name |  | keyword |
| network.packets | Total packets transferred in both directions. If `source.packets` and `destination.packets` are known, `network.packets` is their sum. | long |
| network.protocol | In the OSI Model this would be the Application Layer protocol. For example, `http`, `dns`, or `ssh`. The field value must be normalized to lowercase for querying. | keyword |
| observer.egress.interface.name | Interface name as reported by the system. | keyword |
| observer.ingress.interface.name | Interface name as reported by the system. | keyword |
| observer.product | The product name of the observer. | keyword |
| observer.type | The type of the observer the data is coming from. There is no predefined list of observer types. Some examples are `forwarder`, `firewall`, `ids`, `ips`, `proxy`, `poller`, `sensor`, `APM server`. | keyword |
| observer.vendor | Vendor name of the observer. | keyword |
| observer.version | Observer version. | keyword |
| process.name | Process name. Sometimes called program name or similar. | keyword |
| process.name.text | Multi-field of `process.name`. | match_only_text |
| process.parent.name | Process name. Sometimes called program name or similar. | keyword |
| process.parent.name.text | Multi-field of `process.parent.name`. | match_only_text |
| process.parent.pid | Process id. | long |
| process.parent.title | Process title. The proctitle, some times the same as process name. Can also be different: for example a browser setting its title to the web page currently opened. | keyword |
| process.parent.title.text | Multi-field of `process.parent.title`. | match_only_text |
| process.pid | Process id. | long |
| process.title | Process title. The proctitle, some times the same as process name. Can also be different: for example a browser setting its title to the web page currently opened. | keyword |
| process.title.text | Multi-field of `process.title`. | match_only_text |
| related.hosts | All hostnames or other host identifiers seen on your event. Example identifiers include FQDNs, domain names, workstation names, or aliases. | keyword |
| related.ip | All of the IPs seen on your event. | ip |
| related.user | All the user names or other user identifiers seen on the event. | keyword |
| rsa.counters.dclass_c1 | This is a generic counter key that should be used with the label dclass.c1.str only | long |
| rsa.counters.dclass_c1_str | This is a generic counter string key that should be used with the label dclass.c1 only | keyword |
| rsa.counters.dclass_c2 | This is a generic counter key that should be used with the label dclass.c2.str only | long |
| rsa.counters.dclass_c2_str | This is a generic counter string key that should be used with the label dclass.c2 only | keyword |
| rsa.counters.dclass_c3 | This is a generic counter key that should be used with the label dclass.c3.str only | long |
| rsa.counters.dclass_c3_str | This is a generic counter string key that should be used with the label dclass.c3 only | keyword |
| rsa.counters.dclass_r1 | This is a generic ratio key that should be used with the label dclass.r1.str only | keyword |
| rsa.counters.dclass_r1_str | This is a generic ratio string key that should be used with the label dclass.r1 only | keyword |
| rsa.counters.dclass_r2 | This is a generic ratio key that should be used with the label dclass.r2.str only | keyword |
| rsa.counters.dclass_r2_str | This is a generic ratio string key that should be used with the label dclass.r2 only | keyword |
| rsa.counters.dclass_r3 | This is a generic ratio key that should be used with the label dclass.r3.str only | keyword |
| rsa.counters.dclass_r3_str | This is a generic ratio string key that should be used with the label dclass.r3 only | keyword |
| rsa.counters.event_counter | This is used to capture the number of times an event repeated | long |
| rsa.crypto.cert_ca | This key is used to capture the Certificate signing authority only | keyword |
| rsa.crypto.cert_checksum |  | keyword |
| rsa.crypto.cert_common | This key is used to capture the Certificate common name only | keyword |
| rsa.crypto.cert_error | This key captures the Certificate Error String | keyword |
| rsa.crypto.cert_host_cat | This key is used for the hostname category value of a certificate | keyword |
| rsa.crypto.cert_host_name | Deprecated key defined only in table map. | keyword |
| rsa.crypto.cert_issuer |  | keyword |
| rsa.crypto.cert_keysize |  | keyword |
| rsa.crypto.cert_serial | This key is used to capture the Certificate serial number only | keyword |
| rsa.crypto.cert_status | This key captures Certificate validation status | keyword |
| rsa.crypto.cert_subject | This key is used to capture the Certificate organization only | keyword |
| rsa.crypto.cert_username |  | keyword |
| rsa.crypto.cipher_dst | This key is for Destination (Server) Cipher | keyword |
| rsa.crypto.cipher_size_dst | This key captures Destination (Server) Cipher Size | long |
| rsa.crypto.cipher_size_src | This key captures Source (Client) Cipher Size | long |
| rsa.crypto.cipher_src | This key is for Source (Client) Cipher | keyword |
| rsa.crypto.crypto | This key is used to capture the Encryption Type or Encryption Key only | keyword |
| rsa.crypto.d_certauth |  | keyword |
| rsa.crypto.https_insact |  | keyword |
| rsa.crypto.https_valid |  | keyword |
| rsa.crypto.ike | IKE negotiation phase. | keyword |
| rsa.crypto.ike_cookie1 | ID of the negotiation — sent for ISAKMP Phase One | keyword |
| rsa.crypto.ike_cookie2 | ID of the negotiation — sent for ISAKMP Phase Two | keyword |
| rsa.crypto.peer | This key is for Encryption peer's IP Address | keyword |
| rsa.crypto.peer_id | This key is for Encryption peer’s identity | keyword |
| rsa.crypto.s_certauth |  | keyword |
| rsa.crypto.scheme | This key captures the Encryption scheme used | keyword |
| rsa.crypto.sig_type | This key captures the Signature Type | keyword |
| rsa.crypto.ssl_ver_dst | Deprecated, use version | keyword |
| rsa.crypto.ssl_ver_src | Deprecated, use version | keyword |
| rsa.db.database | This key is used to capture the name of a database or an instance as seen in a session | keyword |
| rsa.db.db_id | This key is used to capture the unique identifier for a database | keyword |
| rsa.db.db_pid | This key captures the process id of a connection with database server | long |
| rsa.db.index | This key captures IndexID of the index. | keyword |
| rsa.db.instance | This key is used to capture the database server instance name | keyword |
| rsa.db.lread | This key is used for the number of logical reads | long |
| rsa.db.lwrite | This key is used for the number of logical writes | long |
| rsa.db.permissions | This key captures permission or privilege level assigned to a resource. | keyword |
| rsa.db.pread | This key is used for the number of physical writes | long |
| rsa.db.table_name | This key is used to capture the table name | keyword |
| rsa.db.transact_id | This key captures the SQL transantion ID of the current session | keyword |
| rsa.email.email | This key is used to capture a generic email address where the source or destination context is not clear | keyword |
| rsa.email.email_dst | This key is used to capture the Destination email address only, when the destination context is not clear use email | keyword |
| rsa.email.email_src | This key is used to capture the source email address only, when the source context is not clear use email | keyword |
| rsa.email.subject | This key is used to capture the subject string from an Email only. | keyword |
| rsa.email.trans_from | Deprecated key defined only in table map. | keyword |
| rsa.email.trans_to | Deprecated key defined only in table map. | keyword |
| rsa.endpoint.host_state | This key is used to capture the current state of the machine, such as \<strong\>blacklisted\</strong\>, \<strong\>infected\</strong\>, \<strong\>firewall disabled\</strong\> and so on | keyword |
| rsa.endpoint.registry_key | This key captures the path to the registry key | keyword |
| rsa.endpoint.registry_value | This key captures values or decorators used within a registry entry | keyword |
| rsa.file.attachment | This key captures the attachment file name | keyword |
| rsa.file.binary | Deprecated key defined only in table map. | keyword |
| rsa.file.directory_dst | \<span\>This key is used to capture the directory of the target process or file\</span\> | keyword |
| rsa.file.directory_src | This key is used to capture the directory of the source process or file | keyword |
| rsa.file.file_entropy | This is used to capture entropy vale of a file | double |
| rsa.file.file_vendor | This is used to capture Company name of file located in version_info | keyword |
| rsa.file.filename_dst | This is used to capture name of the file targeted by the action | keyword |
| rsa.file.filename_src | This is used to capture name of the parent filename, the file which performed the action | keyword |
| rsa.file.filename_tmp |  | keyword |
| rsa.file.filesystem |  | keyword |
| rsa.file.privilege | Deprecated, use permissions | keyword |
| rsa.file.task_name | This is used to capture name of the task | keyword |
| rsa.healthcare.patient_fname | This key is for First Names only, this is used for Healthcare predominantly to capture Patients information | keyword |
| rsa.healthcare.patient_id | This key captures the unique ID for a patient | keyword |
| rsa.healthcare.patient_lname | This key is for Last Names only, this is used for Healthcare predominantly to capture Patients information | keyword |
| rsa.healthcare.patient_mname | This key is for Middle Names only, this is used for Healthcare predominantly to capture Patients information | keyword |
| rsa.identity.accesses | This key is used to capture actual privileges used in accessing an object | keyword |
| rsa.identity.auth_method | This key is used to capture authentication methods used only | keyword |
| rsa.identity.dn | X.500 (LDAP) Distinguished Name | keyword |
| rsa.identity.dn_dst | An X.500 (LDAP) Distinguished name that used in a context that indicates a Destination dn | keyword |
| rsa.identity.dn_src | An X.500 (LDAP) Distinguished name that is used in a context that indicates a Source dn | keyword |
| rsa.identity.federated_idp | This key is the federated Identity Provider. This is the server providing the authentication. | keyword |
| rsa.identity.federated_sp | This key is the Federated Service Provider. This is the application requesting authentication. | keyword |
| rsa.identity.firstname | This key is for First Names only, this is used for Healthcare predominantly to capture Patients information | keyword |
| rsa.identity.host_role | This key should only be used to capture the role of a Host Machine | keyword |
| rsa.identity.lastname | This key is for Last Names only, this is used for Healthcare predominantly to capture Patients information | keyword |
| rsa.identity.ldap | This key is for Uninterpreted LDAP values. Ldap Values that don’t have a clear query or response context | keyword |
| rsa.identity.ldap_query | This key is the Search criteria from an LDAP search | keyword |
| rsa.identity.ldap_response | This key is to capture Results from an LDAP search | keyword |
| rsa.identity.logon_type | This key is used to capture the type of logon method used. | keyword |
| rsa.identity.logon_type_desc | This key is used to capture the textual description of an integer logon type as stored in the meta key 'logon.type'. | keyword |
| rsa.identity.middlename | This key is for Middle Names only, this is used for Healthcare predominantly to capture Patients information | keyword |
| rsa.identity.org | This key captures the User organization | keyword |
| rsa.identity.owner | This is used to capture username the process or service is running as, the author of the task | keyword |
| rsa.identity.password | This key is for Passwords seen in any session, plain text or encrypted | keyword |
| rsa.identity.profile | This key is used to capture the user profile | keyword |
| rsa.identity.realm | Radius realm or similar grouping of accounts | keyword |
| rsa.identity.service_account | This key is a windows specific key, used for capturing name of the account a service (referenced in the event) is running under. Legacy Usage | keyword |
| rsa.identity.user_dept | User's Department Names only | keyword |
| rsa.identity.user_role | This key is used to capture the Role of a user only | keyword |
| rsa.identity.user_sid_dst | This key captures Destination User Session ID | keyword |
| rsa.identity.user_sid_src | This key captures Source User Session ID | keyword |
| rsa.internal.audit_class | Deprecated key defined only in table map. | keyword |
| rsa.internal.cid | This is the unique identifier used to identify a NetWitness Concentrator. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.internal.data | Deprecated key defined only in table map. | keyword |
| rsa.internal.dead | Deprecated key defined only in table map. | long |
| rsa.internal.device_class | This is the Classification of the Log Event Source under a predefined fixed set of Event Source Classifications. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.internal.device_group | This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.internal.device_host | This is the Hostname of the log Event Source sending the logs to NetWitness. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.internal.device_ip | This is the IPv4 address of the Log Event Source sending the logs to NetWitness. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | ip |
| rsa.internal.device_ipv6 | This is the IPv6 address of the Log Event Source sending the logs to NetWitness. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | ip |
| rsa.internal.device_type | This is the name of the log parser which parsed a given session. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.internal.device_type_id | Deprecated key defined only in table map. | long |
| rsa.internal.did | This is the unique identifier used to identify a NetWitness Decoder. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.internal.entropy_req | This key is only used by the Entropy Parser, the Meta Type can be either UInt16 or Float32 based on the configuration | long |
| rsa.internal.entropy_res | This key is only used by the Entropy Parser, the Meta Type can be either UInt16 or Float32 based on the configuration | long |
| rsa.internal.entry | Deprecated key defined only in table map. | keyword |
| rsa.internal.event_desc |  | keyword |
| rsa.internal.event_name | Deprecated key defined only in table map. | keyword |
| rsa.internal.feed_category | This is used to capture the category of the feed. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.internal.feed_desc | This is used to capture the description of the feed. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.internal.feed_name | This is used to capture the name of the feed. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.internal.forward_ip | This key should be used to capture the IPV4 address of a relay system which forwarded the events from the original system to NetWitness. | ip |
| rsa.internal.forward_ipv6 | This key is used to capture the IPV6 address of a relay system which forwarded the events from the original system to NetWitness. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | ip |
| rsa.internal.hcode | Deprecated key defined only in table map. | keyword |
| rsa.internal.header_id | This is the Header ID value that identifies the exact log parser header definition that parses a particular log session. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.internal.inode | Deprecated key defined only in table map. | long |
| rsa.internal.lc_cid | This is a unique Identifier of a Log Collector. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.internal.lc_ctime | This is the time at which a log is collected in a NetWitness Log Collector. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | date |
| rsa.internal.level | Deprecated key defined only in table map. | long |
| rsa.internal.mcb_req | This key is only used by the Entropy Parser, the most common byte request is simply which byte for each side (0 thru 255) was seen the most | long |
| rsa.internal.mcb_res | This key is only used by the Entropy Parser, the most common byte response is simply which byte for each side (0 thru 255) was seen the most | long |
| rsa.internal.mcbc_req | This key is only used by the Entropy Parser, the most common byte count is the number of times the most common byte (above) was seen in the session streams | long |
| rsa.internal.mcbc_res | This key is only used by the Entropy Parser, the most common byte count is the number of times the most common byte (above) was seen in the session streams | long |
| rsa.internal.medium | This key is used to identify if it’s a log/packet session or Layer 2 Encapsulation Type. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness. 32 = log, 33 = correlation session, &lt; 32 is packet session | long |
| rsa.internal.message | This key captures the contents of instant messages | keyword |
| rsa.internal.messageid |  | keyword |
| rsa.internal.msg | This key is used to capture the raw message that comes into the Log Decoder | keyword |
| rsa.internal.msg_id | This is the Message ID1 value that identifies the exact log parser definition which parses a particular log session. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.internal.msg_vid | This is the Message ID2 value that identifies the exact log parser definition which parses a particular log session. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.internal.node_name | Deprecated key defined only in table map. | keyword |
| rsa.internal.nwe_callback_id | This key denotes that event is endpoint related | keyword |
| rsa.internal.obj_id | Deprecated key defined only in table map. | keyword |
| rsa.internal.obj_server | Deprecated key defined only in table map. | keyword |
| rsa.internal.obj_val | Deprecated key defined only in table map. | keyword |
| rsa.internal.parse_error | This is a special key that stores any Meta key validation error found while parsing a log session. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.internal.payload_req | This key is only used by the Entropy Parser, the payload size metrics are the payload sizes of each session side at the time of parsing. However, in order to keep | long |
| rsa.internal.payload_res | This key is only used by the Entropy Parser, the payload size metrics are the payload sizes of each session side at the time of parsing. However, in order to keep | long |
| rsa.internal.process_vid_dst | Endpoint generates and uses a unique virtual ID to identify any similar group of process. This ID represents the target process. | keyword |
| rsa.internal.process_vid_src | Endpoint generates and uses a unique virtual ID to identify any similar group of process. This ID represents the source process. | keyword |
| rsa.internal.resource | Deprecated key defined only in table map. | keyword |
| rsa.internal.resource_class | Deprecated key defined only in table map. | keyword |
| rsa.internal.rid | This is a special ID of the Remote Session created by NetWitness Decoder. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | long |
| rsa.internal.session_split | This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.internal.site | Deprecated key defined only in table map. | keyword |
| rsa.internal.size | This is the size of the session as seen by the NetWitness Decoder. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | long |
| rsa.internal.sourcefile | This is the name of the log file or PCAPs that can be imported into NetWitness. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.internal.statement | Deprecated key defined only in table map. | keyword |
| rsa.internal.time | This is the time at which a session hits a NetWitness Decoder. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness. | date |
| rsa.internal.ubc_req | This key is only used by the Entropy Parser, Unique byte count is the number of unique bytes seen in each stream. 256 would mean all byte values of 0 thru 255 were seen at least once | long |
| rsa.internal.ubc_res | This key is only used by the Entropy Parser, Unique byte count is the number of unique bytes seen in each stream. 256 would mean all byte values of 0 thru 255 were seen at least once | long |
| rsa.internal.word | This is used by the Word Parsing technology to capture the first 5 character of every word in an unparsed log | keyword |
| rsa.investigations.analysis_file | This is used to capture all indicators used in a File Analysis. This key should be used to capture an analysis of a file | keyword |
| rsa.investigations.analysis_service | This is used to capture all indicators used in a Service Analysis. This key should be used to capture an analysis of a service | keyword |
| rsa.investigations.analysis_session | This is used to capture all indicators used for a Session Analysis. This key should be used to capture an analysis of a session | keyword |
| rsa.investigations.boc | This is used to capture behaviour of compromise | keyword |
| rsa.investigations.ec_activity | This key captures the particular event activity(Ex:Logoff) | keyword |
| rsa.investigations.ec_outcome | This key captures the outcome of a particular Event(Ex:Success) | keyword |
| rsa.investigations.ec_subject | This key captures the Subject of a particular Event(Ex:User) | keyword |
| rsa.investigations.ec_theme | This key captures the Theme of a particular Event(Ex:Authentication) | keyword |
| rsa.investigations.eoc | This is used to capture Enablers of Compromise | keyword |
| rsa.investigations.event_cat | This key captures the Event category number | long |
| rsa.investigations.event_cat_name | This key captures the event category name corresponding to the event cat code | keyword |
| rsa.investigations.event_vcat | This is a vendor supplied category. This should be used in situations where the vendor has adopted their own event_category taxonomy. | keyword |
| rsa.investigations.inv_category | This used to capture investigation category | keyword |
| rsa.investigations.inv_context | This used to capture investigation context | keyword |
| rsa.investigations.ioc | This is key capture indicator of compromise | keyword |
| rsa.misc.OS | This key captures the Name of the Operating System | keyword |
| rsa.misc.acl_id |  | keyword |
| rsa.misc.acl_op |  | keyword |
| rsa.misc.acl_pos |  | keyword |
| rsa.misc.acl_table |  | keyword |
| rsa.misc.action |  | keyword |
| rsa.misc.admin |  | keyword |
| rsa.misc.agent_id | This key is used to capture agent id | keyword |
| rsa.misc.alarm_id |  | keyword |
| rsa.misc.alarmname |  | keyword |
| rsa.misc.alert_id | Deprecated, New Hunting Model (inv.\*, ioc, boc, eoc, analysis.\*) | keyword |
| rsa.misc.app_id |  | keyword |
| rsa.misc.audit |  | keyword |
| rsa.misc.audit_object |  | keyword |
| rsa.misc.auditdata |  | keyword |
| rsa.misc.autorun_type | This is used to capture Auto Run type | keyword |
| rsa.misc.benchmark |  | keyword |
| rsa.misc.bypass |  | keyword |
| rsa.misc.cache |  | keyword |
| rsa.misc.cache_hit |  | keyword |
| rsa.misc.category | This key is used to capture the category of an event given by the vendor in the session | keyword |
| rsa.misc.cc_number | Valid Credit Card Numbers only | long |
| rsa.misc.cefversion |  | keyword |
| rsa.misc.cfg_attr |  | keyword |
| rsa.misc.cfg_obj |  | keyword |
| rsa.misc.cfg_path |  | keyword |
| rsa.misc.change_attrib | This key is used to capture the name of the attribute that’s changing in a session | keyword |
| rsa.misc.change_new | This key is used to capture the new values of the attribute that’s changing in a session | keyword |
| rsa.misc.change_old | This key is used to capture the old value of the attribute that’s changing in a session | keyword |
| rsa.misc.changes |  | keyword |
| rsa.misc.checksum | This key is used to capture the checksum or hash of the entity such as a file or process. Checksum should be used over checksum.src or checksum.dst when it is unclear whether the entity is a source or target of an action. | keyword |
| rsa.misc.checksum_dst | This key is used to capture the checksum or hash of the the target entity such as a process or file. | keyword |
| rsa.misc.checksum_src | This key is used to capture the checksum or hash of the source entity such as a file or process. | keyword |
| rsa.misc.client | This key is used to capture only the name of the client application requesting resources of the server. See the user.agent meta key for capture of the specific user agent identifier or browser identification string. | keyword |
| rsa.misc.client_ip |  | keyword |
| rsa.misc.clustermembers |  | keyword |
| rsa.misc.cmd |  | keyword |
| rsa.misc.cn_acttimeout |  | keyword |
| rsa.misc.cn_asn_src |  | keyword |
| rsa.misc.cn_bgpv4nxthop |  | keyword |
| rsa.misc.cn_ctr_dst_code |  | keyword |
| rsa.misc.cn_dst_tos |  | keyword |
| rsa.misc.cn_dst_vlan |  | keyword |
| rsa.misc.cn_engine_id |  | keyword |
| rsa.misc.cn_engine_type |  | keyword |
| rsa.misc.cn_f_switch |  | keyword |
| rsa.misc.cn_flowsampid |  | keyword |
| rsa.misc.cn_flowsampintv |  | keyword |
| rsa.misc.cn_flowsampmode |  | keyword |
| rsa.misc.cn_inacttimeout |  | keyword |
| rsa.misc.cn_inpermbyts |  | keyword |
| rsa.misc.cn_inpermpckts |  | keyword |
| rsa.misc.cn_invalid |  | keyword |
| rsa.misc.cn_ip_proto_ver |  | keyword |
| rsa.misc.cn_ipv4_ident |  | keyword |
| rsa.misc.cn_l_switch |  | keyword |
| rsa.misc.cn_log_did |  | keyword |
| rsa.misc.cn_log_rid |  | keyword |
| rsa.misc.cn_max_ttl |  | keyword |
| rsa.misc.cn_maxpcktlen |  | keyword |
| rsa.misc.cn_min_ttl |  | keyword |
| rsa.misc.cn_minpcktlen |  | keyword |
| rsa.misc.cn_mpls_lbl_1 |  | keyword |
| rsa.misc.cn_mpls_lbl_10 |  | keyword |
| rsa.misc.cn_mpls_lbl_2 |  | keyword |
| rsa.misc.cn_mpls_lbl_3 |  | keyword |
| rsa.misc.cn_mpls_lbl_4 |  | keyword |
| rsa.misc.cn_mpls_lbl_5 |  | keyword |
| rsa.misc.cn_mpls_lbl_6 |  | keyword |
| rsa.misc.cn_mpls_lbl_7 |  | keyword |
| rsa.misc.cn_mpls_lbl_8 |  | keyword |
| rsa.misc.cn_mpls_lbl_9 |  | keyword |
| rsa.misc.cn_mplstoplabel |  | keyword |
| rsa.misc.cn_mplstoplabip |  | keyword |
| rsa.misc.cn_mul_dst_byt |  | keyword |
| rsa.misc.cn_mul_dst_pks |  | keyword |
| rsa.misc.cn_muligmptype |  | keyword |
| rsa.misc.cn_sampalgo |  | keyword |
| rsa.misc.cn_sampint |  | keyword |
| rsa.misc.cn_seqctr |  | keyword |
| rsa.misc.cn_spackets |  | keyword |
| rsa.misc.cn_src_tos |  | keyword |
| rsa.misc.cn_src_vlan |  | keyword |
| rsa.misc.cn_sysuptime |  | keyword |
| rsa.misc.cn_template_id |  | keyword |
| rsa.misc.cn_totbytsexp |  | keyword |
| rsa.misc.cn_totflowexp |  | keyword |
| rsa.misc.cn_totpcktsexp |  | keyword |
| rsa.misc.cn_unixnanosecs |  | keyword |
| rsa.misc.cn_v6flowlabel |  | keyword |
| rsa.misc.cn_v6optheaders |  | keyword |
| rsa.misc.code |  | keyword |
| rsa.misc.command |  | keyword |
| rsa.misc.comments | Comment information provided in the log message | keyword |
| rsa.misc.comp_class |  | keyword |
| rsa.misc.comp_name |  | keyword |
| rsa.misc.comp_rbytes |  | keyword |
| rsa.misc.comp_sbytes |  | keyword |
| rsa.misc.comp_version | This key captures the Version level of a sub-component of a product. | keyword |
| rsa.misc.connection_id | This key captures the Connection ID | keyword |
| rsa.misc.content | This key captures the content type from protocol headers | keyword |
| rsa.misc.content_type | This key is used to capture Content Type only. | keyword |
| rsa.misc.content_version | This key captures Version level of a signature or database content. | keyword |
| rsa.misc.context | This key captures Information which adds additional context to the event. | keyword |
| rsa.misc.context_subject | This key is to be used in an audit context where the subject is the object being identified | keyword |
| rsa.misc.context_target |  | keyword |
| rsa.misc.count |  | keyword |
| rsa.misc.cpu | This key is the CPU time used in the execution of the event being recorded. | long |
| rsa.misc.cpu_data |  | keyword |
| rsa.misc.criticality |  | keyword |
| rsa.misc.cs_agency_dst |  | keyword |
| rsa.misc.cs_analyzedby |  | keyword |
| rsa.misc.cs_av_other |  | keyword |
| rsa.misc.cs_av_primary |  | keyword |
| rsa.misc.cs_av_secondary |  | keyword |
| rsa.misc.cs_bgpv6nxthop |  | keyword |
| rsa.misc.cs_bit9status |  | keyword |
| rsa.misc.cs_context |  | keyword |
| rsa.misc.cs_control |  | keyword |
| rsa.misc.cs_data |  | keyword |
| rsa.misc.cs_datecret |  | keyword |
| rsa.misc.cs_dst_tld |  | keyword |
| rsa.misc.cs_eth_dst_ven |  | keyword |
| rsa.misc.cs_eth_src_ven |  | keyword |
| rsa.misc.cs_event_uuid |  | keyword |
| rsa.misc.cs_filetype |  | keyword |
| rsa.misc.cs_fld |  | keyword |
| rsa.misc.cs_if_desc |  | keyword |
| rsa.misc.cs_if_name |  | keyword |
| rsa.misc.cs_ip_next_hop |  | keyword |
| rsa.misc.cs_ipv4dstpre |  | keyword |
| rsa.misc.cs_ipv4srcpre |  | keyword |
| rsa.misc.cs_lifetime |  | keyword |
| rsa.misc.cs_log_medium |  | keyword |
| rsa.misc.cs_loginname |  | keyword |
| rsa.misc.cs_modulescore |  | keyword |
| rsa.misc.cs_modulesign |  | keyword |
| rsa.misc.cs_opswatresult |  | keyword |
| rsa.misc.cs_payload |  | keyword |
| rsa.misc.cs_registrant |  | keyword |
| rsa.misc.cs_registrar |  | keyword |
| rsa.misc.cs_represult |  | keyword |
| rsa.misc.cs_rpayload |  | keyword |
| rsa.misc.cs_sampler_name |  | keyword |
| rsa.misc.cs_sourcemodule |  | keyword |
| rsa.misc.cs_streams |  | keyword |
| rsa.misc.cs_targetmodule |  | keyword |
| rsa.misc.cs_v6nxthop |  | keyword |
| rsa.misc.cs_whois_server |  | keyword |
| rsa.misc.cs_yararesult |  | keyword |
| rsa.misc.cve | This key captures CVE (Common Vulnerabilities and Exposures) - an identifier for known information security vulnerabilities. | keyword |
| rsa.misc.data_type |  | keyword |
| rsa.misc.description |  | keyword |
| rsa.misc.device_name | This is used to capture name of the Device associated with the node Like: a physical disk, printer, etc | keyword |
| rsa.misc.devvendor |  | keyword |
| rsa.misc.disposition | This key captures the The end state of an action. | keyword |
| rsa.misc.distance |  | keyword |
| rsa.misc.doc_number | This key captures File Identification number | long |
| rsa.misc.dstburb |  | keyword |
| rsa.misc.edomain |  | keyword |
| rsa.misc.edomaub |  | keyword |
| rsa.misc.ein_number | Employee Identification Numbers only | long |
| rsa.misc.error | This key captures All non successful Error codes or responses | keyword |
| rsa.misc.euid |  | keyword |
| rsa.misc.event_category |  | keyword |
| rsa.misc.event_computer | This key is a windows only concept, where this key is used to capture fully qualified domain name in a windows log. | keyword |
| rsa.misc.event_desc | This key is used to capture a description of an event available directly or inferred | keyword |
| rsa.misc.event_id |  | keyword |
| rsa.misc.event_log | This key captures the Name of the event log | keyword |
| rsa.misc.event_source | This key captures Source of the event that’s not a hostname | keyword |
| rsa.misc.event_state | This key captures the current state of the object/item referenced within the event. Describing an on-going event. | keyword |
| rsa.misc.event_type | This key captures the event category type as specified by the event source. | keyword |
| rsa.misc.event_user | This key is a windows only concept, where this key is used to capture combination of domain name and username in a windows log. | keyword |
| rsa.misc.expected_val | This key captures the Value expected (from the perspective of the device generating the log). | keyword |
| rsa.misc.facility |  | keyword |
| rsa.misc.facilityname |  | keyword |
| rsa.misc.fcatnum | This key captures Filter Category Number. Legacy Usage | keyword |
| rsa.misc.filter | This key captures Filter used to reduce result set | keyword |
| rsa.misc.finterface |  | keyword |
| rsa.misc.flags |  | keyword |
| rsa.misc.forensic_info |  | keyword |
| rsa.misc.found | This is used to capture the results of regex match | keyword |
| rsa.misc.fresult | This key captures the Filter Result | long |
| rsa.misc.gaddr |  | keyword |
| rsa.misc.group | This key captures the Group Name value | keyword |
| rsa.misc.group_id | This key captures Group ID Number (related to the group name) | keyword |
| rsa.misc.group_object | This key captures a collection/grouping of entities. Specific usage | keyword |
| rsa.misc.hardware_id | This key is used to capture unique identifier for a device or system (NOT a Mac address) | keyword |
| rsa.misc.id3 |  | keyword |
| rsa.misc.im_buddyid |  | keyword |
| rsa.misc.im_buddyname |  | keyword |
| rsa.misc.im_client |  | keyword |
| rsa.misc.im_croomid |  | keyword |
| rsa.misc.im_croomtype |  | keyword |
| rsa.misc.im_members |  | keyword |
| rsa.misc.im_userid |  | keyword |
| rsa.misc.im_username |  | keyword |
| rsa.misc.index |  | keyword |
| rsa.misc.inout |  | keyword |
| rsa.misc.ipkt |  | keyword |
| rsa.misc.ipscat |  | keyword |
| rsa.misc.ipspri |  | keyword |
| rsa.misc.job_num | This key captures the Job Number | keyword |
| rsa.misc.jobname |  | keyword |
| rsa.misc.language | This is used to capture list of languages the client support and what it prefers | keyword |
| rsa.misc.latitude |  | keyword |
| rsa.misc.library | This key is used to capture library information in mainframe devices | keyword |
| rsa.misc.lifetime | This key is used to capture the session lifetime in seconds. | long |
| rsa.misc.linenum |  | keyword |
| rsa.misc.link | This key is used to link the sessions together. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.misc.list_name |  | keyword |
| rsa.misc.listnum | This key is used to capture listname or listnumber, primarily for collecting access-list | keyword |
| rsa.misc.load_data |  | keyword |
| rsa.misc.location_floor |  | keyword |
| rsa.misc.location_mark |  | keyword |
| rsa.misc.log_id |  | keyword |
| rsa.misc.log_session_id | This key is used to capture a sessionid from the session directly | keyword |
| rsa.misc.log_session_id1 | This key is used to capture a Linked (Related) Session ID from the session directly | keyword |
| rsa.misc.log_type |  | keyword |
| rsa.misc.logid |  | keyword |
| rsa.misc.logip |  | keyword |
| rsa.misc.logname |  | keyword |
| rsa.misc.longitude |  | keyword |
| rsa.misc.lport |  | keyword |
| rsa.misc.mail_id | This key is used to capture the mailbox id/name | keyword |
| rsa.misc.match | This key is for regex match name from search.ini | keyword |
| rsa.misc.mbug_data |  | keyword |
| rsa.misc.message_body | This key captures the The contents of the message body. | keyword |
| rsa.misc.misc |  | keyword |
| rsa.misc.misc_name |  | keyword |
| rsa.misc.mode |  | keyword |
| rsa.misc.msgIdPart1 |  | keyword |
| rsa.misc.msgIdPart2 |  | keyword |
| rsa.misc.msgIdPart3 |  | keyword |
| rsa.misc.msgIdPart4 |  | keyword |
| rsa.misc.msg_type |  | keyword |
| rsa.misc.msgid |  | keyword |
| rsa.misc.name |  | keyword |
| rsa.misc.netsessid |  | keyword |
| rsa.misc.node | Common use case is the node name within a cluster. The cluster name is reflected by the host name. | keyword |
| rsa.misc.ntype |  | keyword |
| rsa.misc.num |  | keyword |
| rsa.misc.number |  | keyword |
| rsa.misc.number1 |  | keyword |
| rsa.misc.number2 |  | keyword |
| rsa.misc.nwwn |  | keyword |
| rsa.misc.obj_name | This is used to capture name of object | keyword |
| rsa.misc.obj_type | This is used to capture type of object | keyword |
| rsa.misc.object |  | keyword |
| rsa.misc.observed_val | This key captures the Value observed (from the perspective of the device generating the log). | keyword |
| rsa.misc.operation |  | keyword |
| rsa.misc.operation_id | An alert number or operation number. The values should be unique and non-repeating. | keyword |
| rsa.misc.opkt |  | keyword |
| rsa.misc.orig_from |  | keyword |
| rsa.misc.owner_id |  | keyword |
| rsa.misc.p_action |  | keyword |
| rsa.misc.p_filter |  | keyword |
| rsa.misc.p_group_object |  | keyword |
| rsa.misc.p_id |  | keyword |
| rsa.misc.p_msgid |  | keyword |
| rsa.misc.p_msgid1 |  | keyword |
| rsa.misc.p_msgid2 |  | keyword |
| rsa.misc.p_result1 |  | keyword |
| rsa.misc.param | This key is the parameters passed as part of a command or application, etc. | keyword |
| rsa.misc.param_dst | This key captures the command line/launch argument of the target process or file | keyword |
| rsa.misc.param_src | This key captures source parameter | keyword |
| rsa.misc.parent_node | This key captures the Parent Node Name. Must be related to node variable. | keyword |
| rsa.misc.password_chg |  | keyword |
| rsa.misc.password_expire |  | keyword |
| rsa.misc.payload_dst | This key is used to capture destination payload | keyword |
| rsa.misc.payload_src | This key is used to capture source payload | keyword |
| rsa.misc.permgranted |  | keyword |
| rsa.misc.permwanted |  | keyword |
| rsa.misc.pgid |  | keyword |
| rsa.misc.phone |  | keyword |
| rsa.misc.pid |  | keyword |
| rsa.misc.policy |  | keyword |
| rsa.misc.policyUUID |  | keyword |
| rsa.misc.policy_id | This key is used to capture the Policy ID only, this should be a numeric value, use policy.name otherwise | keyword |
| rsa.misc.policy_name | This key is used to capture the Policy Name only. | keyword |
| rsa.misc.policy_value | This key captures the contents of the policy. This contains details about the policy | keyword |
| rsa.misc.policy_waiver |  | keyword |
| rsa.misc.pool_id | This key captures the identifier (typically numeric field) of a resource pool | keyword |
| rsa.misc.pool_name | This key captures the name of a resource pool | keyword |
| rsa.misc.port_name | This key is used for Physical or logical port connection but does NOT include a network port. (Example: Printer port name). | keyword |
| rsa.misc.priority |  | keyword |
| rsa.misc.process_id_val | This key is a failure key for Process ID when it is not an integer value | keyword |
| rsa.misc.prog_asp_num |  | keyword |
| rsa.misc.program |  | keyword |
| rsa.misc.real_data |  | keyword |
| rsa.misc.reason |  | keyword |
| rsa.misc.rec_asp_device |  | keyword |
| rsa.misc.rec_asp_num |  | keyword |
| rsa.misc.rec_library |  | keyword |
| rsa.misc.recordnum |  | keyword |
| rsa.misc.reference_id | This key is used to capture an event id from the session directly | keyword |
| rsa.misc.reference_id1 | This key is for Linked ID to be used as an addition to "reference.id" | keyword |
| rsa.misc.reference_id2 | This key is for the 2nd Linked ID. Can be either linked to "reference.id" or "reference.id1" value but should not be used unless the other two variables are in play. | keyword |
| rsa.misc.result | This key is used to capture the outcome/result string value of an action in a session. | keyword |
| rsa.misc.result_code | This key is used to capture the outcome/result numeric value of an action in a session | keyword |
| rsa.misc.risk | This key captures the non-numeric risk value | keyword |
| rsa.misc.risk_info | Deprecated, use New Hunting Model (inv.\*, ioc, boc, eoc, analysis.\*) | keyword |
| rsa.misc.risk_num | This key captures a Numeric Risk value | double |
| rsa.misc.risk_num_comm | This key captures Risk Number Community | double |
| rsa.misc.risk_num_next | This key captures Risk Number NextGen | double |
| rsa.misc.risk_num_sand | This key captures Risk Number SandBox | double |
| rsa.misc.risk_num_static | This key captures Risk Number Static | double |
| rsa.misc.risk_suspicious | Deprecated, use New Hunting Model (inv.\*, ioc, boc, eoc, analysis.\*) | keyword |
| rsa.misc.risk_warning | Deprecated, use New Hunting Model (inv.\*, ioc, boc, eoc, analysis.\*) | keyword |
| rsa.misc.ruid |  | keyword |
| rsa.misc.rule | This key captures the Rule number | keyword |
| rsa.misc.rule_group | This key captures the Rule group name | keyword |
| rsa.misc.rule_name | This key captures the Rule Name | keyword |
| rsa.misc.rule_template | A default set of parameters which are overlayed onto a rule (or rulename) which efffectively constitutes a template | keyword |
| rsa.misc.rule_uid | This key is the Unique Identifier for a rule. | keyword |
| rsa.misc.sburb |  | keyword |
| rsa.misc.sdomain_fld |  | keyword |
| rsa.misc.search_text | This key captures the Search Text used | keyword |
| rsa.misc.sec |  | keyword |
| rsa.misc.second |  | keyword |
| rsa.misc.sensor | This key captures Name of the sensor. Typically used in IDS/IPS based devices | keyword |
| rsa.misc.sensorname |  | keyword |
| rsa.misc.seqnum |  | keyword |
| rsa.misc.serial_number | This key is the Serial number associated with a physical asset. | keyword |
| rsa.misc.session |  | keyword |
| rsa.misc.sessiontype |  | keyword |
| rsa.misc.severity | This key is used to capture the severity given the session | keyword |
| rsa.misc.sigUUID |  | keyword |
| rsa.misc.sig_id | This key captures IDS/IPS Int Signature ID | long |
| rsa.misc.sig_id1 | This key captures IDS/IPS Int Signature ID. This must be linked to the sig.id | long |
| rsa.misc.sig_id_str | This key captures a string object of the sigid variable. | keyword |
| rsa.misc.sig_name | This key is used to capture the Signature Name only. | keyword |
| rsa.misc.sigcat |  | keyword |
| rsa.misc.snmp_oid | SNMP Object Identifier | keyword |
| rsa.misc.snmp_value | SNMP set request value | keyword |
| rsa.misc.space |  | keyword |
| rsa.misc.space1 |  | keyword |
| rsa.misc.spi |  | keyword |
| rsa.misc.spi_dst | Destination SPI Index | keyword |
| rsa.misc.spi_src | Source SPI Index | keyword |
| rsa.misc.sql | This key captures the SQL query | keyword |
| rsa.misc.srcburb |  | keyword |
| rsa.misc.srcdom |  | keyword |
| rsa.misc.srcservice |  | keyword |
| rsa.misc.state |  | keyword |
| rsa.misc.status |  | keyword |
| rsa.misc.status1 |  | keyword |
| rsa.misc.streams | This key captures number of streams in session | long |
| rsa.misc.subcategory |  | keyword |
| rsa.misc.svcno |  | keyword |
| rsa.misc.system |  | keyword |
| rsa.misc.tbdstr1 |  | keyword |
| rsa.misc.tbdstr2 |  | keyword |
| rsa.misc.tcp_flags | This key is captures the TCP flags set in any packet of session | long |
| rsa.misc.terminal | This key captures the Terminal Names only | keyword |
| rsa.misc.tgtdom |  | keyword |
| rsa.misc.tgtdomain |  | keyword |
| rsa.misc.threshold |  | keyword |
| rsa.misc.tos | This key describes the type of service | long |
| rsa.misc.trigger_desc | This key captures the Description of the trigger or threshold condition. | keyword |
| rsa.misc.trigger_val | This key captures the Value of the trigger or threshold condition. | keyword |
| rsa.misc.type |  | keyword |
| rsa.misc.type1 |  | keyword |
| rsa.misc.udb_class |  | keyword |
| rsa.misc.url_fld |  | keyword |
| rsa.misc.user_div |  | keyword |
| rsa.misc.userid |  | keyword |
| rsa.misc.username_fld |  | keyword |
| rsa.misc.utcstamp |  | keyword |
| rsa.misc.v_instafname |  | keyword |
| rsa.misc.version | This key captures Version of the application or OS which is generating the event. | keyword |
| rsa.misc.virt_data |  | keyword |
| rsa.misc.virusname | This key captures the name of the virus | keyword |
| rsa.misc.vm_target | VMWare Target \*\*VMWARE\*\* only varaible. | keyword |
| rsa.misc.vpnid |  | keyword |
| rsa.misc.vsys | This key captures Virtual System Name | keyword |
| rsa.misc.vuln_ref | This key captures the Vulnerability Reference details | keyword |
| rsa.misc.workspace | This key captures Workspace Description | keyword |
| rsa.network.ad_computer_dst | Deprecated, use host.dst | keyword |
| rsa.network.addr |  | keyword |
| rsa.network.alias_host | This key should be used when the source or destination context of a hostname is not clear.Also it captures the Device Hostname. Any Hostname that isnt ad.computer. | keyword |
| rsa.network.dinterface | This key should only be used when it’s a Destination Interface | keyword |
| rsa.network.dmask | This key is used for Destionation Device network mask | keyword |
| rsa.network.dns_a_record |  | keyword |
| rsa.network.dns_cname_record |  | keyword |
| rsa.network.dns_id |  | keyword |
| rsa.network.dns_opcode |  | keyword |
| rsa.network.dns_ptr_record |  | keyword |
| rsa.network.dns_resp |  | keyword |
| rsa.network.dns_type |  | keyword |
| rsa.network.domain |  | keyword |
| rsa.network.domain1 |  | keyword |
| rsa.network.eth_host | Deprecated, use alias.mac | keyword |
| rsa.network.eth_type | This key is used to capture Ethernet Type, Used for Layer 3 Protocols Only | long |
| rsa.network.faddr |  | keyword |
| rsa.network.fhost |  | keyword |
| rsa.network.fport |  | keyword |
| rsa.network.gateway | This key is used to capture the IP Address of the gateway | keyword |
| rsa.network.host_dst | This key should only be used when it’s a Destination Hostname | keyword |
| rsa.network.host_orig | This is used to capture the original hostname in case of a Forwarding Agent or a Proxy in between. | keyword |
| rsa.network.host_type |  | keyword |
| rsa.network.icmp_code | This key is used to capture the ICMP code only | long |
| rsa.network.icmp_type | This key is used to capture the ICMP type only | long |
| rsa.network.interface | This key should be used when the source or destination context of an interface is not clear | keyword |
| rsa.network.ip_proto | This key should be used to capture the Protocol number, all the protocol nubers are converted into string in UI | long |
| rsa.network.laddr |  | keyword |
| rsa.network.lhost |  | keyword |
| rsa.network.linterface |  | keyword |
| rsa.network.mask | This key is used to capture the device network IPmask. | keyword |
| rsa.network.netname | This key is used to capture the network name associated with an IP range. This is configured by the end user. | keyword |
| rsa.network.network_port | Deprecated, use port. NOTE: There is a type discrepancy as currently used, TM: Int32, INDEX: UInt64 (why neither chose the correct UInt16?!) | long |
| rsa.network.network_service | This is used to capture layer 7 protocols/service names | keyword |
| rsa.network.origin |  | keyword |
| rsa.network.packet_length |  | keyword |
| rsa.network.paddr | Deprecated | ip |
| rsa.network.phost |  | keyword |
| rsa.network.port | This key should only be used to capture a Network Port when the directionality is not clear | long |
| rsa.network.protocol_detail | This key should be used to capture additional protocol information | keyword |
| rsa.network.remote_domain_id |  | keyword |
| rsa.network.rpayload | This key is used to capture the total number of payload bytes seen in the retransmitted packets. | keyword |
| rsa.network.sinterface | This key should only be used when it’s a Source Interface | keyword |
| rsa.network.smask | This key is used for capturing source Network Mask | keyword |
| rsa.network.vlan | This key should only be used to capture the ID of the Virtual LAN | long |
| rsa.network.vlan_name | This key should only be used to capture the name of the Virtual LAN | keyword |
| rsa.network.zone | This key should be used when the source or destination context of a Zone is not clear | keyword |
| rsa.network.zone_dst | This key should only be used when it’s a Destination Zone. | keyword |
| rsa.network.zone_src | This key should only be used when it’s a Source Zone. | keyword |
| rsa.physical.org_dst | This is used to capture the destination organization based on the GEOPIP Maxmind database. | keyword |
| rsa.physical.org_src | This is used to capture the source organization based on the GEOPIP Maxmind database. | keyword |
| rsa.storage.disk_volume | A unique name assigned to logical units (volumes) within a physical disk | keyword |
| rsa.storage.lun | Logical Unit Number.This key is a very useful concept in Storage. | keyword |
| rsa.storage.pwwn | This uniquely identifies a port on a HBA. | keyword |
| rsa.threat.alert | This key is used to capture name of the alert | keyword |
| rsa.threat.threat_category | This key captures Threat Name/Threat Category/Categorization of alert | keyword |
| rsa.threat.threat_desc | This key is used to capture the threat description from the session directly or inferred | keyword |
| rsa.threat.threat_source | This key is used to capture source of the threat | keyword |
| rsa.time.date |  | keyword |
| rsa.time.datetime |  | keyword |
| rsa.time.day |  | keyword |
| rsa.time.duration_str | A text string version of the duration | keyword |
| rsa.time.duration_time | This key is used to capture the normalized duration/lifetime in seconds. | double |
| rsa.time.effective_time | This key is the effective time referenced by an individual event in a Standard Timestamp format | date |
| rsa.time.endtime | This key is used to capture the End time mentioned in a session in a standard form | date |
| rsa.time.event_queue_time | This key is the Time that the event was queued. | date |
| rsa.time.event_time | This key is used to capture the time mentioned in a raw session that represents the actual time an event occured in a standard normalized form | date |
| rsa.time.event_time_str | This key is used to capture the incomplete time mentioned in a session as a string | keyword |
| rsa.time.eventtime |  | keyword |
| rsa.time.expire_time | This key is the timestamp that explicitly refers to an expiration. | date |
| rsa.time.expire_time_str | This key is used to capture incomplete timestamp that explicitly refers to an expiration. | keyword |
| rsa.time.gmtdate |  | keyword |
| rsa.time.gmttime |  | keyword |
| rsa.time.hour |  | keyword |
| rsa.time.min |  | keyword |
| rsa.time.month |  | keyword |
| rsa.time.p_date |  | keyword |
| rsa.time.p_month |  | keyword |
| rsa.time.p_time |  | keyword |
| rsa.time.p_time1 |  | keyword |
| rsa.time.p_time2 |  | keyword |
| rsa.time.p_year |  | keyword |
| rsa.time.process_time | Deprecated, use duration.time | keyword |
| rsa.time.recorded_time | The event time as recorded by the system the event is collected from. The usage scenario is a multi-tier application where the management layer of the system records it's own timestamp at the time of collection from its child nodes. Must be in timestamp format. | date |
| rsa.time.stamp | Deprecated key defined only in table map. | date |
| rsa.time.starttime | This key is used to capture the Start time mentioned in a session in a standard form | date |
| rsa.time.timestamp |  | keyword |
| rsa.time.timezone | This key is used to capture the timezone of the Event Time | keyword |
| rsa.time.tzone |  | keyword |
| rsa.time.year |  | keyword |
| rsa.web.alias_host |  | keyword |
| rsa.web.cn_asn_dst |  | keyword |
| rsa.web.cn_rpackets |  | keyword |
| rsa.web.fqdn | Fully Qualified Domain Names | keyword |
| rsa.web.p_url |  | keyword |
| rsa.web.p_user_agent |  | keyword |
| rsa.web.p_web_cookie |  | keyword |
| rsa.web.p_web_method |  | keyword |
| rsa.web.p_web_referer |  | keyword |
| rsa.web.remote_domain |  | keyword |
| rsa.web.reputation_num | Reputation Number of an entity. Typically used for Web Domains | double |
| rsa.web.urlpage |  | keyword |
| rsa.web.urlroot |  | keyword |
| rsa.web.web_cookie | This key is used to capture the Web cookies specifically. | keyword |
| rsa.web.web_extension_tmp |  | keyword |
| rsa.web.web_page |  | keyword |
| rsa.web.web_ref_domain | Web referer's domain | keyword |
| rsa.web.web_ref_page | This key captures Web referer's page information | keyword |
| rsa.web.web_ref_query | This key captures Web referer's query portion of the URL | keyword |
| rsa.web.web_ref_root | Web referer's root URL path | keyword |
| rsa.wireless.access_point | This key is used to capture the access point name. | keyword |
| rsa.wireless.wlan_channel | This is used to capture the channel names | long |
| rsa.wireless.wlan_name | This key captures either WLAN number/name | keyword |
| rsa.wireless.wlan_ssid | This key is used to capture the ssid of a Wireless Session | keyword |
| rule.name | The name of the rule or signature generating the event. | keyword |
| server.domain | The domain name of the server system. This value may be a host name, a fully qualified domain name, or another host naming format. The value may derive from the original event or be added from enrichment. | keyword |
| server.registered_domain | The highest registered server domain, stripped of the subdomain. For example, the registered domain for "foo.example.com" is "example.com". This value can be determined precisely with a list like the public suffix list (http://publicsuffix.org). Trying to approximate this by simply taking the last two labels will not work well for TLDs such as "co.uk". | keyword |
| server.subdomain | The subdomain portion of a fully qualified domain name includes all of the names except the host name under the registered_domain.  In a partially qualified domain, or if the the qualification level of the full name cannot be determined, subdomain contains all of the names below the registered domain. For example the subdomain portion of "www.east.mydomain.co.uk" is "east". If the domain has multiple levels of subdomain, such as "sub2.sub1.example.com", the subdomain field should contain "sub2.sub1", with no trailing period. | keyword |
| server.top_level_domain | The effective top level domain (eTLD), also known as the domain suffix, is the last part of the domain name. For example, the top level domain for example.com is "com". This value can be determined precisely with a list like the public suffix list (http://publicsuffix.org). Trying to approximate this by simply taking the last label will not work well for effective TLDs such as "co.uk". | keyword |
| service.name | Name of the service data is collected from. The name of the service is normally user given. This allows for distributed services that run on multiple hosts to correlate the related instances based on the name. In the case of Elasticsearch the `service.name` could contain the cluster name. For Beats the `service.name` is by default a copy of the `service.type` field if no name is specified. | keyword |
| source.address | Some event source addresses are defined ambiguously. The event will sometimes list an IP, a domain or a unix socket.  You should always store the raw address in the `.address` field. Then it should be duplicated to `.ip` or `.domain`, depending on which one it is. | keyword |
| source.as.number | Unique number allocated to the autonomous system. The autonomous system number (ASN) uniquely identifies each network on the Internet. | long |
| source.as.organization.name | Organization name. | keyword |
| source.as.organization.name.text | Multi-field of `source.as.organization.name`. | match_only_text |
| source.bytes | Bytes sent from the source to the destination. | long |
| source.domain | The domain name of the source system. This value may be a host name, a fully qualified domain name, or another host naming format. The value may derive from the original event or be added from enrichment. | keyword |
| source.geo.city_name | City name. | keyword |
| source.geo.country_name | Country name. | keyword |
| source.geo.location | Longitude and latitude. | geo_point |
| source.ip | IP address of the source (IPv4 or IPv6). | ip |
| source.mac | MAC address of the source. The notation format from RFC 7042 is suggested: Each octet (that is, 8-bit byte) is represented by two [uppercase] hexadecimal digits giving the value of the octet as an unsigned integer. Successive octets are separated by a hyphen. | keyword |
| source.nat.ip | Translated ip of source based NAT sessions (e.g. internal client to internet) Typically connections traversing load balancers, firewalls, or routers. | ip |
| source.nat.port | Translated port of source based NAT sessions. (e.g. internal client to internet) Typically used with load balancers, firewalls, or routers. | long |
| source.port | Port of the source. | long |
| source.registered_domain | The highest registered source domain, stripped of the subdomain. For example, the registered domain for "foo.example.com" is "example.com". This value can be determined precisely with a list like the public suffix list (http://publicsuffix.org). Trying to approximate this by simply taking the last two labels will not work well for TLDs such as "co.uk". | keyword |
| source.subdomain | The subdomain portion of a fully qualified domain name includes all of the names except the host name under the registered_domain.  In a partially qualified domain, or if the the qualification level of the full name cannot be determined, subdomain contains all of the names below the registered domain. For example the subdomain portion of "www.east.mydomain.co.uk" is "east". If the domain has multiple levels of subdomain, such as "sub2.sub1.example.com", the subdomain field should contain "sub2.sub1", with no trailing period. | keyword |
| source.top_level_domain | The effective top level domain (eTLD), also known as the domain suffix, is the last part of the domain name. For example, the top level domain for example.com is "com". This value can be determined precisely with a list like the public suffix list (http://publicsuffix.org). Trying to approximate this by simply taking the last label will not work well for effective TLDs such as "co.uk". | keyword |
| tags | List of keywords used to tag each event. | keyword |
| url.domain | Domain of the url, such as "www.elastic.co". In some cases a URL may refer to an IP and/or port directly, without a domain name. In this case, the IP address would go to the `domain` field. If the URL contains a literal IPv6 address enclosed by `[` and `]` (IETF RFC 2732), the `[` and `]` characters should also be captured in the `domain` field. | keyword |
| url.original | Unmodified original url as seen in the event source. Note that in network monitoring, the observed URL may be a full URL, whereas in access logs, the URL is often just represented as a path. This field is meant to represent the URL as it was observed, complete or not. | wildcard |
| url.original.text | Multi-field of `url.original`. | match_only_text |
| url.path | Path of the request, such as "/search". | wildcard |
| url.query | The query field describes the query string of the request, such as "q=elasticsearch". The `?` is excluded from the query string. If a URL contains no `?`, there is no query field. If there is a `?` but no query, the query field exists with an empty string. The `exists` query can be used to differentiate between the two cases. | keyword |
| url.registered_domain | The highest registered url domain, stripped of the subdomain. For example, the registered domain for "foo.example.com" is "example.com". This value can be determined precisely with a list like the public suffix list (http://publicsuffix.org). Trying to approximate this by simply taking the last two labels will not work well for TLDs such as "co.uk". | keyword |
| url.top_level_domain | The effective top level domain (eTLD), also known as the domain suffix, is the last part of the domain name. For example, the top level domain for example.com is "com". This value can be determined precisely with a list like the public suffix list (http://publicsuffix.org). Trying to approximate this by simply taking the last label will not work well for effective TLDs such as "co.uk". | keyword |
| user.domain | Name of the directory the user is a member of. For example, an LDAP or Active Directory domain name. | keyword |
| user.full_name | User's full name, if available. | keyword |
| user.full_name.text | Multi-field of `user.full_name`. | match_only_text |
| user.id | Unique identifier of the user. | keyword |
| user.name | Short name or login of the user. | keyword |
| user.name.text | Multi-field of `user.name`. | match_only_text |
| user_agent.original | Unparsed user_agent string. | keyword |
| user_agent.original.text | Multi-field of `user_agent.original`. | match_only_text |


### Meraki

The `meraki` dataset collects Cisco Meraki logs.

An example event for `meraki` looks as following:

```json
{
    "@timestamp": "2016-01-29T06:09:59.000Z",
    "agent": {
        "ephemeral_id": "0f004ed2-0b2a-4215-8b24-e652cef37253",
        "hostname": "docker-fleet-agent",
        "id": "0a0be70a-90aa-494d-8be3-b06a8a05e08c",
        "name": "docker-fleet-agent",
        "type": "filebeat",
        "version": "7.16.2"
    },
    "data_stream": {
        "dataset": "cisco.meraki",
        "namespace": "ep",
        "type": "logs"
    },
    "destination": {
        "ip": [
            "10.193.124.51"
        ],
        "port": 5293
    },
    "ecs": {
        "version": "1.12.0"
    },
    "elastic_agent": {
        "id": "0a0be70a-90aa-494d-8be3-b06a8a05e08c",
        "snapshot": false,
        "version": "7.16.2"
    },
    "event": {
        "action": "deny\n",
        "agent_id_status": "verified",
        "code": "security_event",
        "dataset": "cisco.meraki",
        "ingested": "2022-01-25T09:01:37Z",
        "original": "modtempo 1454047799.olab nto_ security_event olaborissecurity_event tur url=https://example.org/odoco/ria.jpg?ritin=uredolor#tatemac src=10.15.44.253:5078 dst=10.193.124.51:5293 mac=01:00:5e:28:ae:7d name=psa sha256=umq disposition=ntium action=deny\n",
        "timezone": "+00:00"
    },
    "input": {
        "type": "udp"
    },
    "log": {
        "source": {
            "address": "172.19.0.4:59238"
        }
    },
    "observer": {
        "product": "Meraki",
        "type": "Wireless",
        "vendor": "Cisco"
    },
    "related": {
        "ip": [
            "10.193.124.51",
            "10.15.44.253"
        ]
    },
    "rsa": {
        "internal": {
            "event_desc": "olaborissecurity_event tur",
            "messageid": "security_event"
        },
        "misc": {
            "action": [
                "deny\n"
            ],
            "disposition": "ntium",
            "event_type": "security_event",
            "node": "nto_",
            "sensor": "nto_"
        },
        "time": {
            "event_time": "2016-01-29T06:09:59.000Z"
        }
    },
    "source": {
        "ip": [
            "10.15.44.253"
        ],
        "mac": "01:00:5e:28:ae:7d",
        "port": 5078
    },
    "tags": [
        "preserve_original_event",
        "cisco-meraki",
        "forwarded"
    ],
    "url": {
        "original": "https://example.org/odoco/ria.jpg?ritin=uredolor#tatemac"
    }
}
```

**Exported fields**

| Field | Description | Type |
|---|---|---|
| @timestamp | Event timestamp. | date |
| client.domain | The domain name of the client system. This value may be a host name, a fully qualified domain name, or another host naming format. The value may derive from the original event or be added from enrichment. | keyword |
| client.registered_domain | The highest registered client domain, stripped of the subdomain. For example, the registered domain for "foo.example.com" is "example.com". This value can be determined precisely with a list like the public suffix list (http://publicsuffix.org). Trying to approximate this by simply taking the last two labels will not work well for TLDs such as "co.uk". | keyword |
| client.subdomain | The subdomain portion of a fully qualified domain name includes all of the names except the host name under the registered_domain.  In a partially qualified domain, or if the the qualification level of the full name cannot be determined, subdomain contains all of the names below the registered domain. For example the subdomain portion of "www.east.mydomain.co.uk" is "east". If the domain has multiple levels of subdomain, such as "sub2.sub1.example.com", the subdomain field should contain "sub2.sub1", with no trailing period. | keyword |
| client.top_level_domain | The effective top level domain (eTLD), also known as the domain suffix, is the last part of the domain name. For example, the top level domain for example.com is "com". This value can be determined precisely with a list like the public suffix list (http://publicsuffix.org). Trying to approximate this by simply taking the last label will not work well for effective TLDs such as "co.uk". | keyword |
| cloud.account.id | The cloud account or organization id used to identify different entities in a multi-tenant environment. Examples: AWS account id, Google Cloud ORG Id, or other unique identifier. | keyword |
| cloud.availability_zone | Availability zone in which this host is running. | keyword |
| cloud.image.id | Image ID for the cloud instance. | keyword |
| cloud.instance.id | Instance ID of the host machine. | keyword |
| cloud.instance.name | Instance name of the host machine. | keyword |
| cloud.machine.type | Machine type of the host machine. | keyword |
| cloud.project.id | Name of the project in Google Cloud. | keyword |
| cloud.provider | Name of the cloud provider. Example values are aws, azure, gcp, or digitalocean. | keyword |
| cloud.region | Region in which this host is running. | keyword |
| container.id | Unique container id. | keyword |
| container.image.name | Name of the image the container was built on. | keyword |
| container.labels | Image labels. | object |
| container.name | Container name. | keyword |
| data_stream.dataset | Data stream dataset. | constant_keyword |
| data_stream.namespace | Data stream namespace. | constant_keyword |
| data_stream.type | Data stream type. | constant_keyword |
| destination.address | Some event destination addresses are defined ambiguously. The event will sometimes list an IP, a domain or a unix socket.  You should always store the raw address in the `.address` field. Then it should be duplicated to `.ip` or `.domain`, depending on which one it is. | keyword |
| destination.as.number | Unique number allocated to the autonomous system. The autonomous system number (ASN) uniquely identifies each network on the Internet. | long |
| destination.as.organization.name | Organization name. | keyword |
| destination.as.organization.name.text | Multi-field of `destination.as.organization.name`. | match_only_text |
| destination.bytes | Bytes sent from the destination to the source. | long |
| destination.domain | The domain name of the destination system. This value may be a host name, a fully qualified domain name, or another host naming format. The value may derive from the original event or be added from enrichment. | keyword |
| destination.geo.city_name | City name. | keyword |
| destination.geo.country_name | Country name. | keyword |
| destination.geo.location | Longitude and latitude. | geo_point |
| destination.ip | IP address of the destination (IPv4 or IPv6). | ip |
| destination.mac | MAC address of the destination. The notation format from RFC 7042 is suggested: Each octet (that is, 8-bit byte) is represented by two [uppercase] hexadecimal digits giving the value of the octet as an unsigned integer. Successive octets are separated by a hyphen. | keyword |
| destination.nat.ip | Translated ip of destination based NAT sessions (e.g. internet to private DMZ) Typically used with load balancers, firewalls, or routers. | ip |
| destination.nat.port | Port the source session is translated to by NAT Device. Typically used with load balancers, firewalls, or routers. | long |
| destination.port | Port of the destination. | long |
| destination.registered_domain | The highest registered destination domain, stripped of the subdomain. For example, the registered domain for "foo.example.com" is "example.com". This value can be determined precisely with a list like the public suffix list (http://publicsuffix.org). Trying to approximate this by simply taking the last two labels will not work well for TLDs such as "co.uk". | keyword |
| destination.subdomain | The subdomain portion of a fully qualified domain name includes all of the names except the host name under the registered_domain.  In a partially qualified domain, or if the the qualification level of the full name cannot be determined, subdomain contains all of the names below the registered domain. For example the subdomain portion of "www.east.mydomain.co.uk" is "east". If the domain has multiple levels of subdomain, such as "sub2.sub1.example.com", the subdomain field should contain "sub2.sub1", with no trailing period. | keyword |
| destination.top_level_domain | The effective top level domain (eTLD), also known as the domain suffix, is the last part of the domain name. For example, the top level domain for example.com is "com". This value can be determined precisely with a list like the public suffix list (http://publicsuffix.org). Trying to approximate this by simply taking the last label will not work well for effective TLDs such as "co.uk". | keyword |
| dns.answers.name | The domain name to which this resource record pertains. If a chain of CNAME is being resolved, each answer's `name` should be the one that corresponds with the answer's `data`. It should not simply be the original `question.name` repeated. | keyword |
| dns.answers.type | The type of data contained in this resource record. | keyword |
| dns.question.domain | Server domain. | keyword |
| dns.question.registered_domain | The highest registered domain, stripped of the subdomain. For example, the registered domain for "foo.example.com" is "example.com". This value can be determined precisely with a list like the public suffix list (http://publicsuffix.org). Trying to approximate this by simply taking the last two labels will not work well for TLDs such as "co.uk". | keyword |
| dns.question.subdomain | The subdomain is all of the labels under the registered_domain. If the domain has multiple levels of subdomain, such as "sub2.sub1.example.com", the subdomain field should contain "sub2.sub1", with no trailing period. | keyword |
| dns.question.top_level_domain | The effective top level domain (eTLD), also known as the domain suffix, is the last part of the domain name. For example, the top level domain for example.com is "com". This value can be determined precisely with a list like the public suffix list (http://publicsuffix.org). Trying to approximate this by simply taking the last label will not work well for effective TLDs such as "co.uk". | keyword |
| dns.question.type | The type of record being queried. | keyword |
| ecs.version | ECS version this event conforms to. `ecs.version` is a required field and must exist in all events. When querying across multiple indices -- which may conform to slightly different ECS versions -- this field lets integrations adjust to the schema version of the events. | keyword |
| error.message | Error message. | match_only_text |
| event.action | The action captured by the event. This describes the information in the event. It is more specific than `event.category`. Examples are `group-add`, `process-started`, `file-created`. The value is normally defined by the implementer. | keyword |
| event.code | Identification code for this event, if one exists. Some event sources use event codes to identify messages unambiguously, regardless of message language or wording adjustments over time. An example of this is the Windows Event ID. | keyword |
| event.dataset | Event dataset | constant_keyword |
| event.ingested | Timestamp when an event arrived in the central data store. This is different from `@timestamp`, which is when the event originally occurred.  It's also different from `event.created`, which is meant to capture the first time an agent saw the event. In normal conditions, assuming no tampering, the timestamps should chronologically look like this: `@timestamp` \< `event.created` \< `event.ingested`. | date |
| event.module | Event module | constant_keyword |
| event.original | Raw text message of entire event. Used to demonstrate log integrity or where the full log message (before splitting it up in multiple parts) may be required, e.g. for reindex. This field is not indexed and doc_values are disabled. It cannot be searched, but it can be retrieved from `_source`. If users wish to override this and index this field, please see `Field data types` in the `Elasticsearch Reference`. | keyword |
| event.outcome | This is one of four ECS Categorization Fields, and indicates the lowest level in the ECS category hierarchy. `event.outcome` simply denotes whether the event represents a success or a failure from the perspective of the entity that produced the event. Note that when a single transaction is described in multiple events, each event may populate different values of `event.outcome`, according to their perspective. Also note that in the case of a compound event (a single event that contains multiple logical events), this field should be populated with the value that best captures the overall success or failure from the perspective of the event producer. Further note that not all events will have an associated outcome. For example, this field is generally not populated for metric events, events with `event.type:info`, or any events for which an outcome does not make logical sense. | keyword |
| event.timezone | This field should be populated when the event's timestamp does not include timezone information already (e.g. default Syslog timestamps). It's optional otherwise. Acceptable timezone formats are: a canonical ID (e.g. "Europe/Amsterdam"), abbreviated (e.g. "EST") or an HH:mm differential (e.g. "-05:00"). | keyword |
| file.attributes | Array of file attributes. Attributes names will vary by platform. Here's a non-exhaustive list of values that are expected in this field: archive, compressed, directory, encrypted, execute, hidden, read, readonly, system, write. | keyword |
| file.directory | Directory where the file is located. It should include the drive letter, when appropriate. | keyword |
| file.extension | File extension, excluding the leading dot. Note that when the file name has multiple extensions (example.tar.gz), only the last one should be captured ("gz", not "tar.gz"). | keyword |
| file.name | Name of the file including the extension, without the directory. | keyword |
| file.path | Full path to the file, including the file name. It should include the drive letter, when appropriate. | keyword |
| file.path.text | Multi-field of `file.path`. | match_only_text |
| file.size | File size in bytes. Only relevant when `file.type` is "file". | long |
| file.type | File type (file, dir, or symlink). | keyword |
| geo.city_name | City name. | keyword |
| geo.country_name | Country name. | keyword |
| geo.name | User-defined description of a location, at the level of granularity they care about. Could be the name of their data centers, the floor number, if this describes a local physical entity, city names. Not typically used in automated geolocation. | keyword |
| geo.region_name | Region name. | keyword |
| group.id | Unique identifier for the group on the system/platform. | keyword |
| group.name | Name of the group. | keyword |
| host.architecture | Operating system architecture. | keyword |
| host.containerized | If the host is a container. | boolean |
| host.domain | Name of the domain of which the host is a member. For example, on Windows this could be the host's Active Directory domain or NetBIOS domain name. For Linux this could be the domain of the host's LDAP provider. | keyword |
| host.hostname | Hostname of the host. It normally contains what the `hostname` command returns on the host machine. | keyword |
| host.id | Unique host id. As hostname is not always unique, use values that are meaningful in your environment. Example: The current usage of `beat.name`. | keyword |
| host.ip | Host ip addresses. | ip |
| host.mac | Host MAC addresses. The notation format from RFC 7042 is suggested: Each octet (that is, 8-bit byte) is represented by two [uppercase] hexadecimal digits giving the value of the octet as an unsigned integer. Successive octets are separated by a hyphen. | keyword |
| host.name | Name of the host. It can contain what `hostname` returns on Unix systems, the fully qualified domain name, or a name specified by the user. The sender decides which value to use. | keyword |
| host.os.build | OS build information. | keyword |
| host.os.codename | OS codename, if any. | keyword |
| host.os.family | OS family (such as redhat, debian, freebsd, windows). | keyword |
| host.os.kernel | Operating system kernel version as a raw string. | keyword |
| host.os.name | Operating system name, without the version. | keyword |
| host.os.name.text | Multi-field of `host.os.name`. | text |
| host.os.platform | Operating system platform (such centos, ubuntu, windows). | keyword |
| host.os.version | Operating system version as a raw string. | keyword |
| host.type | Type of host. For Cloud providers this can be the machine type like `t2.medium`. If vm, this could be the container, for example, or other information meaningful in your environment. | keyword |
| http.request.method | HTTP request method. The value should retain its casing from the original event. For example, `GET`, `get`, and `GeT` are all considered valid values for this field. | keyword |
| http.request.referrer | Referrer for this HTTP request. | keyword |
| input.type | Type of Filebeat input. | keyword |
| log.file.path | Full path to the log file this event came from. | keyword |
| log.flags | Flags for the log file. | keyword |
| log.level | Original log level of the log event. If the source of the event provides a log level or textual severity, this is the one that goes in `log.level`. If your source doesn't specify one, you may put your event transport's severity here (e.g. Syslog severity). Some examples are `warn`, `err`, `i`, `informational`. | keyword |
| log.offset | Offset of the entry in the log file. | long |
| log.source.address | Source address from which the log event was read / sent from. | keyword |
| log.syslog.facility.code | The Syslog numeric facility of the log event, if available. According to RFCs 5424 and 3164, this value should be an integer between 0 and 23. | long |
| log.syslog.priority | Syslog numeric priority of the event, if available. According to RFCs 5424 and 3164, the priority is 8 \* facility + severity. This number is therefore expected to contain a value between 0 and 191. | long |
| log.syslog.severity.code | The Syslog numeric severity of the log event, if available. If the event source publishing via Syslog provides a different numeric severity value (e.g. firewall, IDS), your source's numeric severity should go to `event.severity`. If the event source does not specify a distinct severity, you can optionally copy the Syslog severity to `event.severity`. | long |
| message | For log events the message field contains the log message, optimized for viewing in a log viewer. For structured logs without an original message field, other fields can be concatenated to form a human-readable summary of the event. If multiple messages exist, they can be combined into one message. | match_only_text |
| network.application | When a specific application or service is identified from network connection details (source/dest IPs, ports, certificates, or wire format), this field captures the application's or service's name. For example, the original event identifies the network connection being from a specific web service in a `https` network connection, like `facebook` or `twitter`. The field value must be normalized to lowercase for querying. | keyword |
| network.bytes | Total bytes transferred in both directions. If `source.bytes` and `destination.bytes` are known, `network.bytes` is their sum. | long |
| network.direction | Direction of the network traffic. Recommended values are:   \* ingress   \* egress   \* inbound   \* outbound   \* internal   \* external   \* unknown  When mapping events from a host-based monitoring context, populate this field from the host's point of view, using the values "ingress" or "egress". When mapping events from a network or perimeter-based monitoring context, populate this field from the point of view of the network perimeter, using the values "inbound", "outbound", "internal" or "external". Note that "internal" is not crossing perimeter boundaries, and is meant to describe communication between two hosts within the perimeter. Note also that "external" is meant to describe traffic between two hosts that are external to the perimeter. This could for example be useful for ISPs or VPN service providers. | keyword |
| network.forwarded_ip | Host IP address when the source IP address is the proxy. | ip |
| network.interface.name |  | keyword |
| network.packets | Total packets transferred in both directions. If `source.packets` and `destination.packets` are known, `network.packets` is their sum. | long |
| network.protocol | In the OSI Model this would be the Application Layer protocol. For example, `http`, `dns`, or `ssh`. The field value must be normalized to lowercase for querying. | keyword |
| observer.egress.interface.name | Interface name as reported by the system. | keyword |
| observer.ingress.interface.name | Interface name as reported by the system. | keyword |
| observer.product | The product name of the observer. | keyword |
| observer.type | The type of the observer the data is coming from. There is no predefined list of observer types. Some examples are `forwarder`, `firewall`, `ids`, `ips`, `proxy`, `poller`, `sensor`, `APM server`. | keyword |
| observer.vendor | Vendor name of the observer. | keyword |
| observer.version | Observer version. | keyword |
| process.name | Process name. Sometimes called program name or similar. | keyword |
| process.name.text | Multi-field of `process.name`. | match_only_text |
| process.parent.name | Process name. Sometimes called program name or similar. | keyword |
| process.parent.name.text | Multi-field of `process.parent.name`. | match_only_text |
| process.parent.pid | Process id. | long |
| process.parent.title | Process title. The proctitle, some times the same as process name. Can also be different: for example a browser setting its title to the web page currently opened. | keyword |
| process.parent.title.text | Multi-field of `process.parent.title`. | match_only_text |
| process.pid | Process id. | long |
| process.title | Process title. The proctitle, some times the same as process name. Can also be different: for example a browser setting its title to the web page currently opened. | keyword |
| process.title.text | Multi-field of `process.title`. | match_only_text |
| related.hosts | All hostnames or other host identifiers seen on your event. Example identifiers include FQDNs, domain names, workstation names, or aliases. | keyword |
| related.ip | All of the IPs seen on your event. | ip |
| related.user | All the user names or other user identifiers seen on the event. | keyword |
| rsa.counters.dclass_c1 | This is a generic counter key that should be used with the label dclass.c1.str only | long |
| rsa.counters.dclass_c1_str | This is a generic counter string key that should be used with the label dclass.c1 only | keyword |
| rsa.counters.dclass_c2 | This is a generic counter key that should be used with the label dclass.c2.str only | long |
| rsa.counters.dclass_c2_str | This is a generic counter string key that should be used with the label dclass.c2 only | keyword |
| rsa.counters.dclass_c3 | This is a generic counter key that should be used with the label dclass.c3.str only | long |
| rsa.counters.dclass_c3_str | This is a generic counter string key that should be used with the label dclass.c3 only | keyword |
| rsa.counters.dclass_r1 | This is a generic ratio key that should be used with the label dclass.r1.str only | keyword |
| rsa.counters.dclass_r1_str | This is a generic ratio string key that should be used with the label dclass.r1 only | keyword |
| rsa.counters.dclass_r2 | This is a generic ratio key that should be used with the label dclass.r2.str only | keyword |
| rsa.counters.dclass_r2_str | This is a generic ratio string key that should be used with the label dclass.r2 only | keyword |
| rsa.counters.dclass_r3 | This is a generic ratio key that should be used with the label dclass.r3.str only | keyword |
| rsa.counters.dclass_r3_str | This is a generic ratio string key that should be used with the label dclass.r3 only | keyword |
| rsa.counters.event_counter | This is used to capture the number of times an event repeated | long |
| rsa.crypto.cert_ca | This key is used to capture the Certificate signing authority only | keyword |
| rsa.crypto.cert_checksum |  | keyword |
| rsa.crypto.cert_common | This key is used to capture the Certificate common name only | keyword |
| rsa.crypto.cert_error | This key captures the Certificate Error String | keyword |
| rsa.crypto.cert_host_cat | This key is used for the hostname category value of a certificate | keyword |
| rsa.crypto.cert_host_name | Deprecated key defined only in table map. | keyword |
| rsa.crypto.cert_issuer |  | keyword |
| rsa.crypto.cert_keysize |  | keyword |
| rsa.crypto.cert_serial | This key is used to capture the Certificate serial number only | keyword |
| rsa.crypto.cert_status | This key captures Certificate validation status | keyword |
| rsa.crypto.cert_subject | This key is used to capture the Certificate organization only | keyword |
| rsa.crypto.cert_username |  | keyword |
| rsa.crypto.cipher_dst | This key is for Destination (Server) Cipher | keyword |
| rsa.crypto.cipher_size_dst | This key captures Destination (Server) Cipher Size | long |
| rsa.crypto.cipher_size_src | This key captures Source (Client) Cipher Size | long |
| rsa.crypto.cipher_src | This key is for Source (Client) Cipher | keyword |
| rsa.crypto.crypto | This key is used to capture the Encryption Type or Encryption Key only | keyword |
| rsa.crypto.d_certauth |  | keyword |
| rsa.crypto.https_insact |  | keyword |
| rsa.crypto.https_valid |  | keyword |
| rsa.crypto.ike | IKE negotiation phase. | keyword |
| rsa.crypto.ike_cookie1 | ID of the negotiation — sent for ISAKMP Phase One | keyword |
| rsa.crypto.ike_cookie2 | ID of the negotiation — sent for ISAKMP Phase Two | keyword |
| rsa.crypto.peer | This key is for Encryption peer's IP Address | keyword |
| rsa.crypto.peer_id | This key is for Encryption peer’s identity | keyword |
| rsa.crypto.s_certauth |  | keyword |
| rsa.crypto.scheme | This key captures the Encryption scheme used | keyword |
| rsa.crypto.sig_type | This key captures the Signature Type | keyword |
| rsa.crypto.ssl_ver_dst | Deprecated, use version | keyword |
| rsa.crypto.ssl_ver_src | Deprecated, use version | keyword |
| rsa.db.database | This key is used to capture the name of a database or an instance as seen in a session | keyword |
| rsa.db.db_id | This key is used to capture the unique identifier for a database | keyword |
| rsa.db.db_pid | This key captures the process id of a connection with database server | long |
| rsa.db.index | This key captures IndexID of the index. | keyword |
| rsa.db.instance | This key is used to capture the database server instance name | keyword |
| rsa.db.lread | This key is used for the number of logical reads | long |
| rsa.db.lwrite | This key is used for the number of logical writes | long |
| rsa.db.permissions | This key captures permission or privilege level assigned to a resource. | keyword |
| rsa.db.pread | This key is used for the number of physical writes | long |
| rsa.db.table_name | This key is used to capture the table name | keyword |
| rsa.db.transact_id | This key captures the SQL transantion ID of the current session | keyword |
| rsa.email.email | This key is used to capture a generic email address where the source or destination context is not clear | keyword |
| rsa.email.email_dst | This key is used to capture the Destination email address only, when the destination context is not clear use email | keyword |
| rsa.email.email_src | This key is used to capture the source email address only, when the source context is not clear use email | keyword |
| rsa.email.subject | This key is used to capture the subject string from an Email only. | keyword |
| rsa.email.trans_from | Deprecated key defined only in table map. | keyword |
| rsa.email.trans_to | Deprecated key defined only in table map. | keyword |
| rsa.endpoint.host_state | This key is used to capture the current state of the machine, such as \<strong\>blacklisted\</strong\>, \<strong\>infected\</strong\>, \<strong\>firewall disabled\</strong\> and so on | keyword |
| rsa.endpoint.registry_key | This key captures the path to the registry key | keyword |
| rsa.endpoint.registry_value | This key captures values or decorators used within a registry entry | keyword |
| rsa.file.attachment | This key captures the attachment file name | keyword |
| rsa.file.binary | Deprecated key defined only in table map. | keyword |
| rsa.file.directory_dst | \<span\>This key is used to capture the directory of the target process or file\</span\> | keyword |
| rsa.file.directory_src | This key is used to capture the directory of the source process or file | keyword |
| rsa.file.file_entropy | This is used to capture entropy vale of a file | double |
| rsa.file.file_vendor | This is used to capture Company name of file located in version_info | keyword |
| rsa.file.filename_dst | This is used to capture name of the file targeted by the action | keyword |
| rsa.file.filename_src | This is used to capture name of the parent filename, the file which performed the action | keyword |
| rsa.file.filename_tmp |  | keyword |
| rsa.file.filesystem |  | keyword |
| rsa.file.privilege | Deprecated, use permissions | keyword |
| rsa.file.task_name | This is used to capture name of the task | keyword |
| rsa.healthcare.patient_fname | This key is for First Names only, this is used for Healthcare predominantly to capture Patients information | keyword |
| rsa.healthcare.patient_id | This key captures the unique ID for a patient | keyword |
| rsa.healthcare.patient_lname | This key is for Last Names only, this is used for Healthcare predominantly to capture Patients information | keyword |
| rsa.healthcare.patient_mname | This key is for Middle Names only, this is used for Healthcare predominantly to capture Patients information | keyword |
| rsa.identity.accesses | This key is used to capture actual privileges used in accessing an object | keyword |
| rsa.identity.auth_method | This key is used to capture authentication methods used only | keyword |
| rsa.identity.dn | X.500 (LDAP) Distinguished Name | keyword |
| rsa.identity.dn_dst | An X.500 (LDAP) Distinguished name that used in a context that indicates a Destination dn | keyword |
| rsa.identity.dn_src | An X.500 (LDAP) Distinguished name that is used in a context that indicates a Source dn | keyword |
| rsa.identity.federated_idp | This key is the federated Identity Provider. This is the server providing the authentication. | keyword |
| rsa.identity.federated_sp | This key is the Federated Service Provider. This is the application requesting authentication. | keyword |
| rsa.identity.firstname | This key is for First Names only, this is used for Healthcare predominantly to capture Patients information | keyword |
| rsa.identity.host_role | This key should only be used to capture the role of a Host Machine | keyword |
| rsa.identity.lastname | This key is for Last Names only, this is used for Healthcare predominantly to capture Patients information | keyword |
| rsa.identity.ldap | This key is for Uninterpreted LDAP values. Ldap Values that don’t have a clear query or response context | keyword |
| rsa.identity.ldap_query | This key is the Search criteria from an LDAP search | keyword |
| rsa.identity.ldap_response | This key is to capture Results from an LDAP search | keyword |
| rsa.identity.logon_type | This key is used to capture the type of logon method used. | keyword |
| rsa.identity.logon_type_desc | This key is used to capture the textual description of an integer logon type as stored in the meta key 'logon.type'. | keyword |
| rsa.identity.middlename | This key is for Middle Names only, this is used for Healthcare predominantly to capture Patients information | keyword |
| rsa.identity.org | This key captures the User organization | keyword |
| rsa.identity.owner | This is used to capture username the process or service is running as, the author of the task | keyword |
| rsa.identity.password | This key is for Passwords seen in any session, plain text or encrypted | keyword |
| rsa.identity.profile | This key is used to capture the user profile | keyword |
| rsa.identity.realm | Radius realm or similar grouping of accounts | keyword |
| rsa.identity.service_account | This key is a windows specific key, used for capturing name of the account a service (referenced in the event) is running under. Legacy Usage | keyword |
| rsa.identity.user_dept | User's Department Names only | keyword |
| rsa.identity.user_role | This key is used to capture the Role of a user only | keyword |
| rsa.identity.user_sid_dst | This key captures Destination User Session ID | keyword |
| rsa.identity.user_sid_src | This key captures Source User Session ID | keyword |
| rsa.internal.audit_class | Deprecated key defined only in table map. | keyword |
| rsa.internal.cid | This is the unique identifier used to identify a NetWitness Concentrator. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.internal.data | Deprecated key defined only in table map. | keyword |
| rsa.internal.dead | Deprecated key defined only in table map. | long |
| rsa.internal.device_class | This is the Classification of the Log Event Source under a predefined fixed set of Event Source Classifications. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.internal.device_group | This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.internal.device_host | This is the Hostname of the log Event Source sending the logs to NetWitness. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.internal.device_ip | This is the IPv4 address of the Log Event Source sending the logs to NetWitness. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | ip |
| rsa.internal.device_ipv6 | This is the IPv6 address of the Log Event Source sending the logs to NetWitness. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | ip |
| rsa.internal.device_type | This is the name of the log parser which parsed a given session. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.internal.device_type_id | Deprecated key defined only in table map. | long |
| rsa.internal.did | This is the unique identifier used to identify a NetWitness Decoder. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.internal.entropy_req | This key is only used by the Entropy Parser, the Meta Type can be either UInt16 or Float32 based on the configuration | long |
| rsa.internal.entropy_res | This key is only used by the Entropy Parser, the Meta Type can be either UInt16 or Float32 based on the configuration | long |
| rsa.internal.entry | Deprecated key defined only in table map. | keyword |
| rsa.internal.event_desc |  | keyword |
| rsa.internal.event_name | Deprecated key defined only in table map. | keyword |
| rsa.internal.feed_category | This is used to capture the category of the feed. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.internal.feed_desc | This is used to capture the description of the feed. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.internal.feed_name | This is used to capture the name of the feed. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.internal.forward_ip | This key should be used to capture the IPV4 address of a relay system which forwarded the events from the original system to NetWitness. | ip |
| rsa.internal.forward_ipv6 | This key is used to capture the IPV6 address of a relay system which forwarded the events from the original system to NetWitness. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | ip |
| rsa.internal.hcode | Deprecated key defined only in table map. | keyword |
| rsa.internal.header_id | This is the Header ID value that identifies the exact log parser header definition that parses a particular log session. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.internal.inode | Deprecated key defined only in table map. | long |
| rsa.internal.lc_cid | This is a unique Identifier of a Log Collector. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.internal.lc_ctime | This is the time at which a log is collected in a NetWitness Log Collector. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | date |
| rsa.internal.level | Deprecated key defined only in table map. | long |
| rsa.internal.mcb_req | This key is only used by the Entropy Parser, the most common byte request is simply which byte for each side (0 thru 255) was seen the most | long |
| rsa.internal.mcb_res | This key is only used by the Entropy Parser, the most common byte response is simply which byte for each side (0 thru 255) was seen the most | long |
| rsa.internal.mcbc_req | This key is only used by the Entropy Parser, the most common byte count is the number of times the most common byte (above) was seen in the session streams | long |
| rsa.internal.mcbc_res | This key is only used by the Entropy Parser, the most common byte count is the number of times the most common byte (above) was seen in the session streams | long |
| rsa.internal.medium | This key is used to identify if it’s a log/packet session or Layer 2 Encapsulation Type. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness. 32 = log, 33 = correlation session, &lt; 32 is packet session | long |
| rsa.internal.message | This key captures the contents of instant messages | keyword |
| rsa.internal.messageid |  | keyword |
| rsa.internal.msg | This key is used to capture the raw message that comes into the Log Decoder | keyword |
| rsa.internal.msg_id | This is the Message ID1 value that identifies the exact log parser definition which parses a particular log session. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.internal.msg_vid | This is the Message ID2 value that identifies the exact log parser definition which parses a particular log session. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.internal.node_name | Deprecated key defined only in table map. | keyword |
| rsa.internal.nwe_callback_id | This key denotes that event is endpoint related | keyword |
| rsa.internal.obj_id | Deprecated key defined only in table map. | keyword |
| rsa.internal.obj_server | Deprecated key defined only in table map. | keyword |
| rsa.internal.obj_val | Deprecated key defined only in table map. | keyword |
| rsa.internal.parse_error | This is a special key that stores any Meta key validation error found while parsing a log session. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.internal.payload_req | This key is only used by the Entropy Parser, the payload size metrics are the payload sizes of each session side at the time of parsing. However, in order to keep | long |
| rsa.internal.payload_res | This key is only used by the Entropy Parser, the payload size metrics are the payload sizes of each session side at the time of parsing. However, in order to keep | long |
| rsa.internal.process_vid_dst | Endpoint generates and uses a unique virtual ID to identify any similar group of process. This ID represents the target process. | keyword |
| rsa.internal.process_vid_src | Endpoint generates and uses a unique virtual ID to identify any similar group of process. This ID represents the source process. | keyword |
| rsa.internal.resource | Deprecated key defined only in table map. | keyword |
| rsa.internal.resource_class | Deprecated key defined only in table map. | keyword |
| rsa.internal.rid | This is a special ID of the Remote Session created by NetWitness Decoder. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | long |
| rsa.internal.session_split | This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.internal.site | Deprecated key defined only in table map. | keyword |
| rsa.internal.size | This is the size of the session as seen by the NetWitness Decoder. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | long |
| rsa.internal.sourcefile | This is the name of the log file or PCAPs that can be imported into NetWitness. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.internal.statement | Deprecated key defined only in table map. | keyword |
| rsa.internal.time | This is the time at which a session hits a NetWitness Decoder. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness. | date |
| rsa.internal.ubc_req | This key is only used by the Entropy Parser, Unique byte count is the number of unique bytes seen in each stream. 256 would mean all byte values of 0 thru 255 were seen at least once | long |
| rsa.internal.ubc_res | This key is only used by the Entropy Parser, Unique byte count is the number of unique bytes seen in each stream. 256 would mean all byte values of 0 thru 255 were seen at least once | long |
| rsa.internal.word | This is used by the Word Parsing technology to capture the first 5 character of every word in an unparsed log | keyword |
| rsa.investigations.analysis_file | This is used to capture all indicators used in a File Analysis. This key should be used to capture an analysis of a file | keyword |
| rsa.investigations.analysis_service | This is used to capture all indicators used in a Service Analysis. This key should be used to capture an analysis of a service | keyword |
| rsa.investigations.analysis_session | This is used to capture all indicators used for a Session Analysis. This key should be used to capture an analysis of a session | keyword |
| rsa.investigations.boc | This is used to capture behaviour of compromise | keyword |
| rsa.investigations.ec_activity | This key captures the particular event activity(Ex:Logoff) | keyword |
| rsa.investigations.ec_outcome | This key captures the outcome of a particular Event(Ex:Success) | keyword |
| rsa.investigations.ec_subject | This key captures the Subject of a particular Event(Ex:User) | keyword |
| rsa.investigations.ec_theme | This key captures the Theme of a particular Event(Ex:Authentication) | keyword |
| rsa.investigations.eoc | This is used to capture Enablers of Compromise | keyword |
| rsa.investigations.event_cat | This key captures the Event category number | long |
| rsa.investigations.event_cat_name | This key captures the event category name corresponding to the event cat code | keyword |
| rsa.investigations.event_vcat | This is a vendor supplied category. This should be used in situations where the vendor has adopted their own event_category taxonomy. | keyword |
| rsa.investigations.inv_category | This used to capture investigation category | keyword |
| rsa.investigations.inv_context | This used to capture investigation context | keyword |
| rsa.investigations.ioc | This is key capture indicator of compromise | keyword |
| rsa.misc.OS | This key captures the Name of the Operating System | keyword |
| rsa.misc.acl_id |  | keyword |
| rsa.misc.acl_op |  | keyword |
| rsa.misc.acl_pos |  | keyword |
| rsa.misc.acl_table |  | keyword |
| rsa.misc.action |  | keyword |
| rsa.misc.admin |  | keyword |
| rsa.misc.agent_id | This key is used to capture agent id | keyword |
| rsa.misc.alarm_id |  | keyword |
| rsa.misc.alarmname |  | keyword |
| rsa.misc.alert_id | Deprecated, New Hunting Model (inv.\*, ioc, boc, eoc, analysis.\*) | keyword |
| rsa.misc.app_id |  | keyword |
| rsa.misc.audit |  | keyword |
| rsa.misc.audit_object |  | keyword |
| rsa.misc.auditdata |  | keyword |
| rsa.misc.autorun_type | This is used to capture Auto Run type | keyword |
| rsa.misc.benchmark |  | keyword |
| rsa.misc.bypass |  | keyword |
| rsa.misc.cache |  | keyword |
| rsa.misc.cache_hit |  | keyword |
| rsa.misc.category | This key is used to capture the category of an event given by the vendor in the session | keyword |
| rsa.misc.cc_number | Valid Credit Card Numbers only | long |
| rsa.misc.cefversion |  | keyword |
| rsa.misc.cfg_attr |  | keyword |
| rsa.misc.cfg_obj |  | keyword |
| rsa.misc.cfg_path |  | keyword |
| rsa.misc.change_attrib | This key is used to capture the name of the attribute that’s changing in a session | keyword |
| rsa.misc.change_new | This key is used to capture the new values of the attribute that’s changing in a session | keyword |
| rsa.misc.change_old | This key is used to capture the old value of the attribute that’s changing in a session | keyword |
| rsa.misc.changes |  | keyword |
| rsa.misc.checksum | This key is used to capture the checksum or hash of the entity such as a file or process. Checksum should be used over checksum.src or checksum.dst when it is unclear whether the entity is a source or target of an action. | keyword |
| rsa.misc.checksum_dst | This key is used to capture the checksum or hash of the the target entity such as a process or file. | keyword |
| rsa.misc.checksum_src | This key is used to capture the checksum or hash of the source entity such as a file or process. | keyword |
| rsa.misc.client | This key is used to capture only the name of the client application requesting resources of the server. See the user.agent meta key for capture of the specific user agent identifier or browser identification string. | keyword |
| rsa.misc.client_ip |  | keyword |
| rsa.misc.clustermembers |  | keyword |
| rsa.misc.cmd |  | keyword |
| rsa.misc.cn_acttimeout |  | keyword |
| rsa.misc.cn_asn_src |  | keyword |
| rsa.misc.cn_bgpv4nxthop |  | keyword |
| rsa.misc.cn_ctr_dst_code |  | keyword |
| rsa.misc.cn_dst_tos |  | keyword |
| rsa.misc.cn_dst_vlan |  | keyword |
| rsa.misc.cn_engine_id |  | keyword |
| rsa.misc.cn_engine_type |  | keyword |
| rsa.misc.cn_f_switch |  | keyword |
| rsa.misc.cn_flowsampid |  | keyword |
| rsa.misc.cn_flowsampintv |  | keyword |
| rsa.misc.cn_flowsampmode |  | keyword |
| rsa.misc.cn_inacttimeout |  | keyword |
| rsa.misc.cn_inpermbyts |  | keyword |
| rsa.misc.cn_inpermpckts |  | keyword |
| rsa.misc.cn_invalid |  | keyword |
| rsa.misc.cn_ip_proto_ver |  | keyword |
| rsa.misc.cn_ipv4_ident |  | keyword |
| rsa.misc.cn_l_switch |  | keyword |
| rsa.misc.cn_log_did |  | keyword |
| rsa.misc.cn_log_rid |  | keyword |
| rsa.misc.cn_max_ttl |  | keyword |
| rsa.misc.cn_maxpcktlen |  | keyword |
| rsa.misc.cn_min_ttl |  | keyword |
| rsa.misc.cn_minpcktlen |  | keyword |
| rsa.misc.cn_mpls_lbl_1 |  | keyword |
| rsa.misc.cn_mpls_lbl_10 |  | keyword |
| rsa.misc.cn_mpls_lbl_2 |  | keyword |
| rsa.misc.cn_mpls_lbl_3 |  | keyword |
| rsa.misc.cn_mpls_lbl_4 |  | keyword |
| rsa.misc.cn_mpls_lbl_5 |  | keyword |
| rsa.misc.cn_mpls_lbl_6 |  | keyword |
| rsa.misc.cn_mpls_lbl_7 |  | keyword |
| rsa.misc.cn_mpls_lbl_8 |  | keyword |
| rsa.misc.cn_mpls_lbl_9 |  | keyword |
| rsa.misc.cn_mplstoplabel |  | keyword |
| rsa.misc.cn_mplstoplabip |  | keyword |
| rsa.misc.cn_mul_dst_byt |  | keyword |
| rsa.misc.cn_mul_dst_pks |  | keyword |
| rsa.misc.cn_muligmptype |  | keyword |
| rsa.misc.cn_sampalgo |  | keyword |
| rsa.misc.cn_sampint |  | keyword |
| rsa.misc.cn_seqctr |  | keyword |
| rsa.misc.cn_spackets |  | keyword |
| rsa.misc.cn_src_tos |  | keyword |
| rsa.misc.cn_src_vlan |  | keyword |
| rsa.misc.cn_sysuptime |  | keyword |
| rsa.misc.cn_template_id |  | keyword |
| rsa.misc.cn_totbytsexp |  | keyword |
| rsa.misc.cn_totflowexp |  | keyword |
| rsa.misc.cn_totpcktsexp |  | keyword |
| rsa.misc.cn_unixnanosecs |  | keyword |
| rsa.misc.cn_v6flowlabel |  | keyword |
| rsa.misc.cn_v6optheaders |  | keyword |
| rsa.misc.code |  | keyword |
| rsa.misc.command |  | keyword |
| rsa.misc.comments | Comment information provided in the log message | keyword |
| rsa.misc.comp_class |  | keyword |
| rsa.misc.comp_name |  | keyword |
| rsa.misc.comp_rbytes |  | keyword |
| rsa.misc.comp_sbytes |  | keyword |
| rsa.misc.comp_version | This key captures the Version level of a sub-component of a product. | keyword |
| rsa.misc.connection_id | This key captures the Connection ID | keyword |
| rsa.misc.content | This key captures the content type from protocol headers | keyword |
| rsa.misc.content_type | This key is used to capture Content Type only. | keyword |
| rsa.misc.content_version | This key captures Version level of a signature or database content. | keyword |
| rsa.misc.context | This key captures Information which adds additional context to the event. | keyword |
| rsa.misc.context_subject | This key is to be used in an audit context where the subject is the object being identified | keyword |
| rsa.misc.context_target |  | keyword |
| rsa.misc.count |  | keyword |
| rsa.misc.cpu | This key is the CPU time used in the execution of the event being recorded. | long |
| rsa.misc.cpu_data |  | keyword |
| rsa.misc.criticality |  | keyword |
| rsa.misc.cs_agency_dst |  | keyword |
| rsa.misc.cs_analyzedby |  | keyword |
| rsa.misc.cs_av_other |  | keyword |
| rsa.misc.cs_av_primary |  | keyword |
| rsa.misc.cs_av_secondary |  | keyword |
| rsa.misc.cs_bgpv6nxthop |  | keyword |
| rsa.misc.cs_bit9status |  | keyword |
| rsa.misc.cs_context |  | keyword |
| rsa.misc.cs_control |  | keyword |
| rsa.misc.cs_data |  | keyword |
| rsa.misc.cs_datecret |  | keyword |
| rsa.misc.cs_dst_tld |  | keyword |
| rsa.misc.cs_eth_dst_ven |  | keyword |
| rsa.misc.cs_eth_src_ven |  | keyword |
| rsa.misc.cs_event_uuid |  | keyword |
| rsa.misc.cs_filetype |  | keyword |
| rsa.misc.cs_fld |  | keyword |
| rsa.misc.cs_if_desc |  | keyword |
| rsa.misc.cs_if_name |  | keyword |
| rsa.misc.cs_ip_next_hop |  | keyword |
| rsa.misc.cs_ipv4dstpre |  | keyword |
| rsa.misc.cs_ipv4srcpre |  | keyword |
| rsa.misc.cs_lifetime |  | keyword |
| rsa.misc.cs_log_medium |  | keyword |
| rsa.misc.cs_loginname |  | keyword |
| rsa.misc.cs_modulescore |  | keyword |
| rsa.misc.cs_modulesign |  | keyword |
| rsa.misc.cs_opswatresult |  | keyword |
| rsa.misc.cs_payload |  | keyword |
| rsa.misc.cs_registrant |  | keyword |
| rsa.misc.cs_registrar |  | keyword |
| rsa.misc.cs_represult |  | keyword |
| rsa.misc.cs_rpayload |  | keyword |
| rsa.misc.cs_sampler_name |  | keyword |
| rsa.misc.cs_sourcemodule |  | keyword |
| rsa.misc.cs_streams |  | keyword |
| rsa.misc.cs_targetmodule |  | keyword |
| rsa.misc.cs_v6nxthop |  | keyword |
| rsa.misc.cs_whois_server |  | keyword |
| rsa.misc.cs_yararesult |  | keyword |
| rsa.misc.cve | This key captures CVE (Common Vulnerabilities and Exposures) - an identifier for known information security vulnerabilities. | keyword |
| rsa.misc.data_type |  | keyword |
| rsa.misc.description |  | keyword |
| rsa.misc.device_name | This is used to capture name of the Device associated with the node Like: a physical disk, printer, etc | keyword |
| rsa.misc.devvendor |  | keyword |
| rsa.misc.disposition | This key captures the The end state of an action. | keyword |
| rsa.misc.distance |  | keyword |
| rsa.misc.doc_number | This key captures File Identification number | long |
| rsa.misc.dstburb |  | keyword |
| rsa.misc.edomain |  | keyword |
| rsa.misc.edomaub |  | keyword |
| rsa.misc.ein_number | Employee Identification Numbers only | long |
| rsa.misc.error | This key captures All non successful Error codes or responses | keyword |
| rsa.misc.euid |  | keyword |
| rsa.misc.event_category |  | keyword |
| rsa.misc.event_computer | This key is a windows only concept, where this key is used to capture fully qualified domain name in a windows log. | keyword |
| rsa.misc.event_desc | This key is used to capture a description of an event available directly or inferred | keyword |
| rsa.misc.event_id |  | keyword |
| rsa.misc.event_log | This key captures the Name of the event log | keyword |
| rsa.misc.event_source | This key captures Source of the event that’s not a hostname | keyword |
| rsa.misc.event_state | This key captures the current state of the object/item referenced within the event. Describing an on-going event. | keyword |
| rsa.misc.event_type | This key captures the event category type as specified by the event source. | keyword |
| rsa.misc.event_user | This key is a windows only concept, where this key is used to capture combination of domain name and username in a windows log. | keyword |
| rsa.misc.expected_val | This key captures the Value expected (from the perspective of the device generating the log). | keyword |
| rsa.misc.facility |  | keyword |
| rsa.misc.facilityname |  | keyword |
| rsa.misc.fcatnum | This key captures Filter Category Number. Legacy Usage | keyword |
| rsa.misc.filter | This key captures Filter used to reduce result set | keyword |
| rsa.misc.finterface |  | keyword |
| rsa.misc.flags |  | keyword |
| rsa.misc.forensic_info |  | keyword |
| rsa.misc.found | This is used to capture the results of regex match | keyword |
| rsa.misc.fresult | This key captures the Filter Result | long |
| rsa.misc.gaddr |  | keyword |
| rsa.misc.group | This key captures the Group Name value | keyword |
| rsa.misc.group_id | This key captures Group ID Number (related to the group name) | keyword |
| rsa.misc.group_object | This key captures a collection/grouping of entities. Specific usage | keyword |
| rsa.misc.hardware_id | This key is used to capture unique identifier for a device or system (NOT a Mac address) | keyword |
| rsa.misc.id3 |  | keyword |
| rsa.misc.im_buddyid |  | keyword |
| rsa.misc.im_buddyname |  | keyword |
| rsa.misc.im_client |  | keyword |
| rsa.misc.im_croomid |  | keyword |
| rsa.misc.im_croomtype |  | keyword |
| rsa.misc.im_members |  | keyword |
| rsa.misc.im_userid |  | keyword |
| rsa.misc.im_username |  | keyword |
| rsa.misc.index |  | keyword |
| rsa.misc.inout |  | keyword |
| rsa.misc.ipkt |  | keyword |
| rsa.misc.ipscat |  | keyword |
| rsa.misc.ipspri |  | keyword |
| rsa.misc.job_num | This key captures the Job Number | keyword |
| rsa.misc.jobname |  | keyword |
| rsa.misc.language | This is used to capture list of languages the client support and what it prefers | keyword |
| rsa.misc.latitude |  | keyword |
| rsa.misc.library | This key is used to capture library information in mainframe devices | keyword |
| rsa.misc.lifetime | This key is used to capture the session lifetime in seconds. | long |
| rsa.misc.linenum |  | keyword |
| rsa.misc.link | This key is used to link the sessions together. This key should never be used to parse Meta data from a session (Logs/Packets) Directly, this is a Reserved key in NetWitness | keyword |
| rsa.misc.list_name |  | keyword |
| rsa.misc.listnum | This key is used to capture listname or listnumber, primarily for collecting access-list | keyword |
| rsa.misc.load_data |  | keyword |
| rsa.misc.location_floor |  | keyword |
| rsa.misc.location_mark |  | keyword |
| rsa.misc.log_id |  | keyword |
| rsa.misc.log_session_id | This key is used to capture a sessionid from the session directly | keyword |
| rsa.misc.log_session_id1 | This key is used to capture a Linked (Related) Session ID from the session directly | keyword |
| rsa.misc.log_type |  | keyword |
| rsa.misc.logid |  | keyword |
| rsa.misc.logip |  | keyword |
| rsa.misc.logname |  | keyword |
| rsa.misc.longitude |  | keyword |
| rsa.misc.lport |  | keyword |
| rsa.misc.mail_id | This key is used to capture the mailbox id/name | keyword |
| rsa.misc.match | This key is for regex match name from search.ini | keyword |
| rsa.misc.mbug_data |  | keyword |
| rsa.misc.message_body | This key captures the The contents of the message body. | keyword |
| rsa.misc.misc |  | keyword |
| rsa.misc.misc_name |  | keyword |
| rsa.misc.mode |  | keyword |
| rsa.misc.msgIdPart1 |  | keyword |
| rsa.misc.msgIdPart2 |  | keyword |
| rsa.misc.msgIdPart3 |  | keyword |
| rsa.misc.msgIdPart4 |  | keyword |
| rsa.misc.msg_type |  | keyword |
| rsa.misc.msgid |  | keyword |
| rsa.misc.name |  | keyword |
| rsa.misc.netsessid |  | keyword |
| rsa.misc.node | Common use case is the node name within a cluster. The cluster name is reflected by the host name. | keyword |
| rsa.misc.ntype |  | keyword |
| rsa.misc.num |  | keyword |
| rsa.misc.number |  | keyword |
| rsa.misc.number1 |  | keyword |
| rsa.misc.number2 |  | keyword |
| rsa.misc.nwwn |  | keyword |
| rsa.misc.obj_name | This is used to capture name of object | keyword |
| rsa.misc.obj_type | This is used to capture type of object | keyword |
| rsa.misc.object |  | keyword |
| rsa.misc.observed_val | This key captures the Value observed (from the perspective of the device generating the log). | keyword |
| rsa.misc.operation |  | keyword |
| rsa.misc.operation_id | An alert number or operation number. The values should be unique and non-repeating. | keyword |
| rsa.misc.opkt |  | keyword |
| rsa.misc.orig_from |  | keyword |
| rsa.misc.owner_id |  | keyword |
| rsa.misc.p_action |  | keyword |
| rsa.misc.p_filter |  | keyword |
| rsa.misc.p_group_object |  | keyword |
| rsa.misc.p_id |  | keyword |
| rsa.misc.p_msgid |  | keyword |
| rsa.misc.p_msgid1 |  | keyword |
| rsa.misc.p_msgid2 |  | keyword |
| rsa.misc.p_result1 |  | keyword |
| rsa.misc.param | This key is the parameters passed as part of a command or application, etc. | keyword |
| rsa.misc.param_dst | This key captures the command line/launch argument of the target process or file | keyword |
| rsa.misc.param_src | This key captures source parameter | keyword |
| rsa.misc.parent_node | This key captures the Parent Node Name. Must be related to node variable. | keyword |
| rsa.misc.password_chg |  | keyword |
| rsa.misc.password_expire |  | keyword |
| rsa.misc.payload_dst | This key is used to capture destination payload | keyword |
| rsa.misc.payload_src | This key is used to capture source payload | keyword |
| rsa.misc.permgranted |  | keyword |
| rsa.misc.permwanted |  | keyword |
| rsa.misc.pgid |  | keyword |
| rsa.misc.phone |  | keyword |
| rsa.misc.pid |  | keyword |
| rsa.misc.policy |  | keyword |
| rsa.misc.policyUUID |  | keyword |
| rsa.misc.policy_id | This key is used to capture the Policy ID only, this should be a numeric value, use policy.name otherwise | keyword |
| rsa.misc.policy_name | This key is used to capture the Policy Name only. | keyword |
| rsa.misc.policy_value | This key captures the contents of the policy. This contains details about the policy | keyword |
| rsa.misc.policy_waiver |  | keyword |
| rsa.misc.pool_id | This key captures the identifier (typically numeric field) of a resource pool | keyword |
| rsa.misc.pool_name | This key captures the name of a resource pool | keyword |
| rsa.misc.port_name | This key is used for Physical or logical port connection but does NOT include a network port. (Example: Printer port name). | keyword |
| rsa.misc.priority |  | keyword |
| rsa.misc.process_id_val | This key is a failure key for Process ID when it is not an integer value | keyword |
| rsa.misc.prog_asp_num |  | keyword |
| rsa.misc.program |  | keyword |
| rsa.misc.real_data |  | keyword |
| rsa.misc.reason |  | keyword |
| rsa.misc.rec_asp_device |  | keyword |
| rsa.misc.rec_asp_num |  | keyword |
| rsa.misc.rec_library |  | keyword |
| rsa.misc.recordnum |  | keyword |
| rsa.misc.reference_id | This key is used to capture an event id from the session directly | keyword |
| rsa.misc.reference_id1 | This key is for Linked ID to be used as an addition to "reference.id" | keyword |
| rsa.misc.reference_id2 | This key is for the 2nd Linked ID. Can be either linked to "reference.id" or "reference.id1" value but should not be used unless the other two variables are in play. | keyword |
| rsa.misc.result | This key is used to capture the outcome/result string value of an action in a session. | keyword |
| rsa.misc.result_code | This key is used to capture the outcome/result numeric value of an action in a session | keyword |
| rsa.misc.risk | This key captures the non-numeric risk value | keyword |
| rsa.misc.risk_info | Deprecated, use New Hunting Model (inv.\*, ioc, boc, eoc, analysis.\*) | keyword |
| rsa.misc.risk_num | This key captures a Numeric Risk value | double |
| rsa.misc.risk_num_comm | This key captures Risk Number Community | double |
| rsa.misc.risk_num_next | This key captures Risk Number NextGen | double |
| rsa.misc.risk_num_sand | This key captures Risk Number SandBox | double |
| rsa.misc.risk_num_static | This key captures Risk Number Static | double |
| rsa.misc.risk_suspicious | Deprecated, use New Hunting Model (inv.\*, ioc, boc, eoc, analysis.\*) | keyword |
| rsa.misc.risk_warning | Deprecated, use New Hunting Model (inv.\*, ioc, boc, eoc, analysis.\*) | keyword |
| rsa.misc.ruid |  | keyword |
| rsa.misc.rule | This key captures the Rule number | keyword |
| rsa.misc.rule_group | This key captures the Rule group name | keyword |
| rsa.misc.rule_name | This key captures the Rule Name | keyword |
| rsa.misc.rule_template | A default set of parameters which are overlayed onto a rule (or rulename) which efffectively constitutes a template | keyword |
| rsa.misc.rule_uid | This key is the Unique Identifier for a rule. | keyword |
| rsa.misc.sburb |  | keyword |
| rsa.misc.sdomain_fld |  | keyword |
| rsa.misc.search_text | This key captures the Search Text used | keyword |
| rsa.misc.sec |  | keyword |
| rsa.misc.second |  | keyword |
| rsa.misc.sensor | This key captures Name of the sensor. Typically used in IDS/IPS based devices | keyword |
| rsa.misc.sensorname |  | keyword |
| rsa.misc.seqnum |  | keyword |
| rsa.misc.serial_number | This key is the Serial number associated with a physical asset. | keyword |
| rsa.misc.session |  | keyword |
| rsa.misc.sessiontype |  | keyword |
| rsa.misc.severity | This key is used to capture the severity given the session | keyword |
| rsa.misc.sigUUID |  | keyword |
| rsa.misc.sig_id | This key captures IDS/IPS Int Signature ID | long |
| rsa.misc.sig_id1 | This key captures IDS/IPS Int Signature ID. This must be linked to the sig.id | long |
| rsa.misc.sig_id_str | This key captures a string object of the sigid variable. | keyword |
| rsa.misc.sig_name | This key is used to capture the Signature Name only. | keyword |
| rsa.misc.sigcat |  | keyword |
| rsa.misc.snmp_oid | SNMP Object Identifier | keyword |
| rsa.misc.snmp_value | SNMP set request value | keyword |
| rsa.misc.space |  | keyword |
| rsa.misc.space1 |  | keyword |
| rsa.misc.spi |  | keyword |
| rsa.misc.spi_dst | Destination SPI Index | keyword |
| rsa.misc.spi_src | Source SPI Index | keyword |
| rsa.misc.sql | This key captures the SQL query | keyword |
| rsa.misc.srcburb |  | keyword |
| rsa.misc.srcdom |  | keyword |
| rsa.misc.srcservice |  | keyword |
| rsa.misc.state |  | keyword |
| rsa.misc.status |  | keyword |
| rsa.misc.status1 |  | keyword |
| rsa.misc.streams | This key captures number of streams in session | long |
| rsa.misc.subcategory |  | keyword |
| rsa.misc.svcno |  | keyword |
| rsa.misc.system |  | keyword |
| rsa.misc.tbdstr1 |  | keyword |
| rsa.misc.tbdstr2 |  | keyword |
| rsa.misc.tcp_flags | This key is captures the TCP flags set in any packet of session | long |
| rsa.misc.terminal | This key captures the Terminal Names only | keyword |
| rsa.misc.tgtdom |  | keyword |
| rsa.misc.tgtdomain |  | keyword |
| rsa.misc.threshold |  | keyword |
| rsa.misc.tos | This key describes the type of service | long |
| rsa.misc.trigger_desc | This key captures the Description of the trigger or threshold condition. | keyword |
| rsa.misc.trigger_val | This key captures the Value of the trigger or threshold condition. | keyword |
| rsa.misc.type |  | keyword |
| rsa.misc.type1 |  | keyword |
| rsa.misc.udb_class |  | keyword |
| rsa.misc.url_fld |  | keyword |
| rsa.misc.user_div |  | keyword |
| rsa.misc.userid |  | keyword |
| rsa.misc.username_fld |  | keyword |
| rsa.misc.utcstamp |  | keyword |
| rsa.misc.v_instafname |  | keyword |
| rsa.misc.version | This key captures Version of the application or OS which is generating the event. | keyword |
| rsa.misc.virt_data |  | keyword |
| rsa.misc.virusname | This key captures the name of the virus | keyword |
| rsa.misc.vm_target | VMWare Target \*\*VMWARE\*\* only varaible. | keyword |
| rsa.misc.vpnid |  | keyword |
| rsa.misc.vsys | This key captures Virtual System Name | keyword |
| rsa.misc.vuln_ref | This key captures the Vulnerability Reference details | keyword |
| rsa.misc.workspace | This key captures Workspace Description | keyword |
| rsa.network.ad_computer_dst | Deprecated, use host.dst | keyword |
| rsa.network.addr |  | keyword |
| rsa.network.alias_host | This key should be used when the source or destination context of a hostname is not clear.Also it captures the Device Hostname. Any Hostname that isnt ad.computer. | keyword |
| rsa.network.dinterface | This key should only be used when it’s a Destination Interface | keyword |
| rsa.network.dmask | This key is used for Destionation Device network mask | keyword |
| rsa.network.dns_a_record |  | keyword |
| rsa.network.dns_cname_record |  | keyword |
| rsa.network.dns_id |  | keyword |
| rsa.network.dns_opcode |  | keyword |
| rsa.network.dns_ptr_record |  | keyword |
| rsa.network.dns_resp |  | keyword |
| rsa.network.dns_type |  | keyword |
| rsa.network.domain |  | keyword |
| rsa.network.domain1 |  | keyword |
| rsa.network.eth_host | Deprecated, use alias.mac | keyword |
| rsa.network.eth_type | This key is used to capture Ethernet Type, Used for Layer 3 Protocols Only | long |
| rsa.network.faddr |  | keyword |
| rsa.network.fhost |  | keyword |
| rsa.network.fport |  | keyword |
| rsa.network.gateway | This key is used to capture the IP Address of the gateway | keyword |
| rsa.network.host_dst | This key should only be used when it’s a Destination Hostname | keyword |
| rsa.network.host_orig | This is used to capture the original hostname in case of a Forwarding Agent or a Proxy in between. | keyword |
| rsa.network.host_type |  | keyword |
| rsa.network.icmp_code | This key is used to capture the ICMP code only | long |
| rsa.network.icmp_type | This key is used to capture the ICMP type only | long |
| rsa.network.interface | This key should be used when the source or destination context of an interface is not clear | keyword |
| rsa.network.ip_proto | This key should be used to capture the Protocol number, all the protocol nubers are converted into string in UI | long |
| rsa.network.laddr |  | keyword |
| rsa.network.lhost |  | keyword |
| rsa.network.linterface |  | keyword |
| rsa.network.mask | This key is used to capture the device network IPmask. | keyword |
| rsa.network.netname | This key is used to capture the network name associated with an IP range. This is configured by the end user. | keyword |
| rsa.network.network_port | Deprecated, use port. NOTE: There is a type discrepancy as currently used, TM: Int32, INDEX: UInt64 (why neither chose the correct UInt16?!) | long |
| rsa.network.network_service | This is used to capture layer 7 protocols/service names | keyword |
| rsa.network.origin |  | keyword |
| rsa.network.packet_length |  | keyword |
| rsa.network.paddr | Deprecated | ip |
| rsa.network.phost |  | keyword |
| rsa.network.port | This key should only be used to capture a Network Port when the directionality is not clear | long |
| rsa.network.protocol_detail | This key should be used to capture additional protocol information | keyword |
| rsa.network.remote_domain_id |  | keyword |
| rsa.network.rpayload | This key is used to capture the total number of payload bytes seen in the retransmitted packets. | keyword |
| rsa.network.sinterface | This key should only be used when it’s a Source Interface | keyword |
| rsa.network.smask | This key is used for capturing source Network Mask | keyword |
| rsa.network.vlan | This key should only be used to capture the ID of the Virtual LAN | long |
| rsa.network.vlan_name | This key should only be used to capture the name of the Virtual LAN | keyword |
| rsa.network.zone | This key should be used when the source or destination context of a Zone is not clear | keyword |
| rsa.network.zone_dst | This key should only be used when it’s a Destination Zone. | keyword |
| rsa.network.zone_src | This key should only be used when it’s a Source Zone. | keyword |
| rsa.physical.org_dst | This is used to capture the destination organization based on the GEOPIP Maxmind database. | keyword |
| rsa.physical.org_src | This is used to capture the source organization based on the GEOPIP Maxmind database. | keyword |
| rsa.storage.disk_volume | A unique name assigned to logical units (volumes) within a physical disk | keyword |
| rsa.storage.lun | Logical Unit Number.This key is a very useful concept in Storage. | keyword |
| rsa.storage.pwwn | This uniquely identifies a port on a HBA. | keyword |
| rsa.threat.alert | This key is used to capture name of the alert | keyword |
| rsa.threat.threat_category | This key captures Threat Name/Threat Category/Categorization of alert | keyword |
| rsa.threat.threat_desc | This key is used to capture the threat description from the session directly or inferred | keyword |
| rsa.threat.threat_source | This key is used to capture source of the threat | keyword |
| rsa.time.date |  | keyword |
| rsa.time.datetime |  | keyword |
| rsa.time.day |  | keyword |
| rsa.time.duration_str | A text string version of the duration | keyword |
| rsa.time.duration_time | This key is used to capture the normalized duration/lifetime in seconds. | double |
| rsa.time.effective_time | This key is the effective time referenced by an individual event in a Standard Timestamp format | date |
| rsa.time.endtime | This key is used to capture the End time mentioned in a session in a standard form | date |
| rsa.time.event_queue_time | This key is the Time that the event was queued. | date |
| rsa.time.event_time | This key is used to capture the time mentioned in a raw session that represents the actual time an event occured in a standard normalized form | date |
| rsa.time.event_time_str | This key is used to capture the incomplete time mentioned in a session as a string | keyword |
| rsa.time.eventtime |  | keyword |
| rsa.time.expire_time | This key is the timestamp that explicitly refers to an expiration. | date |
| rsa.time.expire_time_str | This key is used to capture incomplete timestamp that explicitly refers to an expiration. | keyword |
| rsa.time.gmtdate |  | keyword |
| rsa.time.gmttime |  | keyword |
| rsa.time.hour |  | keyword |
| rsa.time.min |  | keyword |
| rsa.time.month |  | keyword |
| rsa.time.p_date |  | keyword |
| rsa.time.p_month |  | keyword |
| rsa.time.p_time |  | keyword |
| rsa.time.p_time1 |  | keyword |
| rsa.time.p_time2 |  | keyword |
| rsa.time.p_year |  | keyword |
| rsa.time.process_time | Deprecated, use duration.time | keyword |
| rsa.time.recorded_time | The event time as recorded by the system the event is collected from. The usage scenario is a multi-tier application where the management layer of the system records it's own timestamp at the time of collection from its child nodes. Must be in timestamp format. | date |
| rsa.time.stamp | Deprecated key defined only in table map. | date |
| rsa.time.starttime | This key is used to capture the Start time mentioned in a session in a standard form | date |
| rsa.time.timestamp |  | keyword |
| rsa.time.timezone | This key is used to capture the timezone of the Event Time | keyword |
| rsa.time.tzone |  | keyword |
| rsa.time.year |  | keyword |
| rsa.web.alias_host |  | keyword |
| rsa.web.cn_asn_dst |  | keyword |
| rsa.web.cn_rpackets |  | keyword |
| rsa.web.fqdn | Fully Qualified Domain Names | keyword |
| rsa.web.p_url |  | keyword |
| rsa.web.p_user_agent |  | keyword |
| rsa.web.p_web_cookie |  | keyword |
| rsa.web.p_web_method |  | keyword |
| rsa.web.p_web_referer |  | keyword |
| rsa.web.remote_domain |  | keyword |
| rsa.web.reputation_num | Reputation Number of an entity. Typically used for Web Domains | double |
| rsa.web.urlpage |  | keyword |
| rsa.web.urlroot |  | keyword |
| rsa.web.web_cookie | This key is used to capture the Web cookies specifically. | keyword |
| rsa.web.web_extension_tmp |  | keyword |
| rsa.web.web_page |  | keyword |
| rsa.web.web_ref_domain | Web referer's domain | keyword |
| rsa.web.web_ref_page | This key captures Web referer's page information | keyword |
| rsa.web.web_ref_query | This key captures Web referer's query portion of the URL | keyword |
| rsa.web.web_ref_root | Web referer's root URL path | keyword |
| rsa.wireless.access_point | This key is used to capture the access point name. | keyword |
| rsa.wireless.wlan_channel | This is used to capture the channel names | long |
| rsa.wireless.wlan_name | This key captures either WLAN number/name | keyword |
| rsa.wireless.wlan_ssid | This key is used to capture the ssid of a Wireless Session | keyword |
| rule.name | The name of the rule or signature generating the event. | keyword |
| server.domain | The domain name of the server system. This value may be a host name, a fully qualified domain name, or another host naming format. The value may derive from the original event or be added from enrichment. | keyword |
| server.registered_domain | The highest registered server domain, stripped of the subdomain. For example, the registered domain for "foo.example.com" is "example.com". This value can be determined precisely with a list like the public suffix list (http://publicsuffix.org). Trying to approximate this by simply taking the last two labels will not work well for TLDs such as "co.uk". | keyword |
| server.subdomain | The subdomain portion of a fully qualified domain name includes all of the names except the host name under the registered_domain.  In a partially qualified domain, or if the the qualification level of the full name cannot be determined, subdomain contains all of the names below the registered domain. For example the subdomain portion of "www.east.mydomain.co.uk" is "east". If the domain has multiple levels of subdomain, such as "sub2.sub1.example.com", the subdomain field should contain "sub2.sub1", with no trailing period. | keyword |
| server.top_level_domain | The effective top level domain (eTLD), also known as the domain suffix, is the last part of the domain name. For example, the top level domain for example.com is "com". This value can be determined precisely with a list like the public suffix list (http://publicsuffix.org). Trying to approximate this by simply taking the last label will not work well for effective TLDs such as "co.uk". | keyword |
| service.name | Name of the service data is collected from. The name of the service is normally user given. This allows for distributed services that run on multiple hosts to correlate the related instances based on the name. In the case of Elasticsearch the `service.name` could contain the cluster name. For Beats the `service.name` is by default a copy of the `service.type` field if no name is specified. | keyword |
| source.address | Some event source addresses are defined ambiguously. The event will sometimes list an IP, a domain or a unix socket.  You should always store the raw address in the `.address` field. Then it should be duplicated to `.ip` or `.domain`, depending on which one it is. | keyword |
| source.as.number | Unique number allocated to the autonomous system. The autonomous system number (ASN) uniquely identifies each network on the Internet. | long |
| source.as.organization.name | Organization name. | keyword |
| source.as.organization.name.text | Multi-field of `source.as.organization.name`. | match_only_text |
| source.bytes | Bytes sent from the source to the destination. | long |
| source.domain | The domain name of the source system. This value may be a host name, a fully qualified domain name, or another host naming format. The value may derive from the original event or be added from enrichment. | keyword |
| source.geo.city_name | City name. | keyword |
| source.geo.country_name | Country name. | keyword |
| source.geo.location | Longitude and latitude. | geo_point |
| source.ip | IP address of the source (IPv4 or IPv6). | ip |
| source.mac | MAC address of the source. The notation format from RFC 7042 is suggested: Each octet (that is, 8-bit byte) is represented by two [uppercase] hexadecimal digits giving the value of the octet as an unsigned integer. Successive octets are separated by a hyphen. | keyword |
| source.nat.ip | Translated ip of source based NAT sessions (e.g. internal client to internet) Typically connections traversing load balancers, firewalls, or routers. | ip |
| source.nat.port | Translated port of source based NAT sessions. (e.g. internal client to internet) Typically used with load balancers, firewalls, or routers. | long |
| source.port | Port of the source. | long |
| source.registered_domain | The highest registered source domain, stripped of the subdomain. For example, the registered domain for "foo.example.com" is "example.com". This value can be determined precisely with a list like the public suffix list (http://publicsuffix.org). Trying to approximate this by simply taking the last two labels will not work well for TLDs such as "co.uk". | keyword |
| source.subdomain | The subdomain portion of a fully qualified domain name includes all of the names except the host name under the registered_domain.  In a partially qualified domain, or if the the qualification level of the full name cannot be determined, subdomain contains all of the names below the registered domain. For example the subdomain portion of "www.east.mydomain.co.uk" is "east". If the domain has multiple levels of subdomain, such as "sub2.sub1.example.com", the subdomain field should contain "sub2.sub1", with no trailing period. | keyword |
| source.top_level_domain | The effective top level domain (eTLD), also known as the domain suffix, is the last part of the domain name. For example, the top level domain for example.com is "com". This value can be determined precisely with a list like the public suffix list (http://publicsuffix.org). Trying to approximate this by simply taking the last label will not work well for effective TLDs such as "co.uk". | keyword |
| tags | List of keywords used to tag each event. | keyword |
| url.domain | Domain of the url, such as "www.elastic.co". In some cases a URL may refer to an IP and/or port directly, without a domain name. In this case, the IP address would go to the `domain` field. If the URL contains a literal IPv6 address enclosed by `[` and `]` (IETF RFC 2732), the `[` and `]` characters should also be captured in the `domain` field. | keyword |
| url.original | Unmodified original url as seen in the event source. Note that in network monitoring, the observed URL may be a full URL, whereas in access logs, the URL is often just represented as a path. This field is meant to represent the URL as it was observed, complete or not. | wildcard |
| url.original.text | Multi-field of `url.original`. | match_only_text |
| url.path | Path of the request, such as "/search". | wildcard |
| url.query | The query field describes the query string of the request, such as "q=elasticsearch". The `?` is excluded from the query string. If a URL contains no `?`, there is no query field. If there is a `?` but no query, the query field exists with an empty string. The `exists` query can be used to differentiate between the two cases. | keyword |
| url.registered_domain | The highest registered url domain, stripped of the subdomain. For example, the registered domain for "foo.example.com" is "example.com". This value can be determined precisely with a list like the public suffix list (http://publicsuffix.org). Trying to approximate this by simply taking the last two labels will not work well for TLDs such as "co.uk". | keyword |
| url.top_level_domain | The effective top level domain (eTLD), also known as the domain suffix, is the last part of the domain name. For example, the top level domain for example.com is "com". This value can be determined precisely with a list like the public suffix list (http://publicsuffix.org). Trying to approximate this by simply taking the last label will not work well for effective TLDs such as "co.uk". | keyword |
| user.domain | Name of the directory the user is a member of. For example, an LDAP or Active Directory domain name. | keyword |
| user.full_name | User's full name, if available. | keyword |
| user.full_name.text | Multi-field of `user.full_name`. | match_only_text |
| user.id | Unique identifier of the user. | keyword |
| user.name | Short name or login of the user. | keyword |
| user.name.text | Multi-field of `user.name`. | match_only_text |
| user_agent.original | Unparsed user_agent string. | keyword |
| user_agent.original.text | Multi-field of `user_agent.original`. | match_only_text |

