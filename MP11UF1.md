# PDF1
# Resum: Protecció de la Informació i Seguretat Informàtica

## Introducció a la Protecció de la Informació

### Concepte Bàsic
- La **protecció de la informació** s'aconsegueix mitjançant l'aplicació d'un conjunt de mecanismes o estratègies de seguretat.

### Principis Clau
1. **Objectiu Global**: La seguretat ha de ser considerada com un objectiu integral i global.
2. **Disseny Organitzatiu**: La seguretat s'ha de dissenyar com a part integral de l'organització, considerant tots els aspectes que la conformen.
3. **Marc Legal**: El marc legal ha de ser considerat des del principi com una part essencial del disseny de les polítiques de seguretat.

### Seguretat Activa
- **Definició**: La seguretat activa inclou tots els mecanismes i mesures (tant físics com lògics) destinats a prevenir i detectar intents de comprometre els components d'un sistema informàtic.

# Sistemes Personals: Atacs i Contramesures

## Atacs segons l’Objectiu

### 1. Interrupció
- **Objectiu**: Atac contra la disponibilitat.
- **Mètode**: Destrucció o inaccessibilitat d'un recurs del sistema.

### 2. Intercepció
- **Objectiu**: Atac contra la confidencialitat.
- **Mètode**: Accés no autoritzat a un recurs, com a espionatge en la comunicació.

### 3. Modificació
- **Objectiu**: Atac contra la integritat.
- **Mètode**: Accés no autoritzat amb la intenció de modificar, esborrar o alterar recursos.

### 4. Fabricació
- **Objectiu**: Atac contra la integritat.
- **Mètode**: Creació o inserció d'objectes falsificats en el sistema (p.ex., afegir usuaris no autoritzats).

## Atacs segons la seva Forma

### 1. Atacs Passius
- **Característiques**: Observació del sistema sense modificar ni destruir recursos, amb l'objectiu d'obtenir informació confidencial.

### 2. Atacs Actius
- **Característiques**: Alteració o destrucció de recursos del sistema, que pot incloure suplantació d'identitat, re-actuació, degradació fraudulenta del servei, i modificació de missatges.

## Atacs segons el Tipus d’Atacant

### 1. Insiders (Dins de la Xarxa)
- **Característiques**: Els atacs interns tenen un percentatge d'èxit més elevat i poden causar més dany.

### 2. Outsiders (Fora de la Xarxa)
- **Característiques**: Els atacs externs són més nombrosos.

### Possibles Atacants
- Personal de la mateixa organització.
- Antics treballadors.
- Intrusos informàtics (hackers).
- Intrusos remunerats, organitzats i coordinats.

# Anatomia dels Atacs Informàtics

Els atacs informàtics solen desenvolupar-se en un cicle de cinc fases:

## 1. Reconeixement
- **Descripció**: Recopilació d'informació sobre el sistema objectiu. Aquesta fase implica la investigació de les vulnerabilitats potencials i l'obtenció de dades generals sobre l'entorn del sistema.

## 2. Escaneig
- **Descripció**: Anàlisi més detallat del sistema. S'utilitzen eines i tècniques específiques per identificar serveis actius, ports oberts, i vulnerabilitats explotables.

## 3. Accés al Sistema
- **Descripció**: Realització de l'atac. En aquesta fase, l'atacant intenta explotar les vulnerabilitats trobades per accedir al sistema, sovint guanyant privilegis d'administrador o un accés similar.

## 4. Manteniment de l'Accés
- **Descripció**: Assegurar un accés continuat al sistema. Els atacants poden instal·lar backdoors o altres eines per mantenir el control del sistema, fins i tot després que les vulnerabilitats originals hagin estat reparades.

## 5. Esborrat d'Empremtes
- **Descripció**: Ocultació de l'activitat maliciosa. L'objectiu és eliminar o modificar els registres i altres evidències que puguin indicar la presència o les accions de l'atacant.

La comprensió del funcionament intern d'un atac informàtic és fonamental per anticipar-se als esdeveniments i preveure activitats que podrien comprometre la seguretat del nostre sistema informàtic.

# Anatomia dels Atacs Informàtics

