<h1>Sprint 4: Configuració del Programari de Base i Sistemes d’Emmagatzematge</h1>

<h2>RAID</h2>

<p>Un RAID (acrònim de Redundant Array of Independent Disks) és una tecnologia que combina diversos discs durs o unitats SSD en una sola unitat lògica.
En comptes de tenir tres discs separats, el sistema els "veu" com un de sol. Per què ho fem, això? Principalment per dues raons: seguretat (per no perdre dades si un disc s'espatlla) i rendiment (per anar més ràpid).</p>

<p>Es recomanabe que els discs utilizats siguin iguals de mida (GB) i de velociatat (MB/s o GB/s)</p>

<div style="display: flex; gap: 10px;">
  <img width="450" height="253" alt="image" src="https://github.com/user-attachments/assets/15038abd-5458-44e0-991b-758b9242b0bd" />
  <img width="450" height="253" alt="image" src="https://github.com/user-attachments/assets/f47b0c0f-1d11-4dee-bb4e-afc59c65e3ee" />
</div>


<p>RAID 0 (Stripping o Fragmentació)</p>
<p>Aquest nivell prioritza la velocitat. Divideix les dades i les reparteix entre els discs.</p>
<p>Com funciona: Si escrius un fitxer, la meitat va al Disc A i l'altra meitat al Disc B.</p>
<p>Avantatge: És el més ràpid.</p>
<p>Inconvenient: Risc total. Si un dels discs falla, perds absolutament tota la informació.</p>
<p>Mínim de discs: 2.</p>

<p>2. RAID 1 (Mirroring o Mirall)</p>
<p>Aquest nivell prioritza la seguretat. Tot el que s'escriu en un disc es duplica exactament en l'altre.</p>
<p>Com funciona: Tens una còpia exacta en temps real.</p>
<p>Avantatge: Si un disc mor, el sistema continua funcionant sense perdre ni un bit.</p>
<p>Inconvenient: Estàs pagant dos discs per tenir la capacitat d'un de sol (perds el 50% de l'espai).</p>
<p>Mínim de discs: 2.</p>

<p>RAID 5 (Paritat distribuïda)</p>
<p>És l'equilibri perfecte i el més utilitzat en servidors i sistemes professionals.</p>
<p>Com funciona: Reparteix les dades entre tots els discs, però reserva un espai per a la "paritat" (una mena de codi matemàtic que permet reconstruir les dades).</p>
<p>Avantatge: Molt bona velocitat i seguretat. Si un disc falla, les dades es recuperen gràcies a la paritat dels altres.</p>
<p>Inconvenient: Si fallen dos discs a la vegada, perds la informació.</p>
<p>Mínim de discs: 3.</p>

<p>RAID 10 (o 1+0)</p>
<p>És una combinació: un "mirall de fragments".</p>
<p>Com funciona: Primer fa un mirall (RAID 1) i després els uneix en un RAID 0.</p>
<p>Avantatge: El millor dels dos mons: màxima velocitat i màxima seguretat.</p>
<p>Inconvenient: Molt car, ja que necessites molts discs i només aprofites la meitat de l'espai total.</p>
<p>Mínim de discs: 4.</p>



<h3>RAID 1</h3>

<p>Primer de tot instalarem mdadm que és l'eina de línia de ordres més potent i utilitzada en sistemes Linux per gestionar el que anomenem RAID</p>
<img width="687" height="76" alt="image" src="https://github.com/user-attachments/assets/5ac555a2-8cd7-4e89-bd31-f73afdc01ed5" />

<p>Executarem fdisk -l per veure el llistat de discs els que ens interesen per a fer el RAID son el sdb i sdc de 2 GB cada un</p>
<img width="774" height="649" alt="image" src="https://github.com/user-attachments/assets/bd8ee64e-f8d4-410a-94db-6f4acd9cd50d" />

<p>Executarem fdisk /dev/sdb per crear una particio nova amb la opcio n utilizarem els valors predeterminats amb p i guardarem amb w</p>
<img width="923" height="631" alt="image" src="https://github.com/user-attachments/assets/20b36a44-b719-491e-a46f-07ea58d3d17e" />

<p>Executarem fdisk /dev/sdc per crear una particio nova amb la opcio n utilizarem els valors predeterminats amb p i guardarem amb w</p>
<img width="925" height="629" alt="image" src="https://github.com/user-attachments/assets/f3b49e39-8353-44eb-8b2c-248339d41daa" />

<p>Tornarem a executar fdisk -l per veure el llistat de discs</p>
<img width="621" height="446" alt="image" src="https://github.com/user-attachments/assets/538ef179-e76d-4c96-9ef1-e294ce8a0e31" />

