Palveluväylään liittyvää infoa
============

## Intro
- Suomeen rakennetteva palveluväylä perustuu Viron X-road järjestelmään. Palveluväylän viralliset sivut https://confluence.csc.fi/pages/viewpage.action?pageId=37816865


## Big picture
![](https://raw.github.com/kakoni/palveluvayla/master/xroad.png)

## Käsitteitä
- Central agency/CA. To simplify key change, the public keys of all security 
servers are registered in the X-Road central agency where certificates are issued to the keys. Certificates for both security server and database server(s)
- Central server, provided by central agency. Provides directory service, used to distribute addresses(=name resolution) and certiﬁcate validity information. Directory service is based on the Secure DNS. Receives periodically query log hashes, thus creating a verifiable audit trail of queries. Log hashes are timestamped.
- Monitoring service, monitors all the servers in the system. Typically runs on central server.
- Web-based portal(=palvelunäkymä), for accessing the X-road services in a simple and centralized way.

- Security Server, Turvapalvelin.  Security server acts as
a gateway between the organisation connected to the X-Road and the X-Road
infrastructure.Local applications see the security server as a provider of all web services offered 
by other organizations. Access rights control is 
performed at the security server. To perform queries from organizations 
information system to other X-Road databases. Security servers use certificate-based authentication for inter-server communication. The security server stores all received messages (queries or responses) to a query log. Security server will sign all the outgoing SOAP messages (requests 
and responses). Security server will verify the signatures of all incoming SOAP 
messages, will time-stamp them and archive them. Security servers contain full history of communication.
- Adapter Server. For a database to share its data over X-Road, it must be equipped with an adapter server, which 
receives SOAP queries from the security server and translates them to the database's native 
language (such as SQL). An adapter server can be either a stand-alone application or a software 
module built in the database. 
- Central Agency + central server + monitoring service + web-based portal run and hosted by goverment.
- Security server+adapter server run and hosted by partipating organisation/entitiy.


## Rajapinnoista
- Palveluväylään liittyneet palvelut keskustelevat keskenään käyttäen SOAP-protokollan mukaisia viestejä. http://x-road.ee/docs/eng/x-road_service_protocol.pdf
- Local applications see the security server as a provider of all web services offered 
by other organizations. Remote service requests by local application will be proxied 
by security server.
- Two types of services available in x-road: data services and metaservices. 
- Data services are services specific to a particular database and usually created individually 
for that database. To give access to these services is the main goal of X-Road. The input 
and output of data services of a database are specified in the database's documentation. 
Data services belong to the namespace of their corresponding database: 
- Metaservices are auxiliary services for obtaining information necessary to perform data
services. The input, output and semantics of metaservices are standardized and will be 
described in this document. They are similar in all servers providing metaservices. 
Metaservices belong to X-Road namespace http://x-road.ee/xsd/x-road.xsd

## Debian paketit
- http://x-road.ee/packages (Turvapalvelin, central palvelin ei saatavissa)

## Ylläpidosta
- The main duty of the security server’s administrator is to install, configure, and maintain the 
server. In addition, the administrator is authorized to take action during an emergency; for 
example, if the system is under attack and the integrity or confidentiality of data is at risk, the 
administrator is authorized to disconnect their security servers from the public network. 
- The security server's administrator must have a trained replacement who can perform all 
management duties. For important national databases or registries, it is essential to have two 
system administrators.
http://ee.x-rd.net/docs/eng/security_server_users_guide.pdf


## Liittyminen
- Kaksi käyttötapausta. 1) Organisaatio haluaa käyttää muita palveluja palveluväylän yli 2) Organisaatio tarjoaa palveluja väylälle

1) Organisaatio käyttää palveluita
- Organisaatio asentaa (ja ylläpitää) Ubuntu 10.04 pohjaisen palvelimen johon asennetaan X-Road package reposta x-tee keyring ja x-tee proxy paketit. 
- CA-certtien asennus
- Organisaation avaimen luonti ja sen jälkeen allekirjoitus Central Authorityssä.
- Kuka saa liittyä väylään?(esim yksittäinen kehittäjä, startup-yritys?)

2) Organisaatio tarjoaa palveluita
- Asennetaan security server kohdan 1 mukaisesti
- Adapter serverin tuottaminen/asennus. Adapter server tarjoaa x-roadin vaatimat metaservice rajapinnat + organisaation tarjoamat dataservice rajapinnat.
- Adapter serverin avainten luonti ja niiden allekirjoitus Central Authorityssä
- ACL määritys adapter servereille security serveriin(=eli mitkä ryhmät/käyttäjät saavat käyttää näitä rajapintoja)



## Kirjastoista
- Javalle j-road, https://code.google.com/p/j-road/
- Webmedia X-tee Maven repo, esimerkki toteuksia; http://maven2.webmedia.ee/ee/webmedia/xtee/
- .NET, X-tee.NET http://xtee.codeplex.com/


## Muuta materiaalia
- http://cyber.ee/uploads/2013/04/Ansper_nordsec.pdf (Designing a Governmental Backbone)
- http://cyber.ee/uploads/2013/05/xroad_Ansper_Willemson.pdf (A Secure and Scalable Infrastructure for Inter-Organizational Data Exchange and eGovernment Applications)

