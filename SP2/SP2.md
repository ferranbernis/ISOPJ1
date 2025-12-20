<h1>Sprint 2. Instal·lació, Configuració de Programari de Base i Gestió de Fitxers</h1>



<h2>1. Sistemes de fitxers i Particions</h2>

<h4>Mida sector</h4> 
<p>És la unitat mínima física on es guarden les dades en un disc.
Per defecte, la mida del sector és de 512 bytes i no es pot modificar.</p>  
<img width="695" height="282" alt="image" src="https://github.com/user-attachments/assets/7534c445-fa4f-4955-81f0-41f33bbc5744" />


<h4>Mida block o clúster</h4> 
<p>És la unitat mínima lògica on es guarden les dades a nivell de sistema operatiu.
Per defecte, la mida és de 4096 bytes (8 sectors) i sí que es pot modificar quan es formateja la partició.
Cada partició del disc pot tenir una mida de bloc i un sistema de fitxers diferent.</p>  
<img width="707" height="98" alt="image" src="https://github.com/user-attachments/assets/56718c51-c336-4287-bbd0-e4e7c8105ca4" />

<h4>La fragmentació interna</h4>
<p>és l'espai no utilitzat dins del darrer bloc assignat a un fitxer. És l'espai perdut dins de les unitats d'emmagatzematge del disc.
Aquest concepte s'origina per la manera com els sistemes operatius gestionen l'espai del disc dur.</p>

<h4>La fragmentació externa</h4>

<p>es refereix a l'espai lliure d'emmagatzematge que no és contigu, sinó que es troba dispers en molts petits forats separats per fitxers que s'han mantingut al disc.
A diferència de la fragmentació interna (que és espai perdut dins d'un bloc), la fragmentació externa és espai lliure totalment utilitzable, però està tan segmentat que pot ser massa petit per allotjar eficaçment fitxers nous i grans.</p>

<p>La comanda e4defrag -c /home s'utilitza en sistemes Linux que fan servir el sistema de fitxers ext4 (el més comú) per comprovar el nivell de fragmentació del directori /home o del sistema de fitxers on es troba.</p>
<img width="521" height="82" alt="image" src="https://github.com/user-attachments/assets/4704b210-cbe1-4938-bf92-580d307ae766" />

<h4>Sistemes de fitxers</h4> 

<p>Sistemes Robustos i Moderns (Linux/Unix)</p>
<p>ext4 (Fourth Extended Filesystem): És l'estàndard de facto actual en la majoria de distribucions Linux. Ofereix un excel·lent rendiment i és molt fiable. La seva característica principal és el journaling (registre per diari), que prevé la corrupció de dades en cas de fallada del sistema.</p>

<p>Btrfs (B-Tree Filesystem): Considerat el futur de Linux. És un sistema Copy-on-Write (CoW), el que significa que cada vegada que es modifica una dada, s'escriu en una nova ubicació, mantenint la versió antiga intacta. Això permet la creació de snapshots (instantànies) molt ràpides i la autocuració d'errors.</p>

<p>XFS: Destaca per la seva escalabilitat i alt rendiment, especialment amb fitxers i volums de dades molt grans. És molt utilitzat en entorns de servidors on es treballa amb arxius massius.</p>

<p>ZFS: Un sistema de fitxers i un gestor de volums integrats que es caracteritza per una gran integritat de dades gràcies a l'ús de sumes de comprovació (checksumming) per detectar i corregir errors de dades. També utilitza el principi CoW.</p>

<p>Sistemes Propietaris (Windows/Mac)</p>
<p>NTFS (New Technology Filesystem): L'estàndard utilitzat per Windows. Incorpora journaling, suport per a ACLs (Llistes de Control d'Accés) per a permisos de seguretat detallats i la capacitat d'encriptació de fitxers.</p>

<p>APFS (Apple File System): El sistema modern d'Apple (macOS, iOS), optimitzat per a dispositius amb memòria flash (SSDs). Està centrat en l'eficiència i la creació d'instantànies ràpides i lleugeres.</p>

<p>Sistemes per a Compatibilitat (Transferència)</p>
<p>exFAT (Extended File Allocation Table): Creat per Microsoft, és l'opció preferida per a memòries USB i targetes SD. El seu avantatge és la compatibilitat universal entre Windows, Linux i macOS, a més d'eliminar la limitació de mida de fitxer de 4 GB que tenia el seu predecessor (FAT32).</p>

<p>FAT32 (File Allocation Table 32): Un sistema antic, però encara utilitzat per la seva compatibilitat amb gairebé qualsevol dispositiu (càmeres, consoles, reproductors). La seva limitació clau és que no pot emmagatzemar fitxers individuals de més de 4 GB.</p>

<p>Ubuntu EXT4</p>
<img width="745" height="243" alt="image" src="https://github.com/user-attachments/assets/f13d0a18-2bce-4e21-be3b-5bd46eb7f195" />

<p>Windows NTFS</p>
<img width="603" height="124" alt="image" src="https://github.com/user-attachments/assets/b6700966-2261-49fa-bbcb-081a921c714f" />

