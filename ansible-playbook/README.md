#  Ansible playbook (Infra config - 1st step)

Playbook for configuring VMs with the monitoring stack (Telegraf, InfluxDB, and Grafana) and Docker.

To use this playbook,

1. You need to create an inventory folder:

```sh
cp inventory_example inventory
```

2. After, configure the InfluxDB and Telegraf variable in the `inventory/group_vars/all.yml` file;

3. Configure hosts access in `inventory/hosts.ini`;

4. Finally, run the playbook:

```sh
ansible-playbook build_infra.yml -i inventory/hosts.ini
```

5. You need to create or import a Grafana dashboard. I use and recommend this one: https://grafana.com/grafana/dashboards/11912.

Now, the TIG and Docker are installed, and you are ready for the next step, the Jenkins configuration.


## References

- https://github.com/sayonarasantos/FOMA

- https://ironlinux.com.br/instalando-a-pilha-tig-telegraf-influxdb-e-grafana-debian9/