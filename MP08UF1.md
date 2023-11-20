# DNS
# Introducció al Servei DNS

## Context i Necessitat
- **Origen del DNS**: El servei de Noms de Domini (DNS) va aparèixer l'any 1983.
- **Motivació**: La necessitat de tenir un sistema per emmagatzemar de manera estructurada els noms dels serveis connectats a Internet.

## Desenvolupament Històric
- **Mètode Original**: Inicialment, s'utilitzava un arxiu anomenat `hosts.txt` en cada màquina, que contenia els noms de domini coneguts.
- **Problemes**: A mesura que Internet creixia, la mida d'aquest fitxer augmentava, provocant problemes de gestió i eficiència.

## Solució i Implementació
- **Contribució de Paul Mockapetris**: Paul Mockapetris va publicar els estàndards (RFC 882 i 883) que van definir el que avui dia coneixem com a DNS.
- **Impacte**: Aquests estàndards van permetre superar els problemes associats amb el mètode original dels arxius `hosts.txt`.

# L'Espai de Noms de Domini en el Servei DNS

## Base de Dades Distribuïda
- **Natura**: DNS consisteix en una base de dades distribuïda.
- **Ubicació**: Emmagatzemada en diverses màquines connectades en xarxa, tant en el mateix lloc físic com distribuïdes.
- **Contingut**: Emmagatzema associacions entre noms de dominis i direccions IP.

## Estructura de l'Espai de Noms
- **Arbre Invertit**: Consta d'un arbre invertit, amb el node arrel al nivell superior.
- **Nivells**: Pot tenir un nombre indeterminat de nivells inferiors, normalment fins a un màxim de 5.
- **Exemple**: Un domini com `lliurex.cult.gva.es` està format per 4 nivells.

## Identificació dels Nodes
- **Noms de Nodes**: Els nodes s'identifiquen mitjançant noms no nuls, amb un màxim de 63 caràcters.
- **Node Arrel**: El node arrel s'identifica amb un nom nul (0 caràcters).
- **Nom Complet**: El nom complet d'un node inclou tota la trajectòria des d'aquest node fins al node arrel.

## Servidors DNS i Registres de Recursos
- **Servidors DNS**: Emmagatzemen informació sobre noms de domini DNS en registres de recursos.
- **Autoritat**: Cada servidor DNS té autoritat sobre certs noms de domini i manté els registres de recursos pertinents.
- 
# La Xarxa TCP/IP Sense Serveis de Noms

## Identificació a Baix Nivell
- **Adreça MAC**: Els dispositius s'identifiquen mitjançant l'adreça MAC de la targeta de xarxa, una combinació única de sis parells de dígits hexadecimals.
  - **Exemple**: `08:00:27:07:cc:27`, on els primers tres parells (08:00:27) indiquen el fabricant (Oracle VM VirtualBox, Inc).

## Adreces IP i Noms de Màquina
- **Adreça IP**: Identificador de més alt nivell en les xarxes TCP/IP, única per a cada element de la xarxa.
- **Nom de Host**: Nom assignat a cada màquina dins de la xarxa.

## Rangs d'Adreçament en Intranets
- **Classes d'Adreces IP**: 
  - Classe A: `10.0.0.0 - 10.255.255.255`
  - Classe B: `172.16.0.0 - 172.31.255.255`
  - Classe C: `192.168.0.0 - 192.168.255.255` (Comú en empreses: `192.168.0.x`).

## Limitacions Sense Servei de Noms
- **Dependència d'Adreces IP**: Sense un servei de noms, es requereix conèixer i utilitzar l'adreça IP per accedir a altres equips.
  - **Exemple**: Per accedir a un servidor web, s'ha d'utilitzar la URL amb l'adreça IP, com `http://192.168.70.1/`.
- **Dificultat d'Ús**: Necessitat d'aprendre i recordar adreces IP, que pot ser complicat i poc pràctic.

