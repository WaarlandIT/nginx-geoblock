# Docker nginx container with GeopBlock proxy functionality

As a base I used the nginx-geoip dockerfile from Karel Bemelmans and changed it so it would fit my needs.

I was looking for a way to setup a GeoIP filter proxy in front of my Docker webservices. 

Karel Bemelmans created a Docketfile with some config examples that gave a good start to create my proxy.

This is a Docker nginx container that includes the MaxMind GeoIP Country database. It injects the X-Origin-Country-Code and X-Origin-Country-Name headers into http requests to the backend with the country code of the requester.

This product includes GeoLite2 data created by MaxMind, available from http://www.maxmind.com.

