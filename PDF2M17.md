# Introducció a Dispositius Mòbils

## Definició
- Segons **Wikipedia**, un **dispositiu mòbil** és un aparell de mides reduïdes i lleuger, dissenyat per ser fàcilment transportable.

## Característiques
- **Connexió a Internet:** Normalment disposen de la capacitat de connectar-se a Internet.
- **Funcionalitats:** Estan dissenyats per realitzar una o diverses tasques específiques.
- **Interacció amb Ordinadors:** Solen poder connectar-se a ordinadors per complementar funcions, actualitzar-se o transferir dades.

## Tipus de Dispositius Mòbils
- Segons Wikipedia, existeixen diversos tipus, incloent:
  - Telèfon mòbil
  - Telèfon intel·ligent (smartphone)
  - Receptor GPS
  - Organitzador personal (PDA)
  - Cercapersones
  - Ordinador portàtil
  - Tauleta tàctil
  - Calculadora
  - Reproductor d’àudio digital
  - Consola portàtil
  - Càmera fotogràfica
  - Càmera de vídeo

## Enfocament d'Estudi
- **Telèfons Mòbils:** Es focalitzarà en els telèfons mòbils, donat que han adquirit gairebé totes les funcionalitats dels altres dispositius mòbils.

# Hardware dels Dispositius Mòbils

## Components Fonamentals
Els dispositius mòbils incorporen una sèrie d'elements clau en el seu hardware:

- **Placa Base:** La peça central que connecta tots els components.
- **CPU:** Unitat Central de Processament, sovint basada en arquitectura ARM.
- **GPU:** Unitat de Processament Gràfic, especialitzada en renderitzar imatges.
- **Memòria RAM:** Memòria d'accés ràpid utilitzada per a processar dades de manera eficient.
- **Memòria d’Emmagatzematge:** Inclou ROM i targetes de memòria per a l'emmagatzematge de dades.
- **Sensors:** Diversos sensors com acceleròmetres, giroscopis, sensors de proximitat, etc.
- **Antenes:** Inclouen antena mòbil, WiFi, i NFC per a diverses formes de connectivitat.
- **Bluetooth:** Permet la connectivitat sense fils amb altres dispositius.
- **Port Infraroig:** Menys comú en els models més recents, utilitzat per a controls remots.
- **Càmera:** Per a fotografies i vídeo.
- **Pantalla:** L'interfície visual de l'usuari.
- **Teclat:** Principalment en models més antics; els mòbils tàctils utilitzen teclats virtuals.
- **Micròfon i Altaveus:** Per a la captura i reproducció de so.
- **Bateria:** Font d'energia recarregable.
- **Port de Càrrega i Dades:** Inclou USB, micro USB, USB-C, entre altres.
- **Mòdul GPS:** Per a serveis de localització.

## Detalls Addicionals
- **Microprocessador:** Sovint una combinació de CPU i GPU, optimitzant rendiment i consum d'energia.
- **Connectivitat i Sensors:** Una àmplia gamma que facilita múltiples funcionalitats, des de navegació fins a la captura de moviments i entorn.

Aquests components treballen conjuntament per oferir una experiència d'usuari completa, des de la navegació per internet fins a l'ús d'aplicacions especialitzades.

# Arquitectura dels Dispositius Mòbils

## Arquitectura i Funcionament Bàsic

### CPU
- **Tipus:** La majoria dels dispositius mòbils utilitzen CPUs ARM, que són de tipus RISC (Reduced Instruction Set Computing), en contrast amb les CPUs CISC (Complex Instruction Set Computing) típiques en PCs convencionals.
- **Característiques de CPUs ARM:** Òptimes en termes de consum energètic, rapidesa, cost, simplicitat i grau d'integració. Pot incloure múltiples nuclis.

### Mòduls Específics
1. **Mòdul de RF (Ràdio Freqüència):**
   - Funció: Tracta les senyals que entren o surten del dispositiu.
2. **Mòdul d'AF (Àudio Freqüència):**
   - Funció: Converteix les senyals de Freqüència Intermitja (FI) del mòdul RF en senyals de veu audibles.
3. **Mòdul Lògic de Control:**
   - Arquitectura: Similar a un ordinador convencional.
   - Variacions: Pot haver-hi petites diferències segons la marca del telèfon (p. ex. Nokia).

