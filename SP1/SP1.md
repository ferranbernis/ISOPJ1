---
layout: default
title: "Sprint 1: Instalacio i Configuracio inicial"
---

# Virtualizacio i instalacio del SO Ubuntu

Primer de tot selecionarem la memoria ram de la maquina virtual el minim son 4 GB i com a el ordinador host de 32GB introduirem 8GB despres com sera dual introduirem 80 GB de disc 40 GB per a ubuntu i 40 GB per a windows el minim de ubuntu son 25 GB i a la xarxa selecionarem xarxa NAT la diferencia amb el NAT es que els dos poden accedir a internet pero la xarxa nat poden veures varies maquines entre si la maquina anfitrio fa de router 

<img width="578" height="666" alt="Captura de pantalla de 2025-09-22 12-41-33" src="https://github.com/user-attachments/assets/76fc07a2-8bf1-4bf5-8acb-44a1f3309e05" />


Despres Apretarem seguent hasta arribar a les particions ficarem 18GB per a la arrel i 15GB per a home i 1GB boot anirem justos de almacenament per culpa de el windows pero funcionara be 

<img width="804" height="770" alt="Captura de pantalla de 2025-09-23 12-56-54" src="https://github.com/user-attachments/assets/05223edc-d1ef-4782-bdf2-9c288dd9a8ee" />

<img width="804" height="770" alt="image" src="https://github.com/user-attachments/assets/7210c626-149d-434e-8527-29abf2a0f211" />

Introduirem totes les dades de el usuari
<img width="809" height="605" alt="image" src="https://github.com/user-attachments/assets/adcc39fb-de2a-4fee-8842-da209bb43bce" />

Despres inserirem el dvd de les guest aditions i obrirem una terminal dintre de el cd i executarem el autorun.sh
<img width="793" height="56" alt="image" src="https://github.com/user-attachments/assets/1fcb60cf-3faf-419f-b031-4c7b80ab3824" />

I JA ESTARIA INSTALAT




# Llicenciament

## Ubuntu

Ubuntu es una distribució de Linux basada en codi obert. La seva filosofia és permetre l'ús, modificació i redistribució del programari, tot respectant les condicions de les llicències corresponents. A continuació es detallen els principals tipus de llicències que trobem a Ubuntu.

## 1. Kernel Linux

- **Llicència:** GPLv2 (GNU General Public License versió 2)  
- **Descripció:** Permet l’ús, modificació i distribució del codi font del nucli Linux. Qualsevol modificació distribuïda ha de mantenir la mateixa llicència.

## 2. Programari lliure i codi obert

La majoria de les aplicacions incloses a Ubuntu estan sota llicencies de codi obert, com per exemple:

- **GPL (General Public License):** Ex. GNU Core Utilities, Bash.  
- **LGPL (Lesser General Public License):** Ex. biblioteques compartides com GTK.  
- **MIT / BSD:** Ex. moltes utilitats de desenvolupament i biblioteques gràfiques.  
- **Apache License:** Ex. alguns serveis i aplicacions web.












#  Gestors d'arrencada per a instal·lacions DUALS

amb Ubuntu ja instalat comencarem a instalar windows selecionarem a virtualbox habilita EFI 

<img width="623" height="462" alt="image" src="https://github.com/user-attachments/assets/f7795260-6774-45af-9f45-332bba8d2c36" />

<img width="249" height="32" alt="image" src="https://github.com/user-attachments/assets/3aab1c39-17bb-468e-944b-da6d820ee61e" />

Assignem el Windows a el espai lliure i continuarem apretant seguent 
<img width="642" height="481" alt="image" src="https://github.com/user-attachments/assets/2beef985-e43e-4a3c-9e72-03d710cbbaef" />

Intoduirem el nom de usuari
<img width="1029" height="772" alt="Captura de pantalla de 2025-09-30 14-09-49" src="https://github.com/user-attachments/assets/8a393c63-6ee3-45d9-9421-b05bacf82797" />

Ja Estaria
<img width="1028" height="769" alt="image" src="https://github.com/user-attachments/assets/3800b9ba-42c2-4f49-a609-bddcc769e8dd" />

Per a recuperar el grub inserirem la ISO de el supergrub
<img width="596" height="76" alt="Captura de pantalla de 2025-10-06 13-02-01" src="https://github.com/user-attachments/assets/bee384ab-808c-498c-960e-591c5753ac03" />

