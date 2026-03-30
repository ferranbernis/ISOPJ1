<h1>Sprint 5: Monitoratge, Auditories i Programari Client/Servidor</h1>

<h2>LOGS (DOCUMENTAT PER EROS A <a href="https://erosmauri.github.io/ISOPJ1/SP5/SP5.html" target="_blank">
    https://erosmauri.github.io/ISOPJ1/SP5/SP5.html</a>)</h2>

<img width="736" height="495" alt="image" src="https://github.com/user-attachments/assets/780c6e79-d968-4800-a41f-56f3e7d971a0" />


<img width="739" height="617" alt="image" src="https://github.com/user-attachments/assets/a7d3a24d-e273-4d41-9776-01466fb93645" />


<p>Rotacio de logs de el sistema</p> 
<img width="619" height="148" alt="image" src="https://github.com/user-attachments/assets/b51f184a-ecee-46ed-b3ef-d7f63fcd91ca" />


<img width="563" height="493" alt="image" src="https://github.com/user-attachments/assets/ebbfc739-c96a-43f7-b611-60569e28c5e2" />

<img width="426" height="336" alt="image" src="https://github.com/user-attachments/assets/bf1a4799-3c4f-4a44-a8e8-d41e818b3a8a" />

<img width="740" height="717" alt="image" src="https://github.com/user-attachments/assets/335999f7-9ba3-45cd-8967-87962357400a" />

<img width="736" height="405" alt="image" src="https://github.com/user-attachments/assets/4562c92b-d40d-4ae8-94c0-a36e6759263d" />

<img width="733" height="99" alt="image" src="https://github.com/user-attachments/assets/2f9adf21-cb25-40bd-9124-a3ccc7b125d2" />
<img width="729" height="42" alt="image" src="https://github.com/user-attachments/assets/ae10314d-2e70-4043-9744-d243e799cde1" />

<img width="738" height="665" alt="image" src="https://github.com/user-attachments/assets/5a8307ee-2bb8-495e-bc7f-0b3222b33a28" />

<img width="736" height="97" alt="image" src="https://github.com/user-attachments/assets/05b183f8-4663-40e1-b044-27f7685e086d" />
<img width="732" height="61" alt="image" src="https://github.com/user-attachments/assets/771aa78e-a855-4d57-a10b-cfc1c674540a" />


<img width="735" height="116" alt="image" src="https://github.com/user-attachments/assets/162a7066-eb19-4186-b15c-aea6ba9c1ffa" />


<img width="735" height="116" alt="image" src="https://github.com/user-attachments/assets/af143dd5-064d-4128-b24d-67f6d0da6ed4" />


<img width="742" height="594" alt="image" src="https://github.com/user-attachments/assets/e2163cc3-89da-4e8a-8e58-dd0cf620dcad" />


<img width="742" height="150" alt="image" src="https://github.com/user-attachments/assets/c2392381-65c2-48c6-85bf-01f239a13d65" />

<img width="736" height="598" alt="image" src="https://github.com/user-attachments/assets/91aa5cd5-39eb-432c-803f-44c640a85c4a" />

<img width="736" height="110" alt="image" src="https://github.com/user-attachments/assets/243d8d25-aa26-45c2-9073-de0f67e78fec" />

<img width="739" height="579" alt="image" src="https://github.com/user-attachments/assets/802f0fb7-d066-4b48-beb9-2c53d4dc5077" />


<img width="588" height="135" alt="image" src="https://github.com/user-attachments/assets/6fb732e0-01a5-4344-8fce-58df9fc344b4" />





<h2>Servidor de Actualizacions</h2>

<h4>Servidor</h4>

<p>Primer de tot instalarem apache</p>
<img width="719" height="177" alt="image" src="https://github.com/user-attachments/assets/495cfb57-fe54-40af-8d80-5741dfaccc38" />

<p>I apt-mirror que serveix per crear una còpia local (un "mirall") dels repositoris oficials de Debian, Ubuntu o qualsevol altra distribució basada en Debian.</p>
<img width="729" height="365" alt="image" src="https://github.com/user-attachments/assets/0dec8e3a-0500-40d6-a862-2673d4302376" />

<p>Despres farem un sudo nano /etc/apt/mirror.list i afegirem la linea deb la extensio de el paquet i arch=amd64 que simifica que sol descarregi els paquets per a 64 bits l'adreça URL del servidor de Google on estan guardats els fitxers del navegador Chrome la versio stable</p> 
<img width="939" height="744" alt="image" src="https://github.com/user-attachments/assets/a9da8d42-9c4b-4cc8-980c-445347ba0925" />

<p>Executarem apt-mirror per a que descarregi el paquet de google chrome</p> 
<img width="939" height="744" alt="image" src="https://github.com/user-attachments/assets/f50d7949-112f-4138-b0e6-0fbf23233654" />

<p>Per a comprovar que el paquet de google chrome es hagui instalat correctament anirem a /var/spool/aptmirror i si existeix la carpeta chrome es que ha funcionat</p>
<img width="744" height="143" alt="image" src="https://github.com/user-attachments/assets/d34929e8-e185-487b-ab2a-796ea67eed1c" />

<p>Crearem un enlaç simbolic amb ln -s 
<p>Origen: /var/spool/apt-mirror/mirror/dl.google.com/. És la carpeta on hi ha les dades reals de Chrome descarregades.</p>
<p>Destí: /var/www/html/. És l'arrel pública del servidor web per aixo fa falta el apache</p>
<p>Efecte: Ara, quan algú accedeixi a l'adreça IP del servidor, el servidor web podrà "veure" i servir la carpeta dl.google.com com si estigués realment dins de /var/www/html/.
<img width="964" height="85" alt="image" src="https://github.com/user-attachments/assets/b6ea7648-8137-476b-9881-75d9ce52f989" />

<h4>Client</h4>
<p>Configuració del fitxer /etc/apt/sources.list en el ordinador client per utilitzar el repositori local de Google Chrome allotjat a la IP 10.0.2.15 (Servidor)</p>
<img width="795" height="794" alt="image" src="https://github.com/user-attachments/assets/d5784c3b-8301-4860-91da-2b625c05321f" />

<p>Executarem un apt update pero donara error perque no podra verificar la clau publica</p>
<img width="849" height="209" alt="image" src="https://github.com/user-attachments/assets/2bd05f4e-6e07-4efc-837f-2775aaf392d9" />

<p>Obtindrem la clau pubica de google chrome amb wget -q -0 el link de la clau i apt-key add</p>
<img width="842" height="113" alt="image" src="https://github.com/user-attachments/assets/39debc5b-1f6f-4bfd-8e28-85349dd6b616" />

<p>Tornarem a executar el apt update</p>
<img width="842" height="297" alt="image" src="https://github.com/user-attachments/assets/bc1bc0e7-72b1-40c0-ba32-9ab4fa4d1c50" />

<p>Per a finalizar executarem el apt install de google chrome i com es veu a la imatge es obte de el servidor 10.0.2.15 configurat anteriorment</p>
<img width="835" height="417" alt="image" src="https://github.com/user-attachments/assets/1051a43b-c873-485c-865c-325f6f4df14e" />

<h3>PACKET EDGE</h3>

<img width="896" height="647" alt="image" src="https://github.com/user-attachments/assets/05d19bfd-3bde-4fac-88ca-842ba112f705" />