### Sistema de Banda Base
- Components: 
  1. **Circuit Integrat Digital:**
     - Inclou un circuit de rellotge, ports CMOS, i s'encarrega del processament de senyals GSM (Global System for Mobile communications) a través de DSP (Digital Signal Processing).
     - Conté un microcontrolador amb RAM interna per a operacions diverses.
  2. **Circuit Integrat Analògic:**
     - Funcions: Incorpora un sistema de conversió A/D – D/A (analògic-digital i digital-analògic) per processar senyals de tipus IQ (I=fase, Q=Quadratura) i senyals de veu.
     - Addicionals: Control RF, control de càrrega de bateria, i sistema d'engegada del mòbil.
- Comunicació:
  - El circuit analògic comunica amb el digital mitjançant ports específics com BSP (port sèrie en banda base) i VSP (comunicació per veu), així com ports per sincronització com UPS (microcontrolador) i TSP (rellotge).

Aquesta arquitectura permet als dispositius mòbils operar de manera eficient, gestionant una àmplia varietat de tasques des de la comunicació fins a la navegació i processament de dades.

# Sistemes Operatius Mòbils

## Història i Variedad
Al llarg del temps, s'han desenvolupat diversos sistemes operatius per a dispositius mòbils, incloent:

- Android
- Bada
- BlackBerry OS
- EMUI
- Firefox OS
- iOS
- MeeGo
- MIUI
- Palm OS
- Symbian OS
- Windows CE
- Windows Mobile
- Windows Phone
- Moblin (proyecto)
- Maemo
- Sailfish OS

## Enfocament d'Estudi: Android i iOS

### Android
- **Tipus:** Sistema operatiu de codi obert.
- **Dispositius:** Present en Smartphones, tablets, Android TV, entre altres.
- **Característiques a Estudiar:**
  - **Estructura:** Com està organitzat i com funciona.
  - **Seguretat:** Mecanismes de protecció, privacitat i gestió de dades.

### iOS
- **Tipus:** Sistema operatiu propietari d'Apple.
- **Dispositius:** Utilitzat en iPhone, iPad, etc.
- **Característiques a Estudiar:**
  - **Estructura:** Organització i funcionament específics de iOS.
  - **Seguretat:** Estratègies de seguretat i privacitat implementades per Apple.

En els estudis subseqüents, es detallaran més profundament les particularitats d'aquests dos sistemes operatius, incloent la seva arquitectura interna, funcionalitats clau i protocols de seguretat.

# Seguretat en Dispositius Mòbils: iOS

## Sistema de Fitxers d'iOS

### Evolució del Sistema de Fitxers
- **HFSX (Sistema Jeràrquic d'Arxius):** Una variació del HFS+ (Sistema Jeràrquic d'Arxius Extès).
- **APFS (Sistema d'Arxius d'Apple):** Introduït el 2017, optimitzat per a unitats flash i d'estat sòlid, substituint HFSX.

### Estructura del Sistema de Fitxers
1. **Partició OS (Sistema Operatiu):**
   - `/Library/`: Plugins del sistema i configuració (àudio, Bluetooth, etc.).
   - `/private/`: Inclou `/etc/` i `/var/`, amb fitxers com `fstab` (discos i particions) i `passwd`.
   - `/System/`: Llibreries core del sistema.
   - `/usr/`: Binàris executables i dades de configuració horària.

2. **Partició DATA (Dades):**
   - `/Keychains/`: Conté `keychain.db`, amb contrasenyes d'usuari de diverses aplicacions.
   - `/Logs/`: Registres del sistema.
   - `/mobile/`: Informació d'aplicacions i configuració de l'usuari (contactes, calendari, cookies, correu, etc.).
   - `/Preferences/`: Configuració relacionada amb els recursos de la xarxa.
   - `/Root/`: Informació del GPS i de certificats.

Aquesta estructura del sistema de fitxers d'iOS reflecteix l'enfocament de la companyia en la seguretat i l'organització eficient de les dades, jugant un paper clau en la protecció de la privacitat i la seguretat de l'usuari.

# Sistema de Fitxers iOS: APFS

## Característiques Clau del APFS

### Suport per a Unitats Flash i SSD
- **Rendiment:** Disposa d'un disseny més ràpid i eficient, especialment adequat per a unitats Flash i SSD.

### Còpies Instantànies per a Backup i Restauració
- **Gestió de Dades:** Permet realitzar còpies de seguretat i restauracions de manera ràpida i eficaç.

