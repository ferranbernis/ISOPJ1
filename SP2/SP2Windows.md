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
<p>xcopy C:\Users\%USERNAME% B:\CopiesUsuaris\%USERNAME% /E /I /Y</p>
<img width="512" height="108" alt="image" src="https://github.com/user-attachments/assets/4117d2aa-feb1-4d58-87a5-4006ef224cf1" />



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

<p>Iniciem sessió amb l’usuari alumne1. L’script s’executa automàticament a l’inici de sessió i copia el contingut de C:\Users\alumne1 a B:\CòpiesUsuaris\alumne1.</p>
<p>La captura del Explorador de Windows confirma que la còpia s’ha realitzat correctament: es veuen totes les carpetes del perfil d’alumne1 (Contacts, Desktop, Documents, Downloads, etc.) dins de B:\CòpiesUsuaris\alumne1\</p>
<img width="1125" height="415" alt="image" src="https://github.com/user-attachments/assets/bb1cd593-18c2-4584-a451-214c4e736139" />

<p>Comprovacio Cuotes (Explicacio mes a dalt)</p>
<img width="740" height="482" alt="image" src="https://github.com/user-attachments/assets/a3a53d01-c48a-4155-8d86-bb892b94db2c" />

<h1>Fase 5: Gestió de processos i serveis</h1>

<p>Iniciem sessió com a alumne1, obrim la consola (CMD) i executem tasklist per obtenir la llista de tots els processos actius, amb el seu PID, sessió i ús de memòria.</p>
<img width="464" height="111" alt="image" src="https://github.com/user-attachments/assets/f6e4beba-5d3c-4989-880e-528f5d42bd88" />

<p>La captura mostra processos típics del sistema: System Idle Process, System, Registry, smss.exe, csrss.exe, wininit.exe, services.exe, lsass.exe, svchost.exe (múltiples instàncies), etc.</p>
<img width="642" height="441" alt="image" src="https://github.com/user-attachments/assets/f6c76da7-4a34-4aad-b7bf-2abf3f87e545" />

<p>Redirigim la sortida a un fitxer de text per poder-la analitzar:
La captura mostra que la comanda s’ha executat correctament i que el fitxer processos_inici.txt (12.950 bytes) s’ha creat al directori de l’usuari alumne1. Fem dir per confirmar-ho.</p>
<img width="550" height="530" alt="image" src="https://github.com/user-attachments/assets/eb7b708d-c6fd-4cd6-a7da-63557a78fa59" />

<p>Comprovem alguns processos clau usant findstr per filtrar del fitxer guardat:</p>
<p>findstr explorer.exe C:\Users\%USERNAME%\processos_inici.txt</p>
<p>findstr SearchIndexer.exe C:\Users\%USERNAME%\processos_inici.txt</p>
<p>findstr OneDrive.exe C:\Users\%USERNAME%\processos_inici.txt</p>

<img width="770" height="234" alt="image" src="https://github.com/user-attachments/assets/8389b57b-6cd9-4356-aff4-36dc806029df" />

<p>explorer.exe (275 MB) → Gestor del sistema de fitxers i escriptori.</p>
<p>SearchIndexer.exe (42 MB) → Servei d’indexació per a la cerca de Windows.</p>
<p>OneDrive.exe (133–135 MB) → Sincronització al núvol de Microsoft; prescindible en entorns de laboratori.</p>

<p>Filtrem el tasklist per trobar processos no essencials per a l’usuari en un entorn educatiu:</p>
<p>La captura mostra que OneDrive.exe s’executa en dues instàncies (PID 4272 i 1480), consumint uns 125 MB de RAM en total.</p>
<img width="631" height="107" alt="image" src="https://github.com/user-attachments/assets/d067828a-b6f3-46ea-bb6f-407cabd64d0b" />

**Taula de processos prescindibles identificats:**

| Nom del procés | Memòria aproximada | Justificació per eliminar |
|----------------|----------------|---------------------------|
| `OneDrive.exe` | 125 MB | Sincronització al núvol innecessària en un entorn de VM sense connexió a internet real |
| `Teams.exe` | 150-400 MB | Client de videoconferència no necessari per a tasques d'aula |
| `SkypeApp.exe` | 80-150 MB | Aplicació de comunicació no requerida en l'entorn de laboratori |