i entrarem a el boot menu i selecionarem iniciar desde el cd 
<img width="638" height="484" alt="Captura de pantalla de 2025-10-06 11-59-02" src="https://github.com/user-attachments/assets/39e044df-31e2-4274-bb85-346887e67b6a" />

<p>Selecionarem la segona opcio</p>
<img width="638" height="484" alt="Captura de pantalla de 2025-10-06 11-59-18" src="https://github.com/user-attachments/assets/4e740b2a-1e9d-48d8-854e-796815d94730" />

<p>Selecionarem la opcio UBUNTU</p> 
<img width="638" height="484" alt="Captura de pantalla de 2025-10-06 11-59-39" src="https://github.com/user-attachments/assets/15c26118-c180-4729-b58f-ca8148d781f5" />

<p>Allavors arrancara el ubuntu</p>
<img width="500" height="370" alt="image" src="https://github.com/user-attachments/assets/e3de3dd8-c24c-4879-ad3b-51203f71ec80" />

<p>Montarem EFI a SDA5</p>
<img width="981" height="44" alt="Captura de pantalla de 2025-10-06 12-32-14" src="https://github.com/user-attachments/assets/59a402cb-b313-44ad-86d7-0f90127c5adc" />

<p>Reinstallarem el grub</p>
<img width="807" height="140" alt="Captura de pantalla de 2025-10-06 12-12-14" src="https://github.com/user-attachments/assets/b222a14e-f2f6-46e8-a4c3-e940d2c35b7a" />

<p>Comentarem les lines GRUB timeout i escriutrem la linea Grub disable OS</p> 
<img width="754" height="525" alt="Captura de pantalla de 2025-10-06 12-27-08" src="https://github.com/user-attachments/assets/e73a0231-cec9-4923-9430-bb32cb63e591" />

<p>Actualizarem el Grub</p> 
<img width="976" height="397" alt="Captura de pantalla de 2025-10-06 12-28-18" src="https://github.com/user-attachments/assets/30a0817a-a2b9-4214-a626-14d6acee4d58" />

<p>Ja estaria </p> 
<img width="900" height="600" alt="Captura de pantalla de 2025-10-12 06-26-53" src="https://github.com/user-attachments/assets/f15c94cd-9c94-4340-80b8-9da1c80f654a" />



#  Punts de restauració

<p>Amb Fdisk crearem la particio amb la opcio n (afegeix una nova partico) unica de 15GB</p>
<img width="872" height="441" alt="Captura de pantalla de 2025-10-07 12-53-38" src="https://github.com/user-attachments/assets/eec22ae8-b180-454b-9aaf-5c6242209a91" />

<p>Donarem format ext4 a la particio sdb1 creada anteriorment</p> 
<img width="754" height="256" alt="Captura de pantalla de 2025-10-07 12-56-11" src="https://github.com/user-attachments/assets/f73f8a22-e193-4590-8d31-bda07294ecec" />

<p>Ja estaria preparat para el us</p> 
<img width="572" height="63" alt="Captura de pantalla de 2025-10-07 12-54-32" src="https://github.com/user-attachments/assets/94158394-38b8-4f46-8c0a-90c7421592d8" />

<p>Despres entrarem a el Programa i selecionarem el assistent</p>  
<img width="651" height="102" alt="image" src="https://github.com/user-attachments/assets/72f620e8-aecc-44f0-8a73-250f1411192e" />

<p>Selecionarem el tipus de instantanea</p>  
<img width="602" height="185" alt="image" src="https://github.com/user-attachments/assets/3b2d2e98-7bed-484b-8e68-c13169115de9" />

<p>Selecionarem La particio de el disc dur</p>   
<img width="604" height="229" alt="Captura de pantalla de 2025-10-07 12-59-00" src="https://github.com/user-attachments/assets/168a6ea1-26e9-45e0-a9ec-979cecea761b" />

<p>Selecionarem que es faci una copia de seguretat al arrancar el sistema</p>  
<img width="605" height="668" alt="Captura de pantalla de 2025-10-07 12-59-11" src="https://github.com/user-attachments/assets/286ee560-9792-4d1b-9d78-10c87ab07be4" />

<p>Selecionarem la carpeta home i excluirem el boot</p> 
<img width="816" height="668" alt="Captura de pantalla de 2025-10-07 12-59-50" src="https://github.com/user-attachments/assets/edadff3e-e4c2-4017-97a1-81c3b5bf46f2" />

