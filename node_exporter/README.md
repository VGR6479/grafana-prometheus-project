To install Node Exporter on Target servers:

sudo useradd node_exporter -s /sbin/nologin

wget https://github.com/prometheus/node_exporter/releases/download/v1.3.1/node_exporter-1.3.1.linux-amd64.tar.gz

tar xvfz node_exporter-*.*-amd64.tar.gz

sudo mv node_exporter-*.*-amd64/ node_exporter

sudo cp node_exporter/node_exporter /usr/sbin/

sudo mv node_exporter.service /etc/systemd/system/

sudo mkdir -p /etc/sysconfig

sudo mv node_exporter /etc/sysconfig

sudo systemctl daemon-reload

sudo systemctl enable node_exporter

sudo systemctl start node_exporter

curl http://localhost:9100/metrics
