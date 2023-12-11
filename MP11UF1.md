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

