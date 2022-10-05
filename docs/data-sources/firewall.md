# routeros_firewall (Data Source)
This datasource contains all supported firewall resources:
- address_list
- nat
- mangle
- rules (aka filter)

## Example Usage
```terraform
data "routeros_firewall" "fw" {
  rules = {
    chain = "input"
    comment = "rule_2"
  }

  nat {}
}

output "rules" {
  value = [for value in data.routeros_firewall.fw.rules: [value.id, value.src_address]]
}

output "nat" {
  value = [for value in data.routeros_firewall.fw.nat: [value.id, value.comment]]
}

resource "routeros_firewall" "rule_3" {
  action = "accept"
  chain  = "input"
  comment = "rule_3"
  src_address = "192.168.0.5"
  place_before = "${data.routeros_firewall_filter.fw.rules[0].id}"
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Optional

- `address_list` (Block List) (see [below for nested schema](#nestedblock--address_list))
- `mangle` (Block List) (see [below for nested schema](#nestedblock--mangle))
- `nat` (Block List) (see [below for nested schema](#nestedblock--nat))
- `rules` (Block List) (see [below for nested schema](#nestedblock--rules))

### Read-Only

- `id` (String) The ID of this resource.

<a id="nestedblock--address_list"></a>
### Nested Schema for `address_list`

Optional:

- `filter` (Map of String) Additional request filtering options.

Read-Only:

- `address` (String)
- `comment` (String)
- `creation_time` (String)
- `disabled` (Boolean)
- `dynamic` (Boolean)
- `id` (String) The ID of this resource.
- `list` (String)
- `timeout` (String)


<a id="nestedblock--mangle"></a>
### Nested Schema for `mangle`

Optional:

- `filter` (Map of String) Additional request filtering options.

Read-Only:

- `action` (String)
- `address_list` (String)
- `address_list_timeout` (String)
- `bytes` (Number)
- `chain` (String)
- `comment` (String)
- `connection_bytes` (String)
- `connection_limit` (String)
- `connection_mark` (String)
- `connection_nat_state` (String)
- `connection_rate` (String)
- `connection_state` (String)
- `connection_type` (String)
- `content` (String)
- `disabled` (Boolean)
- `dscp` (Number)
- `dst_address` (String)
- `dst_address_list` (String)
- `dst_address_type` (String)
- `dst_limit` (String)
- `dst_port` (String)
- `dynamic` (Boolean)
- `fragment` (Boolean)
- `hotspot` (String)
- `icmp_options` (String)
- `id` (String) The ID of this resource.
- `in_bridge_port` (String)
- `in_bridge_port_list` (String)
- `in_interface` (String)
- `in_interface_list` (String)
- `ingress_priority` (Number)
- `invalid` (Boolean)
- `ipsec_policy` (String)
- `ipv4_options` (String)
- `jump_target` (String)
- `layer7_protocol` (String)
- `limit` (String)
- `log` (Boolean)
- `log_prefix` (String)
- `new_connection_mark` (String)
- `new_dscp` (Number)
- `new_mss` (Number)
- `new_packet_mark` (String)
- `new_priority` (String)
- `new_routing_mark` (String)
- `new_ttl` (String)
- `nth` (String)
- `out_bridge_port` (String)
- `out_bridge_port_list` (String)
- `out_interface` (String)
- `out_interface_list` (String)
- `packet_mark` (String)
- `packet_size` (String)
- `packets` (Number)
- `passthrough` (Boolean)
- `per_connection_classifier` (String)
- `port` (String)
- `protocol` (String)
- `psd` (String)
- `random` (Number)
- `route_dst` (String)
- `routing_mark` (String)
- `src_address` (String)
- `src_address_list` (String)
- `src_address_type` (String)
- `src_mac_address` (String)
- `src_port` (String)
- `tcp_flags` (String)
- `tcp_mss` (String)
- `time` (String)
- `tls_host` (String)
- `ttl` (String)


<a id="nestedblock--nat"></a>
### Nested Schema for `nat`

Optional:

- `filter` (Map of String) Additional request filtering options.

Read-Only:

- `action` (String)
- `address_list` (String)
- `address_list_timeout` (String)
- `bytes` (Number)
- `chain` (String)
- `comment` (String)
- `connection_bytes` (String)
- `connection_limit` (String)
- `connection_mark` (String)
- `connection_rate` (String)
- `connection_type` (String)
- `content` (String)
- `disabled` (Boolean)
- `dscp` (Number)
- `dst_address` (String)
- `dst_address_list` (String)
- `dst_address_type` (String)
- `dst_limit` (String)
- `dst_port` (String)
- `dynamic` (Boolean)
- `fragment` (Boolean)
- `hotspot` (String)
- `icmp_options` (String)
- `id` (String) The ID of this resource.
- `in_bridge_port` (String)
- `in_bridge_port_list` (String)
- `in_interface` (String)
- `in_interface_list` (String)
- `ingress_priority` (Number)
- `invalid` (Boolean)
- `ipsec_policy` (String)
- `ipv4_options` (String)
- `jump_target` (String)
- `layer7_protocol` (String)
- `limit` (String)
- `log` (Boolean)
- `log_prefix` (String)
- `nth` (String)
- `out_bridge_port` (String)
- `out_bridge_port_list` (String)
- `out_interface` (String)
- `out_interface_list` (String)
- `packet_mark` (String)
- `packet_size` (String)
- `packets` (Number)
- `per_connection_classifier` (String)
- `port` (String)
- `priority` (Number)
- `protocol` (String)
- `psd` (String)
- `random` (Number)
- `routing_mark` (String)
- `same_not_by_dst` (Boolean)
- `src_address` (String)
- `src_address_list` (String)
- `src_address_type` (String)
- `src_mac_address` (String)
- `src_port` (String)
- `tcp_mss` (String)
- `time` (String)
- `to_addresses` (String)
- `to_ports` (String)
- `ttl` (String)


<a id="nestedblock--rules"></a>
### Nested Schema for `rules`

Optional:

- `filter` (Map of String) Additional request filtering options.

Read-Only:

- `action` (String)
- `address_list_timeout` (String)
- `bytes` (Number)
- `chain` (String)
- `comment` (String)
- `connection_bytes` (String)
- `connection_limit` (String)
- `connection_mark` (String)
- `connection_nat_state` (String)
- `connection_rate` (String)
- `connection_state` (String)
- `connection_type` (String)
- `content` (String)
- `disabled` (Boolean)
- `dscp` (Number)
- `dst_address` (String)
- `dst_address_list` (String)
- `dst_address_type` (String)
- `dst_limit` (String)
- `dst_port` (String)
- `dynamic` (Boolean)
- `fragment` (Boolean)
- `hotspot` (String)
- `hw_offload` (Boolean)
- `icmp_options` (String)
- `id` (String) The ID of this resource.
- `in_bridge_port` (String)
- `in_bridge_port_list` (String)
- `in_interface` (String)
- `in_interface_list` (String)
- `ingress_priority` (Number)
- `invalid` (Boolean)
- `ipsec_policy` (String)
- `ipv4_options` (String)
- `jump_target` (String)
- `layer7_protocol` (String)
- `limit` (String)
- `log` (Boolean)
- `log_prefix` (String)
- `nth` (String)
- `out_bridge_port` (String)
- `out_bridge_port_list` (String)
- `out_interface` (String)
- `out_interface_list` (String)
- `packet_mark` (String)
- `packet_size` (String)
- `packets` (Number)
- `per_connection_classifier` (String)
- `port` (String)
- `priority` (Number)
- `protocol` (String)
- `psd` (String)
- `random` (Number)
- `reject_with` (String)
- `routing_mark` (String)
- `routing_table` (String)
- `src_address` (String)
- `src_address_list` (String)
- `src_address_type` (String)
- `src_mac_address` (String)
- `src_port` (String)
- `tcp_flags` (String)
- `tcp_mss` (String)
- `time` (String)
- `tls_host` (String)
- `ttl` (String)

