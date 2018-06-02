# Pemodelan dan Simulasi Astronomi
### Apa itu Astronomi?
Astronomi merupakan ilmu yang mempelajari tentang benda langit. Astronomi berasal dari kata
*astro* yang artinya luar dan *nomos* yang artinya ilmu. Secara sederhana, astronomi mempelajari
tentang benda-benda yang ada di luar bumi kita. ini berbeda dari astrologi yang merupakan ilmu
yang mempelajari bagaimana benda-benda di luar bumi dapat mempengaruhi kehidupan yang
terjadi di bumi. Astronomi membahas posisi, bentuk, rupa, dan aktivitas-aktivitas dari setiap
entitas yang berada di luar bumi.

Pemodelan dan simulasi yang akan dibahas di artikel ini terdiri dari Celeste dan planetarium,
sebagai model dan simulasi untuk menggambarkan posisi dan pergerakan objek-objek langit di
alam semesta.

### Berkenalan dengan Celeste: Latar Belakang
Manusia sejak zaman dahulu dibekali dengan keinginan untuk melihat angkasa luar, memahami
bagaimana pada malam hari terbentuk suatu pemandangan indah yang terbentuk jauh di atas
sana. Mereka ingin menunjukkannya kepada orang-orang agar mereka bisa mengetahui
keadaan apa yang terjadi. Mereka ingin membuat suatu memori tentang kejadian tersebut,
tetapi untuk menggambarkan objek-objek langit secara jelas dengan tingkat keakuratan yang
tinggi itu sulit. Salah satu teknik yang digunakan untuk mengatasi masalah tersebut adalah
penggunaan foto antariksa.

Foto antariksa bukanlah sekedar foto dengan menggunakan kamera biasa yang sering kita
gunakan. Foto antariksa dibuat dengan kamera detektor khusus penangkap foton dan
gelombang cahaya. Setiap detektor memiliki tingkat cahaya tertentu yang dapat ditangkap
(biasanya berdasarkan panjang gelombangnya) dengan tingkat keakuratan yang berbeda-beda.
Ketika cahaya dengan panjang gelombang tertentu masuk ke dalam teleskop, ia akan
ditangkap oleh detektor pada teleskop tersebut sesuai dengan panjang gelombangnya dan
sensitivitas dari teleskop tersebut.

Terkadang, foto antariksa diambil untuk mengamati suatu objek langit tertentu. Permasalahan
yang dapat timbul adalah objek langit tersebut berada pada jarak yang sangat jauh sehingga
sulit untuk ditangkap oleh detektor, dan di antara objek langit tersebut dengan detektor terdapat
objek-objek langit lainnya. Objek-objek langit yang bersinar akan memancarkan foton yang
dapat menimbulkan inferensi pembiasan cahaya pada detektor, dan bisa menghasilkan gambar
yang bervariasi detailnya, tergantung dari detektor yang digunakan. Padahal, foto antariksa
diharapkan detil untuk semakin menggambarkan objek langit yang difoto. Misalkan ada dua
benda dengan jumlah pelepasan foton yang mendekati satu sama lain, ada kemungkinan dalam
foto antariksa yang terbentuk hanya terdapat satu objek saja, padahal seharusnya dua objek.
Pengurangan objek inilah yang membuat foto antariksa yang terbentuk tidak menjadi akurat.
Berkenalan dengan Celeste: Berkenalan dengan Bintang dan Galaksi
Didefinisikan dua jenis benda langit yang menyumbang pelepasan foton, yaitu bintang dan
galaksi. Bintang adalah benda langit yang bercahaya, sedangkan galaksi adalah alam semesta.
Bintang pada umumnya lebih terang daripada galaksi, meskipun bintang mengalami fluktuasi
pelepasan foton yang menyebabkan kita sering melihat bintang berkelap-kelip di langit. Ukuran
bintang jauh lebih kecil daripada galaksi, sehingga sering digambarkan sebagai titik dalam foto
antrariksa.

