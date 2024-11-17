# libretranslate

![Version: 0.6.5](https://img.shields.io/badge/Version-0.6.5-informational?style=flat-square) ![AppVersion: v1.6.2](https://img.shields.io/badge/AppVersion-v1.6.2-informational?style=flat-square)

A Helm chart for Kubernetes to deploy LibreTranslate API

**Homepage:** <https://libretranslate.github.io/helm-chart/>

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| jessebot |  | <https://github.com/jessebot> |

## Source Code

* <https://github.com/LibreTranslate/LibreTranslate/>
* <https://github.com/LibreTranslate/helm-chart/>

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| adminUser.auth | string | `""` | copy the output from the htpasswd command here as a reference, e.g. YWRtaW46JGFwcjEkYlpydmYvUFYkSHBHSlhqZU1EN0ZON2kyYndsMVRNMQoK |
| adminUser.existingSecret | string | `""` | use an existing secret for admin user |
| adminUser.name | string | `""` | copy the username in base64 as a reference, e.g. YWRtaW4K |
| adminUser.password | string | `""` | copy the password as base64 for the admin user here as a reference e.g. bXlTZWNyZXRQYXNzd29yZAo= |
| adminUser.secretKeys.auth | string | `"auth"` |  |
| adminUser.secretKeys.name | string | `"name"` |  |
| adminUser.secretKeys.password | string | `"password"` |  |
| annotations | object | `{}` | Extra annotations |
| appConfig.apiKeysDbPath | string | `"/app/db/api_keys.db"` | Use a specific path inside the container for the local database. Can be absolute or relative |
| appConfig.apiKeysDbPathMount | string | `"/app/db"` | Use a specific path inside the container for the local database. Must be the same as apiKeysDbPath |
| appConfig.apiKeysRemote | string | `""` | Use this remote endpoint to query for valid API keys instead of using the local database (Default: Empty (use local db instead)) |
| appConfig.batchLimit | string | `"null"` | Set maximum number of texts to translate in a batch request (Default: No limit) |
| appConfig.charLimit | string | `"null"` | Set character limit (Default: No limit) |
| appConfig.frontendLanguageSource | string | `"auto"` | Set frontend default language - source |
| appConfig.frontendLanguageTarget | string | `"locale"` | Set frontend default language - target. Default is to match site's locale |
| appConfig.frontendTimeout | string | `"500"` | Set frontend translation timeout |
| appConfig.gaId | string | `""` | Enable Google Analytics on the API client page by providing an ID (Default: Empty (no tracking)) |
| appConfig.getApiKeyLink | string | `""` | Show a link in the UI where to direct users to get an API key (Default: Empty (no link shown on web ui)) |
| appConfig.host | string | `"0.0.0.0"` | Set host to bind the server to (Default: 127.0.0.1) |
| appConfig.loadOnly | string | `""` | Set available languages (Default: Empty (use all from argostranslate)) |
| appConfig.metricsAuthToken | string | `""` | Protect the /metrics endpoint by allowing only clients that have a valid Authorization Bearer token (Default: Empty (no auth required)) |
| appConfig.port | string | `"5000"` | Set port to bind the server to |
| appConfig.reqLimit | string | `"null"` | Set maximum number of requests per minute per client (outside of limits set by api keys). The default is "null" which means "no limit". If you set this to "null", and you provide an api key secret, we will set the default api key requests per minute to 120 by default, as you MUST set an api key limit |
| appConfig.reqLimitStorage | string | `"memory://"` | Storage URI to use for request limit data storage. See Flask Limiter |
| appConfig.sharedStorage | string | `"memory://"` | Shared storage URI to use for multi-process data sharing (e.g. when using gunicorn) |
| appConfig.threads | string | `"4"` | Set number of threads (Default: 4) |
| appConfig.urlPrefix | string | `""` | Add prefix to URL: example.com:5000/url-prefix/ (Default: /) |
| appSettings.apiKeys | string | `"false"` |  |
| appSettings.debug | string | `"false"` | Enable debug environment (Default: Disabled) |
| appSettings.disableFilesTranslation | string | `"false"` | Disable files translation (Default: File translation allowed) |
| appSettings.disableWebUi | string | `"false"` | Disable web ui (Default: Web Ui enabled) |
| appSettings.existingSecret | string | `""` | use an existing Kubernetes Secret for api key origin and secret |
| appSettings.metrics | string | `"false"` | Enable the /metrics endpoint for exporting Prometheus usage metrics (Default: Disabled) |
| appSettings.requireApiKeyOrigin | string | `""` | Require use of an API key for programmatic access to the API, unless the request origin matches this domain (Default: No restrictions on domain origin) |
| appSettings.requireApiKeySecret | string | `""` | Set this to an api key secret you'd like to use, or an existing k8s Secret use appSettings.existingSecret and appSettings.secretKeys.apiKeySecret. This currently acts as the default API Key. Uses appConfig.reqLimit as the default requests per minute. If you do not set appConfig.reqLimit (or leave it as "null"), the default requests per minute is 120 |
| appSettings.secretKeys.apiKeyOrigin | string | `""` | key in existing Kubernetes Secret for api key origin. If set, ignores appSettings.requireApiKeyOrigin |
| appSettings.secretKeys.apiKeySecret | string | `"secret"` | key in existing Kubernetes Secret for api key secret. If set, ignores appSettings.requireApiKeySecret |
| appSettings.ssl | string | `"false"` | Enable SSL (Default: Disabled) |
| appSettings.suggestions | string | `"false"` | Allow user suggestions (Default: Disabled) |
| appSettings.updateModels | string | `"false"` | Update language models at startup (Default: Only on if no models found) |
| fullnameOverride | string | `""` | Full name of the deployment to override the default one |
| image.pullPolicy | string | `"IfNotPresent"` | if you set the image tag to latest, set the pull policy to "latest" |
| image.repository | string | `"libretranslate/libretranslate"` | default image is pulled from docker hub |
| image.tag | string | `""` | this defaults to appVersion in Chart.yaml, but you can override it |
| imagePullSecrets | list | `[]` |  |
| ingress.annotations."nginx.ingress.kubernetes.io/proxy-body-size" | string | `"10m"` |  |
| ingress.className | string | `""` | set this to the name of the ingress controller class to use like nginx |
| ingress.enabled | bool | `false` |  |
| ingress.hosts[0].host | string | `"translate.example.com"` |  |
| ingress.hosts[0].paths[0].path | string | `"/"` |  |
| ingress.hosts[0].paths[0].pathType | string | `"Prefix"` |  |
| initContainerSecurityContext.runAsGroup | int | `0` |  |
| initContainerSecurityContext.runAsUser | int | `0` |  |
| livenessProbe | object | `{}` | Liveness probe for kubernetes |
| nameOverride | string | `""` | Chart name override |
| persistence.db.accessMode | string | `""` |  |
| persistence.db.existingClaim | string | `""` | use an existing persistent volume claim for the database. Setting this will ignore all other persistence.db parameters |
| persistence.db.size | string | `"1Gi"` |  |
| persistence.db.storageClass | string | `""` |  |
| persistence.enabled | bool | `false` |  |
| persistence.models.accessMode | string | `""` |  |
| persistence.models.existingClaim | string | `""` | use an existing persistent volume claim for the models. Setting this will ignore all other persistence.models parameters |
| persistence.models.size | string | `"10Gi"` | as of August 2023, the models are about 6.6GB in size for all languages |
| persistence.models.storageClass | string | `""` |  |
| podAnnotations | object | `{}` | Extra annotations for pods |
| podSecurityContext.runAsGroup | int | `1032` |  |
| podSecurityContext.runAsUser | int | `1032` |  |
| readinessProbe | object | `{}` | Readiness probe for kubernetes |
| replicaCount | int | `1` | Number of replicas |
| resources.limits.cpu | string | `"2000m"` |  |
| resources.limits.memory | string | `"2Gi"` |  |
| resources.requests.cpu | string | `"500m"` |  |
| resources.requests.memory | string | `"1Gi"` |  |
| securityContext.fsGroup | int | `1032` |  |
| service.port | int | `5000` | targetPort for the service. If you update this, you also need to update appConfig.port to match |
| service.type | string | `"ClusterIP"` |  |
| tolerations | list | `[]` | Extra tolerations for pods |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.14.2](https://github.com/norwoodj/helm-docs/releases/v1.14.2)
