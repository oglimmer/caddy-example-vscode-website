# vscode server (tunnel & http) plus a website with Caddy

# Domains (fake domains)

You have to add these domains to your /etc/hosts

```
127.0.0.1 web.example.com vscode.example.com grafana.example.com loki.example.com
```

Run via

```bash
docker compose up --build -d
```

## Website

Access at:

https://web.example.com/

## VSCode (browser)

Access at:

https://vscode.example.com/

Secured with basic auth: user/password (tne password is literally password)

## VSCode (tunnel)

Check the log files to grant access and connect.

```bash
docker logs vscode-server
```

Then access it at the URL shown in the console.

## Loki

Loki is available via https://loki.example.com/loki/api/v1/push with user loki/loki

## Grafana

Grafana is available via https://grafana.example.com user admin:admin

# Notes

* Running on *.example.com does not work with Firefox (works with Chrome)
* Running VSCode with "tunnel" does not work with Firefox (works with Chrome)
* Remove `caddy.tls: internal` in docker-compose.yml when running on a different domain
* One can use the Caddyfile to service static files from the filesystem directly (without using nginx)
