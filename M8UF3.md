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

## 1.6. Sieve
- **Descripció**: Llenguatge de creació de filtres de correu electrònic al moment de l'entrega final, operatiu al costat del servidor.
- **Independència**: No està vinculat a cap sistema operatiu o servidor de correu específic.
- **Especificació**: Utilitza l'especificació de missatges del RFC 822.
- **Limitacions**: Prohibit definir bucles, funcions o variables per garantir la creació de sistemes de filtratge segurs.
- **Ús**: Al final de l'entrega, pot ser utilitzat en diversos punts finals d'entrega del sistema de correu.

## 1.7. Amavisd-new
- **Descripció**: Interface d'alt rendiment entre el MTA i filtres de continguts com antivirus o Mail::SpamAssassin.
- **Llenguatge**: Escrit en Perl, assegura fiabilitat i facilitat de manteniment.
- **Comunicació**: Via (E)SMTP o LMTP, o amb altres programes.
- **Característiques**: Ofereix un servidor SMTP que compleix amb RFC 2821 i un servidor LMTP que compleix amb RFC 2033.

## 1.8. SpamAssassin
- **Funció**: Filtre de correu que busca identificar spam mitjançant anàlisi de text i llistes negres en temps real.
- **Eficàcia**: Normalment identifica entre un 95% i 99% de l'spam.
- **Suport**: Inclou suport per a informar missatges d'spam a bases de dades com Vipul's Razor.

## 1.9. Clam Antivirus (ClamAV)
- **Descripció**: Eina antivirus GPL per a UNIX, especialitzada en la integració amb servidors de correu.
- **Característiques**: Servei multithread, analitzador de línia de comandes, actualització automàtica via Internet.
- **Detalls addicionals**: Suporta arxius comprimits i formats de correu específics, a més de mantenir una base de dades actualitzada.

## 1.10. Mailman
- **Propòsit**: Software lliure per a la gestió de llistes de distribució i correus electrònics.
- **Integració**: Completament integrat amb la web, permet a usuaris i propietaris gestionar fàcilment les llistes.
- **Funcionalitats**: Suporta creació d'arxius de correu, processament automàtic de correu rebutjat, filtres de spam, etc.

## 1.11. Squirrelmail
- **Descripció**: Client de correu per web basat en PHP 4, compatible amb estàndards.
- **Compatibilitat**: Genera pàgines en HTML 4.0 per a màxima compatibilitat entre navegadors.
- **Funcionalitats**: Suport de MIME, gestió de carpetes, agendes de contactes.
- **Avelsieve**: Plugin de SquirrelMail que permet la creació de scripts Sieve en servidors Cyrus IMAP.

# Instal·lació i configuració de Cyrus IMAP i SASL

## 2.1. SASL. Creació d'usuaris

### Instal·lació de Cyrus en Debian
- **Paquets necessaris**:
  - Per Cyrus IMAP: `cyrus-admin-2.4`, `cyrus-common-2.4`, `cyrus-doc-2.4`, `cyrus-imapd-2.4`
  - Per Cyrus SASL: `libsasl2-2`, `sasl2-bin`, `libsasl2-modules`
- **Comanda d'instal·lació**:
  - `apt-get install libsasl2-2 sasl2-bin libsasl2-modules`

### Configuració de SASL
- **Edició del fitxer /etc/default/saslauthd**:
- Modificar `MECHANISMS="sasldb"`
- Activar el servei amb `START=yes`
- **Reinici del servei**:
 - `/etc/init.d/saslauthd restart`
- **Consideracions de seguretat**: Utilitzar `/dev/random` pot causar bloquejos en màquines amb alta càrrega. Considerar la instal·lació d'una targeta millor si és necessari.

### Base de dades d'usuaris
- **Ubicació**: `/etc/sasldb2`, propietat de l'usuari root i grup sasl.
- **Administració d'usuaris**:
- **Llistar usuaris existents**:
  ```
  # sasldblistusers2
  ```
- **Afegir un nou usuari**:
  ```
  # saslpasswd2 -c [nom_usuari]
  # Exemple: saslpasswd2 -c jvaras
  ```
- **Eliminar un usuari**:
  ```
  # saslpasswd2 -d [nom_usuari]
  # Exemple: saslpasswd2 -d jvaras
  ```
