# HAProxy load balancer for Nginx servers using Docker

Creates HAProxy load balancer for two Nginx web servers using Docker containers with SSL offloading on HAProxy level.

For ease of deployment there is a docker-compose yaml prepared.

## Usage
```
docker-compose up
```
and enter https://localhost (be aware that self-signed certificate is used)

HAProxy stats page is availabe on http://localhost:888
