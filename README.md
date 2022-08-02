# Paperback Komga Proxy

This was created as a workaround to enable downloads from the Paperback (Komga) source in Paperback v0.7.

To run this, you need:

- Docker
- docker-compose

## How to configure the proxy

1. Clone this repository
2. Copy the `.env.example` to a new file named `.env`
3. Generate the base64 string needed for your credentials. This can be generated using the following method:
   - The authorization string is username + ":" + password (like this `yourusername@email.com:yourpassword`), encoded to base64. You can use an online tool, or run this in the console of your browser (press F12 to view the browser dev tools): `btoa('yourusername@email.com:yourpassword')`
4. Set the `AUTH_HEADER` variable in the `.env` file. It should look like something like this: `AUTH_HEADER="Basic eW91cnVzZXJuYW1lQGVtYWlsLmNvbTp5b3VycGFzc3dvcmQ="`
5. Edit the `komga-proxy.conf.template` file. You want to change each of the following:
   - The `server_name x.x.x.x;` should be the IP of the computer running the proxy. (You can add more than one `server_name` directive, if you use tailscale for example.)
   - The `proxy_pass http://ip:port` should be set to the ip + port of Komga.