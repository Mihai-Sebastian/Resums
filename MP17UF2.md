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


  
