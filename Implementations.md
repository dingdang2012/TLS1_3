Here's a list of implementations of TLS 1.3.  Add your own.  Talk to [@martinthomson](/martinthomson) if you have questions.

# Implementations

name | language | role(s) | [[version|Implementations#version-negotiation]] | features/limitations
--- | --- | --- | --- | ---
[NSS](https://hg.mozilla.org/projects/nss) | C | C/S | -14 | FF2048, P-256, no HelloRetryRequest, PSK resumption (*DHE_PSK only), 0-RTT
[Mint](https://github.com/bifurcation/mint) | Go | C/S | -13 | PSK resumption
[nqsb](https://github.com/mirleft/ocaml-tls/tree/tls13) | OCaml | C/S | -11 | PSK/DHE-PSK, no EC*, no client auth, no 0RTT -- live server at tls13test.nqsb.io port 4433, records traces, ping [@hannesm](https://github.com/hannesm), contains a static PSK/DHE_PSK token: id: 0x0000 secret: 0x000102030405060708090a0b0c0d0e0f101112131415161718191a1b1c1d1e1f
ProtoTLS | JavaScript | C/S | -13 | EC/DHE/PSK, no HelloRetryRequest
miTLS | F* | C/S | -13 | EC/DHE/PSK, no HelloRetryRequest
[Tris](https://github.com/cloudflare/tls-tris) | Go | S | -13 | ECDHE, no HelloRetryRequest
BoringSSL | C | C/S | -13 |

# Version Negotiation

As of draft-16 (to be published) version negotiation is in the "supported_versions" extension.
Versions should advertise a draft version of TLS 1.3 as {0x7f, <version-number>}.

# Browsers

## Firefox

Need FF Nightly, uses NSS, updated periodically. Currently on -13.

Go to about:config and set `security.tls.version.max` version to 4.

## Chrome

Need Chrome Canary, uses BoringSSL.

Go to chrome:flags and switch the TLS max version to 1.3.

# Test servers

Implementation | Version | URL
--- | --- | ---
Tris+nginx | -13 | https://tls13.cloudflare.com 
Tris | -13 | https://tris.filippo.io 
[mod_nss](https://fedorahosted.org/mod_nss/) | -13 | https://tls13.crypto.mozilla.org/ 
