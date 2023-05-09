# MW starter scaffold

This helm chart scaffold is like the base helm starter chart with some
improvements, such as:

* Adds two container configuration entrypoints. They are `config.env` and
  `config.secretEnv`; used to mount environment variables on deployments pod
  container. Very useful to decouple configuration from deployment.
* Adds support to use [go templating](https://pkg.go.dev/text/template) in this
  values:
  - `config.env`
  - `config.secretEnv`
  - `ingress.hosts[].host` 
  - `ingress.hosts[].paths[].path` 
  - `ingress.hosts[].paths[].pathType` 
  - `ingress.tls[].secretName`
  - `ingress.tls[].hosts[]`
> Please read [values.yaml](./values.yaml) for more information.
* Add configmap and secret environment hashes to deployments manifest in order to
  automatically redeploy pod on changes.
* Removes hardcoded livenessProbe and readinessProbe in deployment manifest. It
  takes them to the values file instead.
* Add startupProbe in the same way as previous.

## How to use it.

Assuming you already installed `helm-scafolding` to you helm starters, you just
need to execute:

```sh
helm create <chartname> -p helm-scaffolding/mw-starter
```

