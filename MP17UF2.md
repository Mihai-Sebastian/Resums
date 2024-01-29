# Introducció a la Seguretat en Serveis

La seguretat informàtica és un aspecte crític en la gestió de serveis IT. És essencial entendre els atacs informàtics per protegir eficaçment els nostres sistemes. Aquests atacs generalment segueixen un cicle de cinc fases:

## 1. Reconeixement
En aquesta fase, l'atacant recopila informació sobre el sistema objectiu. Això inclou identificar els punts dèbils, com ara versions de programari desactualitzades o configuracions insegures.

## 2. Escaneig
Durant l'escaneig, l'atacant utilitza eines per mapejar la xarxa i identificar serveis exposats. Això pot incloure escanejar ports i buscar vulnerabilitats conegudes.

## 3. Accés al Sistema
Una vegada identificades les vulnerabilitats, l'atacant intenta explotar-les per obtenir accés al sistema. Això pot ser a través d'execució de codi remot, injecció SQL, o altres tècniques d'atac.

## 4. Manteniment de l'Accés
Un cop dins, l'atacant buscarà mantenir l'accés per a activitats futures. Això pot incloure la instal·lació de backdoors o l'ús de tècniques per evitar la detecció.

## 5. Esborrat d'Empremtes
Finalment, l'atacant esforçarà per eliminar qualsevol rastre de l'atac, incloent registres de log i altres evidències que puguin ser utilitzades en una investigació.

Entendre aquestes fases ens ajuda a preveure i prevenir activitats malicioses, protegint així els nostres sistemes informàtics.

# DNS

| SECCION     | Descripción |
|-------------|--------------------------------------------------------------------|
| HEADER      | Contiene información sobre el tipo de mensaje. Incluye campos que informan sobre el número de entradas en otras secciones del mensaje. |
| QUESTION    | Contiene una o más solicitudes de información (queries) que se envían al servidor DNS. |
| ANSWER      | Contiene uno o más registros que responden a la(s) solicitud(es). |
| AUTHORITY   | Contiene uno o más registros que apuntan al servidor autoritativo del dominio en cuestión. |
| ADDITIONAL  | Registros con información adicional no necesaria para responder a la query. |

# Transaccions DNS més comuns

Les transaccions DNS són essencials per al funcionament del sistema de noms de domini. Aquí tenim els tipus més comuns de transaccions:

- **Consultes/respostes DNS (Queries):**
  Aquestes són les operacions més freqüents en DNS. Quan un usuari vol resoldre un nom de domini a una adreça IP, envia una consulta DNS al servidor, que respon amb la informació sol·licitada.

- **Transferències de Zona:**
  Es tracta de la replicació de fitxers de zona entre servidors DNS. Això assegura que múltiples servidors tinguin còpies actualitzades de les dades de la zona, millorant la disponibilitat i redundància.

- **Actualitzacions Dinàmiques:**
  Permeten actualitzar els fitxers de zona d'un servidor DNS de manera dinàmica. Això és útil per a canvis ràpids en els registres DNS, com en el cas de serveis que requereixen freqüents canvis d'adreces IP.

- **Notificacions:**
  Un servidor autoritatiu utilitza notificacions per a informar a altres servidors DNS sobre els canvis en les dades de les zones. Això permet que altres servidors puguin actualitzar les seves còpies de la zona amb la informació més recent.

# Seguretat en el servei DNS: Anàlisi de vulnerabilitats

Els atacs al DNS poden afectar tant el servidor i la xarxa local com les comunicacions entre servidors i clients. A continuació, es presenten les amenaces i contramesures principals:

## 1. Locals
- **Mesures i polítiques de seguretat en la xarxa interna:** Implementació de mecanismes anti-spoofing, sistemes de detecció i prevenció d'intrusions (IDS/IPS).
- **Protecció de l'accés als servidors i arxius:** Restringir l'accés físic i lògic als recursos crítics.

## 2. Servidor-Servidor
- **Actualitzacions dinàmiques:** Utilitzar Dynamic DNS (DDNS) per centralitzar l'administració de les dades.
- **Canal restringit de comunicació:** Implementar Transaction SIGnature (TSIG) per a la autenticació i integritat dels missatges.

## 3. Servidor Master-Esclau
- **Transferències de zona:** Utilitzar TSIG per a l'autenticació i el xifratge de les transferències de zona.
- **Xifratge:** Aplicar SSL/TLS per a la confidencialitat de les comunicacions.
- **Canal privat de xarxa:** Establir una connexió de xarxa segura entre els servidors.

## 4. Servidor Master-Client Caché/Resolver
- **Aleatorietat en el port origen i els identificadors de missatge:** Augmentar la seguretat en les consultes per prevenir manipulacions.
- **DNSSEC:** Implementar DNS Security Extensions per a la integritat i autenticació de les dades del DNS.