### Encriptació Integrada
- **Seguretat:** Ofereix una capa addicional de seguretat mitjançant l'encriptació de dades.

### Optimització per a Dispositius Mòbils
- **Eficiència Energètica:** Disposa d'una optimització que millora el rendiment i redueix el consum d'energia en dispositius mòbils.

### Desduplicació de Dades
- **Gestió d'Espai:** Elimina dades duplicades per optimitzar l'espai d'emmagatzematge disponible.

### Resistència a Errades
- **Fiabilitat:** Dissenyat per ser resistent davant errors tant de hardware com de software.

El sistema de fitxers APFS d'iOS representa una evolució significativa respecte als sistemes anteriors, enfocant-se en la millora de la seguretat, l'eficiència i la gestió de dades, tot això mentre optimitza l'ús en dispositius mòbils amb unitats de memòria flash i SSD.

# Seguretat en iOS: Seguretat del Sistema

## Components de la Seguretat del Sistema
- Inclou el procés d'engegada del dispositiu, les actualitzacions de software, i el funcionament general del sistema operatiu.

## Característiques Clau de Seguretat

### Secure Enclave
- **Descripció:** Un coprocessador que incorpora un gestor de claus basat en hardware, aïllat del processador principal.
- **Funcions:**
  - Encriptació de les claus de dades.
  - Operacions amb un sistema en un xip (SoC), inclou un generador de nombres aleatoris.

### Encriptació dels Arxius (Crypto Engine)
- **Tecnologia:** Sistema de xifrat AES de 256 bits dedicat.

### Generació i Gestió de Claus
- **UID (Unique ID):** Única per a cada dispositiu, es crea durant la fabricació i no es pot llegir directament per software o firmware.
- **GID (Device Group ID):** Comú per a cada família de processadors (A5, A6, etc.).
- **Procés de Creació i Esborrat de Claus:** Segur i robust, inclou l'esborrat a través de l'Effaceable Storage (Emmagatzematge Eficaç).

### Altres Claus Criptogràfiques
- Generades pel generador de nombres aleatoris (RNG) del sistema, usant un algorisme basat en codi font CTR_DRBG.
- L'entropia del sistema es genera a partir de variacions temporals durant l'engegada i d'interrupcions de sincronització post-engegada.

Aquesta robusta infraestructura de seguretat en els dispositius iOS assegura la protecció de les dades de l'usuari, la integritat del sistema operatiu i la seguretat en les transaccions digitals.

# Seguretat iOS: Engegada del Dispositiu

## Procés d'Engegada i Seguretat

### Protecció de l'Arrencada i Execució del SO
- Assegura que el nivell més baix del software no està manipulat.
- Utilitza codi de la Boot ROM (iBoot) per iniciar el procés d'engegada.

### Arrel de Confiança de Hardware
- En la fabricació del xip, s'estableix que el codi de la Boot ROM és de confiança.
- Conté la clau pública Apple Root CA per verificar la signatura d'Apple en el codi d'engegada.

### Verificació i Execució del Codi
- Després de la Boot ROM, s'executa i verifica el nucli d'iOS.
- En dispositius antics, hi ha una etapa addicional LLB (Low-Level Bootloader) abans del iBoot.

### Gestió d'Errors en l'Engegada
- Si falla la càrrega de LLB (en dispositius antics): mode DFU.
- Si falla LLB o iBoot: mode de recuperació.
- En ambdós casos, cal connectar el dispositiu a iTunes per USB i restaurar a la configuració de fàbrica.

### Secure Enclave i BPR (Boot Progress Register)
- Secure Enclave: Coprocessador per a gestió de claus aïllat del processador principal.
- BPR: Utilitzat per Secure Enclave per limitar l'accés a les dades de l'usuari en diferents modes (DFU, mode de recuperació).

### Autorització de Software de Sistema
- Prevenció de downgrades a versions vulnerables d'iOS.

### Protecció del Nucli iOS (Kernel)
- KIP (Kernel Integrity Protection): Evita modificacions no autoritzades del codi del kernel.
- Controlador de Memòria: Protegeix una regió de memòria física on s'ha carregat el kernel i les extensions.
- Unitat de Gestió de Memòria (MMU): Configurada per evitar mapeigs de memòria física no autoritzats i escriptures fora de la regió de memòria del nucli.

Aquestes mesures de seguretat a l'engegada dels dispositius iOS són essencials per assegurar la integritat del sistema operatiu i protegir les dades dels usuaris contra manipulacions no autoritzades.

