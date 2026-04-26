<h1>Fase 1: Preparació del sistema</h1>

<p>Primer de tot afegirem un disc a la maquina virtual anant a parametres emmagatzematge i a controlador sata afegeix un nou disc </p>
<img width="571" height="246" alt="image" src="https://github.com/user-attachments/assets/5b01c074-db11-43ae-83f6-a17a60e5ddbd" />

<p>i veurem la lista de tots els disc durs de les maquines virtuals i anirem a crea</p>
<img width="928" height="822" alt="image" src="https://github.com/user-attachments/assets/2e4456da-35bc-452a-ae37-723d5ffba2c8" />

<p>Triarem el format VDI per a el disc que es el que es seleciona predeterminadament</p>
<img width="734" height="449" alt="image" src="https://github.com/user-attachments/assets/69487a2d-53c1-48f3-8fd6-edcbe37619c6" />

<p>Apretarem seguent sense selecionar cap opcio perque no minteresa reservar tot el espai de el disc i vull que sigui dinamic</p>
<img width="734" height="449" alt="image" src="https://github.com/user-attachments/assets/feefe832-b789-41e7-9b88-542ed8cc7a95" />

<p>Selecionarem la mida de el disc de 5 GB i apretarem a finalizar</p>
<img width="734" height="449" alt="image" src="https://github.com/user-attachments/assets/06ed5000-6a46-460c-a93e-c06168c5e8ac" />
<img width="394" height="110" alt="image" src="https://github.com/user-attachments/assets/77bc7789-a661-47a5-b202-7ad0da1099b7" />

<p>Iniciarem la maquina Windows 10 i per gestionar els discs des de Windows, executem diskmgmt.msc (o clic dret al menú d’inici → Gestió de discs).</p>
<p>Veurem que salta el avis per a inizializar el disc que acabem de inserir i tambe veurem que el disc esta no assignat i apretarem aceptar</p>
<img width="756" height="598" alt="image" src="https://github.com/user-attachments/assets/cc6b2999-6818-4223-a760-73352c908b9f" />

<p>Farem clic dret i a nou volumen simple selecionarem la mida de la particio per exemple que ocupi tot el disc les 5 GB i assignarem una lletra</p>
<img width="754" height="602" alt="image" src="https://github.com/user-attachments/assets/3812e5d7-98b0-444a-b733-fcb1c9578459" />
<img width="754" height="600" alt="image" src="https://github.com/user-attachments/assets/85b8204a-a394-40ac-a974-5247a49ac621" />
<img width="499" height="392" alt="image" src="https://github.com/user-attachments/assets/4e291190-7001-424b-9034-53c566d70d34" />

<p>Selecionarem el sistema de arxius NTFS deixarem el tamany de la unitat de assignacio a el predeterminat i la etiqueta de el volumen tambe i deixarem la opcio del formateix rapid i apretarem finaliza</p>
<img width="499" height="392" alt="image" src="https://github.com/user-attachments/assets/1e1e6bc3-e061-4c68-8d73-ee84148c2884" />

<p>Per a crear les dos particions el que farem es eliminar la que hem creat anteriorment amb clic dret i eliminar volumen i crearem un nou volumen de 3 GB anomenat dades</p>
<img width="501" height="397" alt="image" src="https://github.com/user-attachments/assets/d12f91bf-cedf-468a-8cc8-7edeada9695b" />
<img width="735" height="103" alt="image" src="https://github.com/user-attachments/assets/7fe93c50-86db-436d-9d1a-0086db2d1b27" />

<p>Crearem la particio de portable de 2 GB en FAT 32</p>
<img width="498" height="392" alt="image" src="https://github.com/user-attachments/assets/b56f783b-9b0a-4817-9549-bf49c0e87cad" />
<img width="498" height="392" alt="image" src="https://github.com/user-attachments/assets/53a86d8e-1cc2-4a98-b151-4d19469d1abd" />

<p>Ya estarien les dues particions una amb NTFS i la altra amb FAT 32</p>
<img width="913" height="539" alt="Captura de pantalla de 2026-04-26 21-22-30" src="https://github.com/user-attachments/assets/569d8c06-a683-4ce2-94ad-c5e59eb51535" />

<p>Per a fer la comprovacio obrirem el terminal i executarem diskpart</p>
<img width="255" height="67" alt="image" src="https://github.com/user-attachments/assets/ee89be78-6da4-4c53-8954-a3c39a42506a" />

<p>Exectarem les seguents comandes</p>
<img width="658" height="525" alt="image" src="https://github.com/user-attachments/assets/f116f7a2-015f-4406-9f0d-272a074cb3b5" />

