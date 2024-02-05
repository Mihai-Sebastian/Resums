# PDF1
# Resum del Servei Web

## Descripció General
- El **servei web** permet la publicació de pàgines web amb continguts atractius, accessibles des d’arreu del món.
- Aquests documents, majoritàriament en format HTML, inclouen també imatges, programes cgi d’entorn web, entre d’altres.

## Requisits del Servidor Web
- Ha d’**allotjar fitxers HTML, imatges**, etc., en directoris específics.
- Capaç d’entendre i gestionar diversos tipus d’extensió d’arxius.
- Ha d’incorporar aplicacions de mercat com **Java, JavaScript, Oracle, XML, Flash, vídeo MPEG**, i adaptar-se ràpidament a noves aplicacions.
- **Seguretat**: Implementació de protocols segurs (exemple: https amb SSL) per a la protecció de la informació.

## Apache: Una Aplicació-Base per al Servidor Web
- **Apache** es destaca com una aplicació base ideal per al servidor web.
- Avantatges:
  - **Fiabilitat, potència, flexibilitat, adaptabilitat, eficiència**, i ràpida resposta.
  - Constant evolució per adaptar-se al món d’Internet.
  - És un **programa de lliure distribució**.


# Requeriments per a un Servei Web amb Apache

## Requeriments a Nivell d'Equip Servidor

- **Espai de Disc**: Necessari per emmagatzemar l'estructura de la web.
- **Connexió de Xarxa**: Ha de ser bona, encara que el consum de CPU és baix.
- **Consum de RAM**: Pot ser puntual, augmentant en moments de descàrrega d'arxius via http.
- **Processos d'Apache**: Inicia amb vuit processos "httpd" i s'adapta segons la demanda.
- **Recursos Mínims**: Servidors amb recursos limitats poden experimentar lentitud en aplicacions cgi o connexions https.
- **Uso de la Web**: Per pàgines estàtiques, preocupar-se pel disc dur. Per aplicacions dinàmiques, es requereix més CPU i RAM.

## Requeriments a Nivell dels Clients

- **Navegador Web**: Essencial per accedir al contingut del servidor.
- **Publicació de Continguts**: Necessita un editor HTML i accés al servidor via FTP, utilitzant eines com Filezilla.

## Requeriments a Nivell de Xarxa

- **Connexió de 10Mbits**: Suficient per un rendiment acceptable en usos esporàdics.
- **Millora a 100 Mbit/s**: Recomanat per descàrregues freqüents de fitxers grans, per millorar la velocitat de descàrrega i el temps de resposta.



  # Descripció de l'Aplicació "Apache"

## Introducció

