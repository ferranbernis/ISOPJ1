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