<p>Entarem a la carpeta mnt i crearem la carpeta raid 1 amb mkdir i donarem amb chmod 777 privilegis totals a tots i comprovarem els permisos de la carpeta amb ls -l</p>
<img width="636" height="217" alt="image" src="https://github.com/user-attachments/assets/d10ddd95-53ab-4ec4-a003-5faacb261c96" />

<p>Crearem amb mdadm --create /dev/md0 i --level=1 que es RAID 1 i raid-devices=2 que son els dos disc dur sdb1 i sdc1</p> 
<img width="1070" height="273" alt="image" src="https://github.com/user-attachments/assets/36b66def-7de7-43c9-b5cb-573e92ad9fe2" />

<p>Formatarem el raid amb el sistema de fitxers ext4</p>
<img width="829" height="302" alt="image" src="https://github.com/user-attachments/assets/ab06d109-c248-451f-8001-62d7b0b54ff6" />

<p>I amb mdadm --detail i el RAID md0 comprovarem els detalls</p>
<img width="898" height="623" alt="image" src="https://github.com/user-attachments/assets/57ae05ca-f5dc-450a-81bd-b0777873a7d9" />

<p>Mitjançant mdadm --detail --scan, el sistema obté el UUID (l'identificador únic) del RAID.</p>
<img width="1010" height="91" alt="image" src="https://github.com/user-attachments/assets/3d2478ad-9d46-491d-84f4-4509d4f6d5a5" />

<p>En desar-ho a /etc/mdadm/mdadm.conf, t'assegures que el nucli de Linux sàpiga quins discs formen el dispositiu /dev/md0 durant l'arrencada.</p>
<img width="1087" height="130" alt="image" src="https://github.com/user-attachments/assets/e42853f5-18c0-47a4-92e3-72dbeb60d623" />

<p>He editat el fitxer de la taula de sistemes de fitxers (fstab) per definir on s'ha de "punxar" el RAID de manera permanent que es a la carpeta raid1 dintre de mnt</p>
<img width="1088" height="374" alt="image" src="https://github.com/user-attachments/assets/d05c5e96-0a6a-4d9d-b603-6b397ad32449" />

<p>He executat update-initramfs -u -k all aquesta comanda regenera la imatge d'arrencada de Linux. És un pas crític després de configurar un RAID.</p>
<img width="698" height="92" alt="image" src="https://github.com/user-attachments/assets/6038cdf6-4175-44f0-81bd-6450f2068670" />

<p>He entrat al directori /mnt/raid1 i he llistat el contingut amb ls</p>
<img width="520" height="160" alt="image" src="https://github.com/user-attachments/assets/00705695-3e88-47ff-b251-908642eabbe7" />

<p> Ara simularem que un disc de els dos de el raid 1 per exemple el sdb1 amb mdadm /dev/md0 -f /dev/sdb1</p>
<img width="749" height="46" alt="image" src="https://github.com/user-attachments/assets/eba756ec-d999-456c-8250-3ff7793ed126" />

<p> I amb mdadm --detail i el RAID md0 comprovarem els detalls i veurem que el disc sdb1 esta en faulty (defectuós)</p>
<img width="817" height="589" alt="image" src="https://github.com/user-attachments/assets/1fbacb95-4fa5-4fb7-82dc-7e6ef44a37e2" />

<p>Tornarem a afegir sdb1 amb mdadm /dev/md0 -a /dev/sdb1 i rapid executarem mdadm --detail /dev/md0 i veurem que es esta remontant</p>
<img width="816" height="579" alt="image" src="https://github.com/user-attachments/assets/813b63ae-985f-4703-9cc4-26bff2bfa9c9" />

<p>Per finalizar tornarem a executar mdadm --detail i veurem que els dos discs estan operatius
<img width="898" height="623" alt="image" src="https://github.com/user-attachments/assets/04b1293f-4717-4731-84a6-40481fcf2eba" />



<h4>ESBORRAR RAID </h4>
<img width="920" height="318" alt="image" src="https://github.com/user-attachments/assets/37009c08-97b1-4b6b-9fee-5495a5b18d12" />

<img width="597" height="41" alt="image" src="https://github.com/user-attachments/assets/2d7ea791-b269-4f18-b936-7298f757d70f" />

<img width="654" height="42" alt="image" src="https://github.com/user-attachments/assets/d0383a2e-158b-4ec4-883e-27a8616b5e3d" />

<img width="668" height="55" alt="image" src="https://github.com/user-attachments/assets/282ec5e5-6c5e-431d-8dfa-dc4c013623b7" />

<img width="849" height="131" alt="image" src="https://github.com/user-attachments/assets/3acfbd8b-c973-40e6-b83d-223ed473290a" />

<img width="918" height="113" alt="image" src="https://github.com/user-attachments/assets/18b42fe5-32d6-4461-9275-bad870ab834a" />

<img width="923" height="126" alt="image" src="https://github.com/user-attachments/assets/707b934e-5405-4d41-9203-019f93b1cbeb" />



