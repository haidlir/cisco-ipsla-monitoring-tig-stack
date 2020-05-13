
# Cisco IPSLA Monitoring using TIG Stack

###### Desclaimer
This repo is intended as learning purpose or trial.

## Work Log
- [x] RTT
- [x] Jitter
- [x] Packet Loss

## Cara Mencoba
1. Make sure that docker and docker-compose are already installed.\
[How to install Docker](https://docs.docker.com/get-docker/) and [How to install Docker-Compose](https://docs.docker.com/compose/install/)
2. Clone this repo
     ```
      $ git clone https://github.com/haidlir/cisco-ipsla-monitoring-tig-stack.git
    ```
3. Add the IP address of devices to telegraf.
    ```
    [[inputs.prometheus]]
        ## An array of urls to scrape metrics from.
        urls = [
          "http://snmp-exporter:9116/snmp?target=<target ip address or hostname>&module=ip-sla",
        ]
    ```
4. Modify the snmp configuration matched to the devices's snmp configuration.
    ```
      version: 2
      auth:
        community: "public"
    ```
5. Turn the services by executing file up.sh
   ```
    $ ./up.sh
   ```
6. Open the Grafana, ie: http://localhost:3000
7. Add data source InfluxDB, with database name "cisco-ipsla"\
Username and Pasword can be seen in file ```.env```
8. Import Dashboard from file ```fixtures/grafana-cisco-ipsla-monitoring.json```

### Result Screenshoot
![Cisco-IPSLA-Grafana](https://raw.githubusercontent.com/haidlir/cisco-ipsla-monitoring-tig-stack/master/img/img-1.png "Cisco-IPSLA-Grafana")

## Credits
1. InfluxData
2. Grafana Labs
3. Prometheus SNMP Exporter 