## 5. Servidor-Client
- **Atacs locals i spoofing:** Protegir les comunicacions del client per prevenir la intercepció i suplantació.
- **DNSSEC:** Utilitzar DNSSEC per garantir la veracitat i seguretat de les respostes del DNS.

Aquestes contramesures ajuden a protegir els serveis DNS contra una varietat d'atacs i a assegurar la integritat i la disponibilitat de les dades de noms de domini.

# Atacs i Funcionament dels Mateixos

Els atacs a sistemes de xarxa poden prendre diverses formes. Aquí s'expliquen alguns dels més comuns:

## IP Spoofing
- **Funcionament:** L'atacant falsifica l'adreça IP d'origen en els paquets enviats a la víctima per fer creure que els paquets provenen d'una font confiable o interna.

## DNS Cache Poisoning
- **Funcionament:** Aquest atac consisteix en introduir informació falsa en la caché DNS d'un servidor, redirigint així les peticions a un servidor maliciós controlat per l'atacant.

## DoS (Denial of Service)
- **Funcionament:** Els atacs DoS busquen sobrecarregar els recursos d'un sistema per fer que aquest deixi de prestar servei als usuaris legítims.

## Man in the Middle (MitM)
- **Funcionament:** L'atacant s'interposa en la comunicació entre dues parts, interceptant i potencialment modificat els missatges que s'intercanvien.

## DNS Tunneling
- **Funcionament:** Tècnica que utilitza el protocol DNS per enviar dades no-DNS, sovint per comunicar-se amb un servidor de comandament i control o per exfiltrar dades de manera encoberta.

## DoS DNS Amplification Attack
- **Funcionament:** Un atac d'amplificació DNS comença amb peticions DNS falsificades que tenen com a resposta missatges molt més grans. Aquests són enviats a la víctima, resultant en una sobrecàrrega de trànsit que pot provocar la denegació del servei.

Cadascun d'aquests atacs explota diferents debilitats i requereix estratègies específiques de mitigació per assegurar la integritat i disponibilitat dels serveis de xarxa.

# Assegurament del Servei DNS

L'assegurament del servei DNS pot ser entès com una estructura de tres capes, cadascuna amb elements claus per a la seguretat:

## 1. Entorn Base
Aquesta capa inclou els components fonamentals del servei DNS a nivell de sistemes i comunicacions:
- **Sistema operatiu:** Assegurar la configuració i les actualitzacions per tancar vulnerabilitats.
- **Software de Bind:** Utilitzar la versió més segura i configurar adequadament.
- **Topologia de xarxa:** Disposar els elements de xarxa de manera que minimitzin els riscos de seguretat.

## 2. Dades
Mesures de seguretat relacionades directament amb les dades gestionades pel servei DNS:
- **Parametritzacions:** Aplicar les millors pràctiques en la configuració del DNS.
- **Informació de registres de zona:** Protegir la integritat i confidencialitat dels registres.
- **Transaccions:** Assegurar que les transaccions DNS siguin segures, incloent:
  - **Queries (Consultes/Respostes):** Validar la informació que es passa en cada consulta i resposta.
  - **Transferències de zona:** Utilitzar mètodes segurs com TSIG o DNSSEC per transferir dades de zona.
  - **Notificacions:** Autenticar i verificar la integritat de qualsevol notificació DNS.
  - **Actualitzacions dinàmiques:** Protegir les actualitzacions dinàmiques per evitar modificacions malicioses.

La implementació de mesures de seguretat en cadascuna d'aquestes capes és crítica per assegurar la resiliència i la confiabilitat del servei DNS.

## Transaccions: Protecció dels Missatges en Operacions DNS

Per assegurar la seguretat del DNS, és vital protegir les transaccions i els missatges que es produeixen durant les operacions habituals. Aquí tenim un desglossament de les mesures de seguretat que s'han de considerar:

### Queries: Consultes/Respostes
- **Validació de la informació:** Assegurar-se que les dades rebudes són correctes i provinents de fonts legítimes.
- **Utilització de DNSSEC:** Per a la validació de la integritat i autenticitat de les respostes DNS.

### Transferències de Zona
- **Autenticació amb TSIG:** Utilitzar signatures de transacció per validar la comunicació entre servidors DNS.
- **Xifrat de transferències:** Empregar protocols com SSL/TLS per garantir la confidencialitat de les dades transferides.

### Notificacions
- **Verificació de la font:** Confirmar que les notificacions de canvis de zona provenen del servidor autoritatiu correcte.
- **Seguretat en el protocol:** Implementar TSIG o DNSSEC per assegurar que les notificacions no han estat manipulades.

### Actualitzacions Dinàmiques
- **Control d'accés:** Restringir qui pot realitzar actualitzacions dinàmiques al DNS.
- **Registre de canvis:** Mantenir un historial detallat de totes les actualitzacions per permetre la revisió i la recuperació en cas d'incidència.

Aquestes pràctiques contribueixen a un entorn DNS més segur, reduint el risc d'atacs i la possibilitat de comprometre les operacions de la xarxa.

