# Openfaas Helm Chart for Magda

![Version: 5.5.5-magda.1](https://img.shields.io/badge/Version-5.5.5--magda.1-informational?style=flat-square)

Enable Kubernetes as a backend for OpenFaaS (Functions as a Service)

> This chart is forked from https://github.com/openfaas/faas-netes/tree/master/chart/openfaas.
> Changes Summary:
> - Make it Helm 3 Compatible (Especially, how to handle CRD CustomResourceDefinition)
> - Auto create namespaces. Allows more streamlined / one step deployment via helm
> - Allow to use a different gateway / core namespace name.
> - Allow to overwrite gateway / core / function namespace name through `.Values.global`
> More see https://www.openfaas.com

> Please note: the default [`magda` chart](https://github.com/magda-io/magda/tree/master/deploy/helm/magda) has included this openfaas chart.
> This openfaas chart is only for users who want to create their customised magda deployment chart using [magda-core](https://github.com/magda-io/magda/tree/master/deploy/helm/magda-core).

## How to use

Add Magda Repo:

```bash
helm repo add magda-io https://charts.magda.io
```

Use as a dependecies of your Magda deployment:
```yaml
- name: openfaas
  version: 5.5.5-magda
  repository: "https://charts.magda.io"
  condition: global.openfaas.enabled
```

## Requirements

Kubernetes: `>= 1.14.0-0`

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` |  |
| alertmanager.create | bool | `true` |  |
| alertmanager.image | string | `"prom/alertmanager:v0.18.0"` |  |
| alertmanager.resources.limits.memory | string | `"50Mi"` |  |
| alertmanager.resources.requests.memory | string | `"25Mi"` |  |
| async | bool | `true` |  |
| basicAuthPlugin.image | string | `"quay.io/t1000/openfaas-basic-auth-plugin:0.17.0"` |  |
| basicAuthPlugin.replicas | int | `1` |  |
| basicAuthPlugin.resources.requests.cpu | string | `"20m"` |  |
| basicAuthPlugin.resources.requests.memory | string | `"50Mi"` |  |
| basic_auth | bool | `true` |  |
| clusterRole | bool | `false` |  |
| createFunctionNamespace | bool | `true` |  |
| createMainNamespace | bool | `true` |  |
| defaultValues.functionNamespace | string | `"openfaas-fn"` |  |
| defaultValues.mainNamespace | string | `"openfaas"` |  |
| defaultValues.namespacePrefix | string | `""` |  |
| exposeServices | bool | `true` |  |
| faasIdler.create | bool | `true` |  |
| faasIdler.dryRun | bool | `true` |  |
| faasIdler.image | string | `"quay.io/t1000/openfaas-faas-idler:0.2.1"` |  |
| faasIdler.inactivityDuration | string | `"30m"` |  |
| faasIdler.reconcileInterval | string | `"2m"` |  |
| faasIdler.replicas | int | `1` |  |
| faasIdler.resources.requests.memory | string | `"64Mi"` |  |
| faasnetes.httpProbe | bool | `true` |  |
| faasnetes.image | string | `"quay.io/t1000/openfaas-faas-netes:0.10.1"` |  |
| faasnetes.imagePullPolicy | string | `"Always"` |  |
| faasnetes.livenessProbe.initialDelaySeconds | int | `2` |  |
| faasnetes.livenessProbe.periodSeconds | int | `2` |  |
| faasnetes.livenessProbe.timeoutSeconds | int | `1` |  |
| faasnetes.readTimeout | string | `"60s"` |  |
| faasnetes.readinessProbe.initialDelaySeconds | int | `2` |  |
| faasnetes.readinessProbe.periodSeconds | int | `2` |  |
| faasnetes.readinessProbe.timeoutSeconds | int | `1` |  |
| faasnetes.resources.requests.cpu | string | `"50m"` |  |
| faasnetes.resources.requests.memory | string | `"120Mi"` |  |
| faasnetes.setNonRootUser | bool | `false` |  |
| faasnetes.writeTimeout | string | `"60s"` |  |
| gateway.directFunctions | bool | `true` |  |
| gateway.image | string | `"quay.io/t1000/openfaas-gateway:0.18.10"` |  |
| gateway.logsProviderURL | string | `""` |  |
| gateway.maxIdleConns | int | `1024` |  |
| gateway.maxIdleConnsPerHost | int | `1024` |  |
| gateway.nodePort | int | `31112` |  |
| gateway.readTimeout | string | `"65s"` |  |
| gateway.replicas | int | `1` |  |
| gateway.resources.requests.cpu | string | `"50m"` |  |
| gateway.resources.requests.memory | string | `"120Mi"` |  |
| gateway.scaleFromZero | bool | `true` |  |
| gateway.upstreamTimeout | string | `"60s"` |  |
| gateway.writeTimeout | string | `"65s"` |  |
| gatewayExternal.annotations | object | `{}` |  |
| generateBasicAuth | bool | `false` |  |
| global.openfaas | object | `{}` |  |
| httpProbe | bool | `true` |  |
| ingress.annotations."kubernetes.io/ingress.class" | string | `"nginx"` |  |
| ingress.enabled | bool | `false` |  |
| ingress.hosts[0].host | string | `"gateway.openfaas.local"` |  |
| ingress.hosts[0].path | string | `"/"` |  |
| ingress.hosts[0].serviceName | string | `"gateway"` |  |
| ingress.hosts[0].servicePort | int | `8080` |  |
| ingress.tls | string | `nil` |  |
| ingressOperator.create | bool | `false` |  |
| ingressOperator.image | string | `"quay.io/t1000/openfaas-ingress-operator:0.5.0"` |  |
| ingressOperator.replicas | int | `1` |  |
| ingressOperator.resources.requests.memory | string | `"25Mi"` |  |
| istio.mtls | bool | `false` |  |
| kubernetesDNSDomain | string | `"cluster.local"` |  |
| nats.channel | string | `"faas-request"` |  |
| nats.enableMonitoring | bool | `false` |  |
| nats.external.clusterName | string | `""` |  |
| nats.external.enabled | bool | `false` |  |
| nats.external.host | string | `""` |  |
| nats.external.port | string | `""` |  |
| nats.image | string | `"nats-streaming:0.17.0"` |  |
| nats.resources.requests.memory | string | `"120Mi"` |  |
| oauth2Plugin.audience | string | `"https://example.eu.auth0.com/api/v2/"` |  |
| oauth2Plugin.authorizeURL | string | `"https://example.eu.auth0.com/authorize"` |  |
| oauth2Plugin.baseHost | string | `"http://auth.oauth.example.com"` |  |
| oauth2Plugin.clientID | string | `"ID"` |  |
| oauth2Plugin.clientSecret | string | `"SECRET"` |  |
| oauth2Plugin.cookieDomain | string | `".oauth.example.com"` |  |
| oauth2Plugin.enabled | bool | `false` |  |
| oauth2Plugin.image | string | `"quay.io/t1000/openfaas-oidc-plugin:0.2.5"` |  |
| oauth2Plugin.insecureTLS | bool | `false` |  |
| oauth2Plugin.jwksURL | string | `"https://example.eu.auth0.com/.well-known/jwks.json"` |  |
| oauth2Plugin.license | string | `"example"` |  |
| oauth2Plugin.replicas | int | `1` |  |
| oauth2Plugin.resources.requests.cpu | string | `"50m"` |  |
| oauth2Plugin.resources.requests.memory | string | `"120Mi"` |  |
| oauth2Plugin.scopes | string | `"openid profile email"` |  |
| oauth2Plugin.securityContext | bool | `true` |  |
| oauth2Plugin.tokenURL | string | `"https://example.eu.auth0.com/oauth/token"` |  |
| oauth2Plugin.welcomePageURL | string | `"https://gw.oauth.example.com"` |  |
| openfaasImagePullPolicy | string | `"Always"` |  |
| operator.create | bool | `false` |  |
| operator.image | string | `"quay.io/t1000/openfaas-operator:0.14.1"` |  |
| operator.resources.requests.cpu | string | `"50m"` |  |
| operator.resources.requests.memory | string | `"120Mi"` |  |
| prometheus.create | bool | `true` |  |
| prometheus.image | string | `"prom/prometheus:v2.11.0"` |  |
| prometheus.resources.requests.memory | string | `"512Mi"` |  |
| psp | bool | `false` |  |
| queueWorker.ackWait | string | `"60s"` |  |
| queueWorker.durableQueueSubscription | bool | `false` |  |
| queueWorker.gatewayInvoke | bool | `true` |  |
| queueWorker.image | string | `"quay.io/t1000/openfaas-queue-worker:0.9.0"` |  |
| queueWorker.queueGroup | string | `"faas"` |  |
| queueWorker.replicas | int | `1` |  |
| queueWorker.resources.requests.cpu | string | `"50m"` |  |
| queueWorker.resources.requests.memory | string | `"120Mi"` |  |
| rbac | bool | `true` |  |
| securityContext | bool | `true` |  |
| serviceType | string | `"NodePort"` |  |
| tolerations | list | `[]` |  |