### Berkenalan dengan Celeste: Melihat Model Celeste
Sekelompok ahli yang terdiri dari Jeffrey Regier, University of California; Andrew Miller, Harvard
University; Jon McAuliffe, University of California; Ryan Adams, Harvard University; Matt
Hoffman, Adobe Research; Dustin Lang, Carnegie Mellon University; David Schlegel, Lawrence
Berkeley National Laboratory; dan Prabhat, Lawrence Berkeley National Laboratory
mengusulkan suatu model yang dinamai Celeste. Model ini menggunakan prinsip variabel
random Bernoulli dalam penentuan setiap pixelnya, membagi objek-objek astronomi menjadi
bintang dan galaksi saja(mengabaikan objek astronomi yang bukan kedua jenis ini). Untuk
menyatakan tingkat pelepasan foton(untuk mempermudah disebut kecerlangan), digunakan
sistem fotometrik dibandingkan dengan magnitudo. Magnitudo dapat bernilai berbeda untuk
panjang gelombang yang berbeda sehingga nilainya dapat bervariasi sesuai dengan panjang
gelombang dari foton yang dipancarkan oleh bintang, sedangkan sistem fotometrik memiliki
cakupan yang lebih luas, yaitu magnitudo, perbedaan warna dan *passband*. *Passband* adalah
frekuensi dan panjang gelombang dari suatu cahaya yang dapat melewati filter pada CCD
detektor. *Passband* dibagi menjadi 3 berdasarkan panjang gelombangnya, yaitu: *wide band*
yang setidaknya memiliki ketebalan 400Å, *intermediate band*, yang berada di antara 70 and
400Å, *narrow band* di bawah 70Å.

Celeste memanfaatkan sistem fotometrik yang digabungkan dengan sistem warna dengan
distribusi menggunakan Gaussian multivariat. Bintang dimodelkan dengan titik, sedangkan
galaksi dimodelkan dengan kecerlangan untuk setiap filternya, dan “*light kernel*”, yaitu distribusi
radiasi dari sebuah galaksi di langit yang terdiri dari prototipe eksponensial untuk pemodelan
galaksi spiral dan de Vaucouleur untuk pemodelan galaksi eliptikal dan secara matematis
digambarkan dengan Gaussian yang terdiri dari mean dan matriks kovariansi yang berbeda
sesuai dengan ukurannya.

Model Celeste digambarkan seperti pada gambar 4. *Field* menyatakan bagian dari langit yang
sedang menjadi pembicaraan. Langit terdiri dari beberapa *field* yang dapat saling
tumpang-tindih satu sama lainnya. Untuk setiap *field*, difoto beberapa kali, sekali untuk setiap
filter yang digunakan. Hasil dari foto tersebut terdiri dari beberapa pixel yang menggambarkan
kecerlangan dari langit yang sedang difoto dalam *field*. Kecerlangan latar belakang langit dalam
foto antariksa dimodelkan sebagai proses Poisson yang homogen untuk setiap foto dan
independen terhadap bintang dan galaksi. Efek “blur” yang berada pada foto antariksa
dimodelkan dengan *point spread function* (PSF) yang dibagi menjadi beberapa model Gaussian
sehingga dapat mempengaruhi beberapa pixel yang berdekatan pada foto antariksa.
Inferensi dilakukan dengan teknik *variational inference* terhadap besaran-besaran yang ada,
baik dengan *maximum likehood* , maupun dengan priori dan analisis numerik.

### Planetarium : Sejarah
Pada zaman dahulu, manusia membuat suatu alat peraga mekanik untuk mensimulasikan dan
memperlihatkan pergerakan benda-benda langit khususnya sistem tata surya seperti matahari,
planet , bulan dan bintang. Alat peraga ini merupakan contoh pemodelan dan simulasi
pergerakan benda-benda langit pada zaman dahulu.

