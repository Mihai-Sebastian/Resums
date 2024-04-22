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

## 2.3. Perspectiva general, conceptes i administració del servidor Cyrus IMAP

### 2.3.0. Accés a l'interfície de comandes
- **Cyradm**: Utilitzat per gestionar el servidor Cyrus IMAP.
- **Com accedir**:
  ```bash
  # cyradm --user cyrus localhost
  Password:
  localhost>
  ```
## 2.3.1. Espai de noms de les bústies de correu

**Convenció de noms:** Utilitza la convenció netnews, sense distinció entre majúscules i minúscules, però mantenint el format original.

**Restriccions:**
- No començar o acabar amb un punt.
- No contenir dos punts seguits.

**Estructura de noms:**
Per exemple, `user.jvaras` per a l'usuari jvaras, que actua com la seva bústia d'entrada (inbox).

**Administració:**
Crear i esborrar usuaris implica gestionar els seus inboxes.
Si un usuari té un inbox, pot subscriure's a més bústies.
Esborrar l'inbox d'un usuari també esborra totes les seves bústies personals.

## 2.3.2. Llistes de control d'accés (ACL)

**Funció:** Controlar l'accés a cada bústia de correu individual.

**Estructura:**
Una ACL conté entrades que especifica l'usuari o grup d'usuaris amb permisos específics.
Permisos possibles inclouen: l (lookup), r (read), s (seen), w (write), i (insert), p (post), c (create), d (delete), a (administer).

**Administradors:**
Usuaris especificats com a administradors en `/etc/imapd.conf` tenen permisos `l` i `a` sobre totes les bústies.
Quan es crea una bústia, la seva ACL inicial és una còpia de la de la bústia pare.
L'ACL de l'inbox d'un nou usuari conté tots els permisos per a aquest usuari.

## Gestió de bústies

**Comandes cyradm:**
- Crear bústies: `cm user.nomusuari@domini`
- Llistar bústies: `lm *@domini`

## Administració de dominis virtuals

**Administradors de dominis:**
Especificats amb un identificador complet, e.g., `admin@domini.com`.
Té accés només a les bústies del seu domini.

**Administradors globals:**
Especificats sense qualificador de domini, accedeixen a totes les bústies del servidor.
Necessiten el `defaultdomain` especificat en `/etc/imapd.conf`.
Utilitzen noms de bústia qualificats fora del seu `defaultdomain`.
## 2.3.3. Quotes d'usuari en Cyrus IMAP

### Descripció General
- **Objectiu**: Limitar l'espai d'emmagatzematge que cada usuari o bústia pot utilitzar.
- **Càlcul de la Quota**: Es consideren únicament els bytes dels missatges segons la definició a RFC-822 en kilobytes. No s'inclou l'espai utilitzat per índexs de bústia ni caches.

### Funcionament de les Quotes
- **Quotes Arrel**: Les quotes es poden assignar a qualsevol nivell de la jerarquia de bústies, no necessàriament han de ser bústies.
- **Aplicació**: Una quota arrel afecta tota la bústia situada al mateix nivell i per sota d'aquesta, sempre que no estiguin sota una altra quota arrel.
- **Exemple de jerarquia**:
  - `user.jvaras` (Quota arrel)
  - `user.jvaras.lists` (Quota arrel)
  - `user.jvaras.work` (Quota arrel)
  - Subbústies com `user.jvaras.lists.bulmailing` sota la quota de `user.jvaras.lists`.

### Administració de les Quotes
- **Creació de Quota Arrel**: Utilitzar `setquota` des de `cyradm`.
- **Eliminació de Quota**: No es poden eliminar directament mitjançant comandes; cal esborrar els fitxers de configuració pertinents.

### Comportament de les Quotes en la Pràctica
- **Inserció de Missatges**: Per inserir un missatge en una bústia, l'espai disponible sota la quota arrel ha de ser suficient per no excedir la quota.
- **Entrega de Correu**: Si l'espai utilitzat no excedeix la quota, els missatges es poden entregar independentment de la seva mida, permetent excepcionalment que la quota sigui sobrepassada temporalment. Això dóna l'oportunitat a l'usuari de manejar la situació.