<p>La captura mostra el resultat complet. Podem confirmar:</p>
<p>Disc 0 (50 GB): disc principal del sistema amb la partició C: (NTFS, 49 GB).</p>
<p>Disc 1 (5 GB): el nou disc amb dues particions:</p>
<p>Partició 2 → Volum 4 · Lletra E: · Etiqueta Dades · NTFS · 3000 MB</p> 
<p>Partició 3 → Volum 5 · Lletra F: · Etiqueta PORTABLE · FAT32 · 2117 MB</p>

<h1>Fase 2: Quotes i usuaris</h1>
<p>Les quotes de disc a Windows permeten limitar l’espai que cada usuari pot usar dins d’una partició NTFS. Per activar-les, obrim l’Explorador de Windows, clic dret sobre la unitat Dades (E:) i seleccionem Propietats.</p>
<img width="424" height="430" alt="image" src="https://github.com/user-attachments/assets/e2e87afd-460e-4a0d-aad2-9c1ef8bf2a40" />

<p>A la finestra de propietats ens dirigim a la pestanya Cuota i fem clic a Mostrar configuració de cuota.</p>
<img width="366" height="209" alt="image" src="https://github.com/user-attachments/assets/18810f08-0d2b-40c8-a693-fde44b0c4bd0" />

<p>Dins del panell de configuració de quotes, activem les opcions:</p>
<p>Habilita la administración de cuota: activa el sistema de quotes.</p>
<p>Denegar espacio en disco a usuarios que superen el límite: bloqueja l’escriptura quan se supera el límit.</p>
<p>Limitar espacio en disco a: 300 MB</p>
<p>Establecer el nivel de advertencia en: 100 MB (l’usuari rebrà un avís quan quasi ompli el límit)</p>
<p>Registrar un evento cuando algún usuario supere su límite de cuota</p>
<p>Registrar un evento cuando algún usuario supere su nivel de advertencia</p>
<img width="363" height="450" alt="image" src="https://github.com/user-attachments/assets/230927d4-637b-4677-a813-1b27b5367b7b" />

<p>Per crear usuaris locals a Windows, executem lusrmgr.msc (Gestió d’usuaris i grups locals) des de la finestra Executar (Win + R).</p>
<img width="402" height="209" alt="image" src="https://github.com/user-attachments/assets/50adc7f2-e7d2-46f9-9284-890040f09050" />

<p>Dins de la consola, fem clic dret sobre Usuaris i Usuari nou</p>
<img width="658" height="251" alt="image" src="https://github.com/user-attachments/assets/41c13d8f-fd93-42f6-87df-6f20a84c2b5c" />

<p>Creem l’usuari alumne1 amb la contrasenya corresponent. Activem l’opció La contrasenya mai expira per evitar problemes en les proves.</p>
<img width="416" height="390" alt="image" src="https://github.com/user-attachments/assets/577ef5b4-3cef-4c57-b6f6-23741c532df6" />

<p>De la mateixa manera, creem l’usuari alumne2 amb la mateixa configuració.</p>
<img width="415" height="390" alt="image" src="https://github.com/user-attachments/assets/ff5c6883-c97f-4420-8393-fc9aa20b2c47" />

<p>Ara dins de lusrmgr.msc, fem clic sobre la carpeta Grupos per veure tots els grups existents. Clic dret en un espai buit de la llista → Grupo nuevo</p>
<img width="304" height="261" alt="image" src="https://github.com/user-attachments/assets/d5152946-f5e0-45f5-be37-e3c50dcf663a" />

<p>Introduïm el nom del grup Limitats i afegim els dos usuaris creats (alumne1 i alumne2) com a membres. Fem clic a Crear per finalitzar.</p>
<img width="417" height="391" alt="image" src="https://github.com/user-attachments/assets/e0d3f253-0112-4f40-bf6a-e23785cacde7" />

