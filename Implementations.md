Here's a list of implementations of TLS 1.3.  Add your own.  Talk to [@martinthomson](/martinthomson) if you have questions.

# Implementations

name | language | role(s) | [[version|Implementations#version-negotiation]] | features/limitations
--- | --- | --- | --- | ---
[NSS](https://hg.mozilla.org/projects/nss) | C | C/S | -11 | P-256 only, no HelloRetryRequest, PSK resumption (ECDHE_PSK only)
[Mint](https://github.com/bifurcation/mint) | Go | C/S | -11 | PSK resumption

# Version Negotiation

Note that most of these implementations signal the draft version in a two-octet extension that uses the code point `0xff02`.  Set this to the ASCII encoding of the draft suffix (for example, draft -12 is the value `0x494a`).  Until the final version is released, please require this extension before negotiating TLS 1.3.  If the value is not present, or it doesn't match your implemented version you should negotiate TLS 1.2, or fail.


