# <img src="site/content/docs/latest/img/logo.svg" width="40" align="left"/> Kubeapps

[![Main Pipeline](https://github.com/vmware-tanzu/kubeapps/actions/workflows/kubeapps-main.yaml/badge.svg)](https://github.com/vmware-tanzu/kubeapps/actions/workflows/kubeapps-main.yaml)
[![Full Integration Pipeline](https://github.com/vmware-tanzu/kubeapps/actions/workflows/kubeapps-full-integration.yaml/badge.svg)](https://github.com/vmware-tanzu/kubeapps/actions/workflows/kubeapps-full-integration.yaml)
[![CodeQL](https://github.com/vmware-tanzu/kubeapps/actions/workflows/codeql-analysis.yml/badge.svg)](https://github.com/vmware-tanzu/kubeapps/actions/workflows/codeql-scheduled.yml)
[![Netlify Status](https://api.netlify.com/api/v1/badges/7e0e2833-1d75-43f6-b006-632d359bb83b/deploy-status)](https://app.netlify.com/sites/kubeapps-dev/deploys)

> [!CAUTION]
> After many years of growth and milestones, the time has come for the next chapter of Kubeapps. The current maintainers are concentrating their efforts on new projects. We are looking for volunteers to help us maintain the project going forward. Without new volunteers, the project will be deprecated and the repo archived on August 8th, 2025.

## Overview

Kubeapps is an in-cluster web-based application that enables users with a one-time installation to deploy, manage, and upgrade applications on a Kubernetes cluster.

With Kubeapps you can:

- Browse and deploy different packages like [Helm](https://github.com/helm/helm) charts, [Flux](https://fluxcd.io/) or [Carvel](https://carvel.dev/) packages from public or private repositories (including [VMware Marketplace™](https://marketplace.cloud.vmware.com) and [Bitnami Application Catalog](https://bitnami.com/application-catalog))
- Customize deployments through an intuitive user interface
- Browse, upgrade and delete applications installed in the cluster
- Browse and deploy [Kubernetes Operators](https://operatorhub.io/)
- Secure authentication to Kubeapps using a [standalone OAuth2/OIDC provider](./site/content/docs/latest/tutorials/using-an-OIDC-provider.md) or [using Pinniped](./site/content/docs/latest/howto/OIDC/using-an-OIDC-provider-with-pinniped.md)
- Secure authorization based on Kubernetes [Role-Based Access Control](./site/content/docs/latest/howto/access-control.md)

**_Note:_** Kubeapps 2.0 and onwards supports Helm 3 only. While only the Helm 3 API is supported, in most cases, charts made for Helm 2 will still work.

## Getting started with Kubeapps

Installing Kubeapps is as simple as:

```bash
kubectl create namespace kubeapps
helm install kubeapps --namespace kubeapps oci://registry-1.docker.io/bitnamicharts/kubeapps
```

See the [Getting Started Guide](./site/content/docs/latest/tutorials/getting-started.md) for detailed instructions on how to install and use Kubeapps.

> Kubeapps is deployed using the official [Bitnami Kubeapps chart](https://github.com/bitnami/charts/tree/main/bitnami/kubeapps) from the separate Bitnami charts repository. Although the Kubeapps repository also defines a chart, this is intended for development purposes only.

## Documentation

Complete documentation available in Kubeapps [documentation section](./site/content/docs/latest/README.md). Including complete tutorials, how-to guides, and reference for configuration and development in Kubeapps.

For getting started into Kubeapps, please refer to:

- [Getting started guide](./site/content/docs/latest/tutorials/getting-started.md)
- [Detailed installation instructions](./chart/kubeapps/README.md)
- [Kubeapps user guide](./site/content/docs/latest/howto/dashboard.md) to easily manage your applications running in your cluster.
- [Kubeapps FAQs](./chart/kubeapps/README.md#faq).

See how to deploy and configure [Kubeapps on VMware Tanzu™ Kubernetes Grid™](./site/content/docs/latest/tutorials/kubeapps-on-tkg/README.md)

## Troubleshooting

If you encounter issues, please review the [troubleshooting docs](./chart/kubeapps/README.md#troubleshooting), review our [project board](https://github.com/orgs/vmware-tanzu/projects/38/views/2), file an [issue](https://github.com/vmware-tanzu/kubeapps/issues), or talk to Kubeapps maintainers on the [#Kubeapps channel](https://kubernetes.slack.com/messages/kubeapps) on the Kubernetes Slack server.

- [Sign up](https://slack.k8s.io) to the Kubernetes Slack org.

- Review the FAQs section on the [Kubeapps chart README](./chart/kubeapps/README.md#faq).

## Contributing

If you are ready to jump in and test, add code, or help with documentation, follow the instructions on the [start contributing](./CONTRIBUTING.md) documentation for guidance on how to setup Kubeapps for development.

## Changelog

Take a look at the list of [releases](https://github.com/vmware-tanzu/kubeapps/releases) to stay tuned for the latest features and changes.
