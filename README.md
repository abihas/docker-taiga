Based on https://github.com/benhutchins/docker-taiga

To use this example, as-is, simply clone this repo and startup Docker:

```bash
git clone https://github.com/abihas/docker-taiga mytaiga
cd mytaiga/

# Optional, but likely desired, update your configuration now
nano docker-compose.yml # Be sure to update the TAIGA_HOSTNAME
nano taiga-conf/conf.json
nano taiga-conf/local.py

# Startup docker containers
docker-compose up -d postgres
docker-compose up -d taiga

# Wait ~30 seconds. The taiga container will initialize your postgres database.

# Now open your web browser:
open http://localhost:5555/
````

### How to enable the LDAP plugin

## Customized Example (Adds Slack & LDAP support)

For a slightly more customized setup, this directory provides an example of how
to extend docker-taiga and add [taiga-contrib-slack](https://github.com/taigaio/taiga-contrib-slack) and [taiga-contrib-ldap-auth](https://github.com/ensky/taiga-contrib-ldap-auth) LDAP
plugins.

To enable LDAP as well:

1. Uncomment the relevant lines from the `Dockerfile` and `taiga-conf/local.py`
2. Add this to your `taiga-conf/conf.json` file:

    "loginFormType": "ldap",

### How to enable taiga-events

To enable [taiga-events](https://github.com/taigaio/taiga-events):

1. Uncomment relevant lines from `docker-compose.yml`
2. Update to `eventsUrl` inside the `taiga-conf/conf.json` file
