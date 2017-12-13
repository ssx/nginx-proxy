# nginx-proxy

This repository presents a simple docker-compose to use to provide access to web apps with docker.

## Installation instructions

1) Install [docker](https://www.docker.com/)
1) Clone this repository: `https://github.com/swisscat/nginx-proxy.git`
1) Create the default network: `docker network create nginx-proxy`
1) Go to the cloned repository, execute `docker-compose up -d`

## Adding a new application

To expose a new application to the web, open the corresponding `docker-compose.yml` and
 * Ensure the ports in the container are exposed (but not binded)
 * Append to the container you wish to expose:

```
    environment:
      VIRTUAL_HOST: my-app.my.domain
      LETSENCRYPT_HOST: my-app.my.domain
      LETSENCRYPT_EMAIL: my-emailaddress.com
```

 * Append as well
 
```
networks:
    default:
        external:
            name: nginx-proxy
```