<h1>Sprint 3: Administració de Dominis i Seguretat</h1>


que es un servidor 

usuaris, grups recursos unitats organizatives el bosc i  el arbre 


<h2>Servidor LDAP</h2>

<p>Primer de tot canviarem de DHCP a ip manual</p>
<img width="584" height="472" alt="image" src="https://github.com/user-attachments/assets/6b85db42-4e9a-4f0e-8cf3-612ad963416d" />

<p>Despres canviarem el hostname</p>
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



<img width="1161" height="774" alt="Captura de pantalla de 2026-01-12 12-30-09" src="https://github.com/user-attachments/assets/de8c30ac-5647-4573-958b-1d8bc44efd00" />





<h2>Servidor Samba</h2>

Serveix per compartir fitxers impresores carpetes la diferencia que hi ha es que es fa amb autentificacio a nivell de usuari 

Fet sense usuaris LDAP i fer natros sols en usuaris LDAP

Servidor NFS
