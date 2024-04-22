# Conceptes

## 1.1. Postfix
- **Definició**: Postfix és un MTA (Mail Transportation Agent - Agent de Transport de Correu) dissenyat per ser ràpid, fàcil d'administrar i segur.
- **Compatibilitat**: Manté estil de Sendmail externament, però internament és completament diferent.
- **Funcionament**: Compost per diversos programes petits, cadascun amb funcions especialitzades, utilitzat per enrutament i enviament de correu electrònic.
- **Distribucions**: És l'agent de transport per defecte en moltes distribucions de Linux i les últimes versions de Mac OS.
- **Més informació**: Disponible en la documentació online de la seva website.

## 1.2. TLS
- **Context**: Originalment les comunicacions a Internet són insegures sense xifrat ni autenticació fiable.
- **Evolució**: Netscape va introduir SSL (Secure Sockets Layer), evolucionant cap a TLS (Transportation Layer Security).
- **Funcions**: TLS ofereix xifrat de comunicacions i autenticació forta.
- **Implementació en Postfix**: Utilitza OpenSSL per gestionar el protocol TLS.
- **Recursos**: Documentació disponible en la website d'OpenSSL.

## 1.3. Cyrus IMAP
- **Desenvolupador**: Andrew Systems Group de la Carnegie Mellon University.
- **Funcionalitat**: Protocol de xarxa IMAP per accedir a correus electrònics des de qualsevol lloc amb Internet.
- **Diferències amb POP**: Permet gestió de carpetes del servidor i accés remot sense necessitat de descàrrega de missatges.
- **Almacenament**: Empra fitxers separats per cada missatge, augmentant la fiabilitat.
- **Administració**: Realitzada via comandes d'IMAP o interfaces web.
- **Autenticació**: Utilitza la llibreria SASL per a autenticació de tres capes.

## 1.4. Cyrus SASL
- **Sigles**: SASL significa Simple Authentication and Security Layer.
- **Propòsit**: Afegeix suport d'autenticació a protocols basats en la connexió.
- **Funcionament**: Gestiona les peticions d'autenticació dels clients i pot negociar la protecció de les interaccions.
- **Seguretat**: Utilitza OpenSSL per a xifrar les dades.
- **Més informació**: Disponible a la pàgina web de Cyrus SASL.

## 1.5. LMTP
- **Context**: SMTP i ESMTP són protocols per a la transferència de correu.
- **Diferència**: LMTP (Local Mail Transfer Protocol) és una alternativa que no gestiona cues d'enviament de correu.
- **Funcionalitat**: Basat en la sintaxi i semàntica de ESMTP, permet utilitzar les extensions definides per a ESMTP.
- **Advertència**: No s'ha d'utilitzar amb el port 25.