# Assegurament del Servei DNS: Contramesures als Atacs

## DNSSEC
- **En què consisteix:** DNSSEC (DNS Security Extensions) és un conjunt d'extensions al DNS que proporcionen autenticació de l'origen de les dades del DNS, integritat de dades i rebut de resposta negativa. Això es realitza mitjançant una cadena de confiança construïda amb signatures digitals i claus públiques/privades.
- **Funcionament:** Quan una consulta DNS es realitza, DNSSEC afegeix signatures digitals a les respostes. Els resolvent DNS verifiquen aquestes signatures mitjançant claus públiques que han estat distribuïdes per mitjà de la infraestructura de clau pública del DNS.

## Xifratge DNS
- **DNS over TLS (DoT):**
  - **Port usat:** 853
  - **Funcionament:** DoT encapsula el tràfic DNS dins de la capa de seguretat del transport (TLS), proporcionant confidencialitat i integritat de dades entre el client i el servidor DNS.
  
- **DNS over HTTPS (DoH):**
  - **Port usat:** 443
  - **Funcionament:** DoH passa el tràfic DNS a través del protocol HTTPS, que utilitza TLS per encriptar les dades. Això no només protegeix la comunicació sinó que també la fa indistingible d'altres tipus de tràfic HTTPS, augmentant la privadesa.

- **Ports estàndard:**
  - Les consultes DNS tradicionals utilitzen el port **53 UDP** per a les transaccions ràpides i no xifrades.

L'adopció de DNSSEC, DoT i DoH són passos claus per millorar la seguretat en les consultes DNS, protegint contra una àmplia gamma d'atacs com el DNS spoofing i les intercepcions de tràfic.

# FTP
# File Transfer Protocol (FTP)

- **Definició**: Protocol de transferència de fitxers.
- **Funció**: Protocol de xarxa per la transferència de fitxers entre sistemes (ordinadors) connectats a una xarxa TCP, basat en l'arquitectura client-servidor.
- **Compatibilitat**: Permet enviar fitxers entre ordinadors independentment del seu sistema operatiu.
- **Ubicació en el Model TCP/IP**: Forma part de la capa d'aplicació (Capa 5).
- **Ports de Xarxa**: Utilitza normalment el port 20 (per a dades) i el port 21 (per a comandes i flux de control).
- **Seguretat**: Inicialment dissenyat per a oferir la màxima velocitat, però no la màxima seguretat. L'informació de login-password i la transferència de fitxers es realitzen en text pla, sense xifratge.

# Deficiències de Seguretat del FTP i Solucions

## Deficiències del FTP

FTP, dissenyat per oferir la màxima velocitat de connexió, presenta una sèrie de deficiències importants en termes de seguretat:

- **Mecanisme de Login-Password**: 
  - Problema: El servidor FTP no pot garantir que l'usuari sigui realment qui diu ser.
  - Conseqüència: Vulnerabilitat en la verificació d'identitat.

- **Contrasenyes en Text Clar**: 
  - Problema: Les contrasenyes s'envien sense xifrar.
  - Conseqüència: Amb un sniffer, es poden capturar fàcilment aquestes contrasenyes.

- **No Xifra la Sessió FTP**: 
  - Problema: Tota la informació transferida, inclosos els arxius, es fa en text pla.
  - Conseqüència: Possibilitat d'interceptar i llegir el contingut de la transferència.

## Solucions

Per afrontar aquestes deficiències, s'han desenvolupat alternatives que ofereixen millors garanties de seguretat:

- **SCP (Secure Copy Protocol)**:
  - Forma part del paquet de SSH (Secure Shell).
  - Funció: Permet la transferència segura de fitxers entre sistemes, xifrant tota la informació transferida.

- **SFTP (SSH File Transfer Protocol)**:
  - També inclosa en el paquet SSH.
  - Funció: Ofereix una interfície similar al FTP, però amb totes les comunicacions xifrades, garantint la seguretat de les dades.

## Llista Blanca vs Llista Negra

- **Llista Blanca**: Metodologia de seguretat on només s'allowen accions, processos o entitats específiques considerades segures.
- **Llista Negra**: Enfocament on es bloquegen accions, processos o entitats específiques conegudes per ser nocives o no segures.

## Alternatives al FTP

- **FTPS (File Transfer Protocol Secure)**:
  - Afegeix xifratge SSL/TLS al FTP.
  - Protegeix tant les credencials d'usuari com les dades transferides.

- **SFTP (SSH File Transfer Protocol)**:
  - Part del paquet de Secure Shell (SSH).
  - Xifra tota la sessió de transferència de fitxers, incloent l'autenticació i les dades.
    
## Algoritmes de Transferència de Fitxers

- **Algoritmes de Control de Flux**: FTP utilitza algoritmes de control de flux TCP per a la gestió de la transferència de dades.
- **Modus de Transferència de Fitxers**: Inclou algoritmes per a la transferència en mode ASCII o binari, depenent del tipus de fitxer.