<p>Ara eliminarem el procces One drive amb taskkill /IM OneDrive.exe /F (Ha de estar la terminal com a administrador per a puger eliminar el procces)</p>
<img width="495" height="162" alt="image" src="https://github.com/user-attachments/assets/e130b88e-86ff-43ff-850b-85ec4a886d94" />

<p>Comprovarem amb tasklist | findstr OneDrive.exe</p>
<img width="469" height="143" alt="image" src="https://github.com/user-attachments/assets/d6c9330d-b0df-48b6-a0ab-95d944176212" />

<p>Modifiquem l’script script.bat per incloure les comandes taskkill que eliminaran automàticament OneDrive i Teams cada vegada que un usuari iniciï sessió:</p>
<p>taskkill /IM OneDrive.exe /F</p>
<p>taskkill /IM Teams.exe /F</p>
<img width="520" height="160" alt="image" src="https://github.com/user-attachments/assets/4f1108f0-4f42-4752-9d44-febdf30bc4df" />

<p>Per verificar que funciona, iniciem sessió com a alumne2 i comprovem que OneDrive no s’executa:</p>
<img width="435" height="69" alt="image" src="https://github.com/user-attachments/assets/a222a3bc-2b48-4e93-a3c0-6d91ce3e3024" />

#### Fitxer de processos i anàlisi

El fitxer `processos_inici.txt` generat per `tasklist` conté la llista completa de processos en el moment d'inici de sessió. S'ha adjuntat a la documentació com a evidència.

#### Què passa si mates un procés crític com explorer.exe?

`explorer.exe` és el gestor de l'escriptori i de l'Explorador de fitxers de Windows. Si l'eliminem:

1. L'escriptori desapareix completament (barra de tasques, icones, fons).
2. No podem obrir cap finestra ni accedir a cap fitxer via GUI.
3. El sistema NO es penja: el kernel i els serveis segueixen funcionant.
4. Per recuperar-lo: `Ctrl + Alt + Supr → Administrador de tasques → Arxiu → Executar nova tasca → explorer.exe`

> **Prova controlada:** En un entorn de laboratori, eliminar `explorer.exe` és reversible. En un entorn de producció caldria anar amb molta cura, ja que l'usuari quedaria sense interfície gràfica.

#### Com millora el rendiment en VMs?

| Acció | Recursos alliberats |
|-------|---------------------|
| Matar OneDrive.exe | ~135 MB RAM, CPU esporàdica |
| Matar Teams.exe | ~150-400 MB RAM, CPU i xarxa |
| Deshabilitar SearchIndexer | ~40 MB RAM, I/O disc reduït |
| Total estimat | +300-600 MB RAM disponible |

En màquines virtuals amb 4 GB de RAM, alliberar 300+ MB pot significar la diferència entre un sistema fluid i un de lent.

---

<h1>Fase 6: Gestió de permisos (ACLs) </h1>

### Què són les ACLs i com funcionen a Windows

A Windows, cada fitxer i carpeta té una **llista de control d'accés (ACL, Access Control List)**. Aquesta llista defineix qui pot fer què amb aquell recurs.

Cada entrada d'una ACL es diu **ACE (Access Control Entry)** i indica:
- Quina **identitat** (usuari o grup) està afectada
- Quins **permisos** té (lectura, escriptura, execució, control total, etc.)
- Si el permís és **Permetre** o **Denegar**

**Permisos disponibles a Windows:**

| Permís | Descripció |
|--------|------------|
| Control total (F) | Accés complet: llegir, escriure, modificar, eliminar i canviar permisos |
| Modificar (M) | Llegir, escriure i eliminar fitxers, però no canviar permisos |
| Lectura i execució (RX) | Obrir fitxers i executar programes |
| Mostrar contingut | Llistar el contingut d'una carpeta |
| Lectura (R) | Obrir fitxers en mode només lectura |
| Escriptura (W) | Crear fitxers i subcarpetes |

**Herència:** Els permisos d'una carpeta pare es propaguen automàticament a les subcarpetes i fitxers. Quan es desactiva la herència, cal decidir si es conserven o descarten les entrades heretades.

---


<p> Iniciem sessió com a administrador i creem la carpeta Projectes dintre de la particio dades</p>
<img width="780" height="184" alt="image" src="https://github.com/user-attachments/assets/aa8093a4-c85b-4287-8747-571017c85fb5" />

