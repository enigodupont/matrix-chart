# Matrix Chart

A Helm chart for deploying a Matrix homeserver stack in Kubernetes.

This is a fork of <https://github.com/dacruz21/matrix-chart>

## Features

- Latest version of Synapse

## Experimental Features

- (Optional) Latest version of Riot Web
- (Optional) Choice of lightweight Exim relay or external mail server for email notifications
- (Optional) Coturn TURN server for VoIP calls
- (Optional) PostgreSQL cluster via stable/postgresql chart
- (Optional) [matrix-org/matrix-appservice-irc](https://github.com/matrix-org/matrix-appservice-irc) IRC bridge
- (Optional) [tulir/mautrix-whatsapp](https://github.com/tulir/mautrix-whatsapp) WhatsApp bridge
- (Optional) [Half-Shot/matrix-appservice-discord](https://github.com/Half-Shot/matrix-appservice-discord) Discord bridge
- Fully configurable via values.yaml
- Ingress definition for federated Synapse and Riot

## Installation

Some documentation is available in values.yaml, and a complete configuration guide is coming soon.

Choose one of the two options below to install the chart.

### Chart Repository (recommended)

This chart is published to my Helm chart repository on Dockerhub.

<https://hub.docker.com/repository/docker/enigodupont/matrix>

To install this chart:

1. Create an empty chart to hold your configuration

    ```shell script
    helm create mychart
    cd mychart
    ```

1. Add this chart to your chart's dependencies by editing `Chart.yaml` and adding the following lines:

    ```yaml
    dependencies:
      - name: enigodupont/matrix
        version: 2.8.0
        repository: registry-1.docker.io
    ```

1. Run `helm dependency update` to download the chart into the `charts/` directory.

1. Configure the chart by editing `values.yaml`, adding a `matrix:` object, and adding any config overrides under this object.

1. Deploy your customized chart with `helm install mychart .`

### Git

You can also clone this repo directly and override the values.yaml provided. To do so, run the following commands:

```shell script
git clone https://github.com/enigodupont/matrix-chart
cd matrix-chart
helm dependency update
helm install matrix .
```

## Security

There was an issue with the older security context settings with the latest version of Synapse.

If you find any security vulnerabilities in this Helm chart, please create an issue in the related github.