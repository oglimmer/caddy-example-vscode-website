# vscode server (tunnel & http) plus a website with Caddy

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

!! THIS IS UNSECURED - NO TOKEN NEEDED !!

## VSCode (tunnel)

Check the log files to grant access and connect.

```bash
docker logs vscode-server
```

Then access it at the URL shown in the console.

# Notes

* Running on *.example.com does not work with Firefox (works with Chrome)
* Running VSCode with "tunnel" does not work with Firefox (works with Chrome)
* Remove `caddy.tls: internal` in docker-compose.yml when running on a different domain
* One can use the Caddyfile to service static files from the filesystem directly (without using nginx)
