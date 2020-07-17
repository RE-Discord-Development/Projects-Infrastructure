# Real Engineering Discord Projects Infrastructure
This repo contains the ansible playbooks to spin up the infrastructure hosting the Real Engineering Discord server community projects. At present this means it will do the following:

- Add CatButtes's SSH key to [Digital Ocean](https://www.digitalocean.com)
- Spin up a 1GB Digital Ocean VPS instance
- Install [docker](https://www.docker.com/)
- Install [prometheus](https://www.prometheus.io/)
- Install [grafana](https://grafana.com/)
- Install [Traefik](https://containo.us/traefik/)
- Spin up an instance of the [RE Community Bot](https://github.com/RE-Discord-Development/CommunityBot)

---

## Making it work
Before you begin, you will need the following:
- A [Digital Ocean](https://www.digitalocean.com) Account.
- A linux box with [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/index.html) installed ([WSL](https://docs.microsoft.com/en-us/windows/wsl/install-win10) also works if you are running Windows 10)

Then to fire everything up,,,

1. Create `vars/secrets.yml` with the following contents
```yml
DO_API_TOKEN: << Your Digital Ocean API Token >>
CLOUDFLARE_EMAIL: << Your cloudflare email address >>
CLOUDFLARE_API_TOKEN: << Your Cloudflare API Token >>
```
2. Enter values into `vars/values.yml`
3. Run `ansible-playbook provision-server.yml` to provision a Digital Ocean droplet with associated DNS records
4. Run `ansible-playbook deploy-stack.yml` to deploy the listed stack to the newly provisioned droplet


Enjoy your newly provisioned server, bot and monitoring stack.