# Seguretat iOS: Actualització del Sistema

## Procediment d'Actualització
- **Origen del Software:** Només s'utilitza software conegut i aprovat per Apple.
- **Mètodes d'Actualització:** Es pot actualitzar mitjançant iTunes (descàrrega completa d'iOS) o OTA (Over-The-Air, descàrrega dels components necessaris).

## Verificació i Autorització durant l'Actualització
- **Interacció amb el Servidor d'Apple:** iTunes o el dispositiu en actualitzacions OTA es connecta al servidor d'autorització d'instal·lació d'Apple.
- **Enviament de Dades:** S'envia una llista de mesures criptogràfiques de cada part del paquet d'instal·lació, un valor aleatori antireproducció, i l'ECID (Exclusive Chip ID) del dispositiu.

## Procés de Signatura i Autorització
- **Comprovació de Mesures:** El servidor compara les mesures amb les versions autoritzades per a la instal·lació.
- **Personalització de l'Autorització:** Afegeix l'ECID a la mesura i signa el resultat, creant una autorització personalitzada per al dispositiu.
- **Seguretat de l'Actualització:** Assegura que l'actualització es realitza com Apple ha proporcionat.

## Avaluació de la Cadena de Confiança d'Arrencada
- **Verificació de Signatura:** Es comprova que la signatura és d'Apple i que la mesura del software carregat coincideix amb l'ECID del dispositiu.
- **Secure Enclave:** El coprocessador Secure Enclave utilitza el procés d'engegada segura per comprovar que el software està signat i verificat per Apple.

Aquestes mesures garantitzen que les actualitzacions del sistema operatiu iOS es realitzen de manera segura, mantenint la integritat del software i protegint els dispositius contra manipulacions no autoritzades o software maliciós.

# Seguretat en iOS

## Gestió i Seguretat d'Aplicacions
- **Format d'Aplicació:** .ipa (iOS App Store Package).
- **Llenguatges de Programació:** Principalment Objective-C i Swift.
- **Origen:** Només es permeten aplicacions de l'App Store.
  - **Xifrat d'Aplicacions:** Totes les apps estan xifrades i es desxifren durant l'execució.
  - **Verificació:** Apple verifica manualment totes les aplicacions.
  - **Excepció en Mode de Desenvolupament:** En aquest mode, les apps s'executen amb l'usuari "mobile".
  - **Aïllament d'Aplicacions:** Les apps estan aïllades per impedir l'accés a dades no autoritzades.

## Encriptació i Seguretat de Dades
- **Creació de Fitxers en la Partició de Dades:**
  - Cada fitxer creat s'associa amb una clau de xifrat de 256 bits i una clau de classe.
  - Per desxifrar el fitxer, es necessita la clau de classe del fitxer i el codi de desblocatge del telèfon.

### Encriptació de Volums Complets amb FileVault
- **Algoritme Utilitzat:** AES-XTS per a la protecció de volums complets, tant interns com extraïbles.
- **Encriptació del Volum APFS Intern:**
  - Protegeix l'accés no autoritzat, inclòs si el disc dur és traslladat a un altre dispositiu.
- **Ús del Xip T2:**
  - Aporta seguretat addicional i eficiència en la gestió de l'encriptació.
- **Objectius de Seguretat:**
  1. Desxifratge amb contrasenya d'usuari.
  2. Prevenció d'atacs de força bruta en dispositius d'emmagatzematge extrets.
  3. Mètode ràpid i segur per esborrar contingut eliminant el material d'encriptació necessari.
  4. Permet canviar la contrasenya sense necessitat de reencriptar tot el volum.

Aquestes mesures de seguretat en iOS són clau per a la protecció de les dades dels usuaris, assegurant que tant les aplicacions com les dades estiguin segures i protegides contra l'accés no autoritzat o manipulacions.

# Passcode en iOS: Seguretat i Gestió

