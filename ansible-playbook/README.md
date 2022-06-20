# 1st step

## Ansible plabook

Plabook to configure VMs with monitoring stack (Telegraf, InfluxDB, end Grafana), and Docker.

To use this plabook,
1. You need create a inventory folder:

```sh
cp inventory_example inventory
```

2. After, configure the InfluxDB and Telegraf variable in `inventory/group_vars/all.yml` file;

3. Configure hosts access in `inventory/hosts.ini`;

4. Finally, run the playbook:

```sh
ansible-playbook build_infra.yml -i inventory/hosts.ini
```

Now, the TIG and Docker are installed, and you are ready for the next step, the Jenkins configuration.