Per defecte, FTP no utilitza algoritmes de xifratge per a la protecció de dades:

- **Transferència de Dades**: Les dades es transfereixen en text pla, sense xifratge.
- **Autenticació d'Usuari**: Les credencials d'usuari també es transmeten en text pla.

# FTP Actiu vs. FTP Passiu

## FTP Actiu

### Funcionament
- En el mode FTP actiu, el client inicia la connexió al servidor FTP a través del port 21 (port de comandes).
- Després de l'autenticació, el servidor inicia la connexió de dades cap al client des d'un port aleatori al port 20 del client.

### Canals i Ports
- **Canal de Comandes**: Client (port aleatori) → Servidor (port 21).
- **Canal de Dades**: Servidor (port aleatori) → Client (port 20).

## FTP Passiu

### Funcionament
- En el mode FTP passiu, el client també inicia la connexió al servidor FTP a través del port 21.
- A diferència del mode actiu, en el mode passiu, després de l'autenticació, el servidor informa al client un port aleatori per al qual el client haurà d'iniciar la connexió de dades.

### Canals i Ports
- **Canal de Comandes**: Client (port aleatori) → Servidor (port 21).
- **Canal de Dades**: Client (port aleatori) → Servidor (port aleatori).

## Diferències Clau
- La principal diferència entre els modes actiu i passiu està en qui inicia la connexió de dades i a través de quins ports.
- El mode passiu és més adequat per a clients darrere de firewalls o NAT, ja que permet al client controlar les connexions entrants i sortints.

# Atacs i Vulnerabilitats en Servidors FTP

## Atacs Comuns

### Per Força Bruta
- Intentos repetits d'accés mitjançant la combinació de noms d'usuari i contrasenyes fins a trobar la correcta.

### Rebot FTP
- Utilització d'un servidor FTP vulnerable per a rebotar el tràfic i amagar la font real de l'atac.

### Robatori de Ports
- Endevinar el proper port obert i usurpar una connexió legítima

### Attack Spoofing
- Suplantació de l'adreça IP d'un client legítim per enganyar el servidor i guanyar accés.

### DoS - DDoS
- Atacs de denegació de servei (DoS) i atacs de denegació de servei distribuït (DDoS) per sobrecarregar el servidor.

## Vulnerabilitats Comunes

### Software del Servidor No Actualitzat
- Riscos associats amb l'ús de versions antigues del software del servidor, que poden contenir falles de seguretat conegudes.

### Software del Servidor Mal Configurat
- Problemes deguts a una configuració incorrecta o insegura del servidor FTP.

### Molts Administradors
- Risc augmentat d'errors humans o de seguretat quan hi ha massa persones amb accés administratiu.

### Protocols o Xifratge Ja Vulnerats
- Vulnerabilitats relacionades amb l'ús de protocols de xifratge obsolets o insegurs.

### Entorn Difícil d’Administrar
- Complexitat en la gestió i la supervisió de l'entorn de xarxa pot conduir a brexes de seguretat.

### Falta d’Alertes o Pistes per Auditoria (LOGS)
- Absència de sistemes adequats per a la detecció de comportaments anòmals o la falta de registres per a la realització d'auditories de seguretat.

## Conclusió
La protecció dels servidors FTP requereix una vigilància constant, actualitzacions de software, configuracions segures, i una gestió adequada tant dels accessos com dels protocols i sistemes de registre.

# Mesures de Seguretat per a Servidors FTP

## Deshabilitar Estàndard FTP: Alternatives Més Segures
- **FTPS**: Utilització de FTP sobre SSL/TLS per a xifrar la sessió.
- **SFTP**: Part del protocol SSH, proporciona una transferència de fitxers segura i xifrada.

## Encriptació i Hashos Robustos
- Utilitzar algoritmes de xifratge forts.
- Emprar hashos robustos per a l'emmagatzematge segur de contrasenyes.

## Instal·lació del Servidor Darrera d'un Gateway
- Protegir el servidor col·locant-lo darrera d'un gateway de seguretat.

## Llistes Blanques i Negres d'IPs
- Restringir o permetre accés basant-se en adreces IP específiques.

## Assegurar Servidor FTPS
- **Mode Explícit**: Negociació explícita del xifratge.
- **Mode Implícit**: Xifratge per defecte en tota la connexió.
- Utilitzar TLS 1.2 i certificats SSL per a la seguretat de la connexió.

## Gestió Administrativa del Compte
- Credencials separades del servidor FTP.
- Deshabilitar usuari anònim.
- No compartir comptes d'usuari.
- Deshabilitar comptes després d'un cert nombre d'errors d'inici de sessió.

## Política de Contrasenyes Fortes
- Exigir contrasenyes complexes i canvis regulars.

## Implementació de Seguretat a Nivell de Carpetes
- Configurar permisos adequats.
- Aplicar xifratge i quotes de disc on sigui necessari.

