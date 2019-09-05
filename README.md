Privacy-oriented DNS-over-TLS Resolver
======================================

This ansible playbook / roles can be be used to deploy DNS-over-TLS only
Knot Resolver for Debian 9.

Features
--------

- DNS-over-TLS only - to avoid abuse of resolver for DDoS amplification attacks
- cache pre-warming with [Cisco
  Umbrella](http://s3-us-west-1.amazonaws.com/umbrella-static/index.html)
  domain popularity list for improved performance and privacy
- uses latest upstream [Knot Resolver](https://www.knot-resolver.cz)
- Debian 9 compatible

TODO
----

- automate certificate renewal
- go through [DNS Privacy Service Recommendations](https://datatracker.ietf.org/doc/draft-ietf-dprive-bcp-op/)