- **Afegir un usuari amb domini específic**:
  ```
  # saslpasswd2 -c [nom_usuari] -u [domini]
  # Exemple: saslpasswd2 -c jvaras -u informaticaASIX2.com
  ```

### Notes addicionals
- **Mètodes d'autenticació suportats**: Actualment, el servei només suporta autenticació PLAIN. Per a altres mètodes com CRAM-MD5 o DIGEST-MD5, s'ha d'utilitzar directament la llibreria `libsasl2`.
- **Configuració per a l'ús de mòduls d'autenticació**: Configurar `pwcheck_method=saslauthd` i `auxprop_plugin=sasldb` en cada programa que utilitza la llibreria.
- **Creació d'usuaris sense contrasenya**: L'opció `-n` permet crear usuaris sense contrasenya de text pla, encara que es recomana no usar aquesta opció per motius de seguretat.

## 2.2. Cyrus IMAP
- **Nota**: És important verificar que els paquets no estiguin ja instal·lats en el sistema abans de procedir amb la instal·lació.

### Configuració inicial
- **Instal·lació opcional**: El paquet `cyrus-clients-2.4` és opcional i proporciona l'eina `imtest`, útil per comprovar el funcionament del servidor.
- **Creació de directoris**: S'estableix una jerarquia de directoris a `/var/spool/cyrus/mail` per emmagatzemar les bústies de correu, amb propietat de l'usuari `cyrus` i grup `mail`.

### Fitxers de configuració
1. **/etc/cyrus.conf**: Determina els serveis que s'executaran al iniciar el sistema Cyrus.
2. **/etc/imapd.conf**: Especifica els paràmetres de configuració del servei IMAP de Cyrus.

### Consideracions addicionals
- **Dependència de Postfix**: La instal·lació de Cyrus requereix el paquet `postfix`. Durant la instal·lació de Postfix, seleccionar l'opció "Sense configurar" si no es desitja configurar-lo immediatament.
- **Documentació**: Es recomana llegir la documentació a `/usr/share/doc/cyrus-doc-2.4`, especialment els fitxers `README.Debian.gz`, `README.Debian.simpleinstall.gz`, i `README.postfix.gz` per entendre millor la configuració de Cyrus IMAP i Postfix.

### Permisos i membresia de grups
- **Permisos sobre `/etc/sasldb2`**: Assegurar que el grup `sasl` té permisos de lectura sobre la base de dades d'usuaris.
- **Membresia de l'usuari `cyrus`**: Comprovar que l'usuari `cyrus` pertany al grup `sasl`, això és generalment configurat automàticament pels scripts de `cyrus-common-2.4`, però és recomanable verificar-ho.

## 2.2.1. El fitxer /etc/cyrus.conf

### Descripció de les Seccions
El fitxer de configuració `/etc/cyrus.conf` està estructurat en tres seccions principals:

1. **START**:
   - Funció: Llista scripts que s'executen abans d'arrancar els serveis principals.
   - Ús habitual: Inicialització de bases de dades i llançament de serveis de llarga durada.

2. **SERVICES**:
   - Descripció: És el nucli del fitxer, especifica els processos que s'executaran per gestionar les connexions dels clients a certs sockets, tant TCP com UNIX.

3. **EVENTS**:
   - Funció: Enumera processos que s'executaran a intervals específics, similar a les funcions del cron.
   - Ús comú: Realització de tasques de neteja i manteniment programades.

### Configuració Estàndard i Personalització
- Es recomana realitzar canvis mínims sobre la configuració predeterminada proporcionada per Debian:
  - Desactivar el servei POP3 comentant la línia corresponent.
  - No modificar la configuració per a IMAP sobre SSL si no s'utilitza actualment.