## Facilitar l'Administració
- Utilitzar autenticació AD o LDAP.
- Restringir l'accés a administradors des de xarxes externes.
- Evitar l'ús de noms de compte per defecte com 'admin' o 'root'.
- Restringir els permisos d'administració.

## Seguir Bones Pràctiques de Seguretat
- Mantenir-se informat sobre les millors pràctiques en seguretat de xarxes.

## Altres Mesures
- Implementar un clúster d'alta disponibilitat.
- Unificar tipus de servidors FTP per a una millor gestió.
- Habilitar l'auditoria del servidor FTP.
- Configurar alertes basades en els logs del sistema.
- Bloquejar la gestió remota del servidor FTP.

# Servei de Correu Electrònic: Seguretat i Atacs

## Principals Atacs: Phishing vs. Spoofing

### Phishing
- **Basat en**: Enganyar als destinataris perquè revelin informació sensible o realitzin accions específiques.
- **Metodologia**: Sovint utilitza correus electrònics que semblen ser de fonts fiables però que són fraudulents.

### Spoofing
- **Basat en**: Falsificació de la identitat de l'enviador.
- **Metodologia**: Manipula l'encapçalament del correu electrònic per fer creure que prové d'una font legítima.

## Protocol SPF (Sender Policy Framework)

### Funcionament
- Verifica si l'IP de l'enviador està autoritzada per enviar correus en nom del domini.
- Es basa en registres TXT a DNS que especifiquen quines IP estan autoritzades.

## Protocol DKIM (DomainKeys Identified Mail)

### Funcionament
- Utilitza xifratge amb clau pública/privada per garantir que el contingut del correu no ha estat modificat durant el trànsit.
- Una clau privada xifra l'encapçalament del correu i una clau pública al DNS del domini serveix per a la seva verificació.

## Estàndard DMARC (Domain-based Message Authentication, Reporting and Conformance)

### Funcionament
- Combina SPF i DKIM per validar l'origen dels correus.
- Defineix com tractar els correus que no passen les verificacions i proporciona informes sobre els intents de lliurament.

# Mesures per a l'Ús Segur del Correu Electrònic

## Mesures Quan es Rep un Correu Electrònic

- **Comprovar el Remitent**: 
  - Utilitzar eines com Whois per identificar el propietari del domini.
  - Examinar detalls a la capçalera del correu per a verificació addicional.

- **Precaució amb Enllaços Sospitosos**:
  - Evitar obrir enllaços directament.
  - Situar el cursor sobre l'enllaç per previsualitzar l'URL.
  - Teclejar manualment els enllaços al navegador.

- **Solució Antimalware**:
  - Tenir un sistema antimalware per escanejar els correus entrants.

- **Contrasenyes Robustes i Autenticació de Doble Factor**:
  - Utilitzar contrasenyes fortes i úniques.
  - Implementar autenticació de doble factor en comptes de correu crítics.
  - No marcar l'opció de "recordar contrasenya".

- **Evitar Connexions Públiques**:
  - No utilitzar el correu electrònic des de connexions Wi-Fi públiques o ordinadors compartits.

- **Xifratge de Correus Electrònics**:
  - Utilitzar estàndards com PGP o S/Mime per a la signatura electrònica i xifratge.

- **Gestió de Correu Spam**:
  - No respondre a correus spam.
  - Afegir remitents de spam a la llista negra i eliminar els correus no desitjats.

## Mesures Addicionals

- **Desactivar l'HTML en Correus**:
  - Evitar la inclusió de llenguatges que podrien ser usats per a fins il·lícits.
  - Deshabilitar macros i descàrrega automàtica d'imatges.

- **Usar Còpia Oculta en Enviaments Massius**:
  - Per protegir les adreces de correu dels destinataris.

- **Separació del Correu Corporatiu i Personal**:
  - No utilitzar comptes de correu electrònic corporatius per a fins personals.

- **Gestió de Fitxers Adjunts**:
  - Habilitar l'opció de mostrar extensions de fitxers.
  - Utilitzar eines com Virustotal per a verificar els adjunts.
  - Desconfiar de fitxers amb noms enganyosos o extensions ocultes.

## Interpretació de Capçaleres de Correus Electrònics

- **Dades Identificables**:
  - Informació sobre l'emissor i receptor.
  - Servidors de correu intermitjos.
  - Client de correu utilitzat per l'enviament.
  - Dates d'enviament i recepció.

# Signatura i Xifratge amb OpenPGP

## OpenPGP: Estàndard de Codi Obert Basat en PGP

- **Descripció**: OpenPGP és un estàndard de codi obert per al xifratge i la signatura digital, basat en el mètode de xifratge Pretty Good Privacy (PGP).

## Sistema de Criptografia de Clau Pública

