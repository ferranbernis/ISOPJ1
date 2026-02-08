<h1>Sprint 3: Administració de Dominis i Seguretat</h1>


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

<p> Ara pasarem a el client i instalarem els paquets neccesaris. libnss-ldap: Perquè el sistema pugui consultar noms d'usuari i grups al servidor i libpam-ldap: Perquè el sistema pugui gestionar l'autenticació (contrasenyes) contra el servidor</p> 
<img width="1153" height="255" alt="Captura de pantalla de 2026-01-12 13-00-16" src="https://github.com/user-attachments/assets/be72a1a2-7022-40c8-b42d-730439cdc1f5" />









<h2>Servidor Samba</h2>

Serveix per compartir fitxers impresores carpetes la diferencia que hi ha es que es fa amb autentificacio a nivell de usuari 

Fet sense usuaris LDAP i fer natros sols en usuaris LDAP

Servidor NFS