### Implicacions de la Quota Excedida
- **Errors d'Entrega**: Si una bústia està sobrepassada, l'enviament de correu nou fallarà amb un error temporal. El sistema d'enviament intentarà la entrega diverses vegades durant uns dies, donant temps a l'usuari de resoldre el problema abans de retornar el correu al remitent.

### Notes Addicionals
- **Consells per a Administradors**: Es recomana monitoritzar l'ús de les quotes i comunicar-se amb els usuaris quan s'acosten als seus límits per evitar interrupcions en la recepció de correu.

Amb aquesta configuració, Cyrus IMAP proporciona una gestió flexible i potent de l'espai d'emmagatzematge, permetent als administradors controlar i gestionar eficaçment l'ús dels recursos de correu electrònic.
## 2.3.4. Processos de recuperació de les bases de dades en Cyrus IMAP

### Reconstrucció dels directoris de bústies
- **Components d'un directori de bústies**:
  - **Fitxers de missatges**: Un per missatge, en format RFC 822, amb línies separades per CRLF.
  - **cyrus.header**: Conté un número màgic i informació variable sobre la bústia.
  - **cyrus.index**: Informació fixa sobre la bústia i els missatges.
  - **cyrus.cache**: Dades variables dels missatges.
  - **cyrus.seen**: Estat dels missatges llegits per l'usuari.

- **Ferramenta de reconstrucció**: `cyrreconstruct` (en Debian `cyrreconstruct`).
  - **Funció**: Recuperar fitxers corruptes, preservant els noms dels flags, estat dels flags i la data interna basada en fitxers de missatges existents.
  - **Nota**: No ajusta l'ús de la quota; després d'executar `cyrreconstruct`, s'ha d'executar `quota -f` per reajustar les quotes segons els fitxers de quota arrel.

### Reconstrucció de les quotes arrel
- **Ubicació**: Subdirectori `quota` dins el directori de configuració (`configdirectory`).
  - Conté un fitxer per cada quota arrel amb l'ús de la quota i els límits.
- **Ferramenta de recalcul de quota**: `quota -f`.
  - **Funció**: Recalcula l'ús de cada quota arrel. Per eliminar una quota arrel, esborra el fitxer de la quota i executa `quota -f`.

### El fitxer de bústies
- **Importància**: És el fitxer més crític, contenint una llista ordenada de totes les bústies, quotes arrel i ACLs.
- **Recuperació**: No hi ha eines per reconstruir un fitxer de bústies danyat; cal realitzar còpies de seguretat freqüents.

### Subscripcions
- **Ubicació**: Subdirectori `user` dins el directori de configuració.
  - Conté un fitxer `.sub` per usuari amb les seves subscripcions a bústies.
- **Recuperació de subscripcions**: Restaura els fitxers des de còpies de seguretat, ja que no hi ha eines de recuperació.

### Logging
- **Ubicació dels logs**: Subdirectori `log` dins el directori de configuració, amb logs per usuari.
- **Funcions del servidor IMAP**: Envia logs al syslog local amb diversos nivells de gravetat com CRIT, ERR, WARNING, NOTICE, i INFO.

### El directori proc
- **Funció**: Conté un fitxer per cada procés actiu, amb informació com el host del client, login de l'usuari, i bústia seleccionada.
- **Purga**: Els fitxers dins `proc` es purguen al reiniciar el servidor.

Aquesta secció ofereix una visió completa sobre els mecanismes de recuperació i manteniment de les bases de dades en el servidor Cyrus IMAP, destacant la importància de les pràctiques de backup regulars i la gestió adequada dels recursos del servidor.

## 2.4. Configuració de bústies de correu

L'administració de les bústies de correu es realitza mitjançant el programa cyradm. 

S'haurà d'utilitzar un dels administradors definits al fitxer `/etc/imapd.conf` per connectar-nos, fent el següent:

```bash
/usr/bin/cyradm --user cyrus localhost
```
El parell usuari/contrasenya s'establirà utilitzant la base de dades d'usuaris `/etc/sasldb2` mitjançant el programa `sasldbpasswd2`, com s'ha explicat anteriorment.

Es recomana utilitzar l'usuari cyrus com a administrador. Per tant, procedirem a donar-lo d'alta:

```bash
saslpasswd2 -c cyrus
```
En aquests moments, la nostra base de dades d'usuaris conté els usuaris jvaras i cyrus, com es pot veure executant:

```bash
sasldblistusers2
```
- jvaras@servidor-primari: userPassword
- cyrus@servidor-primari: userPassword
- jvaras@informaticaASIX2.com: userPassword
Ara ja es pot accedir a l'administració de les bústies de Cyrus mitjançant la següent comanda:

```bash
/usr/bin/cyradm --user cyrus localhost
```
Un cop dins, la comanda `help` ens mostrarà una descripció de les comandes disponibles i els seus alies. D'entre totes, els d'ús més freqüent són els següents:

| Comanda       | Àlies | Funció                          | Sintaxi                           | Exemples               |
|---------------|-------|---------------------------------|-----------------------------------|------------------------|
| createmailbox | cm    | Crear bústies de correu         | cm <bústia>                      | cm user.jvaras         |
| deletemailbox | dm    | Esborrar bústies de correu      | dm <bústia>                      | dm user.jvaras         |
| listacl       | lam   | Llistar les ACL d'una bústia   | lam <bústia>                     | lam user.jvaras        |
| setacl        | sam   | Establir les ACL en una bústia | sam <bústia> <usuari> <permisos> | sam user.jvaras jvaras lrswipcda |
| deleteacl     | dam   | Esborrar les ACL d'una bústia  | dam <bústia> <usuari>            | dam user.jvaras jvaras |

Notes:

- La paraula clau `all` agrupa tots els permisos.
- Per assignar permisos a un grup UNIX s'utilitza la forma `group:nom_grup`.
- Un grup UNIX ha d'existir al fitxer `/etc/group`. Els usuaris afegits a aquest grup manualment seran bústies de correu creades amb el programa cyradm, no usuaris de sistema (encara que pot existir una correspondència, però sense cap relació).
- Encara que l'usuari cyrus tingui permisos implícits d'administració sobre totes les bústies, és necessari fer-los explícits per a executar algunes comandes sobre elles (per exemple, per a esborrar-les). Una comanda de l'estil `sam user.bústia cyrus all` solucionaria el problema, ja que s'heretarien els permisos a les subbústies.

En aquest punt, podem crear una bústia qualsevol amb propòsits de prova i establir els permisos de la següent forma:

```bash
cyradm --user cyrus localhost
```
Password:
* localhost> cm user.jvaras
* localhost> lam user.jvaras
* jvaras lrswipcda

En aquest moment hauríem de ser capaços de donar d'alta un compte de correu, utilitzant el protocol IMAP en el nostre client de correu favorit i connectant-nos al servidor utilitzant l'usuari definit amb `saslpasswd2`, a la bústia del mateix nom creada amb `cyradm`.

De la mateixa forma, també podem utilitzar l'eina `imtest` (`/usr/bin/imtest`), inclosa en el paquet `cyrus-clients-2.4`, per a comprovar el seu funcionament correcte. En el següent exemple s'utilitza el mecanisme més bàsic d'autenticació, que és `login`.
```
$ imtest -a jvaras -w <contrasenya> -m login localhost
S: * OK servidor Cyrus IMAP4 v2.1.16-IPv6-Debian-2.1.16-6 server ready
C: C01 CAPABILITY
S: * CAPABILITY IMAP4 IMAP4rev1 ACL QUOTA LITERAL+ MAILBOX-REFERRALS
NAMESPACE UIDPLUS ID NO_ATOMIC_RENAME UNSELECT CHILDREN MULTIAPPEND
SORT THREAD=ORDEREDSUBJECT THREAD=REFERENCES IDLE AUTH=NTLM
AUTH=DIGEST-MD5 AUTH=CRAM-MD5 LISTEXT LIST-SUBSCRIBED ANNOTATEMORE
S: C01 OK Completed
C: L01 LOGIN jvaras {8}
S: + go ahead
C: <omitted>
S: L01 OK User logged in
Authenticated.
Security strength factor: 0
Polsant Ctrl+C abandonarem el programa de proves:
C: Q01 LOGOUT
Connection closed.
```