- Utilitza parelles de claus pública-privada per a les següents funcions:
  - **Clau Privada de l'Emissor**: Utilitzada per a la signatura de la informació.
  - **Clau Pública de l'Emissor**: Permet als destinataris comprovar la signatura.
  - **Clau Pública del Destinatari**: Utilitzada per a xifrar el correu abans d'enviar-lo.
  - **Clau Privada del Destinatari**: Utilitzada pel destinatari per desxifrar el correu rebut.

## Utilitats Principals d'OpenPGP

1. **Comprovació de l'Autenticitat i Integritat**:
   - Empra tècniques de xifratge per verificar qui ha enviat un missatge i que aquest no ha estat modificat.

2. **Xifratge del Contingut del Correu**:
   - Xifra tant el contingut del missatge com els arxius adjunts, garantint la confidencialitat.

## Exemple de Configuració i Ús

- **Configuració Inicial**:
  - Generació de la parella de claus pública i privada.
  - Distribució de la clau pública a destinataris o a un servidor de claus públiques.

- **Enviant un Correu Xifrat**:
  - Xifrar el missatge utilitzant la clau pública del destinatari.
  - Signar el missatge amb la pròpia clau privada.

- **Rebent i Verificant un Correu**:
  - Utilitzar la clau privada pròpia per desxifrar el missatge rebut.
  - Comprovar la signatura del missatge amb la clau pública de l'emissor.

## Conclusió

OpenPGP proporciona una solució eficaç per a la seguretat del correu electrònic, oferint eines per a la confidencialitat, l'autenticació i la integritat dels missatges.

# Arquitectura de Serveis Web

L'arquitectura dels serveis web implica la interacció entre tres parts principals:

## Proveïdor de Serveis Web (Service Provider)
- **Funció**: Ofereix i implementa el servei web.
- **WSDL**: Envía un fitxer WSDL (Web Services Description Language) al publicador amb la definició del servei web.

## Qui Publica (Service Broker)
- **Intermediari**: Actua com a intermediari entre el proveïdor i el sol·licitant del servei.
- **Registre de Serveis**: Manté un registre dels serveis disponibles.
  
## Qui Demana el Servei (Service Requester)
- **Descobriment del Servei**: Contacta amb el publicador per descobrir qui és el proveïdor utilitzant el protocol WSDL.
- **Solicitud del Servei**: Una vegada identificat el proveïdor, contacta amb ell mitjançant el protocol SOAP.


## Comunicació i Validació
- **Petició de Servei**: El proveïdor valida la petició de servei.
- **Resposta**: Envía les dades estructurades en format XML usant SOAP.
- **Validació per Part del Sol·licitant**: El sol·licitant valida el fitxer XML rebut fent servir un fitxer XSD (XML Schema Definition).

## Conclusió
Aquesta arquitectura facilita la comunicació i intercanvi de dades entre diferents parts, utilitzant estàndards i protocols com WSDL, SOAP, i XSD per a garantir una correcta definició, comunicació i validació dels serveis web.

# Arquitectura WSDL en Serveis Web

## WSDL (Web Services Definition Language)

### Descripció General
- **Natura**: Un llenguatge basat en XML.
- **Funció**: Descriu els serveis oferts per un servei web i com accedir-hi.

### Característiques del WSDL
- **Orientat a Màquina**: El format del WSDL està dissenyat per ser interpretat per una màquina, no per ser llegit directament per humans.
- **No Essencial per la Comunicació**: El fitxer WSDL no és estrictament necessari per a la comunicació, però és vital per entendre els serveis oferts si no es coneixen prèviament.

### Estructura del Fitxer WSDL
- **Element Arrel**: `<definitions>` és l'element arrel del document XML.
- **Ús de XSD**: Utilitza XML Schema Definition (XSD) per a definir els tipus de dades involucrats en el servei.
- **Contingut**: Inclou detalls com operacions, missatges i protocols suportats pel servei web.

## Conclusió
El WSDL és un component clau en l'arquitectura dels serveis web, proporcionant una descripció estàndard i completa dels serveis disponibles i com interactuar amb ells.

# Arquitectura SOAP en Serveis Web

## SOAP (Simple Object Access Protocol)

### Descripció General
- **Tipus**: Protocol basat en XML.
- **Funció**: Permet l'intercanvi d'informació entre aplicacions.

### Característiques del SOAP
- **Esquema XML (XSD)**: Disposa d'un esquema XML determinat.
- **Independència**: Independent del llenguatge de programació o plataforma.
- **Regles de Comunicació**: Defineix el format dels missatges, les regles d'intercanvi de missatges, gestió d'errors, i com interactuar amb altres protocols.

## Estructura del Missatge SOAP

### SOAP Envelope
- **Funció**: Element arrel que identifica el missatge com un missatge SOAP.

### SOAP Header
- **Contingut**: Informació sobre autenticació, codificació de dades, i instruccions sobre com processar el missatge.

### SOAP Body
- **Contingut**: La informació principal a ser intercanviada entre les aplicacions.
- **Basat en**: El seu format està basat en l'especificació WSDL del servei.