### Exemple de Configuració
```cyrus
START {
    recover cmd="/usr/sbin/ctl_cyrusdb -r"
    delprune cmd="/usr/sbin/ctl_deliver -E 3"
    tlsprune cmd="/usr/sbin/tls_prune"
}
SERVICES {
    imap cmd="imapd -U 30" listen="imap" prefork=0 maxchild=100
    lmtpunix cmd="lmtpd" listen="/var/run/cyrus/socket/lmtp" prefork=0 maxchild=20
    sieve cmd="timsieved" listen="localhost:sieve" prefork=0 maxchild=100
    notify cmd="notifyd" listen="/var/run/cyrus/socket/notify" proto="udp" prefork=1
    nntp cmd="nntpd -U 30" listen="nntp" prefork=0 maxchild=100
}
EVENTS {
    checkpoint cmd="/usr/sbin/ctl_cyrusdb -c" period=30
    delprune cmd="/usr/sbin/ctl_deliver -E 3" at=0401
    tlsprune cmd="/usr/sbin/tls_prune" at=0401
}
 ```
### Consideracions sobre Sockets
#### Selecció de Sockets:
- **En entorns on tots els serveis s'executen en la mateixa màquina, es recomana utilitzar sockets UNIX per un millor rendiment i simplicitat.
- **Si els serveis com Postfix i Cyrus IMAP operen en màquines separades, caldria utilitzar sockets TCP.

  ## 2.2.2. El fitxer /etc/imapd.conf

### Descripció General
- **Funció**: Fitxer de configuració principal per al servidor Cyrus IMAP.
- **Format**: Cada línia té el format "opció: valor". Línies en blanc o que comencen amb `#` són ignorades.

### Opcions de Configuració Importants
- **`altnamespace`**:
  - Valor per defecte: `no`
  - Comportament: Les subcarpetes d'usuari es creen sota `inbox`. Canviar a `yes` per crear-les a la mateixa altura que `inbox`.

- **`lmtp_downcase_rcpt`**:
  - Valor per defecte: `no` (comentada)
  - Comportament: Converteix el nom d'usuari a minúscules en LMTP, recomanat per uniformitat.

- **`admins`**:
  - Usuari `cyrus` típicament té permisos d'administrador sobre totes les bústies.
  - Configuració: Especificar en `/etc/sasldb2` amb `saslpasswd2 -c cyrus`.

- **`allowanonymouslogin`**:
  - Valor per defecte: `no`
  - Comportament: Permet accés anònim, no recomanat llevat que sigui necessari per funcions específiques.

- **`umask`**:
  - Valor per defecte: `077`
  - Comportament: Configurar a `037` per permetre lectura pel grup, beneficiós per integració amb altres aplicacions.

- **`allowplaintext`**:
  - Valor per defecte: `yes`
  - Comportament: Permet l'autenticació plain text; mantenir fins que el sistema estigui plenament configurat.

- **`sasl_mech_list`**:
  - Llista dels mecanismes d'autenticació suportats, útil per a la seguretat del servidor.

- **`sasl_minimum_layer`**:
  - Valor inicial recomanat: `0`
  - Comportament: Defineix el mínim nivell de seguretat; augmentar una vegada tot estigui funcionant correctament.

- **`sasl_auxprop_plugin`**:
  - Especificar plugins d'autenticació, com `sasldb` si s'utilitza `sasl_pwcheck_method: auxprop`.

### Configuració dels Sockets
- **`lmtpsocket`**, **`idlesocket`**, **`notifysocket`**:
  - Rutes pels sockets UNIX utilitzats per Cyrus. Comprovar que coincideixen amb els especificats en `/etc/cyrus.conf`.

### Reinici o Recàrrega del Servidor
- Després de qualsevol canvi al fitxer, és necessari fer que el servidor recarregui la configuració:
  ```bash
  /etc/init.d/cyrus-imapd restart
  # o bé
  /etc/init.d/cyrus-imapd reload
### Resum de la Configuració Suggestida
  configdirectory: /var/lib/cyrus
  
  defaultpartition: default
  
  partition-default: /var/spool/cyrus/mail
  
  altnamespace: no
  
  lmtp_downcase_rcpt: yes
  
  admins: cyrus
  
  allowanonymouslogin: no
  
  umask: 037
  
  allowplaintext: yes
  
  sasl_mech_list: PLAIN
  
  sasl_minimum_layer: 0
  
  sasl_pwcheck_method: saslauthd
  
  sasl_auxprop_plugin: sasldb
  
  lmtpsocket: /var/run/cyrus/socket/lmtp
  
  idlesocket: /var/run/cyrus/socket/idle
  
  notifysocket: /var/run/cyrus/socket/notify


