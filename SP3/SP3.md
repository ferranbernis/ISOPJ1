<h1>Sprint 3: Administració de Dominis i Seguretat</h1>

<img width="1280" height="668" alt="image" src="https://github.com/user-attachments/assets/1ba31aca-a759-46af-b1b5-cb763b9e604b" />


<p>1. Usuaris, Grups i Recursos
Són els objectes bàsics que conté el directori:
Usuaris: Comptes individuals per a persones (com el teu usuari ferranbernis).
Grups: Conjunts d'usuaris (ex: grup "professors", grup "alumnes") per gestionar permisos de cop.
Recursos: Impressores, carpetes compartides o servidors que estan registrats a la xarxa.</p>

<p>2. Unitats Organitzatives (OU)
Pensa en les OU com a carpetes o contenidors dins del servidor. Serveixen per organitzar els objectes segons la lògica de l'empresa o centre:
Exemple: Una OU anomenada Sistemes i una altra Administració.
Permeten aplicar polítiques (GPOs) diferents a cada grup.</p>

<p>3. L'Arbre (Tree)
Un Arbre és un conjunt d'un o més dominis que comparteixen un espai de noms continu (un nom arrel).
Si el teu domini principal és fje.edu, un subdomini anomenat clot.fje.edu formaria part del mateix arbre. Tots comparteixen una relació de confiança i una base de dades comuna.</p>

<p>4. El Bosc (Forest)
El Bosc és el nivell més alt del disseny. És un conjunt d'un o més arbres que no necessàriament comparteixen el mateix nom, però sí que comparteixen el mateix esquema (les regles de què pot contenir el directori) i configuració.
Exemple: Si l'escola fje.edu compra una empresa anomenada empresa.com, podrien unir els dos arbres en un mateix bosc per poder compartir recursos entre ells.</p>




<h2>Servidor LDAP</h2>

<p>Primer de tot canviarem de DHCP a IP manual</p>
<img width="584" height="472" alt="image" src="https://github.com/user-attachments/assets/6b85db42-4e9a-4f0e-8cf3-612ad963416d" />

<p>Despres canviarem el Hostname</p>
<img width="805" height="114" alt="Captura de pantalla de 2026-01-12 12-08-53" src="https://github.com/user-attachments/assets/b9f3d649-0690-4e8d-b442-abd3cbd61993" />

<p>Ara instalarem LDAP en apt install slapd ldap-utils</p>
<img width="798" height="354" alt="Captura de pantalla de 2026-01-12 12-26-37" src="https://github.com/user-attachments/assets/4b802025-da7c-4df9-8feb-5b3b8f4f18c9" />

<p>Amb la comanda slapcat comprovarem que es ha instalat correctament </p>
<img width="521" height="292" alt="Captura de pantalla de 2026-01-12 12-26-57" src="https://github.com/user-attachments/assets/a2fc5c96-c19d-42a1-b536-97abfb6e4a08" />

<p>Descarregarem el arxiu de el moodle i el descomprimirem</p>
<img width="696" height="205" alt="Captura de pantalla de 2026-01-12 12-27-47" src="https://github.com/user-attachments/assets/29af705c-c9cf-4fea-b80f-80601be5fbee" />

<p>Ara introduirem dpkg-reconfigure slap que serveix per reconfigurar el LDAP</p>
<img width="743" height="25" alt="Captura de pantalla de 2026-01-12 12-28-37" src="https://github.com/user-attachments/assets/61c769c9-eff1-45b2-bf5a-4ecfcd87ae38" />

<p>Respondrem que no volem omitir la configuracio de el servidor LDAP perque el volem configurar</p>
<img width="1029" height="774" alt="Captura de pantalla de 2026-01-12 12-29-20" src="https://github.com/user-attachments/assets/632bd0f3-da58-4482-a77e-0f4f265af717" />

<p>Introduirem el Nom de domini per exemple gina.cat</p>
<img width="1161" height="774" alt="Captura de pantalla de 2026-01-12 12-29-39" src="https://github.com/user-attachments/assets/951f547d-f6cb-4137-97e1-e5925a83669d" />


<p>Introduirem el Nom de la organizacio</p>
<img width="1161" height="774" alt="Captura de pantalla de 2026-01-12 12-30-09" src="https://github.com/user-attachments/assets/de8c30ac-5647-4573-958b-1d8bc44efd00" />