### SOAP Fault
- **Funció**: Conté informació sobre errors en cas que es produeixin.
- **Detalls**: Proporciona detalls específics sobre la naturalesa de qualsevol error ocorregut durant el processament del missatge.

## Conclusió
SOAP és un protocol estàndard per a l'intercanvi d'informació en l'arquitectura de serveis web, amb una estructura de missatge ben definida que facilita la comunicació i gestió d'errors entre aplicacions diferents.

# Atacs i Vulnerabilitats en Serveis Web

## Divulgació WSDL

Els serveis web s'utilitzen normalment en escenaris de transaccions
comercials entre empreses o backend. Només haurien de ser coneguts per
un grup de persones.
• Hi ha serveis web "ocults" que realitzen operacions crítiques. (pagaments,
processament de dades entre negocis, ...)
• Es poden produir atacs per tal de descobrir serveis web no públics
recuperant el fitxer WSDL.

### Descripció
- La divulgació WSDL ocorre quan els arxius WSDL d'un servei web estan massa exposats o accessibles públicament.

### Riscos
- Pot revelar informació detallada sobre l'estructura i funcionament dels serveis web.

### Contramesures
- Restringir l'accés als arxius WSDL.
- No exposar informació sensible a través del WSDL.

## Bomba XML

Document XML petit dissenyat per expandir-se a una mida enorme quan
sigui processat per un parser(analitzador sintàctic) XML desprotegit.
• S'usen crides recursives (permeses pel DTD (definició del tipus de
document)) per créixer de manera exponencial.
• L'atac produeix una DoS. (Es carrega 2³² A's a la memòria del servidor)
• ZERO= A, ONE= AA, TWO=AAAA, …, THIRTYTWO=A32

### Descripció
- Una bomba XML és un atac que utilitza documents XML maliciosament dissenyats per consumir recursos del sistema.

### Riscos
- Pot causar un esgotament de recursos i denegació de servei.

### Contramesures
- Limitar la mida i la complexitat dels documents XML processats.
- Utilitzar eines de processament XML que previnguin aquest tipus d'atac.

## Injecció XPath

XPath és un llenguatge usat per consultar certs parts del document XML,
semblant a l'SQL.
• En alguns casos, els paràmetres dintre el cos dels missatges SOAP, s'usen
directament com a input per la consulta XPath.
• Un atacant podria modificar la consulta XPath per obtenir tot el
document XML.

### Descripció
- Aquest atac s'aprofita de les vulnerabilitats en el codi que utilitza consultes XPath, inserint dades malicioses.

### Riscos
- Pot permetre als atacants manipular consultes i accedir a dades no autoritzades.

### Contramesures
- Validar i sanejar totes les entrades dels usuaris.
- Utilitzar declaracions preparades o APIs que protegeixen contra aquesta vulnerabilitat.

## Injecció XML

XPath és un llenguatge usat per consultar certs parts del document XML,
semblant a l'SQL.
• En alguns casos, els paràmetres dintre el cos dels missatges SOAP, s'usen
directament com a input per la consulta XPath.
• Un atacant podria modificar la consulta XPath per obtenir tot el
document XML.

### Descripció
- L'injecció XML es produeix quan un atacant pot inserir contingut XML maliciós en un sistema.

### Riscos
- Permet l'execució de comandes malicioses, accés a dades confidencials, i altres atacs.

### Contramesures
- Validar tot el contingut XML contra un esquema conegut i segur.
- Utilitzar llistes blanques per a elements i atributs permesos en documents XML.

## Conclusió

És vital per a les organitzacions implementar fortes mesures de seguretat per prevenir i mitigar aquests tipus d'atacs en serveis web, especialment en entorns que processen gran quantitat de dades a través de formats com XML i utilitzen tecnologies com WSDL i XPath.

# Servei de VoIP (Veu sobre IP)

## Descripció General

