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




