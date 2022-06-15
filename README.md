# Kutt (Helm)
## [Kutt.it](https://github.com/thedevs-network/kutt)
**Kutt** is a modern URL shortener with support for custom domains. Shorten URLs, manage your links and view the click rate statistics. This project installs and configures the **Kutt** app using **HELM**. Visit the [Official Website](https://kutt.it) for more details and documentation.
</br>

## Table of Contents
- [Stack](#stack)
- [Setup](#setup)
- [Configuration](#config)

## Stack <a id='stack'></a>
- Redis (Cache Layer)
- Docker (Image Repo)
- PostgresSQL (Database)
- Helm (Kubernetes package manager)

## Setup <a id='setup'></a>

### Helm

* Make sure you have [helm](https://helm.sh/docs/intro/install/) installed on your local computer. 
* Change directory into the root of this repo.
* Modify the [values.yml](values.yaml), [config.yml](./templates/config.yml) and other files in the [template](templates) folder to suit your need.
* Run ``` helm install <chartname> kutt-app ``` **(Change 'chartnname' to a name of your choice)**

### Docker 

* Download the [`docker-compose.yml`](https://github.com/thedevs-network/kutt/blob/develop/docker-compose.yml) and the [`.docker.env`](https://github.com/thedevs-network/kutt/blob/develop/.docker.env)-file from the repository and configure the `.docker.env` ([see below](#config)). 
To execute Kutt you simply have to run `docker-compose up -d` command and then the app should be ready on port "3000".

* The `docker-compose.yml` uses the official kutt docker image available on [Docker Hub](https://hub.docker.com/r/kutt/kutt).

* Visit the [Official Website](https://kutt.it) for more details and documentation.

## Configuration <a id='config'></a>

For the minimal configuration the following settings have to be changed in the `.env`-file:

- **DEFAULT_DOMAIN**: The domain of your kutt instance
- **DB_**: The DB credentials (when you use docker-compose you can skip these)
- **ADMIN_EMAILS**: A comma-separated list of the administrator-accounts
- **RECAPTCHA_**: Enter your credentials to use reCaptchas or delete this setting if you don't want to use it
- **MAIL_**: Enter the SMTP-server's credentials (The experience shows SSL works better than STARTTLS; The mail config is required to easily create accounts, see [this comment](https://github.com/thedevs-network/kutt/issues/269#issuecomment-628604256) how it can be done manually)
- **REPORT_EMAIL**: Kutt offers a form to report malicious links which are sent to this mail-address