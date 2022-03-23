https://github.com/nginxinc/nginx-prometheus-exporter

To install Nginx Exporter on Target servers:

wget https://github.com/nginxinc/nginx-prometheus-exporter/releases/download/v0.10.0/nginx-prometheus-exporter_0.10.0_linux_amd64.tar.gz

tar xvfz nginx

./nginx-prometheus-exporter -nginx.scrape-uri=http://34.101.149.181:8080/stub_status &
