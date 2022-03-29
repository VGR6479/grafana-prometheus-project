https://github.com/prometheus-community/postgres_exporter

wget https://github.com/prometheus-community/postgres_exporter/releases/download/v0.10.1/postgres_exporter-0.10.1.linux-amd64.tar.gz

tar -xvzg postgres.....

mv postgres.../ postgres_exporter/

mv postgres_exporter/ /opt/postgres_exporter/

cd /opt/postgres_exporter

sudo cp postgres_exporter /usr/local/bin

sudo vim postgres_exporter.env

DATA_SOURCE_NAME="postgresql://postgres:postgres@192.168.56.106:5432/?sslmode=disable"

sudo useradd -rs /bin/false postgres

vim /etc/systemd/system/postgres_exporter.service


[Unit]
Description=Prometheus exporter for Postgresql
Wants=network-online.target
After=network-online.target
[Service]
User=postgres
Group=postgres
WorkingDirectory=/opt/postgres_exporter
EnvironmentFile=/opt/postgres_exporter/postgres_exporter.env
ExecStart=/usr/local/bin/postgres_exporter --web.listen-address=192.168.56.106:9100 --web.telemetry-path=/metrics
Restart=always
[Install]
WantedBy=multi-user.target

sudo systemctl daemon-reload
sudo systemctl start postgres_exporter
sudo systemctl enable postgres_exporter
sudo systemctl status postgres_exporter