<p>Direm que no es purgui la base de dades quan es purgui el paquet slapd</p>
<img width="1161" height="774" alt="Captura de pantalla de 2026-01-12 12-30-58" src="https://github.com/user-attachments/assets/3c29a14b-5182-451c-8a46-21f1a73e30b9" />

<p>Direm que si que mogue la base de dades antigua per a que no intefereixi en la nova</p>
<img width="1161" height="774" alt="Captura de pantalla de 2026-01-12 12-31-21" src="https://github.com/user-attachments/assets/65887a8e-8aae-47a1-a787-088469e76cc5" />


<p>Tornarem a executar slapcat per a veure que es ha aplicat tota la configuracio</p>
<img width="604" height="295" alt="Captura de pantalla de 2026-01-12 12-31-49" src="https://github.com/user-attachments/assets/e6468167-cb7c-4672-be38-0f1c9acd2817" />

<p>Entrarem a uo.ldif que estava al archiu comprimit i veurem que es un arxiu que crea una Unitat Organizativa anomenada users</p>
<img width="838" height="188" alt="Captura de pantalla de 2026-01-12 12-36-40" src="https://github.com/user-attachments/assets/ecf4ba69-4c3c-4665-90bd-8ebcadcb0913" />

<p>Entrarem a group.ldif que estava al archiu comprimit i veurem que es un arxiu que crea un grup anomenat alumnes i afegeix al usuari alu1 al grup</p>
<img width="849" height="225" alt="Captura de pantalla de 2026-01-12 12-37-52" src="https://github.com/user-attachments/assets/f26c2af0-9f0f-48b0-9e7f-d85384751f9b" />

<p>Entrarem a usu.ldif i veurem que el axiu crea un usuari anomenat alu1 amb la contrasenya alu1 tambe especifcat la seva shell (bin/bsh) i la home (home/alu1) i el uid (1001)</p>
<img width="849" height="443" alt="Captura de pantalla de 2026-01-12 12-39-01" src="https://github.com/user-attachments/assets/2b2e40a7-c4e5-4781-8c5b-3d808f09ca02" />

<p>Executarem el primer arxiu ou.ldif que creara la unitat organizativa users despres el usu.ldif que creara el usuari alu1 i per ultim el grup.ldif que creara el grup alumnes i introduira al usuari alum1 per aixo el hem executat abans</p>
<img width="1070" height="244" alt="Captura de pantalla de 2026-01-12 12-41-37" src="https://github.com/user-attachments/assets/efaddf8c-51b5-441a-a91e-e50711fa4aaa" />

<p>Comprovacio amb Slapcat</p>
<img width="611" height="697" alt="Captura de pantalla de 2026-01-12 12-43-17" src="https://github.com/user-attachments/assets/90663ece-d956-4ce3-9bb5-3b44c5293383" />
<img width="538" height="586" alt="Captura de pantalla de 2026-01-12 12-43-38" src="https://github.com/user-attachments/assets/aeac8ba9-fd6f-4b3f-9483-054f6fe8ee51" />

<p>Ara pasarem a el client i instalarem els paquets neccesaris. libnss-ldap: Perquè el sistema pugui consultar noms d'usuari i grups al servidor i libpam-ldap: Perquè el sistema pugui gestionar l'autenticació (contrasenyes) contra el servidor</p> 
<img width="1153" height="255" alt="Captura de pantalla de 2026-01-12 13-00-16" src="https://github.com/user-attachments/assets/be72a1a2-7022-40c8-b42d-730439cdc1f5" />

<p>Ens apareixera la pantalla de configuracio de ldap a el client i primer de tot introduirem la ip de el servidor</p>
<img width="1153" height="494" alt="Captura de pantalla de 2026-01-12 13-01-29" src="https://github.com/user-attachments/assets/18347834-83de-40e7-9e78-6db0c53cc7f7" />

<p>Ara introduirem el domini gina.cat</p>
<img width="1153" height="494" alt="Captura de pantalla de 2026-01-12 13-01-43" src="https://github.com/user-attachments/assets/51c828e5-0822-4989-9913-e7d4336442d2" />

<p>La versio de LDAP que es la 3</p>
<img width="1153" height="494" alt="Captura de pantalla de 2026-01-12 13-01-51" src="https://github.com/user-attachments/assets/d9140e36-208e-4be4-be04-5acac1998a22" />

