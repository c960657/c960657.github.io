# RFC 7239 – `Forwarded` HTTP Header
[RFC 7239](https://tools.ietf.org/html/rfc7239) defines a new HTTP header, `Forwarded`, that is intended to replace the de-facto standard header [`X-Forwarded-For`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Forwarded-For) and friends, `X-Forwarded-Proto` and `X-Forwarded-Host`.

`X-Forwarded-For` is widely supported in proxy servers and middleware. `X-Forwarded-Proto` has less support, and with HTTPS becoming the new normal, this is increasingly annoying.

## Support
### Proxy servers
* **Apache httpd, mod_proxy_http**: No support, [bug report with patch available](https://bz.apache.org/bugzilla/show_bug.cgi?id=58001).
* **Apache Traffic Server**: [Supported](https://docs.trafficserver.apache.org/en/latest/admin-guide/files/records.config.en.html#proxy-config-http-insert-forwarded).
* **Go, net/http/httputil**: [Not supported](https://github.com/golang/go/issues/20526).
* **H2O**: [Not supported](https://github.com/h2o/h2o/issues/1617).
* **Nginx**: No native support, but [supported via configuration files](https://www.nginx.com/resources/wiki/start/topics/examples/forwarded/).
* **nghttpx**: [Supported](https://nghttp2.org/documentation/nghttpx.1.html?#cmdoption-nghttpx--add-forwarded).
* **Traefik**: [Not supported](https://github.com/ldez/traefik/blob/master/vendor/github.com/vulcand/oxy/forward/rewrite.go#L22).
* **Varnish**: No native support, but probably supported via configuration files.

### Libraries and middleware
#### Go
* **go-forwarded**: [Supported](https://github.com/stanvit/go-forwarded).
* **Gorilla web toolkit**: [Not supported](http://www.gorillatoolkit.org/pkg/handlers#ProxyHeaders).
* **httpforwarded**: [Supported](https://github.com/theckman/httpforwarded).

#### Java
* **Spring Boot**: [Not supported](https://github.com/spring-projects/spring-boot/blob/master/spring-boot-project/spring-boot-docs/src/main/asciidoc/howto.adoc#running-behind-a-front-end-proxy-server).
* **Spring Framework**: [Supported](https://docs.spring.io/spring/docs/current/javadoc-api/org/springframework/web/reactive/function/server/ServerRequest.html#i22).

#### .NET
* **ASP.NET**: [Not supported](https://github.com/aspnet/BasicMiddleware/issues/28).

#### Node
* **7239**: [Supported](https://www.npmjs.com/package/7239).
* **forwarded-http**: [Supported](https://www.npmjs.com/package/forwarded-http).
* **forwarded-parse**: [Supported](https://www.npmjs.com/package/forwarded-parse).
* **express-redirect-https**: [Supported](https://www.npmjs.com/package/express-redirect-https).

#### PHP
* **Drupal**: [Supported](https://api.drupal.org/api/drupal/vendor%21symfony%21http-foundation%21Request.php/function/Request%3A%3AsetTrustedHeaderName/8.5.x).
* **Laravel**: Supported.
* **MediaWiki**: [Not supported](https://github.com/wikimedia/mediawiki/blob/89843b44ce94bcbb75b69f25c00c30f0ecc12752/includes/WebRequest.php#L1208).
* **Symfony, HttpFoundation**: [Supported](https://symfony.com/doc/3.1/request/load_balancer_reverse_proxy.html).

#### Python
* **AIOHTTP**: [Supported](https://docs.aiohttp.org/en/v3.0.1/web_advanced.html#deploying-behind-a-proxy).

#### Ruby
* **Rails**: [Not supported](https://github.com/rails/rails/blob/master/actionpack/lib/action_dispatch/middleware/remote_ip.rb).

### Cloud services
* **Amazon CloudFront**: [Not supported](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/RequestAndResponseBehaviorCustomOrigin.html#RequestCustomIPAddresses).
* **Amazon Elastic Load Balancing**: [Not supported](https://docs.aws.amazon.com/elasticloadbalancing/latest/classic/x-forwarded-headers.html).
* **CloudFlare**: [Not supported](https://support.cloudflare.com/hc/en-us/articles/200170986-How-does-Cloudflare-handle-HTTP-Request-headers-).