## Fase 1: Reconeixement
- **Objectiu**: Recopilació d'informació sobre el sistema objectiu.
- **Tècniques**:
  - Enginyeria social o trashing per aconseguir informació valuosa.
  - Recerques a Internet.
  - Capturar trànsit de xarxa (sniffing).
  - Ús de l'ordre whois per obtenir dades del sistema.
  - Recursos: [Whois.com](https://www.whois.com/whois/), [ICANN Whois](https://whois.icann.org/es).

## Fase 2: Exploració
- **Objectiu**: Sondar el sistema per detectar vulnerabilitats explotables.
- **Accions**:
  - Recopilar informació sobre comptes d'usuari, versions de sistemes operatius, aplicacions, i ports oberts.
  - Utilització d'escàners de xarxa o de ports com nmap.
  - Ordres com tracert (Windows) o traceroute (Linux/Unix) per rastrejar canvis de xarxa.

## Fase 3: Accés
- **Objectiu**: Explotar vulnerabilitats per accedir al sistema.
- **Tècniques de Crackeig de Contrasenyes**:
  - Online: Tests en viu amb eines com Hydra.
  - Offline: Extracció i anàlisi de contrasenyes encriptades, amb eines com Cain i Abel.
- **Evasió**:
  - Evasió de Firewalls, IDS, IPS, i Honeypots.
  - Eines: 007 Shell, ICMP Shell, AckCmd.

## Fase 4: Manteniment de l'Accés
- **Objectiu**: Preservar l'accés futur al sistema.
- **Mètodes**:
  - Instal·lació de malware com cavalls de Troia i rootkits.
  - Accions: Keylogging, captura de trànsit (sniffing), instal·lació de FTP il·lícits.
  - Uso de Rootkits a nivells de Kernel, Llibreries, i Aplicacions.

## Fase 5: Esborrat d'Empremtes
- **Objectiu**: Ocultar l'activitat maliciosa i evitar detecció.
- **Pasos**:
  - Desactivar Auditoria del sistema si està activa.
  - Eliminar registres (logs) del sistema i aplicacions compromeses.
  - Eliminar evidència d'eines utilitzades mitjançant esteganografia.

Cada fase de l'atac informàtic requereix tècniques i estratègies específiques i el coneixement d'aquestes fases ajuda a prevenir i detectar possibles atacs al nostre sistema.

# PDF2
# Seguretat en la Xarxa Corporativa

La seguretat en una xarxa corporativa és crucial i es basa en una sèrie de eines i polítiques implementades per l'administrador del sistema. 

## Aspectes Clau de la Seguretat de la Xarxa

- **Objectiu**: Prevenir i controlar l'accés no autoritzat, mal ús, modificació o inhabilitació de la xarxa informàtica i els seus recursos.
- **Eines i Polítiques**: Inclouen l'ús de firewalls, sistemes de detecció i prevenció d'intrusions, polítiques d'accés, criptografia, etc.

## Monitoratge del Trànsit de Xarxes

El monitoratge del trànsit de xarxes és un component fonamental de la seguretat de la xarxa.

### 1. Monitoratge Passiu
- **Descripció**: Es basa en l'escolta i anàlisi del trànsit real de la xarxa.
- **Acció**: Recollida i anàlisi de la informació, sense interactuar amb el trànsit.

### 2. Monitoratge Actiu
- **Descripció**: Consisteix a injectar paquets de prova en la xarxa o enviar-los a servidors i aplicacions.
- **Acció**: Mesurar el temps de resposta i el comportament de la xarxa i els servidors davant d'aquests paquets de prova.

El monitoratge, tant passiu com actiu, ajuda els administradors a entendre millor el funcionament de la xarxa, a identificar possibles problemes de seguretat i a prendre mesures per a la seva solució.

# Eines de Monitoratge en Seguretat de Xarxes

## Eines de Monitoratge Passiu

### Sniffers
- **Descripció**: Programes que capturen i registren la informació que circula per una xarxa.
- **Detecció de Sniffers**:
  - Cerca de targetes de xarxa en mode promiscu.
  - Eines: ifconfig, ifstatus, Network Promiscous Ethernet Detector (NEPED), entre altres.

### Mesures de Protecció
- **Xifrat de Documents**: Utilització de PGP per xifrar documents enviats a través de la xarxa.
- **Connexions Segures**: Instal·lació de serveis com Secure Shell (SSH) per iniciar sessions segures, substituint comandes com telnet.

## Eines de Monitoratge Actiu

### Escàners de Seguretat
- **Objectiu**: Detectar vulnerabilitats en un sistema informàtic.
- **Funcionament**: Identificar els ports TCP/UDP oberts en una màquina remota.

### Importància dels Ports Oberts
- **Risc**: Els ports oberts poden indicar possibles vulnerabilitats explotables pels intrusos.
- **Protocols**:
  - **TCP** (Transmission Control Protocol): Utilitzat per a connexions fiables.
  - **UDP** (User Datagram Protocol): Utilitzat per a transmissions ràpides i menys fiables.

El monitoratge, tant passiu com actiu, és una part integral de la seguretat de la xarxa, ja que permet detectar possibles amenaces i vulnerabilitats, i adoptar mesures per mitigar-les.

# Ordres del Sistema per a Diagnosi de Xarxes

## Ordres Clau
- **Ping**: Permet determinar si una màquina està connectada a la xarxa.
- **Traceroute**: Proporciona una descripció del camí que segueixen els paquets de dades fins a una màquina específica, ajudant a identificar on es produeixen els problemes.

## Eines de Monitoratge
- **Exemples**: MRTG (Multi Router Traffic Grapher), Nagios.

# Seguretat en Xarxes Sense Fil

## Conceptes Bàsics
- **Wi-Fi**: Wireless fidelity, connectivitat sense fil.
- **WLAN**: Wireless Local Area Network.

## Modes de Funcionament
1. **Ad Hoc (Client a Client)**: Comunicació directa entre màquines sense necessitat de punt d'accés.
2. **Infraestructura (Client a Punt d'Accés)**: Comunicació a través de punts d'accés que actuen com a repetidors.

## Consideracions de Seguretat
- Les WLAN requereixen mesures de seguretat més estrictes que les xarxes cablejades degut a la seva natura.

## Recomanacions de Seguretat
- **Canviar Contrasenyes Per Defecte**: Evitar l'ús de contrasenyes predeterminades.
- **Filtrat d'Adreces MAC**: Permetre només la connexió de dispositius específics.
- **Xifratge**: Utilitzar protocols com WEP, WPA, o WPA2.
- **Gestió d'IP**: Desactivar l'assignació d'IP per DHCP si no és necessari.
- **SSID Broadcast**: Eliminar la difusió del SSID per reduir la visibilitat de la xarxa.

Aquestes pràctiques ajuden a millorar significativament la seguretat de les xarxes sense fil i a prevenir accés no autoritzats o altres tipus de vulnerabilitats.

# Control d'Accés a la Xarxa Basat en Autenticació

## Conceptes Clau
El control d'accés a la xarxa és un component crític de la seguretat de la xarxa, i es basa en el reconeixement i validació de dispositius a través de la seva adreça MAC.

### Components del Control d'Accés
1. **Client**
   - **Descripció**: Dispositiu que vol connectar-se a la LAN, com un portàtil.
   - **Procés**: El client sol·licita l'accés a la xarxa.

2. **Autenticador**
   - **Funció**: Controla l'accés físic al medi de xarxa.
   - **Comportament**: Els ports inicialment estan en estat "no controlat". Després de l'autenticació, si aquesta és exitosa, passen a estat "controlat", permetent l'accés del dispositiu.

3. **Servidor d'Autenticació**
   - **Rol**: Dispositiu de confiança que realitza la validació de la identitat del client.
   - **Comunicació**: Notifica a l'autenticador el resultat de l'autenticació.

El control d'accés basat en autenticació assegura que només els dispositius autoritzats poden accedir a la xarxa, millorant la seguretat i evitant l'accés no autoritzat.

# Atacs als Serveis de la Xarxa

## Atacs de Denegació de Servei (DoS)
- **Descripció**: Accions que fan inaccessibles els recursos del sistema des de la xarxa.
- **Mètode**:
  - **Protocol d'Establiment de Sessió**: 
    1. L'ordinador client envia una sol·licitud SYN al servidor.
    2. El servidor respon amb un missatge ACK i SYN.
    3. L'ordinador client envia una resposta ACK al servidor.
  - L'atac es produeix quan aquest protocol és interromput o saturat.

## Atacs de Falsejament d'Identitat (Spoofing)
- **Descripció**: L'ús de tècniques de suplantació d'identitat.
- **Tipus**:
  - **Falsejament d'IP**: Suplantació de l'adreça IP d'un dispositiu.
  - **Falsejament d'ARP**: Suplantació en la taula ARP, utilitzada en atacs man-in-the-middle.
  - **Falsejament de DNS (Pharming)**: Redirigeix la sol·licitud d'una adreça IP a una destinació falsa.
- **Conseqüències**: Pot provocar atacs de denegació de servei i desencaminament.

Els atacs als serveis de la xarxa poden pertorbar significativament les operacions normals, i requereixen mesures de seguretat avançades per prevenir-los i mitigar els seus efectes.

# Sistemes de Detecció d'Intrusos (IDS)

## Descripció General
- **Objectiu**: Monitoritzar el flux d'informació de la xarxa per detectar i prevenir atacs.

## Classificacions dels IDS
1. **Segons la Font de la Informació**:
   - **Basats en Xarxa (NIDS)**: Monitoritzen el trànsit de tota la xarxa en mode promiscu.
   - **Basats en Màquina (HIDS)**: Monitoritzen una o diverses màquines, analitzant dades del sistema operatiu.
   - **Basats en Aplicacions**: Monitoritzen els fitxers de registre d'una aplicació específica.

2. **Segons el Tipus d'Anàlisi**:
   - **Basats en Firmes**: Cerquen patrons d'atac coneguts. Requereixen actualitzacions constants de la base de dades de firmes.
   - **Basats en Anomalies**: Detecten comportaments anòmals en la xarxa.

3. **Segons el Tipus de Resposta**:
   - **Resposta Passiva**: Enregistra alarmes o avisa els responsables.
   - **Resposta Activa**: A més de la resposta passiva, pot prendre accions per bloquejar activitats intrusives.

# Seguretat en les Xarxes Públiques

## Consideracions Clau
- **Riscos**: La informació en les xarxes públiques és susceptible de ser observada durant el seu trànsit.
- **Establiment de Confiança**: Relacions de confiança en entorns gairebé anònims.

## Signatura Electrònica
- **Basada en Criptografia de Clau Pública**:
  - **Autenticitat**: Certifica la identitat del remitent.
  - **Integritat**: Assegura que el missatge no ha estat modificat durant la transmissió.
  - **No Repudi**: Impedeix que l'emissor negui haver enviat el missatge.

L'ús d'IDS i la implementació de mesures com la signatura electrònica són essencials per a la seguretat en xarxes, especialment en entorns on la confidencialitat i l'integritat de la informació són crítiques.

# PDF3
# SNORT IDS: Sistema de Detecció d'Intrusos

## Introducció a SNORT
- **Descripció**: Snort és un sistema de detecció d'intrusos (IDS) que analitza el tràfic de la xarxa en temps real i reacciona a patrons detectats.
- **Importància**: Permet detectar comportaments anòmals o intents d'accés no desitjats a la xarxa, essencial en el context de l'augment dels atacs cibernètics.

## Funcionament dels IDS
- **Eines Utilitzades**:
  - Recollida de dades (packet sniffing).
  - Aplicació de regles per detectar riscos.
  - Filtratge comparant els patrons de tràfic amb patrons d'atacs predefinits.
  - Detecció d'esdeveniments no esperats a la xarxa.
  - Generació d'alarmes per diversos mitjans.
  - Actuació sobre el tràfic detectat.

## Modes de Funcionament de SNORT
- **Monitorització (Sniffer Mode)**:
  - `sudo snort -v -i eth0`: Mostra capçaleres de paquets.
  - `sudo snort -vd -i eth0`: Mostra capçaleres i dades de paquets.
- **Enregistrament de Paquets de la Xarxa**:
  - `sudo snort -l ./log -i eth0`: Enregistra paquets en un directori de log.
- **HIDS (Host IDS) / NIDS (Network IDS)**:
  - `sudo snort -A console -c /etc/snort/snort.conf -i eth0`: Utilitza regles predefinides en `snort.conf` per a la monitorització.

Snort, com a part de les tecnologies de seguretat informàtica, ofereix eines avançades per detectar i prevenir intrusions, essent un recurs valuós en la protecció contra atacs cibernètics.

# Ubicació dels IDS i SNORT Inline (IPS)

## Ubicació dels IDS
- **Importància**: Cal situar els IDS de manera que puguin capturar tot el tràfic a monitorar.
- **Depenent de l'ús**:
  - **Com a IDS**: Pot estar situat en diversos punts de la xarxa.
  - **Com a IPS (Intrusion Prevention System)**: Ha de situar-se inline, és a dir, en el mig de la comunicació.
- **Consideracions**:
  - Assegurar que l'IPS no provoqui pèrdues de paquets durant el processament.
  - Comú situar un IDS abans del tallafocs (per monitorar tot el tràfic) i un altre IDS/IPS després (per gestionar tràfic que passa el tallafocs).

## SNORT com a IPS
- **Funcionalitat**: Permet bloquejar el tràfic entre dues interfícies.
- **Paràmetre Inline**: `-Q` indica que SNORT ha de funcionar inline.
- **Modes de Funcionament**:
  - Alertes per consola: `snort -d -A console -c snort.conf -i eth1:eth2 -Q`.
  - Enregistrament d'Alertes: `snort -d -A full -c snort.conf -i eth1:eth2 -Q`.

## Fitxers de Configuració
- **Ubicació**: `/etc/snort/snort.conf`.
- **Característiques**: L'arxiu té un índex i està dividit en diferents seccions per facilitar-ne l'ús.

La correcta ubicació i configuració dels sistemes de detecció i prevenció d'intrusos són claus per a una eficient protecció de la xarxa, i SNORT ofereix eines flexibles per adaptar-se a diferents necessitats de seguretat.

# Regles i Variables en SNORT

## Regles a Snort
- **Instal·lació Bàsica**: Inclou un conjunt de regles base, modificables segons necessitat.
- **Ubicació de les Regles**: `/etc/snort/rules/`.
- **Activació i Desactivació de Regles**:
  - A través de l'arxiu de configuració, amb l'opció `include`.
  - Exemple: `include $RULE_PATH/local.rules`.
- **Estructura de les Regles**:
  - Arxius amb extensió `.rules`.
  - Alertes registrades a `/var/log/snort`.

## Variables SNORT
Les variables en SNORT són crucials per aplicar correctament les regles.

### Tipus de Variables
1. **Variables Estàndard (`var`)**:
   - Exemple: `var RULE_PATH /etc/snort/rules`.
2. **Variables de Ports (`portvar`)**:
   - Exemple: `portvar PORTS_A_MIRAR [22,80,1024:1050]`.
3. **Variables de Xarxa (`ipvar`)**:
   - Exemple: `ipvar HOME_NET 10.0.0.0/24`, `ipvar EXTERNAL_NET !$HOME_NET`.

### Variables Globals Importants
- **HOME_NET**: Defineix el rang de la xarxa interna.
- **EXTERNAL_NET**: Defineix el rang fora de la xarxa interna, normalment usant `!HOME_NET`.
- **SERVERS**: Indica la ubicació dels servidors interns, per defecte igual a `HOME_NET`.
- **PORTS**: Defineix els ports de servei per als servidors.
- **Llista Blanca**: Permet excloure dispositius específics de les regles.
- **Llista Negra**: Defineix hosts que generen una alerta si són detectats a la xarxa.

Les variables i regles en SNORT permeten una configuració detallada i adaptada a les necessitats específiques de la xarxa, proporcionant un alt grau de personalització en la detecció d'intrusos.

# Regles en SNORT

## Estructura de les Regles
Les regles d'Snort es divideixen en dues parts: la Capçalera i els camps específics.

### Capçalera de la Regla
- **Acció**: Defineix què succeeix si la regla s'activa.
  - `Alert`: Envia una alerta i emmagatzema la informació en un arxiu de log.
  - `Log`: Registra l'activitat sense enviar alerta.
  - `Pass`: Ignora el paquet.
  - `Drop`: Bloqueja el paquet i registra en l'arxiu de log.
  - `Reject`: Bloqueja el paquet i força un error en la comunicació.
  - `sdrop`: Bloqueja el paquet sense deixar constància en el log.
- **Protocol**: Tipus de protocol de comunicació.
- **Origen i Destí**: Xarxa, IP o variable definida en l'arxiu de configuració.
- **Ports**: Especificació de ports.
- **Direcció**: 
  - `→`: Actua de l'Origen al Destí.
  - `↔`: Actua en ambdues direccions.

### Camps Específics
- **msg**: Missatge que es mostra en activar-se l'alerta.
- **sid**: Identificador únic de la regla (normativament superior a 1000000 per a regles personalitzades).
- **rev**: Versió de la regla.
- **classtype**: Classificació del tipus d'atac.
- **priority**: Importància de l'alerta.
- **flow**: Indica el flux d'informació (p.ex., connexions establertes TCP).

El format únic de les regles en Snort permet que els analistes puguin revisar, entendre i ajustar les regles segons les necessitats específiques de la seva xarxa, optimitzant així la detecció d'intrusos i la seguretat de la xarxa.

# Creació de Regles Personalitzades en SNORT

## Objectiu de la Regla
- **Determinar l'Objectiu**: Clarificar què es vol aconseguir amb la regla.
  - Detectar un tipus específic de tràfic.
  - Bloquejar tràfic a llocs no permesos.
  - Crear perfils de navegació.
  - Buscar connexions de noves amenaces.
  - Detectar fugues d'informació.

## Acció a Realitzar
- **Reaccions Possibles**:
  - Informar al Centre d'Operacions de Seguretat (SOC).
  - Enregistrar l'activitat en un log.
  - Actuar sobre el Firewall.

## Abast de la Regla
- **Àrea d'Actuació**:
  - Interna o externa.
  - Comunicació de fora a dins o en ambdues direccions.
  - Aplicable a tota la xarxa o a alguns equips específics.

## Optimització de la Regla
- **Millors Pràctiques per a la Cerca**:
  - Utilització de valors hexadecimals.
  - Cadenes de text.
  - Text en la URL.

## Revisió d'Alertes
- **Ubicació dels Logs**: `/var/log/snort`.
- **Contingut d'un Arxiu d'Alerta**: Informació detallada sobre l'activitat detectada.

Crear regles personalitzades en SNORT permet una protecció més enfocada i efectiva, adaptada a les necessitats i riscos específics de la xarxa. La revisió periòdica d'alertes és essencial per a una gestió eficaç de la seguretat.

PAG 17 I 18 NO ESTA FICADA.

# PDF 4
# Xarxes Privades Virtuals (VPN)

## Definició
Una **VPN (Virtual Private Network)** és una tecnologia de xarxa que permet estendre una xarxa privada sobre una infraestructura pública com Internet.

## Funcionament
- **Encapsulació de Dades**: Els paquets de dades són encapsulats per a la seva transmissió.
- **Seguretat**: S'utilitza xifrat per protegir les dades mentre circulen per trams de xarxa pública.
- **Túnel**: La xarxa privada crea un "túnel" a través d'Internet, aprofitant-ne l'accessibilitat i cost reduït, i a la vegada simulant connexions punt a punt segures.

## Aplicacions
- **Accés Remot**: Permet als usuaris connectar-se a xarxes corporatives des de qualsevol lloc, assignant les adreces i privilegis pertinents a l'ordinador remot, tot i utilitzar una xarxa pública.

Les VPNs són una solució eficaç per a empreses i individus que necessiten accedir a recursos de xarxa de forma segura des de localitzacions remotes o a través d'Internet.
# Interconnexió de Xarxes Utilitzant VPNs

## Connexió de Dues Oficines d'una Empresa
- **Establiment de VPN**: Entre dos gateways, cadascun pertanyent a una xarxa privada diferent.
- **Funció dels Gateways**: Actuen com a routers per a les màquines de les seves respectives xarxes.
- **Transmissió de Paquets**: Quan un gateway rep un paquet dirigit a l'altra xarxa, el transmet segurament a través de la VPN.
- **Seguretat**: El trànsit està protegit per la VPN només en el recorregut entre els dos gateways.

## Treballadors Remots (Road Warriors)
- **Connexió Individual**: Permet als treballadors connectar-se des de qualsevol lloc.
- **Requisit**: L'ordinador necessita un client VPN per establir connexió amb el concentrador de VPNs de la xarxa corporativa.
- **Protecció de Trànsit**: Tota la comunicació des de l'ordinador remot fins a la xarxa corporativa queda segura gràcies a la VPN.

Les VPNs són fonamentals per a la interconnexió segura tant en escenaris de connexió d'oficines com per a treballadors que necessiten accés remot a la xarxa corporativa.
# Avantatges i Inconvenients de les VPNs

## Avantatges
- **Seguretat**: Les VPNs ofereixen un alt nivell de seguretat mitjançant xifrat i signatura de paquets.
- **Mobilitat**: Permeten connexions segures des de qualsevol ubicació geogràfica.
- **Transparència**: Faciliten la interconnexió d'ordinadors i xarxes de manera transparent per a l'usuari.
- **Simplicitat**: Simplifiquen l'administració d'equips remots, ja que l'equip remot es veu com a part de la xarxa local.
- **Estalvi Econòmic**: Utilitzar xarxes públiques per al trànsit segur de paquets redueix costos comparat amb xarxes dedicades.

## Mecanismes de Seguretat en VPNs
- **Xifrat**: Per a la confidencialitat de les dades.
- **Signatura**: Per a l'autenticitat i la integritat.

## Inconvenients
- **Fiabilitat**: Dependència d'ISP pot conduir a fallades de xarxa que afecten la comunicació VPN.
- **Confiança**: La seguretat compromesa en un node o subxarxa pot afectar tota la VPN.

Els beneficis de les VPNs, com la seguretat i la mobilitat, són factors clau per a la seva popularitat, mentre que els inconvenients relacionats amb la fiabilitat i la confiança requereixen una atenció i gestió detallades.
# Tunneling i Protocols de Tunneling

## Tunneling
- **Descripció**: Mètode que permet transportar dades d'una xarxa a una altra utilitzant la infraestructura d'Internet.
- **Encapsulació de Dades**: Encapsula els paquets en un protocol de transport d'Internet com IP per establir el túnel.
- **Ruta Lògica**: Els paquets viatgen a través d'un túnel virtual sobre Internet fins al seu destí, on són desencapsulats.

## Protocols de Tunneling Principals
- **IPSec (IP Security)**: Assegura la transmissió i l'autenticació sobre xarxes públiques, operant a la capa de xarxa.
- **PPTP (Protocol de Tunneling Punt a punt)**: Utilitzat per transmissions segures de tràfic basat en Windows, opera a la capa d'enllaç.
- **L2TP (Layer 2 Tunneling Protocol)**: Combina les funcionalitats de capa 2 i PPTP per encapsular trames PPP.
- **OpenVPN**: Protocol de codi obert amb xifrat AES-256 i autenticació RSA, compatible amb gairebé totes les plataformes.

El tunneling facilita la creació de connexions segures i privades sobre xarxes públiques, essent una peça clau en la implementació de VPNs i la seguretat de la xarxa.

# Secure Shell (SSH)

## Introducció a SSH
- **Funcionalitat**: Protocol que permet establir connexions segures per sessions interactives en màquines remotes.
- **Confidencialitat**: Totes les dades transferides estan xifrades, assegurant la privacitat de la informació.
- **Autenticació Mútua**: Client i servidor s'autentifiquen mútuament per confirmar les seves identitats.

## Establiment de Connexió SSH
- **Identitat de Servidor i Client**: Inicialització de la sessió amb verificació de les identitats.
- **Canal Segur**:
  - **Negociació**: Client i servidor acorden els mètodes de xifratge a utilitzar.
- **Autenticació**:
  - **Contrasenya**: Mètode tradicional d'entrada de credencials.
  - **Claus Públiques**: Utilització de parells de claus per una autenticació més segura.

SSH és un pilar fonamental en la seguretat de xarxa, proporcionant un mitjà segur per a la gestió remota d'ordinadors i transferència de fitxers.

