# notWG - obfuscated secure tunnel for OpenWrt & Ubuntu, based on WireGuard

There are several ways DPI can detect WireGurad traffic

- The handshake initiation, response and cookie message have fixed sizes
- All messages have 4 byte tag where the first byte indicates message type [1-4] and remaining three bytes are zeroes.
- Handshake packet header contains sender and receiver indexes which are sent unencrypted and can be tracked.

Packet is obfuscated using two techniques

- Random junk bytes are appended to handshake and cookie packets
- Packet header is encrypted with blake2s hash of interface public key and random nonce.

## Building
see `readme.txt`

**More information may be found at [WireGuard.com](https://www.wireguard.com/).**

## License

This project is released under the [GPLv2](COPYING).