## Solució: Servei de Noms
- **Objectiu**: Implementar un servei de noms per assignar noms 'amigables' als equips, facilitant la comunicació i configuració dins la xarxa.

# Necessitat d'un Servei de Noms a la Xarxa

## Raons Principals
1. **Facilitat d'Ús**: Permet als usuaris accedir als serveis dels equips mitjançant noms clars i fàcils de recordar.
2. **Flexibilitat en Configuracions**: Les configuracions dels serveis s'utilitzen amb noms en comptes d'adreces IP, oferint major flexibilitat.

## Exemple Pràctic
- **Situació**: Configuració del navegador en 400 màquines amb una URL específica per a un fitxer de configuració de proxy.
  - URL Original: `http://192.168.70.1/proxy.pac`
  - Problema: Canviar a un nou servidor implica actualitzar la configuració en totes les màquines.

## Avantatges del Servei de Noms
- **Solució**: Utilitzant noms en lloc d'adreces IP.
  - Nou URL Exemple: `http://proxy.intracentre/proxy.pac`
  - Gestió Centralitzada: Canviar la referència a la nova IP només en el servei de noms.
  - Eficàcia: Evita la necessitat de modificar la configuració en cada estació individualment.

## Conclusió
- **Beneficis Addicionals**: Hi ha molts altres avantatges del servei de noms que es poden descobrir amb la pràctica.

# Característiques del Servei DNS en una Xarxa Local 'Tancada'

## Definició
- **DNS (Domain Name System)**: Servei de noms utilitzat dins les xarxes TCP/IP.

## Tipus de Configuració del DNS
1. **DNS per a Internet (Públic)**:
   - Funció: Escampar adreces de domini vàlides a Internet (assignades per 'Internic') i resoldre peticions a altres dominis.
   - Característiques: Necessita configuració detallada per a refresc de modificacions i transferència d'informació entre servidors.
   - Restriccions: Només pot incloure IP vàlides a Internet.

2. **DNS per a Xarxes Locals (Privat)**:
   - Funció: Resoldre únicament peticions de nom-IP / IP-nom dins la seva xarxa.
   - Característiques: No pot tenir relació directa amb Internet ni publicar adreces externament.

## Implementació en Xarxa Local
- **Servei DNS Intern amb 'Forwarding'**:
  - Objectiu: Permetre que les màquines de la xarxa interna accedeixin a Internet.
  - Funcionament: Actua com a 'client' del DNS Internet de l'Institut de l'Ebre.
  - 'Forwarding': Si no coneix el nom demanat, passa la petició i emmagatzema la resposta en una cache per a ús futur.
# 6. Implementació del Servei DNS

## 6.1. Requeriments de Programari
- **Paquet bind**: El servei DNS funciona mitjançant el paquet `bind`, disponible per a descàrrega lliure.
- **Components del Sistema**: La instal·lació del sistema operatiu hauria d'incloure els components necessaris per al servei DNS.
- **Paquets Rellevants**:
  - `bind9`: Paquet principal per al servei DNS.
  - `bind9-doc`: Documentació per a `bind9`.
  - `bind9utils`: Utilitats addicionals per a `bind9`.
- **Verificació de la Instal·lació**: Utilitzar la comanda `dpkg -l bind9` per comprovar si els paquets estan instal·lats.
dpkg-query: package 'bind9' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

Per instal·lar el servei DNS, cal instal·lar els paquets bind9 i dnsutils amb la comanda:
apt-get install bind9 bind9-doc bind9utils
Una vegada instal·lat, en /etc/bind9/ es poden trobar els següents arxius:

- `named.conf`: Arxiu de configuració principal de BIND.
- `named.conf.options`: Opcions de configuració per al servidor DNS.
- `named.conf.local`: Configuració local, on es defineixen les zones.
- `named.conf.default-zones`: Defineix les zones per defecte.
- `db.127`: Zona per a l'adreça de loopback.
- `db.local`: Zona local per a resolució inversa.
- `db.root`: Arxiu de les arrels DNS, que conté informació sobre els servidors d'arrels DNS.
- `rndc.key`: Clau de seguretat per a la comunicació amb el daemon de BIND.
- `zones.rfc1918`: Definicions de zones per a adreces privades segons RFC 1918.