<p>Fem clic dret sobre E:\Projectes → Propietats → Seguretat. Veiem els permisos actuals (heretats de E:\): Usuaris autenticats, SYSTEM, Administradors i Usuaris.</p>
<p>Fem clic a Opciones avanzadas per accedir a la configuració avançada de permisos.</p>
<img width="363" height="485" alt="image" src="https://github.com/user-attachments/assets/1f7a89a5-3d34-4d16-8953-6390b3c7e328" />

<p>A la finestra d'opcions avançades veiem que els permisos estan heretats des de E:\ (columna "Heredada de"). Fem clic a Deshabilitar herencia per trencar la herència i poder gestionar els permisos de forma independent.</p>
<img width="361" height="480" alt="image" src="https://github.com/user-attachments/assets/25b6ce4e-1ce8-44b0-95c6-55f1c9b8b181" />

<p>Eliminem l'entrada de Usuarios (DESKTOP-6104CQ0\Usuarios) per netejar els permisos per defecte que no necessitem. Seleccionem l'entrada i fem clic a Quitar.</p>
<img width="767" height="526" alt="image" src="https://github.com/user-attachments/assets/dbc3aae9-e599-4268-8bc0-4f8452a3024d" />

<p>Ara afegim el grup Limitats amb Control total. Fem clic a Agregar, introduïm Limitats, i marquem tots els permisos bàsics (Control total, Modificar, Lectura i execució, Mostrar el contingut de la carpeta, Lectura, Escriptura).</p>

<p>El tipus és Permitir i s'aplica a Esta carpeta, subcarpetes y archivos per garantir herència cap avall.</p>
<img width="916" height="413" alt="image" src="https://github.com/user-attachments/assets/199c5a06-640e-47e7-a903-b268d0585506" />

<p>La captura de la configuració avançada final mostra el resultat: la columna "Heredada de" ara diu "Ninguno" per a totes les entrades, confirmant que la herència s'ha desactivat. El grup Limitats (FerranBernis\Limitats) apareix amb Control total.</p>
<img width="1034" height="523" alt="image" src="https://github.com/user-attachments/assets/3219bf11-0417-4ffe-9879-f3666ed9e12f" />

<p>Iniciem sessió com a alumne1 (membre del grup Limitats). Creem un fitxer de text prova.txt a E:\Projectes amb el contingut "hola".</p>

<p>La captura confirma que alumne1 ha pogut crear i escriure el fitxer sense cap problema, tal com s'esperava (té Control total hereta del grup Limitats).</p>
<img width="1771" height="520" alt="image" src="https://github.com/user-attachments/assets/1d1373b4-89db-4934-a3b0-2e016fda449f" />

<p>El fitxer prova.txt.</p>
<img width="258" height="91" alt="image" src="https://github.com/user-attachments/assets/7aa8e58e-825a-4534-8771-19d86cd3130e" />

Tornem a iniciar sessió com a **administrador** i executem la comanda `icacls` per aplicar una excepció específica per a `alumne2`:

```
icacls "E:\Projectes" /grant:r alumne2:(R)
```

**Explicació:**
- `/grant:r` → Substitueix (reset) qualsevol permís existent per a aquell usuari.
- `alumne2:(R)` → Assigna **només lectura (R)** a l'usuari alumne2.

<p>La sortida confirma: *"Se procesaron correctamente 1 archivos"*. Ara `alumne2` té **només lectura**, tot i ser membre del grup Limitats que té Control total (la entrada explícita de l'usuari té **prioritat** sobre la del grup).</p>
<img width="555" height="175" alt="image" src="https://github.com/user-attachments/assets/40a366d4-29a8-4ac2-9239-ac5cd3ff5972" />

<p>Iniciem sessió com a alumne2 i accedim a E:\Projectes.</p>
<p>Quan alumne2 intenta crear un fitxer nou o modificar algun existent, rep un missatge de denegació d'accés.</p>
<img width="1129" height="642" alt="image" src="https://github.com/user-attachments/assets/b3967735-13c1-477b-ae7e-d41b19979b11" />

<p>Executem la comanda des de la consola com a administrador per veure l’estat final de tots els permisos de E:\Projectes:</p>
<img width="573" height="328" alt="image" src="https://github.com/user-attachments/assets/4512eefc-c285-459b-b2e1-18a38ff85686" />