<p>Per comprovar que les quotes funcionen correctament, iniciem sessió com a **alumne1** i intentem crear fitxers de diverses mides a la partició `E:\` amb la comanda `fsutil file createnew`:</p>

<p>fsutil file createnew E:\prova.dat 350000000   → Error 112: Espai insuficient (supera els 300 MB)</p>
<p>fsutil file createnew E:\prova.dat 150000000   → Fitxer creat (150 MB)</p>
<p>fsutil file createnew E:\prova.dat 150000000   → Fitxer creat (re-escriu el mateix)</p>
<p>fsutil file createnew E:\prova2.dat 50000000   → Fitxer creat (50 MB)</p>
<p>fsutil file createnew E:\prova3.dat 50000000   → Fitxer creat (50 MB)</p>
<p>fsutil file createnew E:\prova4.dat 50000000   → Fitxer creat (50 MB)</p>
<p>fsutil file createnew E:\prova5.dat 50000000   → Error 112: Espai insuficient (ja s'han superat els 300 MB)</p>

<p>La captura mostra clarament com el sistema nega l'accés quan l'usuari intenta superar els 300 MB assignats per la quota. L'error 112 és el codi de Windows per "espai en disc insuficient", que en aquest context és provocat artificialment per la quota, no per la mida real del disc.</p>
<img width="740" height="482" alt="image" src="https://github.com/user-attachments/assets/a3a53d01-c48a-4155-8d86-bb892b94db2c" />

<h1>Fase 3: Script de còpia i automatització</h1>

<p>Des de la configuració de VirtualBox, afegim un tercer disc (Windows10_2.vdi) de 5 GB connectat al port SATA 3. Servirà com a unitat de còpies de seguretat.</p>
<img width="881" height="546" alt="image" src="https://github.com/user-attachments/assets/b3d3b78f-ac64-4dd2-a97d-5b4fade78799" />

<p>Un cop dins de Windows, obrim la Gestió de discs i localitzem el nou Disc 2 (4,98 GB, no asignat). Clic dret → Nou volum simple</p>
<img width="744" height="109" alt="image" src="https://github.com/user-attachments/assets/bb5a4c49-7fd9-400e-8249-ba349ef2e2fd" />

<p>Formatem tot el disc com a NTFS i li posem l'etiqueta Backups. Assignem la lletra B:.</p>
<img width="491" height="386" alt="image" src="https://github.com/user-attachments/assets/589fec38-e819-4028-a37d-9df86d501afa" />
<img width="488" height="382" alt="image" src="https://github.com/user-attachments/assets/433c1fb2-e10c-4b7f-ae22-b4a5e266d940" />
<img width="744" height="109" alt="image" src="https://github.com/user-attachments/assets/c215a212-cd0f-4892-aaf2-0711adea7acf" />

<p>Un cop creat i muntat el disc Backups (B:), creem manualment la carpeta CòpiesUsuaris dins de la unitat B:. Aquesta carpeta actuarà com a contenidor principal on l'script crearà una subcarpeta per cada usuari.</p>
<img width="664" height="137" alt="image" src="https://github.com/user-attachments/assets/91dcb468-0f20-4a7f-baf3-4d9f7c505080" />

Creem un fitxer script.bat (per exemple a C:\Users\FerranBernis\Documents\scriptBackup.bat) amb el contingut següent:

<p>@echo off</p>
<p>xcopy C:\Users\%USERNAME% B:\CòpiesUsuaris\%USERNAME% /E /I /Y</p>
<img width="516" height="105" alt="image" src="https://github.com/user-attachments/assets/4cbd26ef-60c5-407f-b10a-11c460fc2d86" />


<p>Explicació de la comanda:</p>
<p>@echo off=	Silencia la sortida de les comandes a la consola</p>
<p>xcopy=	Copia fitxers i directoris (inclou subdirectoris)</p>
<p>%USERNAME%=	Variable d'entorn que s'expandeix automàticament amb el nom de l'usuari actiu</p>
<p>/E=	Copia tots els subdirectoris, fins i tot els buits</p>
<p>/I=	Si la destinació no existeix, la crea com a directori</p>
<p>/Y=	Sobreescriu fitxers existents sense demanar confirmació</p>

<p>Per assignar l'script perquè s'executi automàticament en iniciar sessió, obrim l'Editor de directrius de grup local executant gpedit.msc des de la finestra Executar (Win + R).</p>
<img width="391" height="186" alt="image" src="https://github.com/user-attachments/assets/f82139fc-2e84-4293-883f-04f9887ebf81" />

<p>Dins de l'editor, naveguem per l'arbre de directives:</p>
<p>Configuració d'usuari → Configuració de Windows → Scripts (inici de sessió o tancament de sessió)</p>
<p>Fem doble clic sobre Iniciar sessió per obrir la finestra de propietats.</p>
<img width="679" height="335" alt="image" src="https://github.com/user-attachments/assets/59ad095b-595b-496b-8732-54bf81e5c613" />

<p>A la finestra de propietats d'Iniciar sessió, fem clic a Agregar… i introduïm la ruta completa al nostre script:</p>
<img width="402" height="460" alt="image" src="https://github.com/user-attachments/assets/45d75a7b-c380-478d-81c5-a0c941f54cd5" />
<img width="425" height="293" alt="image" src="https://github.com/user-attachments/assets/df200a3b-b3af-4ed1-adbb-7a6fc8d988cf" />


<h1>Fase 4: Verificació i documentació</h1>