<p>Crearem la instantanea</p>  
<img width="804" height="641" alt="Captura de pantalla de 2025-10-07 13-05-16" src="https://github.com/user-attachments/assets/4c8483e3-5a8b-4bc9-b31b-b09ce81bf451" />

<p>Amb el arxiu de text hola i la carpeta adeu</p>  
<img width="338" height="40" alt="image" src="https://github.com/user-attachments/assets/2320640e-0e81-439d-a565-7dcac3014010" />

<p>Despres eliminarem el text hola i la carpeta adeu i restaurarem la copia de seguretat</p>
<img width="507" height="583" alt="image" src="https://github.com/user-attachments/assets/a9db1693-25a6-40ad-b5ef-4f81965ea529" />

<p>Esperarem </p>
<img width="507" height="583" alt="image" src="https://github.com/user-attachments/assets/88aae583-f0e4-463a-a9f4-8ddaf9fca164" />
<img width="534" height="165" alt="Captura de pantalla de 2025-10-21 13-39-26" src="https://github.com/user-attachments/assets/fd761080-3402-423c-9582-3363f29f68ca" />
<img width="1286" height="804" alt="Captura de pantalla de 2025-10-21 13-39-43" src="https://github.com/user-attachments/assets/bf9c3267-aadd-4742-87ec-2780b59f782a" />

Revisem i ja estaria
<img width="893" height="556" alt="image" src="https://github.com/user-attachments/assets/c56237e6-2318-48a9-b763-113c5fc1c395" />

# Configuracio de la xarxa 
<p>Primer de tot mirarem si tenim conexio fent un ping a iesebre.com i a el DNS de google</p> 
<img width="846" height="225" alt="image" src="https://github.com/user-attachments/assets/75893045-cf51-4c93-b88e-15bdbedf5b4f" />
<img width="661" height="247" alt="image" src="https://github.com/user-attachments/assets/469a5c1c-1854-4e1f-857e-e0e58b05d8a4" />
<p>Per a aplicar una configuracio personalizada per terminal modificarem el arxiu /etc/netplan/01-network-manager-all.yaml
Introduirem la adreça 192.168.203.159 en la mascara /24 i la via 192.168.203.1 que es el router i a nameservers introduirem 
el DNS de google
</p>
<img width="739" height="488" alt="Captura de pantalla de 2025-10-07 14-03-40" src="https://github.com/user-attachments/assets/39ff047f-f914-47a9-886b-1546d48a4163" />

# Comandes generals i instal·lacions 

<p>Farem un sudo apt-cache policy audacity i ens dira el la versio que es la candidata a instalar cuan fem un sudo apt install</p>   
<img width="885" height="204" alt="image" src="https://github.com/user-attachments/assets/bbf6ad31-ff88-4c85-ab6a-7d69814ef14d" />

<p>Despres dintre de la carpeta /etc/apt/preferencies.d crearem el arxiu anomenat audacity</p>
<img width="588" height="29" alt="image" src="https://github.com/user-attachments/assets/f73df6c9-2eef-449a-8813-4a7a224bbb73" />

<p>Introduirem el nom de el packet audacity i un asterisc que simifica que volem instalar les dependencies de el paquet a baix la versio que es la noble-backports la 3.7.3 que es diferent a la candidata que es la 3.4.2 i al final la prioritat com 900 per exemple</p>
<img width="910" height="170" alt="image" src="https://github.com/user-attachments/assets/b892fc10-7028-4350-96d5-b4efeb51e89b" />

<p>Tornem a fer un sudo apt-cache policy audacity i ja ens diu que la versio candidat ha canviat a la que voliem natros</p>
<img width="911" height="223" alt="image" src="https://github.com/user-attachments/assets/d83e64ad-f917-422f-8083-a58472472535" />

<p>Ara farem un sudo apt install audacity</p> 
<img width="914" height="607" alt="image" src="https://github.com/user-attachments/assets/80c2238a-aed4-41a5-8877-1c98d301f7c4" />

<p>Comprovarem que la versio que hem instalat sigui la correcta</p>
<img width="908" height="250" alt="image" src="https://github.com/user-attachments/assets/8c218c31-d7c8-4838-95bb-a69c4ceae9c1" />

<img width="1415" height="751" alt="image" src="https://github.com/user-attachments/assets/e509eac6-9d28-4d7c-936b-419c72096fea" />













