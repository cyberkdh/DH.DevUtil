# CIDR Calculator

[한국어](./CIDR_CALCULATOR.ko.md)

CIDR Calculator calculates IPv4 network details locally in a standalone HTML file.

## Features

- Parse IPv4 addresses with `/0` to `/32` prefixes.
- Show network, broadcast, subnet mask, wildcard mask, total address count, usable host count, and host range.
- Display address and mask in binary.
- Split a network into longer prefixes from `/25` through `/30`.
- Validate input without sending values to a server.
- Switch between English and Korean UI.

## How to use

1. Open [CIDR Calculator](../tools/DH.DevUtil.cidr-calculator.html).
2. Enter an address such as `192.168.10.37/24`.
3. Review the normalized network block and host range.
4. Select a longer prefix to list the resulting subnets.

## Important details

- This tool currently supports IPv4 only.
- Traditional usable host counts exclude network and broadcast addresses. `/31` returns two addresses for point-to-point links, and `/32` returns one address.
- Subnet tables are capped at 4,096 rows to keep the browser responsive.

## Privacy

All processing happens in the current browser tab. No value is uploaded or stored.