Seiring perkembangan zaman, alat ini berkembang menjadi sebuah ruangan dengan atap
berbentuk kubah untuk mensimulasikan keadaan langit yang sebenarnya dipandang dari segala
tempat di Bumi dan segala waktu. Ruangan berkubah ini disebut planetarium. Pertama kali
sistem planetarium yang dibuat masih menggunakan sistem mekanik dan dibuat oleh Eise
Eisinga, seorang tukang pembuat *wool* ada abad ke 18. Planetarium Eisinga masih hanya
berupa simulasi bagaimana sistem tata surya kita bergerak. Planetarium Eisinga ini menjadi
planetarium tertua yang terletak hanya di sebuah ruang tamu kecil dari dua rumah yang
menyatu di sebuah kota bernama Franeker, Belanda.

Saat ini, planetarium bekerja mensimulasikan pergerakan benda-benda langit menggunakan
proyektor dan layar yang berupa kubah dari planetarium itu sendiri. Layar berupa kubah
setengah lingkaran ini dibuat agar hasil simulasi yang diperlihatkan terlihat lebih nyata dan lebih
menyerupai langit-langit bumi (yang pada dasarnya juga merupakan setengah lingkaran).

### Proyektor Planetarium
Pada planetarium, proyektor berfungsi untuk memperagakan pergerakan benda-benda langit
sesuai dengan waktu dan lokasi. Proyektor planetarium mempunyai desain dasar dengan 3
komponen utamanya yaitu :
1. Sistem proyeksi planet
Planet-planet diproyeksikan melalui sistem tersendiri yaitu analog mekanikal. Analog
mekanikal berupa model miniatur dari karakteristik orbit planet-planet (satu analog
untuk setiap proyektor planet), bumi, matahari, dan posisi planet secara mekanis
ditampilkan. Operator dapat memilih baik dari Gambar 7 : Proyektor Planetarium
sudut pandang bumi maupun sudut pandang matahari untuk tampilan gerakan planet-planet.
2. Lampu bintang
Memproyeksikan milyaran bintang-bintang angkasa. Lampu bintang merupakan sebuah
alat yang menghasilkan titik-titik intensitas sumber cahaya yang kecil. Cahaya ini
difokuskan melalui ribuan lensa individual dan lubang-lubang kecil yang diproyeksikan
ke kubah.
3. Penggunaan komputer
Komputer digunakan untuk menyambungkan tiga jenis gerakan sumbu yang
memungkinkan operator untuk memutar bola langit pada titik manapun yang
memungkinkan observasi langit dari planet manapun dalam tata surya atau dari titik
manapun di antariksa. Sistem ini mendemonstrasikan sudut pandang normal bumi ke
langit melalui konsep Copernicus atau Galileo dan mengatur keseluruhan gerakan untuk
dianalisa pengamat. Pertunjukan berlangsung dengan diiringi musik. Materi pertunjukan
bisa berbeda-beda tergantung pada judul pertunjukan dan jadwal.

### Kubah dan Sistem Operasi Planetarium
Kubah difungsikan sebagai layar berbentuk setengah lingkaran yang dipantulkan oleh
proyektor. Kubah pada planetarium umumnya di bangun dengan material lapisan dari rib-rib
baja melengkung sebagai rangka serta terdapat lapisan panel aluminium yang disambung pada
rangka.

Proyektor yang ada di ruang planetarium diletakkan di tengah yang dikelilingi oleh tempat duduk
penonton dan sistem *loudspeaker* yang berada di sisi kubah. Sumber *infrared* dan sistem
kamera mendeteksi cahaya yang dipantulkan dari penonton. Gambar diproses oleh system
Cinematrix, yang mengirimkan informasi kepada prosesor grafis SGI. SGI bertugas mengirim
data melalui MIDI kepada Sistem Interaktif Audio. Dan lagi, planetarium mengoperasikan
sebuah sistem multimedia independen dengan sistem grafis vektor (Digistar) dan banyak audio,
video dan peralatan proyeksi *slide* yang dikendalikan dengan komputer.

