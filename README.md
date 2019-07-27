# Docker nginx container with GeoIP-Block proxy functionality

As a base I used the nginx-geoip dockerfile from Karel Bemelmans and changed it so it would fit my needs.

I was looking for a way to setup a GeoIP filter proxy in front of my Docker webservices. 

Karel Bemelmans created a Docketfile with some config examples that gave a good start to create my proxy.

This is a Docker nginx container that includes the MaxMind GeoIP Country database. It injects the X-Origin-Country-Code and X-Origin-Country-Name headers into http requests to the backend with the country code of the requester.

This product includes GeoLite2 data created by MaxMind, available from http://www.maxmind.com.

## What you get as-is

When you start this container as-is 
- It will allow traffic to the webcontent from the RFC-1918 addresses 
- It will allow traffic to the webcontent from The Netherlands 
- It will allow traffic to the webcontent from the United States
- Everything else gets a Error 418 
- The current proxy settings will proxy https://www.google.com
- It uses a self-signed certificate for https encryption

That's it.

## I do not want to prxy Google.com, what should I do?

Make some volumes:
- For the certificate use: /etc/ssl/certs/
  - The certificate used is called "certificate.crt"
  - The keyfile used is called "certificate.key"

- For the country allow list config use: /etc/nginx/conf.d/
  - Some default config will be placed there when the container starts first, you will get how it works

- The website config example will be placed in: /etc/nginx/sites-enabled/
  - default.conf must exsist it contains also the example config