<p>Comprovem que se han creat amb el format correcte amb lsblk -f</p>
<img width="603" height="124" alt="image" src="https://github.com/user-attachments/assets/46f10528-77ac-47d1-848a-3e7c4553d1fe" />

<h4>Baix Nivell (Low-Level)</h4>
<p>Què fa: Aquest procés realitza una neteja total del disc.</p>
Resultat: Segons la teva definició, "Borra sistema de fitxers, borra formateig, etc.", eliminant totes les dades i totes les estructures lògiques prèvies. El disc queda en un estat de fàbrica, "com a nou", sense cap mena d'organització lògica (sense particions ni sistemes de fitxers).
Accessibilitat: No es pot fer des del sistema operatiu (SO) operatiu normal. Requereix programes adients i especialitzats, ja que treballa directament amb el firmware del disc dur.</p>

<h4>Mig Nivell (Mid-Level)</h4>
<p>Què fa: Aquesta és una operació que se centra en la capa lògica i la integritat del disc.</p>
Resultat: "Només borra el sistema de fitxers" (igual que el format d'Alt Nivell Ràpid), deixant les dades antigues presents però irrellevants per al SO. La funció distintiva és la comprovació de la integritat: si hi ha sectors defectuosos, els marca per evitar que el sistema operatiu els utilitzi en el futur, però "no els arregla".</p>

<h4>Alt Nivell (High-Level)</h4>
<p>Què fa: Aquesta és l'operació més comuna i ràpida.
Resultat: "Només borra el sistema de fitxers". El disc es prepara amb la creació del sistema de fitxers nou (p. ex., ext4 o NTFS) i el directori arrel. El contingut de les dades antigues roman al disc fins que es sobreescriu, cosa que permet la seva recuperació.</p>


<h3>GPARTED</h3>

<p>Desde el Gparted podem veure les particions de una manera grafica i crear modificar redimiencionar i etc...</p>
<img width="968" height="642" alt="image" src="https://github.com/user-attachments/assets/fbf4f020-d5fc-4f97-82a6-05115d84fb79" />

<p>Com la particio de ntfs no ha quedat ve i es de 4gb enves de 5gb redimencionarem la particio selecionarem el GB de espai que queda lliure i apretarem redimensiona</p>
<img width="972" height="327" alt="image" src="https://github.com/user-attachments/assets/e6c60478-ebe8-4986-a424-46808ae9085f" />
<img width="554" height="331" alt="image" src="https://github.com/user-attachments/assets/d4868dd7-65cf-4913-a61f-ba74db554b08" />

<p>Apretarem el tick verd i aplicarem els canvis</p>
<img width="795" height="428" alt="image" src="https://github.com/user-attachments/assets/075fc4a2-7e69-4189-95c8-b87e16d07fa3" />
<img width="964" height="269" alt="image" src="https://github.com/user-attachments/assets/fedcbb2c-9949-4f4f-a81a-9525305ba3a6" />

<p>Ara pasarem a un altre disc este te 25 GB nou i crearem una nova taula de particions gpt</p>  
<img width="971" height="195" alt="image" src="https://github.com/user-attachments/assets/074b22e7-2b4a-446e-940e-03dddacdd4d6" />
<img width="794" height="181" alt="image" src="https://github.com/user-attachments/assets/e91f8aa8-3a02-46c0-8ba5-24352a253099" />

<p>i assignarem els 25 GB tots a una particio apretant nova i selecionant els 25 GB</p> 
<img width="774" height="331" alt="image" src="https://github.com/user-attachments/assets/de14df9c-0192-4213-91b0-d152841122be" />

<p>Aplicariem els canvis i ja estaria</p>
<img width="971" height="280" alt="image" src="https://github.com/user-attachments/assets/b607d6df-ba4c-4511-ab40-d0eff3c06a18" />

<p>Ara montarem la particio sdb1 a /mnt/f1 carpeta creada amb mkdir dintre de mnt</p>
<img width="517" height="21" alt="image" src="https://github.com/user-attachments/assets/6d7d8d70-1f0e-41f8-817b-04d00556a6e6" />
<img width="602" height="48" alt="image" src="https://github.com/user-attachments/assets/40382591-abae-4ca4-9340-9918d930d0bf" />

<p>Crearem una carpeta per provar que funcioni correctament</p>
<img width="459" height="136" alt="image" src="https://github.com/user-attachments/assets/d9dabcef-57d3-448b-83ac-f41c55bdbfd2" />

<p>Afegim la partició /dev/sdb1 al fitxer /etc/fstab per muntar-la automàticament com a ext4 al punt `/mnt/f1` cada vegada que el sistema s'engegui</p>
<img width="741" height="323" alt="image" src="https://github.com/user-attachments/assets/f5001906-f858-43a4-bd9b-6d84526c4364" />



<h2>2. Gestió de Procesos</h2>

<p>Un procés és un programa que s’està executant en aquell moment, juntament amb tots els recursos que necessita per funcionar</p> 


<h4>pstree</h4>

<p>Pstree serveix per mostrar tots els procesos de el sistema operatiu en forma de arbre indicant quins procesos son pare  i quins fill</p>
<p><img width="751" height="728" alt="image" src="https://github.com/user-attachments/assets/302fcb1f-d158-4173-84c6-7e5dd23fb121" /></p>
<p><img width="746" height="672" alt="image" src="https://github.com/user-attachments/assets/7f19b325-944f-4dfe-85f5-2f7f89c57c55" /></p>
<p><img width="724" height="653" alt="image" src="https://github.com/user-attachments/assets/fbdffdfe-97d8-4cee-9e13-f3d0333000c9" /></p>


<h4>top</h4>

<p>Top serveix per mostrar en temps real els processos que s’estan executant i els recursos que utilitzen.</p>
<p>Quan executes top, veuràs informació com:</p>

<p>PID → identificador del procés</p>

<p>USER → usuari que executa el procés</p>

<p>%CPU → percentatge de CPU que està utilitzant</p>

<p>%MEM → percentatge de memòria RAM que utilitza</p>

<p>COMMAND → nom del procés</p>

<img width="920" height="780" alt="image" src="https://github.com/user-attachments/assets/ecf1684a-0583-48d8-8d78-5aca0408be95" />

<h3>Control de procesos</h3>


<h4>CTRL C</h4>
<p>ctrl c serveix per interrompre un procés que s’està executant envia el senyal SIGINT</p>
<p> En aquest exemple el ping para quan el usuari introdueix ctrl c sino es executara infinitament</p>
<img width="821" height="223" alt="image" src="https://github.com/user-attachments/assets/beb1b69d-c81c-4189-9d13-0637db577df6" />


<h4>CTRL Z</h4>  
<p>ctrl z serveix per aturar temporalment un procces i enviar-lo al “background” en estat suspès</p>
<img width="812" height="192" alt="image" src="https://github.com/user-attachments/assets/4e5d0eba-02d3-4f86-a94f-04b7d2a5b5d9" />

<h4>JOBS</h4>
<p>jobs Mostra els processos que tens en estat suspès o en segon pla</p>
<img width="431" height="79" alt="image" src="https://github.com/user-attachments/assets/36445c4c-56ba-43ce-91b4-c18c9bbbbd6a" />


<h4>FG</h4>
<p>fg % Torna en primer pla el proces amb el numero</p>
<p>Com es mostra a la imatge continua el ping i mostra que 6 paquets se han transmitit 2 avans de aturarlo i 4 despres</p>
<img width="811" height="211" alt="image" src="https://github.com/user-attachments/assets/ea9ac0ca-592a-4e3e-b1de-7f8512836049" />

<h4>HTOP</h4>
<p>htop mostra els processos del sistema en temps real, igual que top però amb una interfície més amigable: colors, barres de CPU/memòria i navegació amb el teclat i permet ordenar, filtrar i matar processos fàcilment sense escriure PID</p>
<p><img width="797" height="592" alt="image" src="https://github.com/user-attachments/assets/a5f9d00a-cec8-4978-b076-b2b20fdec386" /></p>

<h4>BTOP</h4>
<p>btop és una evolució moderna de htop i top, amb encara més gràfics i informació visual sobre el sistema </p>
<p>Mostra els processos del sistema, CPU, memòria, swap, discs i xarxa amb gràfics molt visuals.</p>
<p>Permet monitoritzar recursos en temps real de manera intuïtiva.</p>
<p>Té interfície de colors i menús interactius, amb navegació amb fletxes i tecles.</p>
<img width="1041" height="727" alt="image" src="https://github.com/user-attachments/assets/fabaa9d5-4393-4ef2-8881-257fc2b603c0" />



<h4>PS AUX</h4>
<p>ps aux s’utilitza per veure tots els processos que s’estan executant al sistema, amb informació detallada.</p>
<img width="1044" height="633" alt="image" src="https://github.com/user-attachments/assets/f1c1344a-c450-46c1-963a-2d5a1ca8b99d" />




<h4>kill</h4>

<p>kill serveix per enviar senyals a processos.
No només serveix per “matar” un procés; també pots suspendre-lo o reprendre’l.
Cada procés té un PID (identificador únic) que és necessari per enviar-li un senyal.</p>

<p>kill [opció] PID
PID → número del procés (el veus amb ps aux, jobs, top, htop)
Opcions → senyals que vols enviar (SIGTERM, SIGKILL, etc.)</p>

<p>| Senyal  | Número | Efecte                                                    |</p>
<p>| ------- | ------ | --------------------------------------------------------- |</p>
<p>| SIGTERM | 15     | Demana al procés que es tanqui de manera neta             |</p>
<p>| SIGKILL | 9      | Mata immediatament el procés (no neteja recursos)         |</p>
<p>| SIGSTOP | 19     | Suspèn el procés (equivalent a Ctrl+Z)                    |</p>
<p>| SIGCONT | 18     | Torna un procés suspès a executar-se (equivalent a fg/bg) |</p>


<p> Per exemple firefox te el pid 2344 i volem tancar el proces inmediatament utilizarem kill -9 2344 i inmediatament es ha tancat firefox 
<img width="1281" height="802" alt="image" src="https://github.com/user-attachments/assets/d4474593-a507-45b8-983c-c07d3e854365" />







<h2>3. Gestió d'usuaris i grups i permisos</h2>
<p>Gestio de Usuaris per interficie grafica amb gnome-system-tools</p>  
<img width="1028" height="685" alt="Captura de pantalla de 2025-11-04 12-50-16" src="https://github.com/user-attachments/assets/8c0a58f0-1adc-4bf7-bcd1-685ad955b6d9" />


<h3>Fitxers implicats</h3>
<p>El arxiu Passwd emmagatzema informació bàsica sobre tots els usuaris del sistema</p>
<img width="883" height="690" alt="Captura de pantalla de 2025-11-04 12-53-12" src="https://github.com/user-attachments/assets/6ed429c9-94cd-4ba7-a60f-bf0c0f661f6c" />

<p>El arxiu groups gestiona els grups d’usuaris</p>
<img width="876" height="752" alt="Captura de pantalla de 2025-11-04 12-56-24" src="https://github.com/user-attachments/assets/222fc464-5cac-4000-b00c-b50b85ee68f8" />

<p>El arxiu shadow emmagatzema les contrasenyes xifrades dels usuaris i informació addicional de seguretat</p>
<img width="981" height="745" alt="image" src="https://github.com/user-attachments/assets/2eee2fec-e44d-43b9-87c9-aac2bcb3eb51" />

<p>El arxiu gshadow es equivalent a shadow pero amb grups </p>
<img width="981" height="745" alt="Captura de pantalla de 2025-11-04 12-58-48" src="https://github.com/user-attachments/assets/9d8ad1cc-646d-4c7a-b1a3-00ac9e4c7d61" />

<h3>Comandes basiques</h3>
<p>Crearem el usuari gina amb adduser</p>  
<img width="638" height="365" alt="image" src="https://github.com/user-attachments/assets/4fe541b1-0aff-42a0-b53f-64393a86eaa5" />

<p> Iniciem sesio amb el usuari gina i apareixerant les carpetes</p>  
<img width="781" height="112" alt="image" src="https://github.com/user-attachments/assets/94c083bf-f4af-4494-a27f-7544aafaf2a8" />

<p>Crearem el usuari gina2 amb useradd</p>  
<img width="978" height="548" alt="image" src="https://github.com/user-attachments/assets/14ede398-4252-4f88-96d9-2a9cf598a104" />

<p>Comprovarem que gina no es administradora (sudo) i la afegirem a el grup sudo (administradors)</p>
<img width="793" height="744" alt="image" src="https://github.com/user-attachments/assets/4a9456f5-937e-42d7-984a-585e5f30bce8" />

<p>Eliminarem el usuari gina amb deluser que elimina tot el relacionat amb el usuari i eliminarem gina2 amb userdel que es una comanda que sol elimina el usuari i no les carptes</p>
<img width="747" height="351" alt="image" src="https://github.com/user-attachments/assets/bd0e73ea-6b64-4089-9d2c-005745eff1ee" />

<p>Bloquejar i desbloquejar un Usuari </p>
<img width="912" height="220" alt="image" src="https://github.com/user-attachments/assets/19bee0d1-46d3-4767-8458-87eaffb7d2a7" />

<p>Modificar un Grup i eliminarlo</p>
<img width="587" height="154" alt="image" src="https://github.com/user-attachments/assets/1376a1c3-ba7e-41d8-a871-8cebb9f70a42" />

<p>Crear un grup Nou</p>
<img width="863" height="151" alt="image" src="https://github.com/user-attachments/assets/5ff50acf-2849-4915-a246-d9f849a7c07a" />

<p>Afegir Usuaris a un grup de 3 diferentes maneres</p>
<img width="703" height="228" alt="image" src="https://github.com/user-attachments/assets/b8f39d9d-5f38-45c5-a9c1-e9a98649f217" />

<p>Afegir Usuari administrador de un grup</p>
<img width="598" height="116" alt="image" src="https://github.com/user-attachments/assets/eb641b82-e8f1-4307-9c5e-41d7656481a9" />

<p>Afegir el grup principal de el Usuari </p>
<img width="590" height="187" alt="image" src="https://github.com/user-attachments/assets/76bea46c-7e1c-492e-ac9f-eb4c1adfab1f" />

<p> Crearem els usuaris roig,blau,groc i verd</p>
<img width="474" height="119" alt="Captura de pantalla de 2025-11-17 11-53-36" src="https://github.com/user-attachments/assets/663e07df-6e2a-4130-86da-25b6b8c3fcce" />

<p> Crearem el grup dames </p>
<img width="429" height="80" alt="Captura de pantalla de 2025-11-17 11-54-56" src="https://github.com/user-attachments/assets/877671b7-4c0c-4b60-ab74-0b9e7f52dff7" />

<p> Modificarem el nom de el grup amb groupmod de dames a parchis </p>
<img width="526" height="61" alt="Captura de pantalla de 2025-11-17 11-55-08" src="https://github.com/user-attachments/assets/40f2b9be-a51c-4e61-b2de-5a6b74826e5d" />

<p> Agregarem el usuari groc i roig com a grup principal a el grup parchis </p>
<img width="531" height="47" alt="Captura de pantalla de 2025-11-17 11-57-00" src="https://github.com/user-attachments/assets/5137c25b-415f-461b-9dbe-a6aed2bacf25" />
<img width="515" height="42" alt="Captura de pantalla de 2025-11-17 11-57-11" src="https://github.com/user-attachments/assets/5912d1b5-eb70-4179-92e9-0358bbe209cf" />

<p> Ara intentarem eliminar el grup parchis pero no ens deixara perque te un usuari principal que es roig </p>
<img width="616" height="102" alt="Captura de pantalla de 2025-11-17 12-03-15" src="https://github.com/user-attachments/assets/8ef9c4a9-7d41-4713-a32c-29cfba2ffd6f" />

<p> Despres entrarem a cd /etc/skel i veurem que tenim varios arxius mos centrarem en 3 de ells .bash_logout,bashrc i .profile els canvis que fesem en aquestos arxius es aplicaran als usauris futurs  </p>
<img width="605" height="388" alt="Captura de pantalla de 2025-11-17 12-07-39" src="https://github.com/user-attachments/assets/0b06dfe2-ce2d-45c6-8261-0b77c1fb2c29" />

<p> Entrarem a el arxiu adduser.conf que serveix per a modificar els determinats de adduser i editarem el shell a bash i que la carpeta home del usuari estigui ubicada a /var i modificarem el UDI de creacio de els usuaris que comencigue a partir de 3000 </p>
<img width="757" height="575" alt="Captura de pantalla de 2025-11-17 12-11-32" src="https://github.com/user-attachments/assets/a846aeda-4de7-4be0-bfff-fe45eb3a9263" />

<p> Ara pasarem a el segon arxiu login.dfs que modifica els parametres de quan un usuari incia sesio i modificarem el maxim de dies que estara el minim i el avis</p>
<img width="737" height="243" alt="Captura de pantalla de 2025-11-17 12-13-54" src="https://github.com/user-attachments/assets/1a445bfc-57b1-4e92-a59c-9015e5df5255" />


<p>Un grup es por esborrar i a els usuaris no els pasa res a no ser que algun usuari el tingui com a grup principal</p>
<img width="414" height="45" alt="Captura de pantalla de 2025-11-17 11-57-57" src="https://github.com/user-attachments/assets/59ca7721-135b-4fe9-a01e-04a2cf0804fb" />
<img width="414" height="45" alt="Captura de pantalla de 2025-11-17 11-57-57" src="https://github.com/user-attachments/assets/ad513f64-c801-4c62-87d0-1d60e0694de6" />


<p>tot el que es posi a la carpeta /etc/skel es copiara a la home de el usuari</p>
<img width="605" height="388" alt="Captura de pantalla de 2025-11-17 12-07-39" src="https://github.com/user-attachments/assets/fb8168c7-02ac-4695-9435-39d2e080ed37" />


<p>Ara entrarem a el arxiu adduser.conf que son els parametres de la comanda adduser que serveix per crear usuaris introduirem que la Shell la volem en bash i que la carpeta home la volem a /var</p>
<img width="636" height="242" alt="Captura de pantalla de 2025-11-17 12-11-13" src="https://github.com/user-attachments/assets/4431ec59-7a13-471f-bec1-76f66366afe0" />


<p>i canviarem que crei els id de els usuaris a partir de 3000</p>
<img width="757" height="575" alt="Captura de pantalla de 2025-11-17 12-11-32" src="https://github.com/user-attachments/assets/6009580e-22a3-47de-8ea4-9a2b5353c28f" />

<p>Despres obrerem el arxiu login.defs que modifica es regles generals del sistema per a:
contrasenyes
creació d’usuaris
permisos
comportament del login</p>

<p> Introduirem que la contrasenya tingui un maxim de 20 dies i un minim de 15 dies i que te avise als 3 dies</p>
<img width="737" height="243" alt="Captura de pantalla de 2025-11-17 12-13-54" src="https://github.com/user-attachments/assets/c827feb8-6e37-4ed9-9031-9b87a61fcbbd" />

<p>Crearem el usuari gris i comprovarem que tot el anterior es hagui aplicat correctament</p>
<img width="852" height="438" alt="Captura de pantalla de 2025-11-17 12-15-31" src="https://github.com/user-attachments/assets/37c69459-d9c4-48f4-80dc-df27b3c29cea" />

<p>Si comenca a assignar a partir de el 3000</p>
<img width="483" height="57" alt="Captura de pantalla de 2025-11-17 12-15-58" src="https://github.com/user-attachments/assets/ec1c165a-18b2-494d-8951-3164fffbf37c" />

<p>Si la contrasenya la caducitat assignada a el arxiu login.defs</p>
<img width="865" height="40" alt="Captura de pantalla de 2025-11-17 12-16-59" src="https://github.com/user-attachments/assets/d009641c-b3d0-4697-b469-d5dcedf18627" />

<p>I tambe es ha creat la carpeta prova que haviem creat a etc/skel </p>
<img width="504" height="183" alt="Captura de pantalla de 2025-11-17 12-17-56" src="https://github.com/user-attachments/assets/64f22801-b2a5-412a-8fae-ba6878c2b604" />

<p>Ara modificarem el useradd i canviarem el shell a bash</p>
<img width="918" height="382" alt="Captura de pantalla de 2025-11-17 12-19-56" src="https://github.com/user-attachments/assets/76ddda7f-0644-491f-a52f-59ad4e9ae22b" />

<p>Crearem el usuari negre amb useradd i comprovarem el id que es 3001 i que esta en bash</p> 
<img width="501" height="66" alt="Captura de pantalla de 2025-11-17 12-20-36" src="https://github.com/user-attachments/assets/e3497563-6f11-45e7-a290-036c49a70a8a" />

<p>Comprovarem la caducitat de la contrasenya</p> 
<img width="487" height="68" alt="Captura de pantalla de 2025-11-17 12-21-05" src="https://github.com/user-attachments/assets/a350bc0f-a685-41fa-b8a2-cf584a07ef84" />

<p>Ara entrarem a .profile i introduirem que els usuaris cuan facin login estiguin ven situats al directori /var</p>
<img width="729" height="566" alt="Captura de pantalla de 2025-11-17 12-27-37" src="https://github.com/user-attachments/assets/c0e83f5b-fa39-4cc5-baa4-af3a36e5d675" />

<p>Ara a el archiu .bashrc afegirem un alias quan escriguen alias connexio es fara un ls -la</p>
<img width="721" height="305" alt="Captura de pantalla de 2025-11-17 12-30-42" src="https://github.com/user-attachments/assets/18e29570-ad06-4d62-93ba-f0b7f0a81294" />

<p>Despres entrarem a el arxiu bash_logout i introduirem que cuan el usuari tanqui la sesio es elimini el seu directori personal</p> 
<img width="721" height="305" alt="Captura de pantalla de 2025-11-17 12-31-51" src="https://github.com/user-attachments/assets/431ccf76-1f1e-4d39-922f-3598176e64a6" />

<p>Ara entrarem a el usuari rosa i comprovarem que estigui a la carpeta correcta /var/rosa</p> 
<img width="676" height="696" alt="Captura de pantalla de 2025-11-17 12-34-30" src="https://github.com/user-attachments/assets/7c5c2ffe-57bd-4ace-a57b-bdca1eb40f71" />

<p>Tancarem la sesio i tornarem a obrirla i es haura eliminat tot per el introduit anteriorment a el arxiu bash_logout</p>
<img width="619" height="356" alt="Captura de pantalla de 2025-11-17 12-35-33" src="https://github.com/user-attachments/assets/bce3892a-652a-4655-8ad8-cbe8e9adf99d" />


<h3>Gestio permisos</h3>

<p>Primer de tot crearem la carpeta palomes i el grup palomes i afegirem a el usuari nick com a propietari amb chown -R tambe assignarem paloma com a grup de la carpeta</p> 
<img width="576" height="331" alt="Captura de pantalla de 2025-11-18 13-49-12" src="https://github.com/user-attachments/assets/bc3be556-4ab1-45e1-90ac-a397e0281a9c" />

<p>Despres modificarem els permisos de la carpeta amb chmod 750 que simifica permisos totals per a el usuari permisos de lectura i execucio per a el grup i no permisos per als altres</p>  
<img width="512" height="79" alt="Captura de pantalla de 2025-11-18 13-51-25" src="https://github.com/user-attachments/assets/8e993be5-746a-469b-a293-842800a8395d" />



<p>Ara amb chmod o+r donarem permisos als altres per a lectura i en chmod o-r llevarem el permis de llectura als altres i amb ls -l | grep palomes veurem els permisos sol de la carpeta palomes</p>  
<img width="507" height="138" alt="Captura de pantalla de 2025-11-18 13-52-34" src="https://github.com/user-attachments/assets/fe123a6f-77bd-4bc2-8334-56ad7d4938cd" />



<p>Ara comprovarem els permisos primer amb el usuari nick que podrar entrar a la carpeta crear el arxiu sdfsdf i escriure dints despues pasarem a el usuari cire podra entrar dints de la carpeta pero no podra crear cap arxiu i despues provarem amb el usuari ferran que no podrar entrar dints de la carpeta perque nick es el propietari i te permisos totals cire es un usuari de el gurp paloma i ferran es altres que no tenen cap permis</p>   
<img width="948" height="385" alt="Captura de pantalla de 2025-11-18 13-54-14" src="https://github.com/user-attachments/assets/010f0889-6b17-4dbb-bdad-13a19c64f48f" />


<p>Ara afegirem a ferran i a deivy a el grup paloma amb adduser el nom de el usuari i el grup en el que el vols afegir</p>
<img width="722" height="284" alt="Captura de pantalla de 2025-11-18 13-55-40" src="https://github.com/user-attachments/assets/4c99b31b-6f97-4190-a4ad-c46650e603b3" />


<p>Despres en chmod g+w afegirem a el grup paloma el permis de escriptura i ho comprovarem amb ls -l</p> 
<img width="509" height="94" alt="Captura de pantalla de 2025-11-18 13-56-48" src="https://github.com/user-attachments/assets/414eb29d-3e46-4908-bbc6-cbb52c1b310b" />


<p>Devy creara el arxiu practicavaras i ferran el eliminara</p> 
<img width="942" height="368" alt="Captura de pantalla de 2025-11-18 13-58-46" src="https://github.com/user-attachments/assets/a2573745-3011-4fc8-b1af-9d0222f98eee" />

<p>Per evitar que ferran elimini arxius que no son de ell introduirem chmod o+t a la carpeta palomes simifica que sol el propietari de el arxiu el pugi eliminar aquesta regla es nombra sticky bit</p>
<img width="525" height="64" alt="Captura de pantalla de 2025-11-18 14-01-14" src="https://github.com/user-attachments/assets/7f1abc2d-ddf9-462c-902e-da5ed969b988" />

<p>Ara torarem a crear el arxiu practicavaras i ferran el intentara tornar a elminiar pero ya no podrar</p> 
<img width="816" height="456" alt="Captura de pantalla de 2025-11-18 14-03-53" src="https://github.com/user-attachments/assets/0e9aee55-d820-4eed-b30a-5446cf26c49a" />

<p>Traurem el sticky amb chmod o-t i ho tornare a posar amb un chmod 1770 pero ara amb numeros</p> 
<img width="603" height="421" alt="Captura de pantalla de 2025-11-18 14-05-11" src="https://github.com/user-attachments/assets/e971bee4-df4c-42fa-a7cf-fa1b5356d931" />

<p>Ara amb chmod g+s el usuari que execute el arxiu el executara amb els permisos de el grup no de el propi usuari</p> 
<img width="575" height="402" alt="Captura de pantalla de 2025-11-18 14-08-00" src="https://github.com/user-attachments/assets/e3b56bda-32d6-4072-ab4f-306310c8319c" />



<h3>ACL</h3>
<p>Crearem la carpeta proves i el arxiu proves2</p> 
<img width="437" height="26" alt="Captura de pantalla de 2025-11-24 11-58-58" src="https://github.com/user-attachments/assets/183ce5cc-2a9e-4e68-84a3-292dd7595da5" />
<img width="437" height="26" alt="Captura de pantalla de 2025-11-24 11-58-52" src="https://github.com/user-attachments/assets/bbfb613b-43b6-40dc-beff-cca2dc13872a" />

<p>Comprovarem els permisos per defecte que son:</p> 
<p>proves:755 (rwxr-xr-x): El propietari té tots els permisos (7), i el grup i els altres només poden llegir i executar/accedir (5).</p> 
<p>proves2: 644 (rw-r--r--): El propietari pot llegir i escriure (6), i el grup i els altres només poden llegir (4). </p> 
<img width="502" height="80" alt="Captura de pantalla de 2025-11-24 11-58-41" src="https://github.com/user-attachments/assets/4a127a28-5ed6-4afc-8e3e-959527aa2434" />

<p>Ara canviarem els permisos i els comprovarem en getfacl que mostra la llista de control d’accessos (ACL) 
<p>És a dir, et mostra:</p> 

<p>Permisos normalSprint 2. Instal·lació, Configuració de Programari de Base i Gestió de Fitxerss (rwx)</p> 

<p>Permisos extensos (ACL) si n’hi ha</p> 

<p>Propietari i grup</p> 

<p>Entrades especials com mask i permisos heretats</p> 

<img width="502" height="404" alt="Captura de pantalla de 2025-11-24 12-00-15" src="https://github.com/user-attachments/assets/9bf553f1-f70f-40b0-afa6-84057aff7074" />


<p>amb setfacl, atorgant a l'usuari específic roig permisos addicionals de Lectura i Escriptura (rw-) sobre el fitxer proves2, sense modificar els permisos estàndards del grup o d'altres.</p> 
<img width="624" height="232" alt="Captura de pantalla de 2025-11-24 12-02-51" src="https://github.com/user-attachments/assets/15cca446-631e-439d-a6ae-96a135e1aada" />


<p>Si entro a el arxiu com a el usuari roig el puc modificar</p>  
<img width="736" height="665" alt="Captura de pantalla de 2025-11-24 12-16-29" src="https://github.com/user-attachments/assets/bd5a45ae-5ac7-44b2-9a9a-8d1de4ced7a4" />

<p>i si entro com a el usuari blau no perque es altres i no te permisos com demostra el getfacl</p> 
<img width="732" height="620" alt="Captura de pantalla de 2025-11-24 12-03-51" src="https://github.com/user-attachments/assets/d2e6582b-da54-4f84-88d2-736ad9ea7c0e" />

<p>Si volem eliminar totes les ACL de proves2 podem ferho amb la comanda setfacl -b proves2</p> 
<img width="739" height="484" alt="Captura de pantalla de 2025-11-24 12-22-34" src="https://github.com/user-attachments/assets/986108fb-f6f5-402a-8524-a063bfef78e8" />

<p>Crearem una carpeta que es dira compartida i tindra permisos 777 que son tots els permisos a tothom pero ara modificarem perque volem que el usuari roig no tingui cap permis amb setfacl -m user:roig --- compartida/</p>  
<p>(Els tres gions simifica cap permis)</p> 
<img width="622" height="256" alt="image" src="https://github.com/user-attachments/assets/9a8a864d-509f-41ce-84ff-a54b1cbbec42" />



<h3>Mascara</h3>
<p>Explicar la mascara de el usuari cuan el usuari crea una carpeta els permisos que es creen per defecte</p> 

<p>Primer de tot veurem en la comanda unmask la mascara de el usuari i la mascara quan el usuari es root</p> 
<img width="530" height="215" alt="Captura de pantalla de 2025-11-25 13-12-11" src="https://github.com/user-attachments/assets/7b8f355e-b0c7-4b04-84aa-fb614a9c430a" />

<p> Despres entrarem a el arxiu login.defs que defineix els parametres globals de els usuaris i podrem modificar la mascara de els usuaris que es creein despres de la modificacio</p> 
<img width="747" height="669" alt="Captura de pantalla de 2025-11-25 13-13-01" src="https://github.com/user-attachments/assets/c61cf294-9d02-4ec8-93a3-5a72689dc31a" />


<p>Per a canviar la mascara de el usuari actual entrarem a el arxiu .profile i canviarem la mascara</p> 
<img width="743" height="663" alt="Captura de pantalla de 2025-11-25 13-14-24" src="https://github.com/user-attachments/assets/1e585f01-98b9-41d8-bc9e-ba167bc80b5f" />

<p>Ara si volem canviar la mascara de un usuari temporalment hasta que reinici i comprovarem creant una carpeta i un arxiu que la mascara  </p> 
<img width="728" height="185" alt="Captura de pantalla de 2025-11-25 13-17-08" src="https://github.com/user-attachments/assets/b14aa729-7e2f-4f49-8013-825293846eb3" />


<p>Ara Modificarem el arxiu login.defs i canviarem la mascara de 22 a 33 </p> 
<img width="742" height="341" alt="Captura de pantalla de 2025-11-25 13-19-11" src="https://github.com/user-attachments/assets/10887633-9390-436e-a337-c9a82f3ecd61" />

<p>Crearem el usuari prova</p>  
<img width="724" height="331" alt="Captura de pantalla de 2025-11-25 13-20-46" src="https://github.com/user-attachments/assets/6f70fd0e-a7dd-4274-944e-105aa0daacc7" />

<p> Crearem una carpeta i un axiu i comprovarem que la mascara 33 es ha aplicat</p> 
<img width="472" height="149" alt="Captura de pantalla de 2025-11-25 13-23-34" src="https://github.com/user-attachments/assets/421959cd-6277-4296-b3bf-cb10a9ae697b" />



<h2>4. Còpies de seguretat i automatització de tasques</h2>

<h3>1.Teoria copies de seguretat</h3>

Que es una copia de seguretat i els tres tipus i que es neccesita

Completa
Neccesita res

diferencial 
Neccesita una completa

incremental

1 completa o diferencial 




<h3>2.Teoria commandes Backups</h3>

**CP** es una copia simple que no es inteligent transfereix arxius nomes localment i no optimiza ni temps ni espai</p>

**RSYNC** es una eina inteligent que nomes copia els fitxers modificats treballa en local i en remot</p>

**DD** no es una eina per a copiar pero cuan volem copiar tot un disc o particio se utilizar es per a clonar</p>




<h3>3.Practica commandes Backups</h3>
<h4>1.cp</h4>
<h4>2.rsync</h4>
<h4>3.dd</h4>

<h3>4.Practica programes Backups</h3>
<h4>1.Deja-Dup</h4>
<h4>2.Duplicity</h4>

<h3>5.Teoria de automatizacio scripts, cron i anacron</h3>
Cron i anacron son dues eines de automatizacio per a exectutar tasques periodiques son a traves de scripts 

**Cron** Executa tasques programades en una data i una hora especifiques si el sistema esta apagat la tasca es perd es ideal per a tasces en dates i hores conquretes i per a accions especifiques de un usuari 

**Anacron** es ideal per a executar tasques periodices on no cal una data i una hora especifica normalment se utiliza per a tasques de el manteniment de el sistema no requereix que el sistema estigui obert perque cuan se obrigue ja la executara no es perd la tasca com en el Cron 

<h3>6.Practica automatizacio</h3>
<h4>1.Cron</h4>
<h4>2.anacron</h4>






<h2>5. Quotes d'usuari</h2>

Una cuota de disc es la llimitacio que es dona als usuaris de espai de el disc







