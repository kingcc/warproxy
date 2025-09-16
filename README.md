# WARProxy

Use a single command to turn `Cloudflare WARP` into your SOCKS5/HTTP proxy server! 
The most minimal docker image includes all the features you might need!

Includes:
- WGCF: generate cf warp accounts and wireguard config automatically.
- WireProxy: create socks5 proxy.
- Warp+: refresh warp+ traffic.
- Health check etc.

## Usage

`docker`:

```sh
docker run --name warproxy \
  -p 1080:1080 \
  -d ghcr.io/kingcc/warproxy:latest
```

or `docker-compose`:

```yaml
services:
  warproxy:
    image: ghcr.io/kingcc/warproxy:latest
    restart: always
    ports:
      - 1080:1080
```


## Environment variables

| ENV  | Description  | Default  |
|---|---|---|
| ```PUID``` / ```PGID```  | uid and gid for running an app  | ```911``` / ```911```  |
| ```TZ```  | timezone  | ```Asia/Shanghai```  |
| ```SOCKS5_PORT```  | to run socks5 proxy in a different port  | ```1080``` |
| ```USERNAME```  | username of socks5 auth  | None |
| ```PASSWORD```  | password of socks5 auth  | None |
| ```HTTP_PORT```  | to run http proxy in a different port  | None |
| ```ENDPOINT```  | endpoint of cloudflare | ```engage.cloudflareclient.com``` |
| ```DNS```  | remote dns options  | ```1.1.1.1``` |
| ```WARP_PLUS```  | set ```true``` to enable auto WARP+ quota script  | ```false``` |
| ```VERBOSE```  | show verbose level logs   | ```false```  |

### To change license key
If you have an existing Warp+ license key, edit `/config/wgcf-account.toml` and,  delete two files :  
`/config/wgcf-profile.conf` and `/config/wireproxy.conf`  
When you restart container, it will update your account info and re-generate conf files automatically.


## Thanks
* [105PM](https://github.com/105PM/docker-warproxy)
* [by275 (docker-dpitunnel)](https://github.com/by275/docker-dpitunnel)