# Execució i Configuració d'un Servidor DNS amb bind9

## Procés `named`
- **Arxiu de Configuració**: `named.conf`.
- **Estructura**: Sentències delimitades per `;` i blocs de configuració en `{}`.
- **Inclusió d'Arxius**: 
  - `named.conf.options`: Opcions globals del servidor DNS.
  - `named.conf.local`: Definició de zones locals.
  - `named.conf.default-zones`: Zones per defecte.

## Verificació del Servei DNS
- **Herramienta**: Paquet `nmap`.
- **Comanda**: `nmap -sU localhost -p 53`.
- **Resultat**: Verifica si el port 53 (port DNS) està obert (indicant que el servei DNS està en funcionament).

## Configuració de Caching Only Server
- **Funcionament**: Intenta resoldre peticions i, si no té la resposta, redirigeix a servidors DNS externs.
- **Servidors DNS Externs**:
  - **OpenDNS**:
    - IPs: `208.67.222.222`, `208.67.220.220`.
    - Web: [OpenDNS IP Addresses](http://www.opendns.com/opendns-ip-addresses/)
  - **Google Public DNS**:
    - IPs: `8.8.8.8`, `8.8.4.4`.
    - Web: [Google Public DNS](https://developers.google.com/speed/publicdns/?csw=1)

# 6.2. Estructura dels Fitxers del Servidor DNS

Suposant una xarxa `192.168.70.x` amb el domini `informaticaASIX2.com`.

## /etc/bind/named.conf.options
- **Opcions generals**:
  ```conf
  options {
    directory "/var/cache/bind";
    forward only;
    forwarders {
      192.168.202.2;
      8.8.8.8;
    };
    auth-nxdomain no;
    listen-on-v6 { any; };
  };
  
Descripció de Directives:

- directory: Camí on es guarden els arxius temporals de named.
- forward only: Només utilitza els forwarders per a consultes externes.
- forwarders: Servidors externs per a la resolució de consultes DNS que no pot fer el servidor local.
- auth-nxdomain: Configura el bit AA per a indicar autorització sobre les zones gestionades.
Declaracions específiques:

- forwarders: Defineix els servidors DNS externs com OpenDNS o l'ISP/router local per a la resolució de noms.
  ```conf
  forwarders {
  // OpenDNS servers
  208.67.222.222;
  208.67.220.220;
  // IP del router local
  192.168.1.1;
};

- allow-query: Restringeix qui pot fer consultes DNS al servidor.
  ```conf
  allow-query { 192.168.70.0/24; };
- blackhole: Bloqueja consultes DNS de xarxes específiques definites en una acl.

  ```conf
  acl xarxes { 192.168.0.0/16; 192.168.70.1; };
  blackhole { xarxes;};

## Consideracions Addicionals
- dnssec-validation: S'ha d'activar per utilitzar DNSSEC, una extensió de seguretat per a DNS.
  
La configuració del named.conf.options és crucial per a assegurar que el servidor DNS operi correctament, tant per a la resolució de noms interna com per a la interacció amb servidors DNS externs.

# Resum de Configuració DNS - `named.conf.local` i `db.ASIX2.hosts`

## Fitxer: `/etc/bind/named.conf.local`
- **Ús**: Conté la configuració de les zones locals DNS (directa i inversa).
- **Exemples de Zones**:
  - Zona Directa: `zone "informaticaASIX2.com"`
  - Zona Inversa: `zone "70.168.192.in-addr.arpa"`

## Configuració de Zones
- **Tipus**: Master.
- **Arxius de Configuració**:
  - Zona Directa: `/etc/bind/db.ASIX2.hosts`
  - Zona Inversa: `/etc/bind/192.168.70.rev`
- **Notificació**: Activada (`notify yes`).

## Fitxer: `/etc/bind/db.ASIX2.hosts` (Zona Directa)
- **Contingut**: Configuració per trobar les IP a partir dels noms.
- **Registre SOA**:
  - Propietari: `informaticaASIX2.com`
  - Servidor Mestre: `servidor-primari.informaticaASIX2.com`
  - Persona responsable: `root.informaticaASIX2.com` (ús de punt en lloc de @)
  - Número de Sèrie: Format `AAAAMMDDNN` o `NN`
  - Actualització (Refresh Time)
  - Reintents (Retry Time)
  - Caducitat (Expire Time)
  - TTL mínim

## Registres DNS Mínims
- **IN NS**: Defineix els servidors DNS autoritzats per la zona.
- **IN A**: Correspondència entre IP i nom de domini.
  - Exemple: `pc01.informaticaASIX2.com IN A 192.168.70.21`
- **IN CNAME**: Defineix àlies per a IPs definides.
  - Exemple: `www IN CNAME servidor-primari`

## Exemples Addicionals d’Entrades `IN A`
- `secretaria.informaticaASIX2.com. IN A 192.168.70.120`
- `biblioteca.informaticaASIX2.com. IN A 192.168.70.121`

# Configuració DNS - Resum

## /etc/bind/named.conf.local
- **Propòsit**: Defineix la configuració de les zones locals del DNS, tant directes com inverses.
- **Exemples de Configuració**:
  - Zona Directa: `zone "informaticaASIX2.com"`
    - Tipus: `master`
    - Arxiu: `/etc/bind/db.ASIX2.hosts`
    - Notificació: `yes`
  - Zona Inversa: `zone "70.168.192.in-addr.arpa"`
    - Tipus: `master`
    - Arxiu: `/etc/bind/192.168.70.rev`
    - Notificació: `yes`

## /etc/bind/db.ASIX2.hosts
- **Funció**: Zona directa per trobar IPs a partir dels noms.
- **Contingut Important**:
  - `$TTL 604800`
  - SOA Record per `informaticaASIX2.com.`
    - Servidor Mestre: `servidor-primari.informaticaASIX2.com.`
    - Responsable: `root.informaticaASIX2.com.`
    - Serial: `1`
    - Refresh: `604800`
    - Retry: `86400`
    - Expire: `2419200`
    - Negative Cache TTL: `604800`
  - Registres NS, A, i CNAME per a `informaticaASIX2.com`, `servidor-primari`, `pc01.inform

## Fitxer: `/etc/bind/named.conf.local`
- **Ús**: Conté la configuració de les zones locals DNS (directa i inversa).
- **Exemples de Zones**:
  - Zona Directa: `zone "informaticaASIX2.com"`
  - Zona Inversa: `zone "70.168.192.in-addr.arpa"`

## Configuració de Zones
- **Tipus**: Master.
- **Arxius de Configuració**:
  - Zona Directa: `/etc/bind/db.ASIX2.hosts`
  - Zona Inversa: `/etc/bind/192.168.70.rev`
- **Notificació**: Activada (`notify yes`).

## Fitxer: `/etc/bind/db.ASIX2.hosts` (Zona Directa)
- **Contingut**: Configuració per trobar les IP a partir dels noms.
- **Registre SOA**:
  - Propietari: `informaticaASIX2.com`
  - Servidor Mestre: `servidor-primari.informaticaASIX2.com`
  - Persona responsable: `root.informaticaASIX2.com` (ús de punt en lloc de @)
  - Número de Sèrie: Format `AAAAMMDDNN` o `NN`
  - Actualització (Refresh Time)
  - Reintents (Retry Time)
  - Caducitat (Expire Time)
  - TTL mínim

## Registres DNS Mínims
- **IN NS**: Defineix els servidors DNS autoritzats per la zona.
- **IN A**: Correspondència entre IP i nom de domini.
  - Exemple: `pc01.informaticaASIX2.com IN A 192.168.70.21`
- **IN CNAME**: Defineix àlies per a IPs definides.
  - Exemple: `www IN CNAME servidor-primari`

## Exemples Addicionals d’Entrades `IN A`
- `secretaria.informaticaASIX2.com. IN A 192.168.70.120`
- `biblioteca.informaticaASIX2.com. IN A 192.168.70.121`

  # Resum de Configuració DNS - Zones Directes i Inverses

## Importància del Punt Final en Noms de Domini
- **Regla**: Sempre afegir un punt final al nom de la zona.
  - **Exemple**: `www.iesebre.com.` en lloc de `www.iesebre.com`
  - **Conseqüència sense Punt**: Es considera una abreviatura. Ex: `www.iesebre.com` es converteix en `www.iesebre.com.iesebre.com`

## Ús del Tabulador
- **Separació entre ítems**: Obligatòriament amb tabulador.

## Fitxer: `/etc/bind/192.168.70.rev` (Zona Inversa)
- **Ús**: Trobar els noms a partir de l'adreça IP.
- **Contingut**: 
  - Registre SOA idèntic a la zona directa.
  - Registres `IN PTR` per a resolució inversa.

## Formats de Registres `IN PTR`
- **Format Tradicional**:
  - `1.70.168.192.in-addr.arpa. IN PTR informaticaASIX2.com.`
  - `1.70.168.192.in-addr.arpa. IN PTR servidor-primari`
  - `21.70.168.192.in-addr.arpa. IN PTR pc01.informaticaASIX2.com`
- **Format Alternatiu**:
  - `1 IN PTR informaticaASIX2.com.`
  - `1 IN PTR servidor-primari`
  - `21 IN PTR pc01.informaticaASIX2.com`

## Consistència amb la Zona Directa
- **Coincidència Exacta**: Totes les entrades IP han de coincidir amb els noms definits en la zona directa.
- **Actualitzacions**: Si es modifica la zona directa, cal actualitzar també la zona inversa.

## Altres Registres DNS
- **IN PTR**: Utilitzat en resolució inversa, el contrari del registre A.
- **Registres No Utilitzats en Aquest Context**:
  - `MX (Mail Exchange)`: Indica servidors de correu.
  - `SRV`: Indica la ubicació dels servidors per a un servei específic.

# 6.3 Explicació de la Notació `in-addr.arpa`

## Funcionament de `in-addr.arpa`
- **Propòsit**: Utilitzat per a la resolució inversa de noms de domini (de l'adreça IP al nom de domini).
- **Lògica**: Les consultes van de dreta a esquerra, similar a la resolució dels noms de domini.
- **Diferència**: A diferència dels noms de domini que comencen per '.', `in-addr.arpa` s'utilitza per a adreces IP.

## Exemple Pràctic
- **Adreça IP**: `192.168.70.1`
- **Procés de Resolució**:
  - Cerca comença amb els servidors `arpa`.
  - Continua a `in-addr.arpa`.
  - Segueix a `192.in-addr.arpa`.
  - Finalitza a `1.70.168.192.in-addr.arpa` per trobar el registre corresponent.
- **Notació**: Puntejada inversa, on els primers octets identifiquen la xarxa.

## Manteniment via Aplicacions Web
- **Webmin**:
  - **Requisits**: Instal·lació dels paquets `webmin` i `webmin-bind`.
  - **Accés**: Via web a `https://localhost:10000/`.
  - **Ús**: Permet mantenir de manera còmoda la configuració DNS.
- **GADMIN-BIND**:
  - **Descripció**: Una aplicació gràfica disponible en els repositòris.
  - **Funció**: Facilita la gestió de la configuració DNS.

# 6.4 Comandes per Comprovar la Configuració DNS

## 1. `named-checkconf`
- **Ús**: Comprovar la sintaxi de `named.conf` i fitxers inclosos.
- **Opció Addicional**: `-z` per obtenir informació addicional.

## 2. `named-checkzone`
- **Ús**: Comprovar la sintaxi dels arxius de zona.
- **Exemple**: `named-checkzone informaticaASIX2.com /etc/bind/db.ASIX2.hosts`
- **Opció per Debugging**: `-D` per assegurar que tots els noms de màquina s’han creat correctament.

## 3. `dig`
- **Ús**: Realitzar consultes a un servidor DNS, detectar problemes de configuració.
- **Exemples**:
  - `dig informaticaASIX2.com`
  - `dig 0.70.168.192.in-addr.arpa`
  - `dig -t PTR 1.70.168.192.in-addr.arpa`

## 4. `host`
- **Ús**: Convertir noms a adreces IP i viceversa, comprovar zones directes i inverses.
- **Exemple**: `host servidor-primari.informaticaASIX2.com`

## 5. `nslookup`
- **Ús**: Realitzar consultes al servidor DNS.
- **Exemples**:
  - `nslookup servidor-primari.informaticaASIX2.com`
  - `nslookup www.informaticaASIX2.com`

## 6. Visualització de Logs amb `tail`
- **Comanda**: `tail -f /var/log/syslog | grep named`
- **Esperat**: Missatges de registre de `named`.

## 7. `rndc`
- **Ús**: Consultar l'estatus del servidor DNS.
- **Exemple**: `rndc status`

## 8. `dnstop`
- **Ús**: Monitorització en temps real de peticions DNS.
- **Exemple**: `dnstop eth1`

## Modificació d'`/etc/resolv.conf`
- **Contingut**: 
  - `search informaticaASIX2.com`
  - `nameserver 192.168.70.1`
- **Nota**: El contingut s'esborra en reiniciar. Necessita modificació per a fer-ho permanent.

# 6.5 Posada en Marxa del Servei de Noms (named/bind9)

## Assegurar l'Arrencada Automàtica
- **Objectiu**: Que `named (bind9)` s'iniciï automàticament en arrencar el servidor.
- **Mètode**:
  - La instal·lació del paquet crea enllaços simbòlics en `/etc/rc?.d/` per l'ordre d'arrencada.
  - Si l'arrencada és en el nivell 2, es pot crear un enllaç en `/etc/rc2.d/`.
- **Creació d'Enllaç**:
  - Comanda: `ln -s ../init.d/bind9 S15bind9`
  - Directori: `/etc/rc2.d/`
  - Verificació: Llistar `/etc/rc2.d/` per veure si l'enllaç s'ha creat.

## Gestió Manual del Servei
- **Arrencada**:
  - Comanda: `/etc/init.d/bind9 start`
- **Aturada**:
  - Comanda: `/etc/init.d/bind9 stop`

## Verificació de l'Arrencada
- **Comanda**: `tail -f /var/log/syslog`
- **Propòsit**: Verificar que `bind9` ha arrencat correctament.

# Configuració de Clients per Utilitzar Servei DNS

## Context
- **Fitxer `hosts`**: Tradicionalment utilitzat per a la resolució de noms en xarxes TCP/IP.
  - **Ubicació**:
    - Unix/Linux: `/etc/hosts`
    - Windows: `c:\windows\system32\drivers\etc\hosts`
  - **Inconvenient**: Necessitat de mantenir-lo actualitzat en totes les màquines.

## 6.6.1 Configuració en Unix/Linux
- **Objectiu**: Fer que el servidor sigui client del servei DNS.
- **Fitxers a Modificar**:
  - `/etc/nsswitch.conf`
    - Verificar línia: `hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4`
  - `/etc/resolv.conf`
    - Contingut necessari: 
      - `search informaticaASIX2.com` o `domain informaticaASIX2.com`
      - `nameserver 192.168.70.1`
    - Eliminar referències no necessàries (si hi són): 
      - `nameserver 192.168.202.2`
      - `nameserver 8.8.8.8`
- **Verificació**:
  - Executar `nslookup servidor-primari` per comprovar el funcionament.

## 6.6.2 Configuració en Windows
- **Pas Inicial**: Configurar una IP dins del rang del servidor.
- **Configuració del DNS**:
  - Accedir a les propietats de la xarxa.
  - Modificar la configuració del DNS en les opcions avançades.
- **Verificació**:
  - Reiniciar Windows.
  - Comprovar la resposta del DNS executant comandes pertinents.

## Neteja del Fitxer `hosts`
- **Acció**: Eliminar qualsevol referència en els fitxers `hosts` (excepte `localhost 127.0.0.1`).
- **Rao**: Evitar definicions incorrectes que podrien interferir amb el DNS.

# 6.7 Configuració d'un Servidor DNS Esclau

## Concepte
- **Propòsit**: Configurar un servidor DNS per actuar com a esclau d’un servidor mestre.
- **Beneficis**: Distribució de càrrega, alta disponibilitat.

## Configuració del Servidor Mestre
- **Arxiu**: `/etc/bind/db.ASIX2.hosts` (Zona Directa)
  - Afegir línia per al DNS esclau.
- **Arxiu**: `/etc/bind/192.168.70.rev` (Zona Inversa)
  - Repetir el procés anterior.
- **Arxiu**: `/etc/bind/named.conf.local`
  - Utilitzar `also-notify` per sincronitzar canvis amb l’esclau.
  - Exemple de Configuració:
    ```bash
    zone "informaticaASIX2.com" {
    type master;
    file "/etc/bind/db.ASIX2.hosts";
    also-notify {ip_de_l’esclau;};
    notify yes;
    };
    ```

## Configuració del Servidor Esclau
- **Arxiu**: `/etc/bind/named.conf.local`
  - Indicar tipus `slave`.
  - Especificar el mestre amb `masters { 192.168.70.1; };`.
  - Exemple de Configuració:
    ```bash
    zone "informaticaASIX2.com" {
    type slave;
    file "/etc/bind/db.ASIX2.hosts";
    masters { 192.168.70.1; };
    notify yes;
    };
    ```

## Manteniment de la Sincronització
- **Actualització del Paràmetre Serial**: Incrementar-lo en una unitat en el servidor mestre per a que els DNS esclaus s'actualitzin.
- **Arxius Afectats**: `/etc/bind/db.ASIX2.hosts` i `/etc/bind/192.168.70.rev` del mestre.

# 6.7.1 Possibles Errors en la Configuració DNS Primari i Esclau

## Errors Comuns
1. **Error de Connexió entre Màquines (Host Unreachable)**
   - **Causes Possibles**: Targetes mal configurades o IPs incorrectes en fitxers DNS.
2. **Error en Trobar Fitxer o Carpeta**
   - **Manifestació**: Transferència s'inicia però no es completa.
   - **Exemples**: Per a zones inverses (192.168.69.x) i directes (dam2.informatica.com).
3. **Error de ‘Permission Denied’**
   - **Informació Addicional**: Relacionat amb ‘apparmor’.

# 6.7.2 Monitorització del Funcionament del DNS de Backup

## Comprovació de la Comunicació i Transferència
- **Servidor Principal**: Veure l'inici i la finalització de l'enviament de zones.
- **Servidor Secundari**: Confirmar la recepció de zones (ex. asix2.informatica.com) i verificar dades enviades.

## Comandes per Comprovar Funcionament DNS
- `dig nom_de_la_zona`: Comprovar càrrega correcta de la zona.
- `host direcció_IP_servidor_DNS`: Comprovar funcionament de la zona inversa.
- `host nom_servidor_DNS`: Comprovar funcionament de la zona directa.
- `ping al DNS`: Comprovar la comunicació amb el DNS.



# DHCP