- **Definició**: VoIP (Veu sobre Protocol d'Internet) és una tecnologia que permet la transmissió de veu i altres serveis de telecomunicacions sobre xarxes IP.

## Avantatges i Inconvenients Comparats amb la Telefonia Convencional

### Avantatges
- **Cost Reduït**: Generalment ofereix un cost menor, especialment en trucades internacionals.
- **Flexibilitat i Portabilitat**: Permet als usuaris fer i rebre trucades des de qualsevol lloc amb accés a Internet.
- **Integració amb Altres Serveis**: Facilita la integració amb altres serveis basats en IP.

### Inconvenients
- **Dependència de la Connexió a Internet**: Requereix una connexió a Internet estable i de bona qualitat.
- **Problemes de Latència i Jitter**: Pot experimentar retards o variacions en la transmissió de veu.
- **Seguretat**: Pot ser més susceptible a atacs cibernètics.

## Elements Clau en VoIP

### Terminals
- Dispositius finals utilitzats per a la comunicació, com telèfons IP o softphones en ordinadors.

### Gateways
- Actuen com a ponts entre la xarxa de telefonia tradicional i la xarxa IP.

### Gatekeepers
- Gestiona la connexió i l'autorització d'accés en xarxes VoIP basades en H323.

## Protocols Importants

### RTP (Real-time Transport Protocol)
- Maneja la lliurament de dades en temps real, com ara l'àudio i vídeo.

### RTCP (Real-time Transport Control Protocol)
- Treballa conjuntament amb RTP per proporcionar informació de control i monitorització.

### H323
- Un dels primers protocols estàndards utilitzats en VoIP per a la comunicació multimèdia.

### SIP (Session Initiation Protocol)
- Protocol ampliament utilitzat per a la iniciació, modificació i finalització de sessions interactives de comunicació multimèdia.

## Tipus de Servidors en VoIP

- **Servidors de Proxy SIP**: Gestionen les trucades SIP.
- **Servidors de Registre**: Mantenen informació sobre els usuaris i els seus dispositius.
- **Servidors de Localització**: Ajuda a trobar la ubicació actual dels usuaris per a dirigir les trucades.
- **Servidors d'Autenticació**: Verifiquen la identitat dels usuaris abans d'establir les trucades.

# Vulnerabilitats i Atacs al Servei VoIP

## Accessos Desautoritzats i Fraus
- **Descripció**: Obtenció il·lícita d'accés a serveis VoIP per a ús personal o comercial.

## Vulnerabilitats de la Xarxa Subjacent
- **Descripció**: Debilitats en la xarxa sobre la qual opera el VoIP, que poden ser explotades per a atacs.

## Atacs de Denegació de Servei (DoS)
- **Descripció**: Atacs destinats a sobrecarregar el sistema VoIP, impedint el seu funcionament normal.

## Atacs als Dispositius
- **Descripció**: Compromís de telèfons IP i altres dispositius VoIP.

## Enumeració i Descobriment
- **Descripció**: Tècniques per descobrir usuaris, números de telèfon, o dispositius en una xarxa VoIP.

## Atacs a Nivell d'Aplicació
- **Descripció**: Explotació de vulnerabilitats específiques de les aplicacions VoIP.

## Autenticació en VoIP
- **Descripció**: Exploració de febleses en els mecanismes d'autenticació de VoIP.

## Manipulació de la Senyalització
- **Descripció**: Alteració de la senyalització per controlar o redirigir trucades.

## Suplantació d'Identitat
- **Descripció**: Impersonació d'altres usuaris o serveis en una xarxa VoIP.

## Desregistrar i Desconnectar Usuaris
- **Descripció**: Accions malicioses destinades a desregistrar o desconnectar usuaris del servei.

## Redirecció de Trucades
- **Descripció**: Canvi del destí de les trucades sense el consentiment de l'usuari.

## Manipulació de la Transmissió
- **Descripció**: Alteració de l'àudio o altres dades transmeses.

## Eavesdropping (Escoltar Converses)
- **Descripció**: Intercepció i escolta de converses privades.

## Inserció d'Àudio
- **Descripció**: Inserció d'àudio addicional en trucades.

## Fuzzing
- **Descripció**: Enviaments de dades aleatòries o malformades per provocar errors o fallades.

## Atacs DoS
- **Descripció**: Atacs destinats a interrompre el servei incapacitant el servidor o la xarxa.


# Assegurament del Servei VoIP

## Utilització de TLS (Transport Layer Security)

- **Propòsit**: Proporcionar una capa de seguretat addicional mitjançant l'encriptació de les comunicacions.
- **Aplicació**: Utilitzat per a xifrar el trànsit de senyalització en protocols com SIP.

## Implementació de VPNs (Xarxes Privades Virtuals)

- **Funció**: Establir canals segurs de comunicació a través d'Internet o altres xarxes públiques.
- **Benefici**: Aïlla el tràfic de VoIP, protegint-lo de l'intercepció o la manipulació en xarxes no segures.

## Protocol SRTP (Secure Real-time Transport Protocol)

- **Descripció**: Una extensió del RTP que proporciona xifratge, autenticació i integritat del missatge.
- **Ús**: Assegura que les dades de veu i vídeo transmeses siguin confidencials i no manipulades.

## Configuració de VLANs (Xarxes Locals Virtuals)

- **Objectiu**: Separar el tràfic de VoIP del tràfic de dades general de la xarxa.
- **Avantatge**: Redueix el risc d'atacs de xarxa i millora la qualitat del servei.

## Limitar l'Accés a la Xarxa VoIP

- **Mesures**: Restricció d'accés a la xarxa VoIP només als dispositius autoritzats.
- **Metodologia**: Utilització de llistes de control d'accés, autenticació fortificada i gestió de dispositius.

## Limitar el Volum de Dades

- **Tècnica**: Establir límits en la quantitat de dades que poden ser enviades o rebudes per la xarxa VoIP.
- **Propòsit**: Prevenir atac




  