- **Popularitat**: Apache és un dels servidors web més utilitzats a nivell mundial, amb una quota de mercat propera al 65%.
- **Orígens**: Va començar com un conjunt de "parxes" (d'aquí el nom, A PAtCHy sErver) per al servidor WWW de NCSA a principis de 1995.
- **Objectius**: Es va proposar ser el servidor web més ràpid, eficient i funcional sota l'enfocament de lliure distribució.
- **Llicència**: Regit per la GNU General Public License, evidenciant el seu compromís amb el programari de lliure distribució.
- **Comunitat**: Desenvolupat per un gran equip de voluntaris a nivell mundial, superant servidors web de grans companyies com Microsoft i Netscape.
- **Suport d'IBM**: La companyia IBM va ser atreta pel projecte, oferint suport tant a nivell de suport com de desenvolupament.



# Característiques Generals d'Apache

- **Multiplataforma**: Funciona en diversos sistemes operatius.
- **Protocols HTTP Actualitzats**: S'adapta als canvis i necessitats actuals del protocol HTTP.
- **Modularitat**: Permet la personalització i l'adaptació a diferents entorns i necessitats mitjançant l'ús de mòduls.
- **Desenvolupament Obert**: Beneficia de la contribució comunitària en forma de noves idees, registres d'errors i solucions.
- **Extensibilitat**: Capacitat d'incorporar extensions com PHP per augmentar les funcionalitats.

# El Protocol HTTP

- **Bàsics del Protocol**: Facilita la comunicació entre clients i servidors a través de la connexió TCP, amb peticions i respostes.
- **Operacions HTTP 1.0**:
  - `GET`: Demanar una pàgina.
  - `HEAD`: Demanar la capçalera d'una pàgina.
  - `POST`: Enviar dades a una URL.
- **Estructura de la Petició**:
  - Mètode d’invocació.
  - Versió del protocol.
  - Missatge amb paràmetres de la petició.
  - Informació del client.
  - Cos opcional amb més dades.
- **Resposta del Servidor**:
  - Línia d'estat amb versió del protocol, èxit o fracàs, i informació rellevant.
- **Descripció HTTP**: Un protocol de nivell d'aplicació per a sistemes distribuïts, genèric i orientat a objectes, adaptable a diverses aplicacions.
- **Negociació de Tipus de Dades**: Permet la independència dels tipus de dades utilitzats.
- **Evolució**: Adaptació a les necessitats d'escalabilitat i rendiment, evolucionant des de la versió 1.0.



# Versions del Protocol HTTP

## Versió 1.0

- **Connexions TCP**: Lentes d'establir degut a la connexió en tres passos i ajust de finestres de recepció.
- **Establiment de Connexions**: Necessitat d'establir una nova connexió per cada pàgina i imatge, alentint significativament la transmissió de dades.
- **Rendiment**: Per a transmetre 1Kbyte de dades, podria tardar uns 500 ms.

## Versió 1.1

- **Connexions Persistents**: No es tanquen després de l’enviament de cada part d’un document, reduint la sobrecàrrega per l’establiment de connexions TCP.
- **Peticions Simultànies**: Permet diverses peticions d’un mateix client en una sola connexió sense esperar la resposta per a cada una.
- **Negociació de Contingut**: Assignació de diferents valors a les característiques de la comunicació.
- **Nous Mètodes**:
  - `DELETE`: Esborrar un recurs del servidor.
  - `TRACE`: Veure què rep el servidor.
  - `PUT`: Enviar dades.
  - `PATCH`: Aplicar correccions.
  - `COPY`: Copiar recursos.
  - `MOVE`: Moure recursos.
  - `LINK`: Establir enllaços.
  - `OPTIONS`: Obtenir característiques del servidor.
  - `WRAPPED`: Unir peticions amb seguretat.
- **Mètode d'Autenticació Encriptat**: Les claus d'accés van encriptades per a la seguretat, fidelitat, i confidencialitat de les dades.




# HTTP Versió 1.2 i Futur del Protocol

## Versió 1.2

- La versió HTTP 1.2 actua com a pont cap a l'HTTP-Next Generation (HTTP-NG), amb l'objectiu de cobrir noves funcionalitats com el comerç electrònic.

## Criteris de Disseny d'HTTP-NG

- **Simplicitat**: Mantenir la facilitat d'implementació com en HTTP/1.0.
- **Rendiment**: Eficiència en la transmissió d'objectes en xarxes de comunicació.
- **Asincronia**: Capacitat per fer peticions en paral·lel a través d'una única connexió.
- **Seguretat**: Encriptació d'objectes transmesos sense imposar polítiques de seguretat específiques.
- **Autenticació**: Suport per a l'autenticació bilateral i per a la realització de pagaments en línia.
- **Servidors Intermediaris**: Suport per a la comunicació entre servidors, manteniment de caches, mirrors i proxys.
- **Visualització Obligatòria de Dades**: Capacitat per exigir la visualització de dades específiques (autor, copyright, llicència).
- **Informació de Registre**: Possibilitat d'enviar informació de registre entre diferents servidors.
- **Requeriments de Xarxa**: Independència de la capa de transport, amb especial eficàcia sobre TCP.

## Suport en Apache

- Els avenços d'HTTP ja estan suportats en Apache 1.2.
- Per a futures versions (com la 3.0), l'objectiu serà el suport complet a HTTP-NG, implementant-lo de manera automàtica per consolidar i augmentar la seva quota de mercat.

# Projectes Associats a Apache

Apache s'enriqueix amb diversos projectes associats per augmentar la seva funcionalitat. Destaquem dos principals:

## PHP

- **Ús**: Extremadament útil per als desenvolupadors d'aplicacions web.
- **Característiques**:
  - Fàcil d'utilitzar i molt potent.
  - Pot substituir la programació CGI.
  - Ofereix una llibreria de funcions per a l'accés directe a les principals bases de dades (Informix, Oracle, MySQL, PostgreSQL, Adabas...).

## SSL (Secure Socket Layer)

- **Enfocament**: Orientat a la privacitat de les comunicacions, especialment per al comerç electrònic.
- **Característiques**:
  - Inclou seguretat mitjançant encriptació i autenticació.
  - Els mòduls i les llibreries d'encriptació (com RSA de 128 bits, DES, MD5) són de lliure distribució.

## Pàgina Web Principal del Projecte Apache

- **Apache Software Foundation**: El projecte httpd Apache és iniciat i suportat per l'Apache Software Foundation.
- **URL**: [http://httpd.apache.org/](http://httpd.apache.org/)

# Instal·lació d'Apache

## Opcions d'Instal·lació

- **Descàrrega Directa**: Baixar la versió més actual en format `*.tar.gz` des de la web d'Apache i seguir els passos d'instal·lació manual (`./configure`, `make`, `make install`).
- **Gestor de Paquets**: Utilitzar `apt-get install apache2` per a instal·lar des del gestor de paquets en Ubuntu.

## Ubicacions d'Instal·lació

- Executables: `/usr/sbin`
- Fitxer `httpd.pid`: `/var/run`
- Logs: `/var/log/httpd` o `/var/log/apache2`
- Arrel de l'estructura web: `/usr/local/apache2/htdocs` o `/var/www/html`
- Mapejat inicial `cgi-bin`: `/usr/local/apache2/cgi-bin` o `/usr/lib/cgi-bin`
- Configuració: `/usr/local/apache2/conf` o `/etc/apache2/`
- Scripts d'arrencada: `/etc/rc?.d/`
- Documentació en HTML: `/usr/local/apache2/manual` o `/usr/share/doc/apache2`

# Configuració Bàsica

- L'aplicació hauria d'arrencar amb la configuració per defecte, reconeixent el nom del host i donant servei pel port estàndard.

# Arrencada del Servei

- Assegurar que el servei `apache` s'inicia en l'arrencada del sistema i s'atura correctament en el seu apagament.
- Comprovar si el port 80 està en ús amb `netstat -tulpn | grep :80` per evitar conflictes amb altres versions d'Apache.
- Per a versions manualment instal·lades:
  - Arrencada: `# /usr/local/apache2/bin/httpd -f /usr/local/apache2/conf/httpd.conf`
  - Aturada: `# pkill httpd`
- Per a versions instal·lades via gestor de paquets:
  - Arrencada: `# /etc/init.d/apache2 start`
  - Aturada: `# /etc/init.d/apache2 stop`

# PDF2
# Estructura de Carpetes i Fitxers de Configuració d'Apache

## Fitxers de Configuració Principals

- **apache2.conf**: Fitxer principal de configuració d'Apache. Configura els valors per defecte.
- **ports.conf**: Especifica els ports per als "virtual hosts". Important per configurar servidors HTTPS.
- **envvars**: Defineix les variables d'entorn necessàries per al funcionament d'Apache.

## Subcarpetes Importants

- **sites-available**: Conté els fitxers de configuració dels "virtual hosts". Inclou un de tipus HTTP (`000-default.conf`) i un altre de tipus HTTPS (`default-ssl.conf`).
- **sites-enabled**: Conté enllaços als fitxers de "sites-available" activats.
- **mods-available**: Ubica els fitxers de mòduls disponibles. Cada mòdul té un arxiu `.load` (imprescindible) i un `.conf` (opcional).
- **mods-enabled**: Conté enllaços als fitxers de "mods-available" activats.
- **conf-available**: Conté trossos de configuració específics com si fossin part de `apache2.conf`.
- **conf-enabled**: Conté enllaços als fitxers de "conf-available" activats.

## Nota sobre els Virtual Hosts

- Els fitxers .conf dels "virtual hosts" són llegits en ordre alfabètic, d'aquí que `000-default.conf` sigui el primer en ser processat.

## Gestió de Configuració

- Per activar o desactivar "virtual hosts" o mòduls, s'utilitza l'enllaçat simbòlic entre les carpetes "available" i "enabled" amb comandes `ln -s` per crear o esborrar enllaços.

# Activació i Desactivació de Mòduls i "Virtual Hosts" en Apache

Per gestionar els mòduls i els "virtual hosts" sense necessitat d'utilitzar manualment `ln -s`, Apache ofereix un conjunt de comandes senzilles:

- **Activar Mòdul**: `a2enmod nomModul`
- **Desactivar Mòdul**: `a2dismod nomModul`
- **Activar Virtual Host**: `a2ensite nomarxiuVH`
- **Desactivar Virtual Host**: `a2dissite nomarxiuVH`

Cal reiniciar o recarregar el servidor per aplicar els canvis amb:
- `# /etc/init.d/apache2 restart` o
- Reiniciar manualment amb `# pkill httpd` seguit de `# ./usr/local/apache2/bin/httpd –f /usr/local/apache2/conf/httpd.conf` per a la versió compilada.

# Configuració General del Servidor Web Apache

- **Fitxer de Configuració**: `httpd.conf` per Apache compilat (`/usr/local/apache2/conf/`) o `apache2.conf` per Apache instal·lat via gestor de programari (`/etc/apache2/`).
- Configuracions específiques es poden trobar dins la carpeta `conf-available`.
- Qualsevol canvi en la configuració requereix reiniciar el servei per a la seva activació.


# Personalització del Servei Apache

## Usuari d'Execució d'Apache

- **Recomanació de Seguretat**: No executar Apache com a `root` per evitar riscos de seguretat.
- **Usuari Predeterminat**: Utilitzar `nobody` o un usuari creat específicament (normalment `www-data` en distribucions Linux modernes).
- **Configuració**: Especificar l'usuari amb el paràmetre `User nobody`. Tot i això, es recomana utilitzar les variables d'entorn `APACHE_RUN_USER` i `APACHE_RUN_GROUP` definides a `envvars`.
- **Permisos Importants**: L'usuari d'Apache ha de poder llegir els directoris publicats i ser el propietari dels directoris de logs.

## Selecció del Port per Atendre Peticions HTTP

- **Port Estàndard**: Per defecte, Apache escolta en el port HTTP estàndard (80).
- **Canvi de Port**: Es pot canviar el port d'escolta amb el paràmetre `Listen 8008` per, per exemple, evitar conflictes amb altres serveis o per raons de seguretat.
- **Ports d'Usuari**: Ports superiors a 1024 poden ser utilitzats per qualsevol usuari, permetent la configuració de servidors personals Apache sense necessitat de permisos `root`.

# Mapejats per Servir HTML Bàsic amb Apache

## 'Arrel' o Directori Principal del Servidor Web

- **Ubicació per Defecte**: `/usr/local/apache2/htdocs` o `/var/www/html`. Qualsevol directori afegit aquí serà accessible a través de la URL principal.
- **Exemple**: Crear un directori "yoda" permet accedir a `http://www.informaticaASIX2.com/yoda`.
- **Pàgina per Defecte**: `index.html` o `index.htm`, buscades en aquest ordre per a qualsevol URL sense fitxer .htm específic.
- **Permisos de Directori**: Els directoris han de tenir permissos d'execució per a tothom (755) per permetre l'accés del servidor web.

## Publicació de Pàgines Personals

- **URLs d'Usuari**: Apache permet la publicació de pàgines personals amb URLs del tipus `http://www.informaticaASIX2.com/~usuari`, agafant el contingut de la carpeta `public_html` de l'usuari.
- **Configuració de Permisos**: L'usuari `root` ha d'obrir els drets d’execució per a tothom als directoris dels usuaris que volen publicar pàgines personals.
- **Activació del Mòdul `userdir`**:
  - **Apache Compilat**: Descomentar la línia referent al mòdul `userdir` en `httpd.conf`.
  - **Apache via Gestor de Programari**: Activar el mòdul amb `a2enmod` o creant enllaços a `mods-enabled`.

# Configuració de Noves URL contra Directoris Específics del Disc amb Apache

Per vincular noves URL a directoris específics fora de la carpeta arrel (`/usr/local/apache2/htdocs` o `/var/www/html`), utilitzem la directiva `Alias`:

```apache
Alias /jedis /home/jedis/web/

<Directory /home/jedis/web/>
  Options Indexes FollowSymLinks
  # Permet seguir enllaços simbòlics i aplicar directives del mòdul dir.
  AllowOverride None
  # Indica si els fitxers .htaccess seran ignorats o no.
  Require all granted
  # Permet accés complet a aquest directori.
</Directory>
```

## Exemple de Configuració
Per crear una nova URL http://www.informaticaASIX2.com/jedis que apunti al directori /home/jedis/web, s'afegiria a la configuració d'Apache:
```
Alias /jedis /home/jedis/web/
<Directory /home/jedis/web/>
  Options Indexes FollowSymLinks
  AllowOverride None
  Require all granted
</Directory>
```

## Consideracions Importants

- **Permisos de Directori**: Assegureu-vos que tots els directoris en la cadena fins al directori final tenen els permisos adequats perquè l'usuari sota el qual s'executa Apache (`www-data`) pugui accedir-hi.
- **Missatge d'Accés Denegat**: Si apareix un missatge d'accés denegat, reviseu els permisos dels directoris i els registres d'errors d'Apache (`/usr/local/apache2/logs/error_log` o `/var/log/apache2/error_log`) per detalls específics.
- **Extensions de la Pàgina Index**: La configuració d'Apache permet múltiples extensions per a la pàgina index per defecte, com `index.html`, `index.htm`, etc., a través del fitxer `dir.conf`.


# Mapejats per Utilitzar Aplicacions Tipus CGI amb Apache

Apache permet executar aplicacions CGI, que normalment són scripts fets amb llenguatge shell de Linux o Perl.

## Directori per a CGI

- **Ubicació per Defecte**: `/usr/local/apache2/cgi-bin` o `/usr/lib/cgi-bin`
- **Accés via Web**: Les aplicacions CGI poden ser executades des de `http://www.informaticaASIX2.com/cgi-bin/nom_executable`

## Exemple d'Ús

Si guardem un script anomenat `test-cgi` (amb drets d'execució per a tothom) dins del directori CGI, es pot executar accedint a:


## Activació del Mòdul CGI

- Important: Necessiteu activar el mòdul CGI si encara no està actiu. Això es pot fer amb la comanda `a2enmod cgi` o bé, en sistemes que no utilitzin aquesta eina, assegurant-se que el mòdul CGI està habilitat dins la configuració d'Apache.

## Consideracions

- **Execució des de Pàgines Web**: És comú executar scripts CGI des de pàgines web mitjançant enllaços o passant paràmetres.
- **Desenvolupament de Funcionalitats**: Amb els scripts CGI, es poden crear pàgines web interactives, formularis de recollida de dades, comptadors de visites, etc.

Aquesta configuració obre la porta a una major interactivitat dins dels serveis web, permetent la creació de contingut dinàmic i la recollida de dades a través de formularis.


# Control d'Accés als Continguts del Servidor Apache

## Preparació per a Zones Restringides

Per permetre al servidor web Apache gestionar zones d'accés restringit, cal habilitar l'ús de fitxers `.htaccess` per a la configuració de restriccions d'accés.

### Configuració General per a `.htaccess`

Modifica la configuració d'Apache per permetre l'ús de fitxers `.htaccess` amb restriccions d'accés:

```apache
<Directory />
  Options FollowSymLinks
  AllowOverride AuthConfig
</Directory>
```

Per aplicar restriccions només a un directori específic, utilitza l'etiqueta <Directory> apuntant al directori desitjat:

```
<Directory /home/jedis/web/>
  Options Indexes FollowSymLinks
  AllowOverride AuthConfig
  Require all granted
</Directory>
```
# Reiniciar Apache en sistemes utilitzant systemd
sudo systemctl restart apache2

# O, en sistemes que utilitzen init.d
sudo /etc/init.d/apache2 restart

# Control d'Accés Senzill amb Usuari/Contrasenya

## Creació d'Usuari i Contrasenya

Per restringir l'accés a una part específica del teu lloc web, com l'espai web dels jedis (`http://www.informaticaASIX2.com/jedis`), pots utilitzar un sistema d'autenticació bàsic amb usuari i contrasenya.

1. **Genera el Fitxer de Contrasenyes**:
   Utilitza `htpasswd` per crear un fitxer de contrasenyes. Si és el primer usuari, utilitza l'opció `-c` per crear el fitxer:
   
   ```shell
   sudo htpasswd -c /etc/apache2/.jedis-passwd luke
    ```
Afegeix més usuaris omitint -c:
```
sudo htpasswd /etc/apache2/.jedis-passwd anotherUser
```

Dins del directori que vols protegir (/home/jedis/web), crea un fitxer .htaccess amb el següent contingut:
```
AuthType Basic
AuthUserFile /etc/apache2/.jedis-passwd
AuthName "Espai web the force awakens"
Require valid-user

```
Quan intentis accedir a http://www.informaticaASIX2.com/jedis, el navegador et demanarà l'usuari i la contrasenya. Només els usuaris definits en el fitxer .jedis-passwd podran accedir.

Per canviar la contrasenya d'un usuari existent, executa htpasswd sense l'opció -c:
```
sudo htpasswd /etc/apache2/.jedis-passwd luke
```
Nota Important
Assegura't que Apache està configurat per permetre l'ús de fitxers .htaccess amb AllowOverride AuthConfig en la configuració del directori pertinent.

# Resum del Control d'Accés per IP i Combinat en Fitxers de Configuració Apache

## 3.5.3. Control Senzill per Adreça IP

Per facilitar l'accés a les pàgines reservades sense necessitat de recordar contrasenyes, s'implementa un control d'accés basat en l'adreça IP. Això permet que només certs equips puguin accedir a l'espai web destinat als jedis.

- **Adreces IP Permeses:** `192.168.202.21`, `192.168.202.22`, `192.168.202.23`
- **Configuració Apache:**
  ```apache
  Alias /jedis "/home/jedis/web/"
  <Directory "/home/jedis/web"> 
      Allow from 192.168.202.21 192.168.202.22 192.168.202.23 
      Deny from all 
  </Directory>
  ```
Efecte: Només els equips amb les IP esmentades poden accedir a l'espai web dels jedis després de reiniciar el servidor web.

## 3.5.4. Control Combinat, Usuari / IP

Es busca ampliar l'accés a l'espai web "the force awakens" per a tot el temple jedi i també des de l'exterior, però restringint l'accés a informació sensible mitjançant autenticació d'usuari i contrasenya.
- Estratègia: Combinar el control per IP amb la validació d'usuari i contrasenya.
  ```
  <Directory "/home/jedis/web"> 
      Allow from 192.168.202
      Deny from all 
      AuthType Basic 
      AuthUserFile /etc/httpd/.jedis­passwd 
      AuthName "Intranet the force awakens" 
      Require valid­user 
      Satisfy any 
  </Directory>

  ```

  - Com Funciona: El paràmetre Satisfy any permet l'accés si es compleix qualsevol de les dues condicions: estar dins la xarxa 192.168.202.x o proporcionar un usuari i contrasenya vàlids des de qualsevol altra xarxa.
  - Observació Important: Les configuracions dins del fitxer de configuració tenen prioritat sobre les del fitxer .htaccess.
 
# 3.6. Control de l'Aplicació de Monitorització: Apache-status

Apache-status és una eina interna d'Apache que proporciona una pàgina d'estat per monitoritzar la càrrega del servidor web. Aquesta pàgina és útil per a administradors de sistemes i desenvolupadors que necessiten una visió en temps real de la salut i el rendiment del servidor.

## Activació d'Apache-status

Per activar la pàgina d'estat d'Apache, és necessari modificar els fitxers de configuració per "des-comentar" les entrades relacionades. Aquesta acció permet l'accés a una URL específica que mostra l'estat del servidor.

- **Configuració a modificar:**
  ```apache
  <Location /stat-web> 
      SetHandler server-status 
      Allow from 192.168.202 .informaticaASIX2.com 
      Deny from all 
  </Location>

  ```

# Configuració d'Apache: Correu de Contacte i Gestió de Logs

## Correu Electrònic de Contacte
Per millorar la comunicació entre usuaris i l'administrador del sistema en cas de problemes amb el servidor, es pot definir un correu electrònic de contacte.

- **Directiva a Configurar:**
```
ServerAdmin yoda@informaticaASIX2.com
```

- **Benefici:**
L'adreça de correu s'inclou automàticament en els missatges d'error mostrats als usuaris, facilitant així la comunicació directa amb l'administrador.

## Gestió de Logs en Apache
L'Apache registra les activitats del servidor en fitxers de log, essencials per a la monitorització i el diagnòstic de problemes.

### Access_log
Recull informació sobre totes les peticions realitzades al servidor.

- **Ubicacions Comunes:**
- `/usr/local/apache2/logs/access_log`
- `/var/log/apache2/access_log`
- **Gestió de la Rotació:**
Per evitar que els logs ocupin massa espai en disc, es realitza una rotació periòdica. La configuració per defecte realitza rotacions diàries, mantenint quatre còpies.

### Error_log
Registra els errors que s'han produït en el servidor, ajudant en el diagnòstic de problemes.

- **Ubicacions Comunes:**
- `/usr/local/apache2/logs/error_log`
- `/var/log/apache2/error_log`
- **Nivell de Log:**
Per defecte, es configura a `warn`, però pot ser ajustat per incloure més detalls com `debug`, `info`, `crit`, `emerg`.

### Personalització de la Rotació de Logs
Es pot ajustar la quantitat de còpies de logs guardades per optimitzar l'ús de l'espai en disc.

- **Exemple de Configuració:**
Modificar el fitxer de configuració en `/etc/logrotate.d/apache2`, afegint la línia `rotate 2` per limitar a dues les còpies de cada log.

La configuració adequada del correu electrònic de contacte i la gestió eficient dels logs són elements clau per a la bona administració d'un servidor web Apache, permetent una comunicació efectiva amb els usuaris i un manteniment òptim del sistema.






