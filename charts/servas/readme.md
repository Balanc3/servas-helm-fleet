

## Parameters

### image configuration

| Name               | Description                                                    | Value                      |
| ------------------ | -------------------------------------------------------------- | -------------------------- |
| `image.repository` | location of docker image repository                            | `docker.io/beromir/servas` |
| `image.pullPolicy` | This sets the pull policy for images.                          | `IfNotPresent`             |
| `image.tag`        | Overrides the image tag whose default is the chart appVersion. | `""`                       |

### service

| Name                | Description                                                                                                                                                 | Value       |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- |
| `service.type`      | set the service type more information can be found here: https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types | `ClusterIp` |
| `service.port`      | set the exports port of the service information can be found here: https://kubernetes.io/docs/concepts/services-networking/service/#field-spec-ports        | `80`        |
| `ingress.enabled`   | enables the ingress for the service information can be found here: https://kubernetes.io/docs/concepts/services-networking/ingress/                         | `true`      |
| `ingress.className` | class of ingress. This fleet package install traefik by default, change if you have different ingress controller                                            | `traefik`   |

### Servas Env Variables

| Name                     | Description                                                                                                                                                                            | Value                            |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------- |
| `Servas.appName`         | configures name of servas instance                                                                                                                                                     | `servas-app`                     |
| `Servas.appEnv`          | configures name of environment of instance                                                                                                                                             | `Production`                     |
| `Servas.appDebug`        | enables or disabled debug logging                                                                                                                                                      | `false`                          |
| `Servas.appURL`          | url of servas instance.                                                                                                                                                                | `http://test-servas.localdev.me` |
| `Servas.appRegistration` | Whether to allow app registration through UI                                                                                                                                           | `true`                           |
| `Servas.showVersion`     | shows Version of instance                                                                                                                                                              | `true`                           |
| `Servas.dbUserName`      | user name for MariaDB, passwords for this user and root user are in secret and auto configured.                                                                                        | `mdb_User`                       |
| `Servas.dbName`          | name of maria DB                                                                                                                                                                       | `sservasDB`                      |
| `Servas.secretName`      | Secret can and does get created from another chart but if you want to create a secret the keys are: app-key (APP_KEY), mdbUser (MARIADB_PASSWORD), and mdbRoot (MARIADB_ROOT_PASSWORD) | `servas-keys`                    |
