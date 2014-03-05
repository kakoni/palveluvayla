Palveluväylään liittyvää materiaalia
============

## Intro
- Suomeen rakennetteva palveluväylä perustuu Viron X-road järjestelmään.

## Käsitteitä
- Central agency/CA. To simplify key change, the public keys of all security 
servers are registered in the X-Road central agency where certificates are issued to the keys. Certificates for both security server and database server(s)
- Central server. provides name resolution and receives 
periodically query log hashes, thus creating a verifiable audit trail of queries. 

- Security Server, Turvapalvelin. Access rights control is 
performed at the database's security server. To perform queries from organizations 
information system to other X-Road databases. Security servers use certificate-based authentication for inter-server communication. The security server stores all received messages (queries or responses) to a query log

- Adapter Server. For a database to share its data over X-Road, it must be equipped with an adapter server, which 
receives SOAP queries from the security server and translates them to the database's native 
language (such as SQL). An adapter server can be either a stand-alone application or a software 
module built in the database. 

## Rajapinnoista
- Palveluväylään liittyneet palvelut keskustelevat keskenään käyttäen SOAP-protokollan mukaisia viestejä. http://x-road.ee/docs/eng/x-road_service_protocol.pdf

## Ylläpidosta
http://ee.x-rd.net/docs/eng/security_server_users_guide.pdf

