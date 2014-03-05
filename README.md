Palveluväylään liittyvää materiaalia
============

## Intro
- Suomeen rakennetteva palveluväylä perustuu Viron X-road järjestelmään.

## Käsitteitä
- Central agency/CA. To simplify key change, the public keys of all security 
servers are registered in the X-Road central agency where certificates are issued to the keys. Certificates for both security server and database server(s)
- Central server. Provides domain name resolution and where the security server sends query log hashes
- Security Server, Turvapalvelin. Access rights control is 
performed at the database's security server, and the rights to perform one query or another are 
granted to organizations or organization groups as a whole. It is up to the organization to grant 
access rights to its individual employees. 

- Adapter Server. For a database to share its data over X-Road, it must be equipped with an adapter server, which 
receives SOAP queries from the security server and translates them to the database's native 
language (such as SQL). An adapter server can be either a stand-alone application or a software 
module built in the database. 

- 

## Rajapinnoista
- Palveluväylään liittyneet palvelut keskustelevat keskenään käyttäen SOAP-protokollan mukaisia viestejä. http://x-road.ee/docs/eng/x-road_service_protocol.pdf
 