<p>Pregunta si volem que el usuari local sigui adminsitrador de la base de dades i que el arxiu de les contrasenyes sol sera accesible per root</p>
<img width="1153" height="494" alt="Captura de pantalla de 2026-01-12 13-02-05" src="https://github.com/user-attachments/assets/754c2838-ac63-410a-b5e1-b200c666908c" />

<p>I si volem que la base de dades de ldap requereixque login</p>
<img width="1153" height="494" alt="Captura de pantalla de 2026-01-12 13-02-12" src="https://github.com/user-attachments/assets/42589406-e479-4847-81d4-8bd0a890fe5b" />

<p>Ara ens detmanara que introdueixim un usuari administrador de LDAP i la contrasenya</p> 
<img width="1153" height="494" alt="Captura de pantalla de 2026-01-12 13-03-04" src="https://github.com/user-attachments/assets/a4b35617-2e93-45f8-aee1-e567f2691c49" />
<img width="1147" height="488" alt="Captura de pantalla de 2026-01-12 13-03-19" src="https://github.com/user-attachments/assets/4891b417-5e8c-4155-b27b-8c61fb2219dc" />

<p>I ara el usuari que iniciarem sessio a la base de dades LDAP</p> 
<img width="1147" height="488" alt="Captura de pantalla de 2026-01-12 13-03-55" src="https://github.com/user-attachments/assets/fda24184-3e84-4dcd-81d0-a29cc2a5953c" />

<p>Si ens hem equivocat en algun pas podem reconfiguraro amb dpkg-reconfigure ldap-auth-config</p>
<img width="772" height="62" alt="Captura de pantalla de 2026-01-12 13-04-53" src="https://github.com/user-attachments/assets/37f4e426-fb21-42b2-b713-de3689314508" />

<p>Hi hauran unes pantalles que es afegiran de mes com aquesta que diu permetràs que les futures actualitzacions del sistema utilitzin aquesta configuració que estàs posant ara</p>
<img width="1147" height="483" alt="Captura de pantalla de 2026-01-12 13-07-30" src="https://github.com/user-attachments/assets/fc145129-6185-4ed7-acce-02d41319eb98" />

<p>Tambe sortira aquesta pantalla sobre el metode de xifratge de la contrasenya cuan dexideixes canviarla desde el client i te preguntara el metode natros triarem md5</p>
<img width="1147" height="483" alt="Captura de pantalla de 2026-01-12 13-08-08" src="https://github.com/user-attachments/assets/f960d76e-6fa0-4cd9-9bb6-8db292e8ed81" />
<img width="1147" height="483" alt="Captura de pantalla de 2026-01-12 13-08-17" src="https://github.com/user-attachments/assets/d13fbab6-7fb6-4588-959b-2f4a4d551b66" />

<p>Modificarem el arxiu nsswitch i a passwd i group introduirem ldap compact files systemd això vol dir que quan el sistema busqui un usuari per fer login, primer preguntarà a la base de dades LDAP. </p> 
<img width="795" height="482" alt="Captura de pantalla de 2026-01-12 13-10-50" src="https://github.com/user-attachments/assets/b8664468-5fcf-48c8-9d45-0293d294118e" />

