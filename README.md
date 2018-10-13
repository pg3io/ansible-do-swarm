![version](https://img.shields.io/badge/version-v1.0-orange.svg)
[![Twitter](https://img.shields.io/twitter/follow/pg3io.svg?style=social)](https://twitter.com/intent/follow?screen_name=pg3io)


Playbook Ansible to install a Docker Swarm cluster at Digital Ocean

# Requirements
* Ansible 2.7

```
pip install ansible==2.7
```

# Playbook Variables

All variables of the playbook can be found in [vars.yml](vars.yml)
* do_token : token Digital Ocean [lien](https://www.digitalocean.com/docs/api/create-personal-access-token/)
* droplets : list of droplets to deploy, first of the list will be the manager
* do_region : datacenter location . Listing: `curl -X GET --silent "https://api.digitalocean.com/v2/regions?per_page=999" -H "Authorization: Bearer <DO TOKEN>" |jq -r '{name: .regions[].name, regions_id: .regions[].slug}'`
* do_size : droplet size. Listing: `curl -X GET --silent "https://api.digitalocean.com/v2/sizes?per_page=999" -H "Authorization: Bearer <DO TOKEN>" |jq -r '.sizes[] .slug' | sort`
* ssh_pubkey : Digital ocean name public key


# Run

```
ansible-playbook do-swarm.yml -e do_token="<DO TOKEN>"
```

# Futur features

* Number management of manager for Docker Swarm [ref](https://docs.docker.com/engine/swarm/admin_guide/#add-manager-nodes-for-fault-tolerance)
* Reverse proxy with service discovery [ref](https://traefik.io/)
* Digitlan Ocean load balancer [ref](https://www.digitalocean.com/products/load-balancer/) (no Ansible module currently available to create)

# Features V1.0
* Init playbook
* Create droplets
* Create cluster Docker Swarm with single manager


# License

![Apache 2.0 Licence](https://img.shields.io/hexpm/l/plug.svg)

This project is licensed under the [Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0) license - see the [LICENSE](LICENSE) file for details.

# Author Information
This role was created in 11/10/2018 by [PG3](https://pg3.io)