## Configuracions i Temps d'Atac per Força Bruta
- **Passcode Estàndard:** 4 dígits (temps d'atac per força bruta: aproximadament 18 minuts).
- **Passcodes Més Llargs:** Més de 4 dígits (temps d'atac augmenta significativament).
- **Passcodes Alfanumèrics:** Entre 8 i 13 mil anys per un atac per força bruta.
  - **Detall:** Un passcode alfanumèric amb majúscules i números de 6 caràcters triga uns 5,5 anys a ser trencat per força bruta.
  - **Retard entre Intents:** Cada intent triga 80 mil·lisegons, amb un retard que s'incrementa entre intent i intent.

## Mesures Addicionals de Seguretat
- **Touch ID i Face ID:** Afegeixen capes addicionals de seguretat.
- **Bloqueig Automàtic:** Si el dispositiu no ha estat desbloquejat durant 1 hora.

## Situacions que Requereixen el Passcode
- Actualitzacions de software, esborrat del dispositiu, canvis en les configuracions del passcode, instal·lació de perfils de configuració d'iOS, després d'un reinici o si el dispositiu ha estat bloquejat remotament.
- Si no s'ha desbloquejat amb el passcode en els últims 6 dies i mig o amb mètodes biomètrics en les últimes 4 hores.
- Després de 5 intents fallits de desbloqueig biomètric o en iniciar l'opció d'emergència SOS.
- En connectar un accessori desconegut durant el període de bloqueig.

## Política d'Esborrat i Retard d'Intents Fallits
- **Esborrar Dades:** Opció per esborrar les dades del telèfon després de 10 intents fallits.
- **Política de Retards:**
  - 1 - 4 intents: Cap retard.
  - 5è intent: 1 minut.
  - 6è intent: 5 minuts.
  - 7è i 8è intents: 15 minuts.
  - 9è intent: 1 hora.

## Reversing iOS Apps
- **Xifrat d'Apps:** Les apps estan xifrades i és millor volcar-les des de la memòria quan s'estan executant.
- **Jailbreak:** Per a aquesta operació, cal un iPhone amb jailbreak (root).

Aquest sistema de passcode en iOS proporciona una protecció robusta contra intents d'accés no autoritzat, mitjançant la combinació de passcodes forts, mètodes de retard en els intents d'entrada i opcions de seguretat biomètriques.

# Sistema Android

## Visió General
- **Basat en:** Kernel de Linux amb software de codi obert.
- **Codi Font:** AOSP (Android Open Source Project) sota llicència d'Apache.
- **Propietari:** Google.
- **Aplicacions a Google Play (2018):** 2 milions.
- **Altres Botigues:** Existències d'altres tendes de codi obert amb aplicacions compatibles, com F-Droid.
- **Llenguatge de Programació:** Inicialment les aplicacions s'executaven en un framework Java.
- **Màquina Virtual Original:** Dalvik, amb compilació en temps d'execució (JIT - Just In Time).
- **Mida del Sistema Operatiu:** Al voltant de 12 milions de línies de codi.

## Evolució de les Aplicacions
- **Compilació del Codi Font:** Inicialment, els desenvolupadors creaven aplicacions en Java i les compilaven en arxius .class.
- **Traducció a Codi Dalvik:** Utilitzant eina dx del Android SDK, es traduïa a arxius .dex.
- **Empaquetat de l'Aplicació:** Combinació d'arxius .dex amb altres recursos en arxius .apk.
- **Instal·lació i Execució:** Descompressió d'arxius .dex i inici de DVM (Dalvik Virtual Machine).

## Transició a Android Runtime (ART)
- **Introducció:** A partir d'Android 4.4 "Kit Kat", amb una substitució completa en la versió 5.0 "Lollipop".
- **Funcionament d'ART:** 
  - Crea un arxiu de compilació durant la instal·lació de l'aplicació, evitant la necessitat de compilar cada vegada que s'executa.
- **Font d'Informació:** [Wikipedia sobre Android Runtime](https://es.wikipedia.org/wiki/Android_Runtime)

## Altres Detalls
- **Llançament d'Android:** Setembre de 2008.
- **Gestió de Dades:** Utilitza una base de dades SQLite.

Aquesta estructura i evolució de Android reflecteixen la seva naturalesa de codi obert i la seva adaptabilitat, amb milions d'aplicacions disponibles i un sistema operatiu en constant evolució.

# Arquitectura d'Android

## Versions d'Android
Cada versió d'Android té un nom distintiu, normalment relacionat amb dolços, i s'associa amb una lletra específica i un número de versió:

- **A:** Apple Pie - 1.0
- **B:** Banana Bread - 1.1
- **C:** Cupcake - 1.5
- **D:** Donut - 1.6
- **E:** Éclair - 2.0 / 2.1
- **F:** Froyo - 2.2
- **G:** Gingerbread - 2.3
- **H:** Honeycomb - 3.0 / 3.1 / 3.2
- **I:** Ice Cream Sandwich - 4.0
- **J:** Jelly Bean - 4.1 / 4.2 / 4.3
- **K:** KitKat - 4.4
- **L:** Lollipop - 5.0 / 5.1
- **M:** Marshmallow - 6.0
- **N:** Nougat - 7.0 / 7.1.1 / 7.1.2
- **O:** Oreo - 8.0 / 8.1
- **P:** Pie - 9.0
- **Q:** Android 10 - 10.0

## Components de l'Arquitectura

### Aplicacions
- Escrites principalment en Java.
- Aplicacions bàsiques incloses com el client de correu electrònic, SMS, calendari, mapes, navegador i contactes.

### Framework d'Aplicacions
- API completes disponibles per als desenvolupadors.

### Biblioteques
- Biblioteques nativas C/C++ com la System C library, biblioteques multimèdia, gràfiques, 3D, SQLite, entre d'altres.

### Runtime d'Android
- Anteriorment Dalvik, ara Android Runtime (ART).
- Compilació anticipada (AOT) quan s'instal·la l'aplicació.

### Nucli de Linux
- Gestiona la memòria, els processos, la pila de xarxa i el model de controladors.

# Sistema Android: Aplicacions i Sistema de Fitxers

## Aplicacions Android
- **Desenvolupament:** Principalment en Java, amb Android SDK o Google App Inventor.
- **Format d'Aplicació:** .APK (Android Application Package), variant del format JAR de Java.
- **Botigues d'Aplicacions:** Google Play (Play Store), Amazon Appstore, i altres.

## Sistema de Fitxers Android

### FileSystem YAFFS (Yet Another Flash File System)
- **Descripció:** Primer sistema de fitxers per a memòria Flash NAND.
- **Característiques:**
  - Wear leveling per prolongar la vida de les memòries Flash.
  - Robustesa en cas de fallades d'energia.
  - Minimització de la sobrecàrrega de la memòria RAM.
- **Versions:**
  - YAFFS1: Limitat a 1GiB, amb restriccions de grandària de fitxer i nombre.
  - YAFFS2: Suporta fins a 8GiB.

### FileSystem EXT4
- **Beneficis:** Major seguretat de dades i velocitat de lectura/escriptura.
- **Ús:** A partir de la versió Android 2.3 (Gingerbread).

### FileSystem F2FS (Flash-Friendly FileSystem)
- **Optimització:** Dissenyat per a SSDs o targetes SD.
- **Ús:** En dispositius de marques com Samsung, Motorola.
- **Rendiment:** Millor en accés a bases de dades i escriptures aleatòries que EXT4.

## Particions del Sistema Android

### /boot
- Conté bootloader i kernel. Essencial per a l'engegada del dispositiu.

### /system
- Conté el sistema operatiu, aplicacions pre-instal·lades i la interfície d'usuari.

### /recovery
- Utilitzat per la recuperació del sistema i el manteniment.

### /data
- Emmagatzema dades d'usuari com correus, contactes, configuracions de xarxa, etc.

### /cache
- Guarda informació d'ús habitual de l'usuari i aplicacions. Pot ser esborrat sense riscos.

### /sdcard i /sd-ext
- Per a dades i configuracions d'aplicacions. Inclou tant la memòria interna com targetes SD externes.

Amb aquesta estructura, Android proporciona un sistema operatiu flexible amb un enfocament modular en la gestió de fitxers i aplicacions.

# Seguretat Android

## Com Funciona la Seguretat en Android?
- **Aïllament d'Aplicacions:** Cada aplicació opera en una zona de proves de seguretat amb la seva pròpia màquina virtual (VM).
- **Usuari de Sistema Linux:** Android utilitza un model multiusuari on cada aplicació és un usuari diferent amb un ID únic.
- **Permisos de Fitxers:** El sistema estableix permisos perquè només l'aplicació amb l'ID d'usuari corresponent pugui accedir als seus fitxers.
- **Procés Independent:** Cada aplicació s'executa dins del seu propi procés Linux.
- **Gestió de Memòria:** Android inicia i tanca processos d'aplicació segons la necessitat de recursos o l'ús de l'aplicació.
- **Mínim Privilegi:** Les aplicacions només tenen accés als components que necessiten per la seva funció.

## Compartició de Dades i Serveis del Sistema
- **Compartició de Dades:** Es pot compartir dades entre aplicacions que tenen el mateix ID d'usuari i estan signades amb el mateix certificat.
- **Accessos Permisos:** Les aplicacions poden sol·licitar permisos per accedir a dades o serveis del dispositiu com contactes, missatges, càmera, etc.

## Components d'Aplicacions Android

### Activity (Activitat)
- Funciona com el punt d'interacció amb l'usuari.
- Cada activitat és independent i pot iniciar altres activitats.

### Services (Serveis)
- Operen en segon pla sense interfície d'usuari.
- Poden ser iniciats o enllaçats per altres aplicacions o pel sistema.

### Content Providers (Proveïdors de Continguts)
- Gestiona conjunts de dades que altres aplicacions poden consultar o modificar.
- Per exemple, administració de la informació de contactes del dispositiu.

### Broadcast Receivers (Receptors d'Emissions)
- Responen a events del sistema o emissions d'aplicacions.
- Poden operar fins i tot quan l'aplicació no està en execució.

## Sistema de Fitxers Android

### FileSystems Utilitzats
- **YAFFS:** Ideal per a memòria Flash NAND amb suport de wear leveling.
- **EXT4:** Utilitzat des de Gingerbread, millorant la velocitat i seguretat.
- **F2FS:** Optimitzat per a memòries SSD o targetes SD, utilitzat per Samsung i Motorola.

## Particions Android

- **/boot:** Conté el bootloader i el kernel, necessari per l'engegada del dispositiu.
- **/system:** Alberga el sistema operatiu, aplicacions preinstal·lades i la UI.
- **/recovery:** Utilitzat per a operacions de recuperació del sistema.
- **/data:** Emmagatzema les dades personals de l'usuari.
- **/cache:** Conté dades d'ús freqüent, pot ser esborrat sense riscos.
- **/sdcard:** Per a emmagatzemament de dades d'aplicacions, pot ser intern o en una targeta SD externa.

Amb aquesta arquitectura, Android garanteix que les aplicacions funcionen de manera segura i eficient, mantenint la privacitat i seguretat de les dades de l'usuari.

# Seguretat Android

## Activity Lifecycle
- **Gestió per l'S.O.:** El sistema operatiu gestiona l'execució de les activities.
- **Callbacks:** Especifica accions per a cada canvi d'estat de l'activity.
- **Tancament d'Apps:** Quan una app sembla tancada, en realitat l'S.O. gestiona quan es tanca completament.

## Entorn d'Execució i Memòria
- **C++ Natiu:** Execució de codi a nivell de sistema.
- **Java (JVM):** Utilitza la Java Virtual Machine per a executar aplicacions.
- **Seguretat de Memòria:**
  - **DEP (Data Execution Prevention):** Evita l'execució de codi en regions de memòria no executables.
  - **ASLR (Address Space Layout Randomization):** Aleatorització de l'espai d'adreces per dificultar els atacs.

## Debug i Permisos
- **Mode Debug:** Permet accés a la memòria durant el desenvolupament.
- **Permisos de Linux:** Gestiona els permisos d'usuari per propietari, grup i altres.

## Sandboxing i Control d'Accés
- **Sandboxing:** Cada Activity opera com un usuari diferent, sense privilegis de root ni system.
- **MAC (Mandatory Access Control):** Control d'accés obligatori, utilitzant la granularitat de SEAndroid, basat en SELinux.

## Sistema de Fitxers Xifrat
- Protegeix les dades emmagatzemades en el dispositiu.

## APK (Android Application Package)
- **Components:**
  - **AndroidManifest.xml:** Configuració, permisos i components de l'aplicació.
  - **META-INF:** Conté el manifest, el certificat de l'aplicació i una llista de recursos.
  - **classes.dex:** Classes compilades en format dex per la màquina virtual.
  - **res:** Recursos no compilats.
  - **resources.arsc:** Recursos precompilats.
  - **lib:** Codi compilat específic per l'arquitectura del processador.
    - **armeabi:** Per processadors ARM.
    - **x86:** Per processadors x86, i així successivament per altres arquitectures.

Aquesta estructura i mecanismes de seguretat en Android proporcionen un entorn segur i controlat per l'execució d'aplicacions, minimitzant el risc de vulnerabilitats i garantint la protecció de les dades de l'usuari.

# Permisos d'Android

Per concedir a les aplicacions l'accés a funcions específiques del dispositiu, es requereixen els següents permisos:

- `ACCESS_LOCATION_EXTRA_COMMANDS`
- `ACCESS_NETWORK_STATE`
- `ACCESS_NOTIFICATION_POLICY`
- `ACCESS_WIFI_STATE`
- `BLUETOOTH`
- `BLUETOOTH_ADMIN`
- `BROADCAST_STICKY`
- `CHANGE_NETWORK_STATE`
- `CHANGE_WIFI_MULTICAST_STATE`
- `CHANGE_WIFI_STATE`
- `DISABLE_KEYGUARD`
- `EXPAND_STATUS_BAR`
- `FOREGROUND_SERVICE`
- `GET_PACKAGE_SIZE`
- `INSTALL_SHORTCUT`
- `INTERNET`
- `KILL_BACKGROUND_PROCESSES`
- `MANAGE_OWN_CALLS`
- `MODIFY_AUDIO_SETTINGS`
- `NFC`
- `READ_SYNC_SETTINGS`
- `READ_SYNC_STATS`
- `RECEIVE_BOOT_COMPLETED`
- `REORDER_TASKS`
- `REQUEST_COMPANION_RUN_IN_BACKGROUND`
- `REQUEST_COMPANION_USE_DATA_IN_BACKGROUND`
- `REQUEST_DELETE_PACKAGES`
- `REQUEST_IGNORE_BATTERY_OPTIMIZATIONS`
- `SET_ALARM`
- `SET_WALLPAPER`
- `SET_WALLPAPER_HINTS`
- `TRANSMIT_IR`
- `USE_FINGERPRINT`
- `VIBRATE`
- `WAKE_LOCK`
- `WRITE_SYNC_SETTINGS`
- `CALL_PHONE`
- `PROCESS_OUTGOING_CALLS`
- `ACCESS_GPS`
- `ACCESS_COARSE_LOCATION`
- `ACCESS_COARSE_UPDATES`
- `ACCESS_FINE_LOCATION`
- `READ_PHONE_STATE`
- `READ_CONTACTS`
- `WRITE_CONTACTS`
- `SEND_SMS`
- `READ_SMS`
- `WRITE_SMS`
- `RECORD_AUDIO`
- `WRITE_EXTERNAL_STORAGE`

Cada permís ha de ser declarat a l'`AndroidManifest.xml` de l'aplicació i, segons la versió d'Android, l'usuari pot haver de concedir aquests permisos explícitament en temps d'execució.

# Seguretat Android

## Signatura d'Aplicacions
- **Verificació d'Integritat:** La signatura digital permet confirmar que una aplicació no ha estat alterada des de la seva creació.

## Authorities (Autoritats de Confiança)
- **Google Play:** Confiança principalment en signatures de Google.
- **Altres Botigues d'Aplicacions:** Confiança basada en el criteri de cada botiga.
- **Orígens Desconeguts:** Permet instal·lar apps de fonts no oficials, augmentant el risc de seguretat.

## Reversing Android
- **Màquina Virtual Dalvik:** On s'executen les aplicacions Android.
- **Format dex:** Dalvik Executable, format utilitzat per les aplicacions Android.
- **Compilació de Codi Font Java:** Inclou optimitzacions de memòria, reutilització de codi i gestió d'errors.

## Exemples d'Atacs i Vulnerabilitats
- **Self-Sign App:** Creació d'apps signades per l'atacant.
- **Cryo Root:** Obtenir privilegis de root en el dispositiu.
- **Links WhatsApp:** Enllaços maliciosos enviats a través de WhatsApp.
- **Pin Pantalla Visible:** Obtenir el PIN de la pantalla si es deixa visible.
- **Desbloquejar amb Foto:** Utilitzar una foto per enganyar el reconeixement facial.
- **AndroidTV Exposat:** Dispositius AndroidTV sense contrasenya establerta.
- **Bar Spoofing:** Suplantació de barres d'estat per enganyar l'usuari.
- **Man in the Middle:** Atacs en llocs públics utilitzant una connexió Wi-Fi no segura.
- **Enginyeria Social:** Tàctiques per manipular els usuaris a revelar dades personals.

La seguretat en Android és una responsabilitat compartida entre els desenvolupadors, les botigues d'aplicacions i els usuaris. És important mantenir-se informat sobre les pràctiques segures i estar al corrent de les actualitzacions de seguretat per protegir-se contra possibles amenaces.