### *Software* Planetarium
Di era modern saat ini, segala sesuatu terutama yang berkaitan dengan menggambarkan,
memperagakan, memodelkan dan mensimulasikan sesuatu hal telah dapat digunakan secara
praktis melalui aplikasi / *software* di komputer maupun *smartphone*. Hal ini terjadi tidak
terkecuali dengan planetarium yang mensimulasikan pergerakan benda-benda langit.
Beberapa contoh *software* planetarium yaitu Stellarium, Asynx Planetarium, Celestia, dan lain
sebagainya. Stellarium merupakan salah satu *software* yang paling banyak digunakan sebagai
pembelajaran maupun mengamati simulasi penampakan benda - benda langit. Bahkan pada
kebanyakan proyektor planetarium menggunakan *software* Stellarium untuk dijalankan. *Software*
ini merupakan *software open source* planetarium yang dapat memperlihatkan langit dalam
tampilan tiga dimensi (3D), seperti apa yang terlihat ketika dalam keadaan mata telanjang, atau
memakai teropong, maupun teleskop dengan letak koordinat dan waktu yang dapat kita
tentukan.

### Pembagian Tugas
Kevin - Apa itu Astronomi dan Celeste
Aldo - Planetarium

### Referensi :
[http://www.skyandtelescope.com/astronomy-resources/whats-difference-astrology-vs-astronomy](http://www.skyandtelescope.com/astronomy-resources/whats-difference-astrology-vs-astronomy)
[https://www.spacetelescope.org/projects/fits_liberator/improc/](https://www.spacetelescope.org/projects/fits_liberator/improc/)
[https://ivanbatara.wordpress.com/2009/02/23/bintang-berjalan/](https://ivanbatara.wordpress.com/2009/02/23/bintang-berjalan/)
[http://proceedings.mlr.press/v37/regier15.pdf](http://proceedings.mlr.press/v37/regier15.pdf)
[http://www.dictionary.com/browse/passband](http://www.dictionary.com/browse/passband)
[http://www.astro.caltech.edu/~george/ay122/Bessel2005ARAA43p293.pdf](http://www.astro.caltech.edu/~george/ay122/Bessel2005ARAA43p293.pdf)
[http://star-www.rl.ac.uk/docs/sc6.htx/sc6se7.html](http://star-www.rl.ac.uk/docs/sc6.htx/sc6se7.html)
[https://www.viva.co.id/gaya-hidup/travel/689279-mengunjungi-planetarium-tertua-di-dunia](https://www.viva.co.id/gaya-hidup/travel/689279-mengunjungi-planetarium-tertua-di-dunia)
[https://zenosphere.wordpress.com/2014/08/30/astronomi-open-source-lewat-stellarium/](https://zenosphere.wordpress.com/2014/08/30/astronomi-open-source-lewat-stellarium/)
[https://sinta.unud.ac.id/uploads/wisuda/1204205006-3-bab%202.pdf](https://sinta.unud.ac.id/uploads/wisuda/1204205006-3-bab%202.pdf)
[http://tipsandtrick-chipunk.blogspot.com/2014/01/stellarium-sebagai-media-pembelajaran.html](http://tipsandtrick-chipunk.blogspot.com/2014/01/stellarium-sebagai-media-pembelajaran.html)
[https://www.cnnindonesia.com/teknologi/20170105114413-199-184251/astronom-klaim-temukan-sumber-suara-misterius-dari-antariksa](https://www.cnnindonesia.com/teknologi/20170105114413-199-184251/astronom-klaim-temukan-sumber-suara-misterius-dari-antariksa)
[https://ilmualamkita.wordpress.com/2010/12/20/galaksi/](https://ilmualamkita.wordpress.com/2010/12/20/galaksi/)

