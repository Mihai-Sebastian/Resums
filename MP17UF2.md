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




