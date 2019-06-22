Privacy-oriented DNS-over-TLS Resolver
======================================

This ansible playbook / roles can be be used to deploy DNS-over-TLS only
Knot Resolver for Debian 9.

dns.dns-tls.com
---------------

These playbooks are used to deploy and manage dns.dns-tls.com.

You can try out the resolver with `kdig` (part of `knot-dnsutils` in
Debian/Ubuntu or `knot-utils` in CentOS/Feodra):

```
kdig @dns.dns-tls.com +tls gnu.org
# or
kdig @185.8.166.185 +tls gnu.org
```

The server doesn't log your queries or IP address, only server-wide
[statistics](https://knot-resolver.readthedocs.io/en/latest/modules.html#statistics-collector)
(such as total number of queries answered) are collected. You can check out
[kresd.conf](./roles/knot-resolver/templates/kresd.conf) yourself.

The following configuration snippet can be used to configure your local [Knot
Resolver](https://www.knot-resolver.cz) to forward queries over TLS to
dns.dns-tls.com:

```
policy.add(policy.all(policy.TLS_FORWARD{{
	'185.8.166.185',
	hostname='dns.dns-tls.com',
}}))
```

To configure other DNS software, use the following information:
```
IPv4: 185.8.166.185
IPv6: 2a03:3b40:100::1:512
port: 853
hostname: dns.dns-tls.com
```

There is no SLA, so be prepared to use a backup server in case of an outage.

Happy Forwarding!

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
