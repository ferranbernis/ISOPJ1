<h1>Sprint 2. Instal·lació, Configuració de Programari de Base i Gestió de Fitxers</h1>

<h2>1. Sistemes de fitxers i Particions</h2>









<h2>2. Gestió de Procesos</h2>





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
<img width="636" height="242" alt="Captura de pantalla de 2025-11-17 12-11-13" src="https://github.com/user-attachments/assets/515eb864-3981-47f5-88af-1cb3c3ed3fbf" />
<img width="757" height="575" alt="Captura de pantalla de 2025-11-17 12-11-32" src="https://github.com/user-attachments/assets/a846aeda-4de7-4be0-bfff-fe45eb3a9263" />

<p> Ara pasarem a el segon arxiu login.dfs que modifica els parametres de quan un usuari incia sesio i modificarem el maxim de dies que estara el minim i el avis</p>
<img width="737" height="243" alt="Captura de pantalla de 2025-11-17 12-13-54" src="https://github.com/user-attachments/assets/1a445bfc-57b1-4e92-a59c-9015e5df5255" />

crearem el usuari gris i comprovarem que tots 
<img width="852" height="438" alt="Captura de pantalla de 2025-11-17 12-15-31" src="https://github.com/user-attachments/assets/a7740f16-a365-4c90-971d-7f55b695b322" />


<p>Un grup es por esborrar i a els usuaris no els pasa res a no ser que algun usuari el tingui com a grup principal</p>
<img width="414" height="45" alt="Captura de pantalla de 2025-11-17 11-57-57" src="https://github.com/user-attachments/assets/59ca7721-135b-4fe9-a01e-04a2cf0804fb" />
<img width="414" height="45" alt="Captura de pantalla de 2025-11-17 11-57-57" src="https://github.com/user-attachments/assets/ad513f64-c801-4c62-87d0-1d60e0694de6" />




<p>tot el que es posi a la carpeta /etc/skel es copiara a la home de el usuari</p>
<img width="605" height="388" alt="Captura de pantalla de 2025-11-17 12-07-39" src="https://github.com/user-attachments/assets/fb8168c7-02ac-4695-9435-39d2e080ed37" />









<h3>Gestio permisos</h3>





<h3>ACL</h3>





















<h2>4. Còpies de seguretat i automatització de tasques</h2>






<h2>5. Quotes d'usuari</h2>