<p>Tambe modificarem el arxiu common-session que es molt important perque crea la carpeta home de els usuaris LDAP quan iniciesim sessio i tambe indica en crear la carpeta nova, ha de copiar els fitxers de configuració bàsics (com el .bashrc) des de la carpeta "esquelet" del sistema i tambe defineix els permisos per defecte de la nova carpeta (l'usuari pot fer-ho tot, la resta només llegir).</p> 
<img width="795" height="482" alt="Captura de pantalla de 2026-01-12 13-14-16" src="https://github.com/user-attachments/assets/4773c176-bd41-4cf6-9c2f-74c24156197c" />

<p>Tambe modificarem el arxiu common password afegint la 4 linea blanca de password que fa:</p> 
<p>pam_pwquality.so: Primer es comprova que la contrasenya nova sigui prou segura (complexitat).</p> 
<p>pam_unix.so: S'encarrega dels usuaris locals.</p> 
<p>pam_ldap.so: És la línia clau que s'ha afegit. El paràmetre try_first_pass fa que el sistema intenti fer servir la contrasenya que ja has escrit abans de tornar-te-la a demanar.</p> 
<p>[success=1 user_unknown=ignore default=die]: Aquest és un codi de control. Diu que si el mòdul de LDAP té èxit, se saltarà el següent pas (que sol ser un missatge d'error).</p> 
<img width="1095" height="483" alt="Captura de pantalla de 2026-01-12 13-15-21" src="https://github.com/user-attachments/assets/d2ddd22d-3e19-4fe4-a971-c9ae0d56a6e8" />

<p>Per finalizar els arxiu modificarem es e 50-ubuntu.conf afegint la ultima linea que mostra una llista amb els usuaris locals que ja existeixen a la màquina. Com que els teus usuaris de l'Arbre LDAP són remots i encara no han entrat mai, no apareixerien a la llista.</p> 
<img width="1150" height="485" alt="Captura de pantalla de 2026-01-12 13-16-46" src="https://github.com/user-attachments/assets/6b645c44-93d0-4dc1-9c9d-45b586783f67" />


<p>Tancarem sessio de el usuari actual i clicarem no esta en la llista i introduirem el nom de usuari alu1 i la contrasenya i es creara la carpeta home per a alu1 i comprovarem el la terminal que som el usuari alu1 i que te carpeta home</p> 
<img width="133" height="34" alt="image" src="https://github.com/user-attachments/assets/b476bfde-6769-4f8c-8382-2f25bc773946" />
<img width="402" height="290" alt="image" src="https://github.com/user-attachments/assets/86d9c67b-d2be-4c4f-b8bd-57dd938537d5" />
<img width="741" height="485" alt="Captura de pantalla de 2026-01-12 13-23-30" src="https://github.com/user-attachments/assets/661c6d35-80b5-4e8e-b8c6-3915d5c9573b" />


<h2>Interfice Grafica LDAP</h2>

<p>Primer de tot instalarem el programa jxplorer que es un progarama amb interfice grafica que es un navegador de fitxers per al servidor LDAP.</p> 
<img width="744" height="490" alt="Captura de pantalla de 2026-01-13 13-48-33" src="https://github.com/user-attachments/assets/b2318f19-0d21-4b77-9177-77098d2fde70" />

<p>El podem executar posant jxplorer a la terminal o desde la llista de aplicacions</p> 
<img width="486" height="68" alt="image" src="https://github.com/user-attachments/assets/d0e800fc-94b3-4311-8f2e-9f47a6972205" />
<img width="99" height="124" alt="image" src="https://github.com/user-attachments/assets/7464a50f-dd48-446b-8cfd-7954dcf29f28" />

<p>Al entar al progarma anirem a file i a connect</p> 
<img width="448" height="266" alt="image" src="https://github.com/user-attachments/assets/5bf68380-20f1-4954-9b0f-a2e8c7fb7e6f" />

<p>Introduirem la ip de el servidor a host despres a base DN introduirem el domini gina.cat i a security selecionarem la opcio user+password i introduirem el usuari admin mes el domini i la contrasenya i apretarem OK</p> 
<img width="676" height="513" alt="Captura de pantalla de 2026-02-08 06-09-35" src="https://github.com/user-attachments/assets/8d499245-01ed-48fa-a00e-9a10bd6dac3b" />

<p> Desde aqui podem gestionar el servidor LDAP graficament com crear usuaris,grups i unitats organizatives</p>
<img width="805" height="605" alt="image" src="https://github.com/user-attachments/assets/7eb383b7-eb5a-41e9-a867-9a317e100f3b" />




<h2>Servidor Samba</h2>

<p>Samba serveix per compartir fitxers, impressores i carpetes en una xarxa local. La seva gran característica, és que permet gestionar l'accés mitjançant una autenticació a nivell d'usuari. Això significa que el servidor no només comparteix el recurs, sinó que verifica qui ets abans de deixar-te entrar, permetent que cada usuari tingui els seus propis permisos i carpetes privades.</p>

<p>Primer de tot instalarem SAMBA</p>
<img width="738" height="419" alt="Captura de pantalla de 2026-01-26 11-50-39" src="https://github.com/user-attachments/assets/d3d8cd03-a0a2-4011-bdf2-4a7b164fb43d" />

<p>Ara crearem una carpeta anomenada proves donarem tots els permisos a tothom amb chmod 777 i canviarem el propietari amb chown indicant que no volem propietari a la carpeta i tampoc volem grup i comprovarem que es hagui creat correctament</p>

<img width="732" height="302" alt="Captura de pantalla de 2026-01-26 11-53-00" src="https://github.com/user-attachments/assets/b7a32977-6e55-40c5-8562-808f1f6862d7" />













Fet sense usuaris LDAP i fer natros sols en usuaris LDAP

Servidor NFS
