image_proxy
===========

Proxy scheme for http images embedded in https elgg sites


Non-https image urls not originating from the elgg host name are replaced with a proxy
url to mod/image_proxy/image.php
This file forwards the headers and image content from the http source through to the browser
using the elgg site ssl thereby removing unsecure content warnings from browsers.


The proxy has an encryption element to ensure that urls passed through are originating as
elgg content.  This uses the elgg site secret by default.
The elgg engine is not booted during the proxy forwarding process to keep things as lean as
possible.  A single database query is used to retrieve the site secret.

A custom secret solely for image proxying can optionally be set in settings.php

```
$CONFIG->image_proxy_secret = 'my secret string';
```