# entitlements

![Version: 0.0.1](https://img.shields.io/badge/Version-0.0.1-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: main](https://img.shields.io/badge/AppVersion-main-informational?style=flat-square)

A deployed service to configure entity/attribute mappings in an OpenTDF ABAC system

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| Virtru |  |  |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` | Pod scheduling preferences |
| autoscaling.enabled | bool | `false` | Enables autoscaling. When set to `true`, `replicas` is no longer applied. |
| autoscaling.maxReplicas | int | `100` | Sets maximum replicas for autoscaling. |
| autoscaling.minReplicas | int | `1` | Sets minimum replicas for autoscaling. |
| autoscaling.targetCPUUtilizationPercentage | int | `80` | Target average CPU usage across all the pods |
| fullnameOverride | string | `""` | The fully qualified appname override |
| global.opentdf.common.imagePullSecrets | list | `[]` | JSON passed to the deployment's `template.spec.imagePullSecrets` |
| global.opentdf.common.oidcExternalBaseUrl | string | `"http://localhost:65432"` | Base external url of OIDC provider |
| global.opentdf.common.oidcInternalBaseUrl | string | `"http://keycloak-http"` | Base internal url of OIDC provider |
| global.opentdf.common.oidcUrlPath | string | `"auth"` | Optional path added to base OIDC url |
| global.opentdf.common.postgres.database | string | `"tdf_database"` | The database name within the given server |
| global.opentdf.common.postgres.host | string | `"postgresql"` | postgres server's k8s name or global DNS for external server |
| global.opentdf.common.postgres.port | int | `5432` | postgres server port |
| image.pullPolicy | string | `"IfNotPresent"` | The container's `imagePullPolicy` |
| image.repo | string | `"ghcr.io/opentdf/entitlements"` | The image selector, also called the 'image name' in k8s documentation and 'image repository' in docker's guides. |
| image.tag | string | `nil` | `Chart.AppVersion` will be used for image tag, override here if needed |
| imagePullSecrets | string | `nil` | JSON passed to the deployment's `template.spec.imagePullSecrets`. Overrides `global.opentdf.common.imagePullSecrets` |
| ingress.annotations | object | `{}` | Ingress annotations |
| ingress.className | string | `nil` | Ingress class to use. |
| ingress.enabled | bool | `false` | Enables the Ingress |
| ingress.hosts | object | `{}` | Map in the form: [hostname]:   [path]:     pathType:    your-pathtype [default: "ImplementationSpecific"]     serviceName: your-service  [default: `service.fullname`]     servicePort: service-port  [default: `service.port` above] |
| ingress.tls | string | `nil` | Ingress TLS configuration |
| logLevel | string | `"INFO"` | Sets the default loglevel for the application. One of the valid python logging levels: `DEBUG, INFO, WARNING, ERROR, CRITICAL` |
| nameOverride | string | `""` | Select a specific name for the resource, instead of the default, entitlements |
| nodeSelector | object | `{}` | Node labels for pod assignment |
| oidc.clientId | string | `"tdf-entitlement"` | Client id used for swagger-ui oauth |
| oidc.externalHost | string | `nil` | Override for `global.opentdf.common.oidcExternalBaseUrl` & url path |
| oidc.internalHost | string | `nil` | Override for `global.opentdf.common.oidcInternalBaseUrl` & url path |
| oidc.realm | string | `"tdf"` | Realm used for swagger-ui oauth |
| oidc.scopes | string | `"email"` | OIDC scopes used for swagger-ui pauth |
| openapiUrl | string | `""` | Set to enable openapi endpoint |
| podAnnotations | object | `{}` | Values for the deployment `spec.template.metadata.annotations` field |
| podSecurityContext | object | `{}` | Values for deployment's `spec.template.spec.securityContext` |
| postgres.database | string | `nil` | Override for `global.opentdf.common.postgres.database` |
| postgres.host | string | `nil` | Override for `global.opentdf.common.postgres.host` |
| postgres.port | string | `nil` | Override for `global.opentdf.common.postgres.post` |
| postgres.schema | string | `"tdf_entitlement"` | The entitlement schema |
| postgres.user | string | `"tdf_entitlement_manager"` | Must be a postgresql user with the `tdf_entitlement_manager` role |
| replicaCount | int | `1` | Sets the default number of pod replicas in the deployment. Ignored if `autoscaling.enabled` == true |
| resources | object | `{}` | Specify required limits for deploying this service to a pod. We usually recommend not to specify default resources and to leave this as a conscious choice for the user. This also increases chances charts run on environments with little resources, such as Minikube. |
| secretRef | string | `"name: {{ template \"entitlements.fullname\" . }}-secret"` | JSON to locate a k8s secret containing environment variables. Notably, this file should include the following environemnt variable definitions:     POSTGRES_PASSWORD: Password corresponding to `postgres.user` below |
| securityContext | object | `{}` | Values for deployment's `spec.template.spec.containers.securityContext` |
| serverCorsOrigins | string | `""` | Allowed origins for CORS |
| serverPublicName | string | `"Entitlement"` | Name of application. Used during oauth flows, for example when connecting to the OpenAPI endpoint with an OAuth authentication |
| serverRootPath | string | `"/"` | Base path for this service. Allows serving multiple REST services from the same origin, e.g. using an ingress with prefix mapping as suggested below. |
| service.port | int | `4030` | Port to assign to the `http` port |
| service.type | string | `"ClusterIP"` | Service `spec.type` |
| serviceAccount.annotations | object | `{}` | Annotations to add to the service account |
| serviceAccount.create | bool | `true` | Specifies whether a service account should be created |
| serviceAccount.name | string | `nil` | The name of the service account to use. If not set and create is true, a name is generated using the fullname template |
| tolerations | list | `[]` | Tolerations for nodes that have taints on them |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.11.0](https://github.com/norwoodj/helm-docs/releases/v1.11.0)