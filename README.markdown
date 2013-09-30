# rewriting REST

confsed is a tool that proxies HTTP requests to a REST API that
returns JSON, allowing rewrites of string responses.

I wrote this because I'm NATting a service that self-describes, but
doesn't know how to address itself when sending clients off to
different ports.

I'm using this currently with a double-natted service (couchbase
server in docker in virtualbox via vagrant) successfully.

# Usage

Write a JSON rewrite rule thing:

```json
{
    "original": "rewritten",
    "1.2.3.4": "5.6.7.8"
}
```

Then run

    confsed -rewriteconf myconf.json http://origin/

Now, make all requests to the confsed server (default port is `7081`)
and the magic happens.
