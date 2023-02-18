# ingress-redirector
Helm chart for creating ingress configuration to redirect traffic from one domain to another

Requires nginx based ingress controller, but do not require any running pods or deployments.

Syntax error in configuration will block configuration reload on the ingress controller level. See more: [Disadvantages of Using Snippets](https://docs.nginx.com/nginx-ingress-controller/configuration/ingress-resources/advanced-configuration-with-snippets/#disadvantages-of-using-snippets)

See values.yaml for configuration instructions:

```yaml
namespace: ingress-redirector

## Defaults to nginx
# ingressClassName: "nginx"

ingress:
## Uncomment to choose certificate manager and other annotations
#  annotations:
#    cert-manager.io/cluster-issuer: "letsencrypt-prod"
 
  hosts:
    - host: old-domain.tld

## TLS rules if applicable
#  tls:
#    - secretName: ingress-redirector-certificate
#      hosts:
#        - old-domain.tld

## Set of redirect rules, from is a path, but to is a full URL
redirectRules: []
#  - from: /path
#    to: https://new-domain.tld/newpath
#    code: 301
#  - from: /
#    to: https://new-domain.tld/
#    code: 302

```