# Certificate tools

## showcert

Display information about certificates (or certificate bundles).

To show information about a single certificate:

```
showcert server.crt
```

To show information about all certificates in a bundle:

```
showcert -a cabundle.crt
```

## makecert

A tool for quickly creating self-signed certificates.

Create a certificate for your server `host.example.com`:

```
makecert server.crt host.example.com
```

The resulting certificate will have the provided hostname (`host.example.com`) as both the `commonName` as as a `subjectAlternativeName`:

```
$ showcert server.crt
sha256 Fingerprint=F8:7F:6B:60:53:71:1B:50:91:61:26:8E:19:9D:A1:05:8D:AA:2B:9F:C3:AD:D7:98:42:CD:33:A3:5F:B9:A6:09
subject=CN=host.example.com
issuer=CN=host.example.com
notBefore=Oct 23 17:10:48 2024 GMT
notAfter=Oct 21 17:10:48 2034 GMT
X509v3 Subject Alternative Name:
    DNS:host.example.com
```

You can add additional `subjectAlternativeName` values. E.g., to create a wildcard certificate:

```
makecert -d '*.example.com' server.crt host.example.com
```

## urlcert

Retrieve certificate from a website.

```
urlcert https://google.com | showcert
```

## splitcert

Split a certificate bundle into individual certificate files.

```
splitcert cabundle.crt
```
