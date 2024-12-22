<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="icon" type="image/png" href="website/MajorMatch.png">
    <title>MajorMatch</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            font-family: Arial, sans-serif;
            color: white;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            flex-direction: column;
            background-image: url('https://cdn.pixabay.com/photo/2021/01/21/15/54/books-5937716_1280.jpg');
            background-size: cover;
            background-repeat: no-repeat;
            background-position: center;
        }
        .welcome-container {
            text-align: center;
        }
        .welcome-container h1 {
            font-size: 3rem;
            margin-bottom: 1rem;
            color: white;
            padding: 5px 10px;
            border-radius: 5px;
        }
        .welcome-container p {
            font-size: 1.2rem;
            margin-bottom: 25rem;
            color: white;
        }
        .welcome-container button {
            padding: 10px 20px;
            font-size: 1.2rem;
            background-color: #ff9900;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            position: absolute;
            bottom: 380px; /* Tombol diposisikan 20px dari bawah */
            right: 675px; /* Tombol diposisikan 20px dari kanan */
        }
        .welcome-container button:hover {
            background-color: #872b00;
        }
    </style>
</head>
<body>
    <div class="welcome-container">
        <h1>Welcome to MajorMatch!</h1>
        <p>Find your best major with your favourite lesson!</p>
        <button onclick="startWebsite()">Mulai</button>
    </div>

    <script>
        function startWebsite() {
            // Redirect ke halaman utama
            window.location.href = "major-match.html"; // Ganti dengan nama file HTML utama Anda
        }
    </script>
</body>
</html>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Temukan jurusan terbaik berdasarkan mata pelajaran favorit Anda di Website Rekomendasi Jurusan ini. Dapatkan rekomendasi jurusan secara mudah dan cepat! (Diawali dengan huruf kapital, contoh: Matematika, Geografi.)">
    <link rel="icon" type="image/png" href="website/MajorMatch.png">
    <title>MajorMatch</title>
    <style>
        body {
            font-family: Arial, sans-serif;
        margin: 0;
        padding: 0;
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        background-image: url('https://graduate.binus.ac.id/files/2023/04/GAMBAR-SPLAH-10-scaled.jpg');
        background-size: cover;
        background-repeat: no-repeat;
        background-position: center;
        }
        .chat-container {
            width: 100%;
            max-width: 400px;
            background: white;
            padding: 20px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
            border-radius: 10px;
        }
        .chat-header {
            text-align: center;
            margin-bottom: 20px;
        }
        .chat-header h1 {
            font-size: 1.5rem;
            color: #333;
        }
        .chat-form {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }
        .chat-form input[type="text"] {
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
            font-size: 1rem;
        }
        .chat-form button {
            padding: 10px;
            background: #ff9500;
            color: white;
            border: none;
            border-radius: 5px;
            font-size: 1rem;
            cursor: pointer;
        }
        .chat-form button:hover {
            background: #893e00;
        }
        .chat-output {
            margin-top: 20px;
            padding: 10px;
            background: #f8f9fa;
            border-radius: 5px;
            font-size: 1rem;
        }
    </style>
</head>
<body>
    <div class="chat-container">
        <div class="chat-header">
            <h1>Rekomendasi Jurusan Berdasarkan Pelajaran Favorit</h1>
            <p>Website ini dirancang untuk membantu Anda menemukan jurusan yang sesuai dengan mata pelajaran favorit Anda. Masukkan pelajaran favorit Anda dan dapatkan rekomendasi jurusan yang relevan! (Diawali dengan huruf kapital, contoh: Matematika, Geografi.)</p>
        </div>
        <form class="chat-form" id="chatForm">
            <label for="subject">Apa mata pelajaran favoritmu?</label>
            <input type="text" id="subject" placeholder="Masukkan mata pelajaran, contoh: Matematika...">
            <button type="submit">Cari Jurusan</button>
        </form>
        <div class="chat-output" id="chatOutput" style="display: none;"></div>
    </div>

    <script>
        const recommendations = {
            "Matematika": ["Pendidikan Matematika" ,"Teknik Informatika", "Aktuaria", "Statistika", "Matematika", "Matematika Bisnis", "Sistem Informasi", "Sistem Komputer", "Ilmu Komputer", "Teknik Komputer", "Teknologi Informasi", "Teknik Telekomunikasi", "Sains Data", "Cyber Security", "Teknologi Rekayasa Multimedia", "Manajemen Informatika", "Perencanaan Wilayah dan Kota", "Konstruksi", "Arsitektur", "Arsitektur Lanskap", "Rekayasa Perangkat Lunak"],
            "Fisika": ["Geofisika", "Fiska", "Pendidikan Fisika", "Teknik Mesin", "Teknik Elektro", "Astronomi", "Meteorologi", "Teknik Geologi", "Teknik Geodesi", "Teknik Geomatika", "Instrumentasi", "Teknik Robotika", "Teknik Otomotif", "Teknik Fisika", "Teknik Material", "Teknik Nuklir"],
            "Biologi": ["Kedokteran", "Bioteknologi", "Farmasi", "Biologi", "Pendidikan Biologi", "Ilmu Lingkungan", "Kehutanan", "Peternakan", "Pertanian", "Teknik Biomedis", "Kebidanan", "Kesehatan Lingkungan", "Gizi", "Fisioterapi", "Kedokteran Hewan", "Pendidikan Kedokteran Gigi", "Biokimia", "Mikrobiologi", "Ilmu Biomedis", "Ilmu Kelautan", "Ilmu Perikanan"],
            "Kimia": ["Kimia", "Pendidikan Kimia", "Teknik Kimia", "Gizi", "Biokimia", "Teknik Pertambangan", "Teknik Perminyakan", "Teknik Metalurgi", "Teknik Nuklir", "Teknik Material"],
            "Sosiologi": ["Kesejahteraan Sosial", "Antropologi Sosial", "Pendidikan Sosiologi", "Ilmu Komunikasi", "Hubungan Internasional", "Psikologi", "Ilmu Politik", "Administrasi Publik", "Kriminologi", "Studi Pembangunan", "Sosiologi", "Pariwisata", "Perhotelan", "Tata Boga"],
            "Ekonomi": ["Ilmu Ekonomi", "Ekonomi Pembangunan", "Ekonomi Syariah", "Akuntansi", "Manajemen", "Keuangan dan Perbankan", "Bisnis Internasional", "Ekonomi Pertanian", "Ekonomi Sumberdaya dan Lingkungan", "Statistika", "Pendidikan Ekonomi Koperasi", "Bisnis Digital", "Teknik Industri"],
            "Sejarah": ["Sejarah", "Pendidikan Sejarah", "Ilmu Politik", "Hubungan Internasional", "Antropologi", "Arkeologi", "Sastra dan Bahasa Daerah", "Ilmu Hukum", "Ilmu Komunikasi", "Administrasi Publik"],
            "Geografi": ["Geografi", "Pendidikan Geografi", "Teknik Geologi", "Geofisika", "Meteorologi", "Oseanografi", "Planologi", "Teknik Geodesi", "Teknik Geomatika", "Ilmu Pengelolaan dan Pemberdayaan Sumber Daya Alam dan Lingkungan", "Ilmu Lingkungan", "Pariwisata", "Konservasi Sumber Daya Hutan", "Manajemen Bencana"],
            "Seni": ["DKV", "Seni Rupa", "Seni Kriya", "Desain Grafis", "Fotografi", "Desain Interior", "Seni Tari", "Seni Musik", "Seni Pertunjukan", "Sinematografi", "Animasi", "Film dan Televisi", "Tata Busana"],
            "Bahasa": ["Sastra Asing", "Sastra Indonesia", "Sastra Inggris", "Pendidikan Bahasa Indonesia", "Pendidikan Bahasa Inggris", "Ilmu Linguistik", "Filsafat"],
            "Olahraga": ["Pendidikan Olahraga", "Ilmu Keolahragaan", "Pendidikan Jasmani, Kesehatan, dan Rekreasi", "Manajemen Olahraga"],
            "Agama": ["Ilmu Agama Islam", "Pendidikan Agama Islam", "Manajemen Dakwah", "Psikologi Islam", "Sastra Arab"]
        };

        document.getElementById('chatForm').addEventListener('submit', function(event) {
            event.preventDefault();
            const subject = document.getElementById('subject').value.trim();
            const outputDiv = document.getElementById('chatOutput');

            if (subject in recommendations) {
                const result = recommendations[subject]
                .map(jurusan => `<a href="detail.html?major=${encodeURIComponent(jurusan)}">${jurusan}</a>`)
                .join('<br>');

                outputDiv.innerHTML = `Rekomendasi jurusan:<br>${result}`;
        } else {
            outputDiv.textContent = "Maaf, jurusan untuk mata pelajaran tersebut belum tersedia.";
        }

            outputDiv.style.display = "block";
        });
    </script>
</body>
</html>

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Detail Jurusan</title>
  <style>
    body {
        font-family: Arial, sans-serif;
        margin: 0;
        padding: 0;
        background-image: url('https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQj6L6CYieZ_z4HqI3IvEdwX4cqp6Z03iN6Ig&s'); /* Ganti dengan URL wallpaper Anda */
        background-size: cover;
        background-position: center;
        background-repeat: no-repeat;
        color: white;
        text-shadow: 1px 1px 2px rgb(12, 12, 12);
    }

    h1, h2, h3 {
        text-align: center;
    }

    #details {
        background: rgba(89, 2, 2, 0.7); /* Latar belakang semi-transparan untuk teks */
        margin: 50px auto;
        padding: 20px;
        border-radius: 10px;
        max-width: 600px;
        text-align: justify;
    }
</style>
</head>
<body>
  <h1>Detail Jurusan</h1>
  <div id="details"></div>

  <script>
    // Ambil jurusan dari query string
    const params = new URLSearchParams(window.location.search);
    const major = params.get('major');

    // Data detail jurusan
    const majorDetails = {
      "Pendidikan Matematika": {
        description: "Pendidikan Matematika merupakan jurusan yang mempelajari teori-teori dasar matematika, misalnya aljabar, geometri, statistika, kalkulus, matematika diskrit, dan lainnya. Nah yang membedakan jurusan ini dengan ilmu murni adalah, kamu dibekali kemampuan terkait cara menyampaikan pelajaran Matematika kepada murid-murid tentunya dengan cara-cara yang menarik supaya mudah dimengerti. Pokoknya jurusan ini cocok banget untuk kamu yang suka Matematika tapi juga punya passion mengajar.",
        jobs: ["Account Officer", "Guru", "Dosen", "Data Scientist", "Content Creator", "Content Writer", "Research and Development", "System Analyst", "Aktuaris"]
      },
      "Teknik Informatika": {
        description: "Teknik Informatika merupakan bidang ilmu yang mempelajari bagaimana menggunakan teknologi komputer secara optimal guna menangani masalah transformasi atau pengolahan data dengan proses logika. Di Jurusan Teknik Informatika kamu akan mempelajari berbagai prinsip terkait ilmu komputer mulai dari proses perancangan, pengembangan, pengujian, hingga evaluasi sistem operasi perangkat lunak. Selama kuliah kamu akan banyak mengkaji pemrograman dan komputasi, dan dibekali pula dengan keterampilan merancang perangkat lunak.",
        jobs: ["Application Engineer", "Game Creator", "Game Developer", "Software Engineering", "Konsultan IT", "Data Scientist", "Programmer", "Robot Engineer", "Dosen", "Teknisi Rekam Medis", "Technopreneur"]
      },
      "Aktuaria": {
        description: "Jurusan Aktuaria adalah jurusan yang mempelajari ilmu probabilitas, matematika, statistik dan keuangan untuk dapat melakukan pengelolaan resiko dan ketidakpastian dalam membantu client meminimalkan resiko. Lulusan Jurusan Aktuaria akan mendapat gelar Sarjana Ilmu Aktuaria (S.Aktr), tetapi belum bisa disebut sebagai aktuaris. Untuk menjadi seorang aktuaris, kamu harus mengikuti dan lulus ujian profesi aktuaris yang diselenggarakan oleh Persatuan Aktuaris Indonesia (PAI). Profesi aktuaris tengah menjadi sorotan atau prioritas Otoritas Jasa Keuangan (OJK) yang gencar melakukan sosialisasi program 1000 aktuaris. Data menyebutkan saat ini jumlah aktuaris di Indonesia baru memenuhi sekitar 50% dari kuota yang diharapkan.",
        jobs: ["Akuntan", "Ekonom", "Aktuaris"]
      },
      "Statistika": {
        description: "Statistika merupakan perpanjangan dari bidang studi Matematika. Bedanya, Statistika lebih fokus ke arah data dan pengolahannya. Sederhananya, jika kamu kuliah di jurusan Statistika akan mempelajari cara mengumpulkan, menganalisis, dan menyajikan data ke dalam bahasa yang mudah dipahami sehingga bisa dijadikan sebuah informasi untuk banyak orang.",
        jobs: ["Pegawai Negeri Sipil", "Pegawai Negeri Sipil Daerah", "Account Officer", "Market Researcher", "Data Scientist", "Dosen", "Ahli Statistik", "System Analyst", "Aktuaris"]
      },
      "Matematika": {
        description: "Jurusan Matematika fokus mempelajari berbagai teori matematika secara mendalam, seperti geometri, aljabar, hingga matematika diskrit. Jadi, kamu akan bertemu dengan beragam konsep dalam matematika seperti mempelajari fitur lain dari angka, juga ruang multidimensi. Selain itu, ada juga lho matematika terapan untuk mempelajari aplikasi matematika di bidang lainnya.",
        jobs: ["Penilai Real Estate", "Market Researcher", "Application Engineer", "Software Egineering", "Data Scientist", "Programmer", "Guru", "Dosen", "Quality Assurance & Quality Control", "Ahli Statistik", "Aktuaris"]
      },
      "Matematika Bisnis": {
        description: "Matematika Bisnis adalah jurusan yang mempelajari penerapan ilmu matematika, statistik, dan komputasi dalam pemecahan masalah di dunia bisnis. Perusahaan dan organisasi komersial menerapkan ilmu matematika untuk mencatat dan mengelola operasional bisnis seperti akuntansi, manajemen persediaan, pemasaran, peramalan penjualan, dan analisis keuangan perusahaan. So, nggak heran ya kalau Matematika Bisnis kini mulai dibuka sebagai program studi di kampus karena ilmu ini dianggap penting untuk mendukung berjalannya segala aktivitas di dunia bisnis. Di beberapa kampus di Indonesia, Matematika Bisnis juga sering ditemukan sebagai pilihan peminatan di dalam Jurusan Matematika.",
        jobs: ["Market Researcher", "Data Scientist", "Finance", "Data Analyst"]
      },
      "Sistem Informasi": {
        description: "Jurusan Sistem Informasi adalah bidang keilmuan yang menggabungkan ilmu komputer dengan bisnis dan manajemen. Di prodi ini kamu akan belajar gimana mengidentifikasi kebutuhan dan proses bisnis perusahaan berdasarkan data-data yang dimiliki perusahan, kemudian merancang sistem yang sesuai dengan kebutuhan perusahaan. Jadi, selain belajar teknik pemrograman, kamu juga dituntut untuk mempelajari proses bisnis yang ada di perusahaan. Oleh karena itu, lulusan Prodi Sistem Informasi diharapkan dapat mengembangkan sebuah sistem pengolahan data dari berbagai sumber untuk dapat disajikan sebagai informasi yang bermanfaat bagi perusahaan.",
        jobs: ["Application Engineer", "Konsultan IT", "Data Scientist", "Programmer", "Dosen", "Rekam Medis", "Digital Marketing", "Research and Development", "Technopreneur"]
      },
      "Sistem Komputer": {
        description: "Jurusan Sistem Komputer merupakan sebuah jurusan perkuliahan yang juga dikenal dengan nama Jurusan Teknik Komputer. Jurusan ini sangat direkomendasikan bagi kamu yang suka terhadap dunia teknik, komunikasi, dan juga jaringan. Melalui Jurusan Sistem Komputer, mahasiswa akan belajar mengenai pengintegrasian antara teknik elektro dan teknik komputer. Kedua ilmu teknik yang diintegrasikan tersebut akan dimanfaatkan untuk kepentingan pengembangan hardware, software, dan juga jaringan komputer (network). Mahasiswa akan dibimbing untuk merancang sebuah prosesor dari komputer atau perangkat elektronik lainnya. Keberadaan prosesor ini sangat penting untuk melakukan pengontrolan sebuah sistem yang akan berjalan pada sebuah komputer atau perangkat lain. Untuk menghasilkan central processing komputer yang benar-benar brilian, mahasiswa Jurusan Sistem Komputer akan berkutat pada perancangan berbagai komponen central processing unit (CPU). Ketika sudah mahir dalam merancang CPU, mahasiswa akan pandai merakit CPU sendiri berdasarkan requirement yang mereka inginkan terhadap jalannya sistem komputer nantinya. Di samping itu, dalam jurusan ini mahasiswa juga akan diajarkan bagaimana melakukan rekayasa perangkat lunak dan juga membuat perangkat lunak yang baru. Skill pengembangan perangkat lunak tersebut akan sangat berguna pada era saat ini yang mana semuanya membutuhkan aplikasi dan software yang sangat menarik untuk membantu aktivitas sehari-hari.",
        jobs: ["Application Engineer", "Software Engineering", "Konsultan IT"]
      },
      "Ilmu Komputer": {
        description: "Ilmu Komputer merupakan bidang studi yang identik dengan computer programming. Kamu akan dibekali keterampilan menyusun algoritma dan programming untuk mengembangkan sebuah aplikasi maupun sistem perangkat lunak. Jadi, pada dasarnya kamu akan belajar bagaimana cara agar komputer mampu melakukan berbagai hal yang diinginkan penggunanya. Di jurusan ini, ide-ide kreatifmu bisa diwujudkan apalagi di dunia informasi digital yang semakin tak terbatas ini!",
        jobs: ["Web Designer", "Application Engineer", "Game Creator", "Game Developer", "Software Engineering", "Konsultan IT", "Data Scientist", "Programmer", "Dosen", "Technopreneur"]
      },
      "Teknik Komputer": {
        description: "Kuliah di Jurusan Teknik Komputer tentunya sangat cocok bagi kamu yang senang mengulik komputer. Apalagi, perkembangan komputer juga semakin pesat dan telah digunakan oleh hampir semua bidang pekerjaan. Kini semakin banyak universitas atau perguruan tinggi yang membuka program studi tersebut. Peminatnya semakin meningkat karena prospek kerja lulusannya dinilai cukup luas. Teknik Komputer adalah salah satu jurusan kuliah yang berkaitan dengan Ilmu Komputer. Jurusan Teknik Komputer merupakan disiplin Ilmu Rekayasa Komputasi (Computer Engineering) yang mengkombinasikan Ilmu Komputer (Computer Science) dengan Ilmu Teknik Elektro (Electrical Engineering). Teknik Komputer adalah ilmu yang kokoh berdiri pada teori dan prinsip komputasi, Matematika, serta rekayasa. Hal tersebut diaplikasikan untuk merancang perangkat lunak, perangkat keras, jaringan, dan instrumen atau peralatan terkomputerisasi untuk menyelesaikan berbagai permasalahan teknis serta bisa diterapkan pada berbagai area. Sementara itu, bahan kajian keilmuan Teknik Komputer ini meliputi desain dan rekayasa sistem perangkat keras digital. Termasuk mikrokomputer, jaringan komputer, sistem embedded, serta perangkat lain yang berbasis pada komputer. Kajian keilmuan Jurusan Teknik Komputer juga meliputi perkembangan perangkat lunak yang fokus pada desain serta rekayasa perangkat lunak sebagai antarmuka bagi perangkat digital antara pengguna (user interface) dengan perangkat lainnya (device interface). Namun, kurikulum jurusan ini lebih ditekankan pada perangkat keras dibandingkan dengan perangkat lunak. Pada kondisi tertentu, dapat terjadi kemungkinan pembelajaran yang seimbang antara perangkat keras dan perangkat lunak.",
        jobs: ["Web Designer", "Application Engineer", "Konsultan IT", "Data Scientist", "Programmer", "Dosen", "Technopreneur"]
      },
      "Teknologi Informasi": {
        description: "Jurusan Teknologi Informasi atau TI mendalami solusi-solusi terkait teknologi komputer yang diterapkan pada berbagai bidang, di antaranya yakni pemerintahan, kesehatan, pendidikan, termasuk pengembangan bisnis. Banyak orang yang menyamakan Jurusan TI ini dengan jurusan lain seperti Sistem Informasi dan Teknik Informatika, padahal ketiganya tidak sama. Jurusan Teknik Informatika berfokus pada pemrograman dan pengembangan software atau aplikasi, sedangkan Jurusan Sistem Informasi berfokus pada hal lain di luar pemrograman yakni implementasi ilmu komputer dalam mendukung fungsi manajemen ataupun bisnis. Lalu, Jurusan Teknologi Informasi sendiri merupakan jurusan yang mempelajari tentang sistem atau teknologi olah data termasuk implementasinya pada berbagai hal, termasuk pengembangan software, artificial intelligence, dan pengembangan sistem informasi berbasis cloud. Dengan begitu, nantinya, lulusan Jurusan Teknologi Informasi akan sangat berperan dalam berbagai proses dalam membangun sistem informasi mulai dari pembuatan database, network, software, hardware, dan lain sebagainya. Lulusan Jurusan Teknologi Informasi banyak dibutuhkan karena saat ini peradaban dunia sudah memasuki era serba digital. Di mana kehidupan masyarakat banyak bergantung pada teknologi yang tengah berkembang pesat, sehingga tidak mengherankan jika Jurusan TI menjadi sasaran para millenials. Jika sudah menempuh pendidikan Prodi Teknologi Informasi, setelah lulus kamu akan mempunyai kemampuan dan pengetahuan secara detail terkait hardware dan software, serta bagaimana mengatasi segala bentuk masalah yang terjadi pada komputer. Kamu pun akan memiliki kemampuan untuk mengelola informasi dan data yang cepat dan juga berkualitas.",
        jobs: ["Application Engineer", "Konsultan IT", "Programmer", "Dosen", "Technopreneur"]
      },
      "Teknik Telekomunikasi": {
        description: "Era digital industri telekomunikasi saat ini menjadi tulang punggung pada setiap jenis telekomunikasi baik itu seluler, satelit dan internet dalam bentuk suara, gambar dan video untuk dapat berjalan secara efisien. Teknik Telekomunikasi adalah jurusan yang mempelajari pengiriman data berupa suara, gambar dan video melalui media komunikasi seluler, wireless atau satellite, anda akan belajar mulai menginstall, menguji, memelihara dan mengoperasikan secara luas semua piranti telekomunikasi. Program studi ini dirancang untuk membekali mahasiswa teknik telekomunikasi berdasarkan teknologi terbaru dengan ruang lingkup jaringan internet, komunikasi seluler, radio, satelite dan komputer sistem. Kurikulum dasar yang akan dipelajari mencakup matematika, fisika dan teknik komputer mata kuliah dasar ini yang akan menjadi dasar keahlian lulusan sehingga mampu mendesain hingga implementasi teknologi komunikasi, pemahaman teknologi terbaru bidang telekomunikasi seperti Wireless, 5G dan Cloud Computing wajib diketahui.",
        jobs: ["Engineer Telekomunikasi", "Analis Jaringan", "Manager Proyek Telekomunikasi", "Spesialis Keamanan Siber", "Researcher di Bidang Telekomunikasi", "Konsultan", "Network Designer", "Teknisi Lapangan", "Marketing Specialist", "Operator Network Operations Center"]
      },
      "Sains Data": {
        description: "Dengan kemunculan Revolusi Industri 4.0 ditambah dengan begitu banyaknya teknologi yang muncul, jurusan Sains Data menjadi cukup menarik dijadikan sebagai pilihan. Lebih-lebih jika mengingat sekarang ini banyak perusahaan yang ikut menggunakan sains data untuk pengembangan bisnis. Dengan adanya trend ini, kebutuhan perusahaan pada tenaga data sains tentu menjadi semakin meningkat. Bahkan, salah satu survei yang dilakukan oleh IBM atau Institute of Business Management for Business Value mengungkapkan bila kebutuhan lulusan jurusan data sains mengalami lonjakan yang begitu signifikan dari seluruh dunia. Data scientist, menjadi salah satu profesi lulusan data sains yang semakin diincar karena memiliki penghasilan yang sangat baik. Tidak mengherankan, peminat jurusan data science di Indonesia juga terus meningkat. Lantas, data scientist jurusan apa? Untuk mengetahui pengertian sains data, kamu harus mengetahui pengertian data terlebih dahulu. Data adalah kumpulan data yang diolah menjadi informasi, olahan informasi tersebut akan digunakan sebagai medium agar dapat mengambil keputusan. Data sendiri terdiri dari berbagai jenis seperti yang terstruktur, semi terstruktur serta tidak terstruktur. Sedangkan, sains data adalah sebuah ilmu terapan yang menganalisis serta mempelajari data, khususnya data numeric, baik terstruktur atau tidak terstruktur. Ilmu sains data ini adalah bidang ilmu gabungan mulai dari statistika, bisnis dan ilmu komputer.",
        jobs: ["Data Scientist", "Data Analyst", "Data Storyteller", "Business Analyst", "Pegawai Negeri Sipil"]
      },
      "Cyber Security": {
        description: "Jurusan Cyber Security adalah jurusan yang mempelajari cara melindungi data dan sistem dari serangan dunia maya. Jurusan ini sangat relevan dengan perkembangan teknologi dan kebutuhan industri di era digital. Lulusannya memiliki prospek kerja yang menjanjikan karena banyak perusahaan dan pemerintah yang membutuhkan ahli keamanan siber. Jurusan Cyber Security membekali mahasiswa dengan pengetahuan dan keterampilan dalam pengujian, perancangan, dan implementasi pertahanan dalam dunia maya. Di jurusan ini, kamu juga akan belajar tentang aspek hukum, etika, dan manajemen risiko yang berkaitan dengan keamanan siber.",
        jobs: ["Konsultan IT", "IT Support", "Analis Cyber Security", "Ethical Hacker", "Information Security Engineer", "Security Software Developer"]
      },
      "Teknologi Rekayasa Multimedia": {
        description: "Media dalam bentuk video, musik, ataupun animasi semakin sering digunakan untuk menyampaikan informasi sekarang ini. Selain membutuhkan kreativitas dalam proses pembuatannya, kemampuan menggunakan software dan hardware komputer juga diperlukan. Untuk memenuhi hal tersebut, beberapa perguruan tinggi pun menyediakan jurusan yang dapat mempelajari ilmu komputer serta multimedia di waktu yang bersamaan. Nah, kalau kamu tertarik dan ingin tahu bagaimana rasanya mendalami dua bidang keilmuan tersebut, kamu dapat berkuliah di Jurusan Teknologi Rekayasa Multimedia. Jurusan Teknologi Rekayasa Multimedia merupakan jurusan yang mempelajari ilmu terapan yang berkaitan dengan teknologi untuk memproses informasi pada media digital dalam bentuk grafik, teks, animasi, video on demand, dan musik yang dibuat menggunakan komputer. Di jurusan ini, kamu akan dibekali keterampilan untuk menguasai bidang teknologi komputer yang mencakup software dan hardware, grafik komputer, webmaster, dan database komputer. Adapun untuk bidang multimedia, hal yang kamu pelajari antara lain mencakup komunikasi multimedia, hak cipta multimedia, animasi digital, Musical Instrument Digital Interface (MIDI), dan scoring musik.",
        jobs: ["Video Editor", "UI/UX Designer", "Fotografer", "Graphic Designer", "Entreupreneur", "Animator"]
      },
      "Manajemen Informatika": {
        description: "Manajemen Informatika adalah ilmu yang mempelajari teori-teori dalam teknologi informasi serta penggunaannya dalam membuat bisnis perusahaan menjadi lebih mudah. Dalam hal ini Manajemen Informatika mengkaji bagaimana membuat desain suatu sistem yang tepat dan sesuai dengan tujuan organisasi maupun perusahaan yang sifatnya mendukung kebutuhan dan proses di dalam bisnis. Ilmu Manajemen Informatika bermanfaat untuk membantu perusahaan ataupun organisasi agar bisa mencapai apa yang ditargetkan dan menjadi tujuannya secara lebih efektif dan efisien. Jurusan ini muncul sebagai jawaban dari kebutuhan sumber daya manusia yang memiliki kemampuan untuk melakukan manajemen pada fungsi software supaya bisa berjalan sebagaimana mestinya dan lancar. Oleh sebab itu, perbedaan antara mahasiswa pada Jurusan Manajemen Informatika dengan Ilmu Komputer terdapat pada ruang lingkup yang dipelajarinya. Jika pada Jurusan Ilmu Komputer hanya diberikan pengetahuan tentang pemrograman saja, maka di Jurusan Manajemen Informatika mahasiswanya juga dibekali dengan ilmu manajemen dan bisnis.",
        jobs: ["Web Designer", "Konsultan IT", "Software Developer", "Dosen"]
      },
      "Perencanaan Wilayah dan Kota": {
        description: "Perencanaan Wilayah dan Kota (PWK) dikenal juga dengan nama jurusan Teknik Planologi. Jurusan ini mempelajari perencanaan kota dan wilayah dengan mempertimbangkan berbagai aspek termasuk aspek sosial, ekonomi, dan politik. Kamu juga akan dibekali dengan keterampilan menyusun rencana tata ruang serta mengevaluasi berbagai kebijakan dan program yang berhubungan sama rencana tata ruang dan tata wilayah.",
        jobs: ["Pegawai Negeri Sipil", "Account Officer", "Penilai Real Estate", "Bagian Perencanaan dan Pengembangan Real Estate", "Konsultan Properti", "Bagian Penjualan Perusahaan Perumahan", "Surveyor Tanah", "Dosen", "Bartender", "System Analyst", "Arsiparis"]
      },
      "Konstruksi": {
        description: "Konstruksi adalah ilmu yang digunakan untuk melakukan perencanaan, pelaksanaan, dan perbaikan bangunan. Di jurusan ini, kamu akan mempelajari bagaimana proses pembuatan bangunan dengan memperhatikan fungsi, aspek struktural, keindahan, dan ekonomi.",
        jobs: ["Account Officer", "Penilai Real Estate", "Bagian Perencanaan dan Pengembangan Real Estate", "Sales Perusahaan Konstruksi", "Bagian Penjualan Perusahaan Perumahan", "Surveyor Tanah", "Kontraktor", "Bartender", "Quality Assurance & Quality Control", "System Analyst"]
      },
      "Arsitektur": {
        description: "Meski tergolong sebagai salah satu jurusan di Fakultas Teknik, Jurusan Arsitektur sebetulnya tidak melulu membahas masalah teknik, bahkan cenderung ke bidang seni dan estetika. Di Program Studi Arsitektur, kamu bakal mendesain bangunan sesuai kebutuhan dan tentu saja dengan memperhatikan nilai fungsi, keindahan, dan keamanan, ya! Tidak cuma berhenti sampai menciptakan desain nih, kamu juga akan dibekali dengan kemampuan perencanaan anggaran yang berguna saat membuat bagunan. Wah, kalau rumah orang aja lain bisa dirancang seindah mungkin, apalagi rumahmu dengan dia? Pasti akan sangat nyaman, bukan?",
        jobs: ["Penilai Real Estate", "Bagian Perencanaan dan Pengembangan Real Estate", "Drafter", "Resepsionis (Front Office)", "Operator CAD (Computer-Aided-Design)", "Arsitek", "Dosen", "Entrepreuner"]
      },
      "Arsitektur Lanskap": {
        description: "Arsitektur Lanskap merupakan jurusan yang fokus pada perencanaan dan perancangan desain area luar ruangan atau outdoor. Secara garis besar, hal yang akan kamu pelajari melalui jurusan Arsitektur Lanskap yakni bagaimana berkolaborasi dalam beragam proyek besar luar ruangan, contohnya yakni desain kota, remediasi bekas kawasan industri, dan kompleks perumahan. Arsitektur lanskap adalah jurusan yang bertanggung jawab bukan hanya dalam aspek estetika, namun juga ekologi. Jadi, dalam jurusan ini kamu akan memahami betul tentang desain dan konstruksi bangunan luar ruangan serta pengetahuan akan pelestarian ekologis. Lulusan Arsitektur Lanskap diharapkan mampu untuk menciptakan desain konstruksi luar ruangan yang memperhatikan lingkungan. Sehingga sumber daya yang ada di sekitar lingkungan tersebut tidak rusak dan tetap terjaga.",
        jobs: ["Arsitek Lanskap", "Konsultan Lanskap", "Wirausaha", "ASN", "Ahli Teknik Lingkungan", "Pengembang Permukiman"]
      },
      "Rekayasa Perangkat Lunak": {
        description: "Jurusan Rekayasa Perangkat Lunak merupakan jurusan yang didalamnya mempelajari prinsip sekaligus teknik mendesain perangkat lunak yang mudah digunakan dan tepat guna. Jurusan yang juga disebut Software Engineering ini bisa menjadi wadah yang tepat bagi kamu yang ingin mempelajari desain program dan mengembangkan sebuah software ataupun sistem operasi. Melalui jurusan ini, kamu akan diajari bagaimana cara mendesain dan melakukan analisis algoritma, guna membuat program aplikasi berbasis mobile atau web. Selain itu, kamu juga akan belajar mengenai pengembangan sebuah sistem operasi dengan menggunakan struktur data yang efisien. Pada dasarnya, Jurusan Rekayasa Perangkat Lunak disiapkan untuk menyokong kebutuhan profesional dalam bidang teknologi. Tentu saja hal ini menjadi berita baik bagi kamu yang suka terhadap hal-hal berbau teknologi, apalagi bagi kamu yang memang bercita-cita menjadi ahli pada bidang tersebut. Dengan perkembangan teknologi yang semakin pesat dari waktu ke waktu, peluang karier pada bidang ini pun semakin menjanjikan. Tidak hanya itu, kamu juga bisa memperoleh gaji dengan nominal yang cukup besar Sudah cukup banyak perguruan tinggi yang menyediakan Jurusan Rekayasa Perangkat Lunak. Umumnya, jurusan ini bisa kamu temui di Fakultas Ilmu Komputer maupun Fakultas Teknik, tergantung dari kurikulum yang digunakan oleh suatu kampus.",
        jobs: ["Application Engineer", "Software Engineering", "Konsultan IT", "Programmer", "Dosen"]
      },
      "Geofisika": {
        description: "Geofisika merupakan bidang ilmu kebumian yang mempelajari bumi dengan kaidah-kaidah fisika. Kamu akan dibekali dengan keterampilan melakukan telaah dan menyelesaikan berbagai permasalahan yang bersumber dari pendayagunaan sumber daya alam, sumber daya energi, dan sumber daya lingkungan. Selain itu, kamu juga akan belajar mitigasi bencana kebumian yang dalam praktiknya membutuhkan pemodelan dan pengolahan data geofisika.",
        jobs: ["Pegawai Negeri Sipil", "Teknisi Tambang, Minyak, dan Material", "Teknisi Konservasi Lingkungan", "Tenaga Ahli Prakiraan Cuaca", "Dosen", "Research and Development", "Bartender", "System Analyst", "Arsiparis"]
      },
      "Fisika": {
        description: "Dibalik kerumitan rumus dan angka yang lekat dengan Fisika, pasti banyak dari kalian yang menjadikan ilmu ini sebagai mata pelajaran favorit selama sekolah. Fisika merupakan bidang ilmu yang fokus mempelajari gejala alam tidak hidup (materi) dalam lingkup ruang dan waktu. Mulai dari menelusuri dasar-dasar hukum alam partikel submikroskopis yang membentuk materi hingga perilaku materi alam semesta sebagai satu kesatuan kosmos. Selain itu, kamu juga bakal belajar fisika secara fundamental dan modern seperti; dinamika, gaya elektromagnetik, mekanika kuantum, termodinamika, dan sebagainya.",
        jobs: ["Pegawai Negeri Sipil", "Account Officer", "Bagian Operasional dan Logistik", "Data Scientist", "Bagian Perencanaan Produk Otomotif", "Teknisi Tambang, Minyak, dan Material", "Guru", "Instruktur Pelatihan Kejuruan", "Dosen", "Electrical Engineer", "Research and Development", "Quality Assurance & Quality Control", "System Analyst"]
      },
      "Pendidikan Fisika": {
        description: "Jurusan Pendidikan Fisika adalah program studi yang mempelajari tentang ilmu fisika dan penerapannya dalam konteks pendidikan dan pengajaran. Jurusan ini membekali mahasiswanya dengan pengetahuan dan keterampilan yang dibutuhkan untuk menjadi guru fisika yang profesional. Tujuan dari jurusan Pendidikan Fisika adalah untuk menghasilkan lulusan yang memiliki kompetensi pedagogik, kepribadian, sosial, dan profesional serta mampu membangun pembelajaran berbasis ICT, mampu berwirausaha dalam bidang pendidikan maupun bidang non kependidikan, serta mampu menghasilkan karya ilmiah di bidang pendidikan fisika.",
        jobs: ["Tenaga Pengajar di Lembaga Bimbingan Belajar", "Dosen", "Peneliti di Bidang Fisika", "Guru", "Ahli Fisika, Konsultan Fisika, atau Quality Control", "Konten Kreator"]
      },
      "Teknik Mesin": {
        description: "Jurusan Teknik Mesin tidak melulu soal mesin motor, mobil, dan kegiatan perbengkelan lainnya. Tapi kamu juga akan belajar hal-hal terkait konversi energi, konstruksi dan perancangan, teknik produksi, juga material. Memang benar sih, secara umum kamu akan mempelajari mesin dengan menggunakan dasar fisika dan matematika, seperti pergerakan mesin, aliran air untuk mesin, material dan desain mesin, elemen penting seperti roda gigi dan sumber mata air, metode pengolahan, metode produksi, pengendalian melalui komputer, dsb.",
        jobs: ["Mekanik Pesawat", "Bagian Perencanaan Produk Otomotif", "Mekanik Mobil", "Perancang dan Teknisi Mesin", "Teknisi dan Operator Pabrik", "Robot Engineer", "Dosen", "Research and Development", "System Analyst"]
      },
      "Teknik Elektro": {
        description: "Teknik Elektro merupakan bidang ilmu yang mempelajari listrik dan aplikasinya dalam kehidupan sehari-hari. Kamu akan dibekali dengan ilmu dan pengetahuan seputar konsep, perancangan, pengembangan, serta produksi perangkat listrik dan elektronik. Kamu juga akan banyak membahas metode pembangkit dengan sumber energi baru, metode penyimpanan energi, dan metode kontrol penghematan energi.", 
        jobs: ["Product Manager", "Bagian Perencanaan Produk Otomotif", "Perancang dan Teknisi Mesin", "Teknisi dan Operator pabrik", "Robot Engineer", "Dosen", "Electrical Engineer", "Research and Development", "Quality Assurance & Quality Control", "System Analyst"]
      },
      "Astronomi": {
        description: "Jurusan Astronomi adalah salah satu jurusan yang masih kurang familiar di Indonesia. Pertanyaan seperti mau kerja di mana lulusannya?, juga pasti sering menghantui mahasiswa jurusan ini. Meski begitu, ternyata jurusan ini unik dan seru untuk dipelajari lho! Perlu kamu ketahui, di Indonesia sendiri Jurusan Astronomi masih sangat langka, bahkan hanya ada di satu kampus saja, yaitu Institut Teknologi Bandung (ITB). So, sebenarnya seperti apa sih Jurusan Astronomi itu? Secara umum, ilmu astronomi mempelajari tentang fenomena berbagai benda langit. Dengan begitu, mahasiswa Jurusan Astronomi akan mempelajari berbagai benda angkasa beserta berbagai peristiwa yang terjadi di luar angkasa. Seluruh kajian keilmuan astronomi berhubungan dengan 3 bidang keilmuan yakni kimia, biologi, dan fisika.",
        jobs: ["Jurnalis (Reporter)", "Konsultan IT", "Astronot", "Dosen", "Content Writer", "Peneliti"]
      },
      "Meteorologi": {
        description: "Kamu suka penasaran nggak sih apa yang menyebabkan cuaca sering tiba-tiba berubah, misalnya dari panas menjadi hujan, atau sebaliknya? Nah, hal-hal seperti itu bisa kamu pelajari di Jurusan Meteorologi. Secara umum, Meteorologi adalah ilmu yang mempelajari tentang bumi dan berbagai gejalanya, termasuk tentang penyebab perubahan iklim dan cuaca serta hubungannya terhadap kelangsungan hidup manusia. Selain itu, kamu juga akan mendalami gejala-gejala alam seperti puting beliung, angin topan, dan sebagainya. Kamu pun nggak hanya mempelajari penyebab bencana tersebut bisa terjadi ya, tetapi kamu juga akan mengkaji mengenai solusi untuk menghadapi dan meminimalisir dampak dari berbagai bencana alam.",
        jobs: ["Pegawai Negeri Sipil", "Tenaga Ahli Prakiraan Cuaca", "Dosen"]
      },
      "Teknik Geologi": {
        description: "Teknik Geologi merupakan bidang studi yang banyak melakukan penelitian terkait bumi, komposisi, struktur, sifat-sifat fisik, sejarah, hingga proses pembentukannya. Perkembangan ilmu geologi saat ini sangat luas, sehingga tidak hanya terbatas pada sumber daya mineral, tetapi juga konstruksi bangunan hingga bencana.",
        jobs: ["Pegawai Negeri Sipil", "Teknisi Tambang, Minyak, dan Material", "Surveyor Tanah", "Dosen", "Kontraktor", "Entrepreuner", "Research and Development", "Bartender", "Quality Assurance (QA) & Quality Control (QC)", "System Analyst"]
      },
      "Teknik Geodesi": {
        description: "Teknik Geodesi merupakan salah satu bidang ilmu kebumian yang berkaitan erat sama lingkungan fisik bumi. Di jurusan ini kamu akan banyak melakukan survei, dan pemetaan. Saat ini, pembelajaran penentuan posisi telah berkembang menjadi lebih terpadu mulai dari pengukuran, analisis, pengelolaan, penyimpanan, sampai penyajian deskripsi dan lokasi dan data berbasis muka bumi. Oleh karena itu ada pula kampus yang menamai jurusan ini dengan Teknik Geomatika.",
        jobs: ["Pegawai Negeri Sipil", "Teknisi Tambang, Minyak, dan Material", "Surveyor Tanah", "Dosen", "Kontraktor", "Ahli Pemetaan (Kartografer)", "Research and Development", "Bartender", "Quality Assurance (QA) & Quality Control (QC)", "System Analyst"]
      },
      "Teknik Geomatika": {
        description: "Geomatika adalah ilmu yang merupakan gabungan dari geodesi dan informatika. Geodesi sendiri merupakan ilmu yang mempelajari tentang pengukuran dan perepresentasian dari bumi dan benda-benda langit lainnya, termasuk medan gaya beratnya masing-masing, dalam ruang tiga dimensi yang berubah dengan waktu. Sedangkan informatika merupakan bidang yang mempelajari struktur, sifat, dan interaksi dari beberapa sistem yang dipakai untuk mengumpulkan data, memproses, dan menyimpan hasil pemrosesan data, serta menampilkannya dalam bentuk informasi. Secara umum geomatika bisa diartikan sebagai bidang ilmu yang menyajikan pemetaan, pemodelan, dan analisis data spasial dengan menggunakan dukungan teknologi informasi. Produk yang dihasilkan dari kajian Jurusan Teknik Geomatika yakni berupa peta dengan dukungan informasi yang komprehensif untuk digunakan sebagai dasar pengambilan keputusan pada berbagai bidang, misalnya pertambangan, kesehatan, kehutanan, perikanan, pertanian, perencanaan wilayah, militer, dan masih banyak lagi. Perlu kamu pahami, perbedaan geodesi dan geomatika terletak pada produk peta yang dihasilkan. Geodesi masih condong menggunakan pendekatan manual sementara geomatika sudah mengaplikasikan pendekatan teknologi atau digitalisasi pemetaan.",
        jobs: ["Teknisi Tambang, Minyak, dan Material", "Surveyor Tanah", "Tentara"]
      },
      "Instrumentasi": {
        description: "Jurusan Instrumentasi berhubungan dengan ilmu teknologi, instrumentasi, fisika, dan juga informatika. Di samping itu, jurusan ini juga berkaitan dengan bidang pengembangan peralatan yang digunakan untuk keperluan industri. Terkait dengan hal ini, memang istilah instrumentasi sendiri berasal dari kata berbahasa Inggris “instrument” yang artinya adalah peralatan. Oleh sebab itu, dapat dikatakan bahwa jurusan ini akan menghasilkan lulusan yang mampu menciptakan berbagai peralatan baru dalam dunia industri agar semakin canggih dan sesuai kebutuhan yang ada. Di jurusan ini, kamu akan belajar bagaimana suatu instrumen bekerja pada beberapa bidang seperti elektronika analog dan digital, perangkat mikrokontroler, komputer, dan sistem optik. Selain itu juga mempelajari bagaimana cara mengolah sinyal informasi baik menggunakan perangkat keras maupun perangkat lunak. Dengan begitu, kamu yang kuliah di Jurusan Instrumentasi akan paham betul bagaimana sebuah instrumen disusun, bekerja, dan memberikan dampak sesuai dengan tujuan pembuatan instrumen tersebut. Lulusan Jurusan Instrumentasi ini juga dipastikan akan memiliki kemampuan memadai bukan hanya dari segi teori, tapi juga praktik. Kemampuan yang diasah berkaitan dengan bidang pengukuran, pengendalian kerja, penyusunan instrumen, pengembangan instrumen, dan tentunya tentang cara kerja sebuah instrumen.",
        jobs: ["Perancang dan Teknisi Mesin", "Teknisi Tambang, Minyak, dan Material", "Teknisi dan Operator Pabrik", "Robot Engineer", "Electrical Engineer"]
      },
      "Teknik Robotika": {
        description: "Bagi yang suka mengikuti perkembangan teknologi yang begitu singkat dan pesat, tentu jurusan ini akan sangat menarik perhatian. Jurusan Teknik Robotika dibuat untuk mencetak generasi penerus yang bisa mengimbangi percepatan kemajuan teknologi itu sendiri. Jurusan Teknik Robotika merupakan perpaduan beberapa ilmu diantaranya adalah sistem ilmu mekanika, elektronika, serta ilmu komputer. Program studi yang satu ini memang difokuskan pada pengembangan robotika dan kecerdasan buatan. Dari perpaduan tersebut diharapkan ada karya berupa sistem yang cerdas dan bisa digunakan serta diaplikasikan pada semua bidang yang pastinya untuk memberi manfaat bagi kehidupan manusia. Bagi kalian yang memilih kuliah di Jurusan Teknik Robotika, tentunya akan banyak belajar bagaimana merancang sebuah robot agar bisa digunakan dan dimanfaatkan pada dunia industri. Materi yang dipelajari akan cukup beragam tetapi tidak akan jauh dari komputer atau teknologi itu sendiri.",
        jobs: ["Software Engineering", "Data Scientist", "Programmer", "Perancang dan Teknisi Mesin", "Robot Engineer", "Electrical Engineer", "Research and Development"]
      },
      "Teknik Otomotif": {
        description: "Sesuai dengan namanya, Jurusan Teknik Otomotif akan mempelajari terkait segala cara maupun proses dalam pengoperasian dan pembuatan kendaraan yang beroperasi di darat seperti mobil, truk, motor, kereta, serta bus. Namun, bukan cuma itu saja, karena nantinya mahasiswa Jurusan Teknik Otomotif pun juga harus siap mengambil spesialisasi sendiri dalam bidang khusus, seperti mempelajari mesin pembakaran, sistem pembuangan, body, rangka internal, dan sebagainya. Ada beberapa hal seru yang akan dipelajari dalam Jurusan Teknik Otomotif ini yang tentunya tidak bisa kamu temukan di jurusan lainnya. Kira-kira apa saja ya? Nah, sebagai gambaran awal jika kamu kuliah di jurusan ini, nantinya kamu akan belajar memproduksi dan merancang model visual kendaraan. Dalam membuat model, media yang digunakan untuk membuat model ini termasuk model kayu, pensil dan kertas, model tanah liat, sampai dengan model yang dibuat dengan software berbasis komputer. Kemudian, tidak lupa juga untuk belajar bagaimana mengoptimalkan, memilih, serta mendesain dan menentukan pemakaian bahan sesuai komponen otomotif masing-masing. Selain itu, kamu akan belajar menerapkan berbagai prinsip seperti termodinamika, mekanik, serta prinsip mekatronik untuk mengakhiri masalah yang ada serta bertemu solusi yang paling baik. Terakhir, menginvestigasi, merancang, serta melakukan suatu tes pemeliharaan sistem otomotif yang diakhiri dengan mengatur dan melaksanakan kontrol kualitas kendaraan mulai dari manufaktur, desain, sampai perakitan. Gimana? Seru banget kan?",
        jobs: ["Jurnalis (Reporter)", "Marketing Produk Otomotif", "Bagian Perencanaan Produk Otomotif", "Mekanik Mobil", "Perancang dan Teknisi Mesin", "Teknisi dan Operator Pabrik", "Dosen", "Research and Development"]
      },
      "Teknik Fisika": {
        description: "Bagi kamu yang hendak masuk Fakultas Teknik, jurusan ini dapat menjadi salah satu pilihan yang tepat. Teknik Fisika merupakan salah satu jurusan terbaik dan bergengsi. Tak sedikit kampus-kampus ternama yang memiliki Jurusan Teknik Fisika. Bagi kamu yang hendak masuk ke jurusan ini, hendaklah mempersiapkan diri dengan matang, karena rangkaian tes masuknya sangat sulit. Cakupan disiplin ilmu yang dipelajari di Jurusan Teknik Fisika berhubungan dengan segala hal mengenai gejala fisika. Dalam penerapannya, Teknik Fisika mempelajari berbagai ilmu keteknikan termasuk di dalamnya ilmu Fisika terapan, pemanfaatan teknologi, dan juga bidang ilmu sains dasar seperti Matematika dan Kimia. Jadi, di Jurusan Teknik Fisika tidak hanya mempelajari seputar Fisika murni ya! Namun, sesuai namanya dan dengan kurikulumnya, jurusan ini berkaitan dengan teknologi dan keteknikan sesuai dengan ruang lingkup fakultas teknik yang lain. Lulusan dari Jurusan Teknik Fisika disiapkan agar mampu untuk menyelesaikan masalah yang berhubungan dengan dunia industri. Misalnya saja, kamu juga mempelajari tentang perencanaan dan desain konstruksi, manajemen alat berat, dan masih banyak lagi.",
        jobs: ["Teknisi Tambang, Minyak, dan Material", "Teknisi dan Operator Pabrik", "Insinyur Profesional dalam Bidang Instrumentasi, Bidang Tata Udara, Tata Cahaya dan Suara, Bidang Rekayasa Sistem dan Teknologi Informasi dan Sebagainya di Industri Proses"]
      },
      "Teknik Material": {
        description: "Jurusan Teknik Material merupakan jurusan yang mempelajari tentang semua aspek yang berkaitan dengan struktur, sifat, dan karakteristik material beserta interaksinya. Di jurusan ini, kamu akan dibimbing untuk menjadi seorang ahli yang mampu menciptakan dan melakukan rekayasa material. Jadi, kamu bisa menghasilkan material yang berkualitas tinggi dan memiliki banyak manfaat. Selain itu, kamu juga akan belajar cara menentukan material yang cocok untuk membuat sesuatu. Makanya, di sini, kamu akan banyak bertemu dengan pembelajaran berbentuk eksperimen. Seru banget, kan? FYI, Jurusan Teknik Material berkaitan erat dengan beberapa jurusan lainnya, lho. Salah satunya adalah Jurusan Teknik Penerbangan. Misalnya, dalam proses pembuatan kerangka pesawat terbang, mahasiswa Teknik Penerbangan berperan untuk mendesain dan merancang struktur kerangka pesawat, sementara mahasiswa Teknik Material bertugas untuk menentukan material yang tepat untuk desain dan struktur yang telah dirancang.",
        jobs: ["Teknisi Tambang, Minyak, dan Material", "Teknisi dan Operator Pabrik", "Quality Assurance (QA) & Quality Control (QC)"]
      },
      "Teknik Nuklir": {
        description: "Apa sih yang terlintas di pikiranmu saat mendengar kata nuklir? Bom? Senjata? Berbahaya? Eits, padahal nuklir nggak selalu berbahaya, lho. Jika digunakan dengan benar, nuklir bisa membantu kehidupan manusia. Oleh karena itu, hadirlah Jurusan Teknik Nuklir yang mempelajari seluk-beluk nuklir agar bisa memanfaatkannya dengan tepat. Jurusan Teknik Nuklir adalah jurusan yang mempelajari pemanfaatan energi nuklir, pengembangan teknologi nuklir, ilmu rekayasa nuklir, serta faktor-faktor keamanan dan keselamatan nuklir. Di jurusan ini, kamu akan belajar merancang, mengembangkan, mengoperasikan, dan merawat sistem serta komponen fisi nuklir. Beberapa komponen fisi nuklir adalah reaktor nuklir, Pembangkit Listrik Tenaga Nuklir (PLTN), dan senjata nuklir. Di samping itu, pembelajaran di jurusan ini berfokus pada pemanfaatan teknologi nuklir untuk kehidupan manusia, misalnya pada bidang industri dan kesehatan. Dalam bidang industri, teknologi nuklir dimanfaatkan untuk mendeteksi kebocoran pipa. Sementara di bidang kesehatan, keberadaan teknologi nuklir dapat mendeteksi penyakit seperti kanker atau tumor.",
        jobs: ["Bekerja di Lembaga Pemerintah", "Bekerja di Perusahaan", "Peneliti", "Spesialis", "Fisikawan Kesehatan", "Ilmuwan Fusi", "Analis Lingkungan"]
      },
      "Kedokteran": {
        description: "Ini nih, salah satu Jurusan favorit banyak calon mahasiswa. Meski dikenal dengan perkuliahan yang padat dan ditempuh dengan waktu yang cukup lama, Jurusan Pendidikan Dokter nggak pernah sepi peminat. Saat berkuliah di Pendidikan Dokter kamu akan mempelajari cara mendiagnosis penyakit yang dialami pasien kemudian mengobati dan mencegah timbulnya kembali penyakit itu. Selama kuliah kamu banyak belajar anatomi tubuh manusia, biologi sel dan molekuler, genetika, biokimia, juga farmakologi. Kamu juga dibekali dengan latihan keterampilan dalam skill lab. Nah setelah fase perkuliahan pre-klinik, kamu bakalan dapat pelatihan dasar di berbagai stase di Rumah Sakit. Setelah itu, baru deh diputuskan mau langsung ambil program spesialisasi atau bekerja pada institusi kesehatan.",
        jobs: ["Teknisi Medis Gawat Darurat (Paramedis)", "Bagian Pengendalian Mutu Produk dan Kesehatan", "Ahli Diet (Dietitian)", "Dokter", "Ahli Gizi (Nutritionist)", "Teknisi Radiologi Medis", "Penyuluh Kesehatan Masyarakat", "Teknisi Laboratorium Klinis", "Teknisi Alat Kesehatan", "Bagian Administrasi Rumah Sakit", "Staf Ahli Informasi Medis (Rekam Medis)", "Terapis Wicara", "Terapis Okupasi", "Ahli Akupuntur", "Terapis Fisik (Fisioterapis)", "Psikolog Klinis", "Research and Development", "Psikiater"]
      },
      "Bioteknologi": {
        description: "Bicara soal vaksin, tahukah kamu kalau ilmu bioteknologi erat kaitannya dalam proses pengembangan vaksin? Bukan cuma vaksin, masih banyak penerapan ilmu bioteknologi dalam kehidupan manusia. Mulai dari penemuan dan pengembangan baru pada jenis tanaman, pembuatan roti, keju, nata de coco dan hasil fermentasi pangan lainnya. Kalau dipikir-pikir, bermanfaat banget ya ilmu bioteknologi untuk kehidupan manusia. Otomatis, kalau kamu mendalami ilmu bioteknologi, karier yang cemerlang juga menunggu kamu lho! Memilih kuliah di Jurusan Bioteknologi artinya kamu akan mempelajari hal-hal yang berhubungan dengan pemanfaatan makhluk hidup, khususnya mikroorganisme beserta produk yang dihasilkan dari suatu proses biologis. Jurusan Bioteknologi berfokus pada pengembangan teknologi yang diterapkan kepada makhluk hidup agar bisa menghasilkan sesuatu yang bernilai guna bagi kehidupan manusia. Lalu, seiring dengan kemajuan teknologi, bidang garapan di bidang bioteknologi juga semakin luas dan modern. Bidang bioteknologi berkembang seiring kemajuan peradaban manusia. Bioteknologi dapat dikatakan sebagai ilmu yang kompleks, di dalamnya kita mempelajari kimia, biologi, hingga teknologi modern. Melihat betapa banyaknya lingkup yang dipelajari di Jurusan Bioteknologi ini, tidak heran jika prospek pekerjaan lulusannya juga sangat luas.",
        jobs: ["Pegawai Negeri Sipil", "Pegawai Negeri Sipil Daerah", "Peneliti Bioteknologi", "Bagian Perencanaan, Pengembangan, dan Penelitian Produk Bioteknologi", "Ahli Bioteknologi", "Dosen", "Wirausaha", "Quality Assurance (QA) & Quality Control (QC)"]
      },
      "Farmasi": {
        description: "Jurusan yang satu ini bisa jadi pilihan yang cocok bagi kamu jika ingin berkecimpung di dunia medis selain menjadi dokter atau perawat. Farmasi merupakan kombinasi antara ilmu kesehatan dengan ilmu kimia dan tentunya sangat diperlukan di dunia medis. Selama kuliah di jurusan Farmasi, kamu akan banyak berkutat dengan senyawa kimia untuk dikembangkan jadi bahan obat. Bukan nggak mungkin kalau suatu saat nanti kamu bisa saja menjadi salah satu penemu obat penyembuh dari berbagai penyakit. Selain itu, kamu akan mempelajari bagaimana menggunakan obat-obatan secara efektif dalam ilmu kesehatan hingga pengobatan higienis.",
        jobs: ["Bagian Penjualan (Sales)", "Peneliti Bioteknologi", "Bagian Perencanaan, Pengembangan, dan Penelitian Produk Bioteknologi", "Ahli Bioteknologi", "Ahli Kecantikan (Aesthetician)", "Dosen", "Bagian Administrasi Rumah Sakit", "Staf Ahli Informasi Medis (Rekam Medis)", "Apoteker", "Wirausaha", "Research and Development", "System Analyst"]
      },
      "Biologi": {
        description: "Kamu pasti sudah nggak asing dengan pelajaran Biologi, karena umumya telah ditemui sejak jenjang SMP. Biologi merupakan cabang dari Ilmu Pengetahuan Alam. Lebih jauh, jika kamu memilih jurusan Biologi pada jenjang kuliah maka kamu akan mendalami segala fenomena yang berkaitan sama benda hidup seperti sel, struktur/ fungsi organ/ fenomena psikologis yang menjangkiti organisme, interaksi biologi dan lingkungan, keragaman spesies dan warisan, perkembangan, dan evolusi. Jurusan biologi adalah ilmu yang mempelajari proses kehidupan makhluk hidup pada semua tingkatan molekuler, seluler, organisme dan ekologi pada hewan dan tumbuhan. serta perkembangan atau evolusi meliputi perilaku, fisiologi dan genetika.",
        jobs: ["Pet Salon & Grooming", "Perawat Hewan", "Petani", "teknisi Konservasi Lingkungan", "Peneliti Bioteknologi", "Bagian Perencanaan, Pengembangan, dan Penelitian Produk Bioteknologi", "Ahli Bioteknologi", "Dosen", "Ekonom", "Wirausaha", "Research and Development", "Quality Assurance (QA) & Quality Control (QC)"]
      },
      "Pendidikan Biologi": {
        description: "Pendidikan Biologi adalah sebuah jurusan yang bertujuan menghasilkan tenaga pengajar Biologi yang terampil pada tingkat pendidikan dasar sampai menengah. Sebagai calon tenaga pendidik profesional, di jurusan ini kamu akan mempelajari bagaimana cara mengajar yang baik, membuat soal-soal, kurikulum, manajemen sekolah, dan berbagai hal lain yang berhubungan dengan teknis atau administrasi sekolah. Tentunya kamu juga akan belajar mengenai hal-hal yang berkaitan dengan Biologi. Kamu akan memiliki pengetahuan seputar Biologi seluler molekuler, genetika, evolusi, keanekaragaman hayati, lingkungan, dan lain-lain.",
        jobs: ["Guru", "Dosen", "Peneliti", "Ahli Teknik Biologi", "Analis Laboratorium", "Quality Control (QC)", "Penulis", "Pengusaha"]
      },
      "Ilmu Lingkungan": {
        description: "Jurusan Ilmu Lingkungan mempelajari hubungan antara makhluk hidup, termasuk manusia dengan lingkungannya. Tujuan mempelajari Ilmu Lingkungan adalah untuk menanamkan rasa tanggung jawab, kesadaran diri, dan kepekaan manusia terhadap makhluk hidup dan lingkungan sekitarnya. Umumnya, di jurusan ini, kamu akan dibimbing untuk memahami berbagai masalah mengenai lingkungan hidup, mengembangkan solusi terkait masalah lingkungan, hingga mempelajari cara mencegah kerusakan pada lingkungan. Oleh karena itu, kamu akan bertemu dengan berbagai disiplin ilmu, seperti Geografi, Hidrologi, Perikanan dan Peternakan, Ekonomi, Kesehatan Masyarakat, dan masih banyak lagi. Hal ini akan membantu kamu dalam memahami masalah terkait lingkungan dan menemukan solusinya. Lantas, apa sih bedanya jurusan ini dengan Jurusan Teknik Lingkungan? Sederhananya, Ilmu Lingkungan merupakan fondasi dasar dari Teknik Lingkungan. Jadi, Ilmu Lingkungan lebih berperan dalam memberikan teori dasar keilmuan yang bisa diterapkan oleh ahli Teknik Lingkungan untuk menyelesaikan permasalahan lingkungan. Contohnya, saat membangun instalasi pengolahan air, ahli Teknik Lingkungan bertanggung jawab untuk mendesain bak, menghitung hidrolika, dan mengatur pipa. Sementara, ahli Ilmu Lingkungan berperan dalam menentukan tanaman dan media yang cocok untuk mengolah air limbah pada bak tersebut. Dengan demikian, keduanya merupakan ilmu yang nggak bisa terpisahkan.",
        jobs: ["Pegawai Negeri Sipil", "Teknisi Konservasi Lingkungan", "Dosen", "Aktivis", "Peneliti"]
      },
      "Kehutanan": {
        description: "Kehutanan adalah ilmu yang secara komprehensif mempelajari fungsi dan penggunaan dari ekosistem hutan seperti, keanekaragaman hayati, konservasi lingkungan, teknologi kehutanan, hukum penebangan hutan, dll. Selain itu, kamu juga akan belajar bagaimana memanfaatkan hasil hutan tanpa merusak ekosistem hutan itu sendiri. Cocok deh dengan kamu yang punya jiwa petualang dan hobi mendaki gunung! Karena kamu bisa menikmati keindahan gunung termasuk hutan, sekaligus belajar gimana cara memelihara hutan yang baik.",
        jobs: ["Pegawai Negeri Sipil", "Pengrajin Mebel", "Teknisi Konservasi Lingkungan", "Peneliti Bioteknologi", "Dosen", "Chocolatier", "Ekonom", "Wirausaha"]
      },
      "Peternakan": {
        description: "Peternakan merupakan bidang ilmu yang mempelajari ilmu hewan-hewan ternak yang bisa diolah dalam skala industri. Mulai dari bagaimana tata cara dalam produksi ternak yang baik, perkembangbiakan hewan ternak dan pengelolaannya, penanganan penyakit pada hewan ternak, mengatur kecukupan nutrisi pada makanan ternak, mengelola hasil produksi agar efisien dari hulu sampai hilir, serta bagaimana mengolah hasil ternak agar memiliki nilai tambah. Eits, kamu juga akan dibekali cara mengembangkan penelitian menggunakan bioteknologi lho!",
        jobs: ["Pegawai Negeri Sipil", "Bagian Pengendalian Mutu Produk dan Kesehatan", "Peternak", "Peneliti Bioteknologi", "Bagian Perencanaan, Pengembangan, dan Penelitian Produk Bioteknologi", "Ahli Bioteknologi", "Dosen", "Wirausaha", "Quality Assurance (QA) & Quality Control (QC)", "System Analyst"]
      },
      "Pertanian": {
        description: "Dunia pertanian terus mengalami perkembangan yang begitu cepat juga dinamis. Perkembangan tersebut mencakup berbagai hal seperti rekayasa genetika tanaman, sumber daya yang berkelanjutan, metode pertanian secara organik, teknologi agrikultur, serta berbagai masalah lingkungan yang diakibatkan oleh cuaca. Jurusan pertanian memiliki potensi yang sangat besar di Indonesia. Sebagai negara agraris yang beriklim tropis, tanaman di Indonesia bisa tumbuh dengan subur. Mahasiswa jurusan pertanian memiliki peran bagaimana cara memaksimalkan hasil panen dengan bantuan teknologi dan penemuan-penemuan baru di bidang pertanian. Tidak hanya itu, jurusan pertanian juga menawarkan berbagai macam pilihan mata kuliah seperti manajemen pedesaan, manajemen pertanian, dan pengelolaan tanah untuk mendukung segala kegiatan pertanian.",
        jobs: ["Penyuluh Bidang Pertanian", "Pengawas Perkebunan", "Peneliti Pertanian", "Pengusaha", "Bekerja di Instansi Terkait di Pemerintahan", "Dosen", "Staf Penanaman di Perkebunan"]
      },
      "Teknik Biomedis": {
        description: "Setiap kali pergi ke rumah sakit, pastinya kamu pernah melihat deretan alat-alat canggih masa kini seperti pengukur detak jantung, CT-Scan, MRI, hingga mesin yang digunakan untuk rontgen? Nah, semua peralatan tersebut merupakan hasil dari pengembangan teknologi, dan ilmu biomedis banyak diterapkan di dalamnya. So, Jurusan Teknik Biomedis merupakan gabungan dari dua ilmu penting yaitu ilmu teknik atau engineering dan ilmu medis atau kedokteran. Tujuan dari bidang ilmu ini sebenarnya untuk mengembangkan teknologi dalam bidang kedokteran atau medis. Hal tersebut tentunya akan sangat bermanfaat untuk mempermudah proses diagnosis, rehabilitasi, pengobatan, dan penyembuhan pasien. Lulusan dari jurusan ini diharapkan bisa melakukan pengukuran, perawatan, dan kalibrasi peralatan medis yang ada di rumah sakit. Bukan cuma itu, para lulusan Teknik Biomedis juga diharapkan bisa mengembangkan teknologi atau perangkat baru yang berguna di bidang kesehatan. Apalagi jumlah penduduk di dunia kian meningkat, yang pastinya membuat kebutuhan akan seorang ahli bidang kesehatan turut mengalami peningkatan juga. Di jurusan ini, mahasiswa akan diajarkan tentang kelistrikan, ilmu biologi, kedokteran, ilmu kimia, ilmu komputer, ilmu elektro, dan banyak lagi ilmu yang spesifik di bidang biomedis dan keteknikan. Mahasiswa Jurusan Teknik Biomedis akan berteman baik dengan peralatan-peralatan medis dan hal-hal yang berbau kesehatan. Karena itu, mahasiswa diharuskan memiliki dasar pengetahuan yang kuat di bidang ilmu sains atau kedokteran dan ilmu teknik.",
        jobs: ["Pegawai Negeri Sipil", "Guru", "Dosen", "teknisi Radiologi Medis", "Teknisi Laboratorium Klinis", "Teknisi Alat Kesehatan", "Staf Ahli Informasi medis (Rekam Medis)", "Teknisi Rekam Medis"]
      },
      "Kebidanan": {
        description: "Jurusan Kebidanan merupakan jurusan yang akan mengajarkan kamu cara menolong persalinan, kamu akan berperan dalam membantu dan memimpin persalinan. Kamu juga akan dilatih untuk melakukan pemeriksaan kehamilan, melakukan perawatan, juga memberikan asuhan kepada pasien. Selain disiapkan menjadi tenaga medis dalam proses persalinan, kamu juga akan berperan dalam membantu ibu saat proses menyusui, pemulihan kesehatan ibu pasca melahirkan, hingga program keluarga berencana. Kuliahnya nggak cuma teori lho, tapi juga didukung oleh praktek. Dijamin seru deh!",
        jobs: ["Dosen", "Pengasuh Anak/Bayi", "Pekerja Sosial Medis", "Perawat Lansia (Care Worker)", "Pekerja Sosial (Social Worker)", "Bidan", "Penyuluh Kesehatan Masyarakat", "Wirausaha", "Research and Development", "System Analyst"]
      },
      "Kesehatan Lingkungan": {
        description: "Hadirnya Jurusan Kesehatan Lingkungan bertujuan untuk menciptakan SDM yang sigap meminimalisir dan menangani adanya bahaya baru dari lingkungan dengan berbagai cara seperti memaksimalkan pengaturan segala sudut sumber lingkungan. Maka bagi kamu yang cinta alam, jurusan ini sangat cocok untukmu. Beberapa hal yang akan kamu pelajari di antaranya yaitu memahami adanya hubungan antara lingkungan hidup dengan masyarakatnya, khususnya pada sesuatu yang punya potensi berbahaya ataupun menimbulkan suatu efek kesehatan tersendiri. Terlebih lagi, masyarakat masih sering tak acuh atas kelestarian dan kebersihan lingkungan yang akhirnya membuat berbagai dampak negatif. Dampak yang bisa kita lihat jelas seperti banyaknya binatang ataupun serangga yang menyebabkan penyakit, minimnya air bersih, menumpuknya sampah plastik, dan lain sebagainya. Kamu tergerak untuk berbuat sesuatu demi kebaikan lingkungan? Bisa dimulai dengan mempelajari hal terkait lingkungan di perguruan tinggi dengan masuk ke Jurusan Kesehatan Lingkungan ini.",
        jobs: ["Pegawai Negeri Sipil", "Teknisi Konservasi Lingkungan", "Dosen", "Aktivis", "Peneliti"]
      },
      "Gizi": {
        description: "Jurusan Ilmu Gizi adalah bidang ilmu yang mempelajari pentingnya nutrisi pada kehidupan manusia, terutama hubungan antara asupan makanan dengan kesehatan. Hal lain yang juga akan dipelajari meliputi pemahaman tetang pola makan sehat, gaya hidup, hingga cara memproses makanan. Di jurusan ini mahasiswa akan mempelajari zat gizi apa saja yang dibutuhkan dan bagaimana takaran idealnya sesuai dengan ilmu pengetahuan. Seperti kita ketahui, masalah kekurangan gizi masih belum mampu dituntaskan. Di samping itu, masalah kesehatan akibat kelebihan gizi seperti diabetes dan obesitas juga meningkat. Di tambah lagi, pertumbuhan yang sangat pesat di sektor industri pangan turut mendorong tingginya kebutuhan akan ahli gizi yang profesional.",
        jobs: ["Pegawai Negeri Sipil", "Bagian Pengendalian Mutu Produk dan Kesehatan", "Terapis Aroma (Aromatherapist)", "Ahli Diet (Dietitian)", "Ahli Gizi (Nutritionist)", "Chef (Koki)", "Wirausaha", "Quality Assurance (QA) & Quality Control (QC)", "System Analyst"]
      },
      "Fisioterapi": {
        description: "Jurusan Fisioterapi merupakan salah satu bagian dari ilmu kesehatan yang mempunyai wilayah di bidang promotif (promosi), preventif (pencegahan), kuratif (pengobatan), dan rehabilitatif (rehabilitasi) yang ditujukan kepada individu atau kelompok. Secara umum, Jurusan Fisioterapi mempelajari metode penyembuhan bagian tubuh yang bermasalah dengan gerak, Nah, di Jurusan Fisioterapi, kamu bakalan akrab dengan anatomi, fisiologi, kinesiologi, sistem saraf, dan lain-lain yang berhubungan dengan fungsi tubuh manusia.",
        jobs: ["Fisioterapis Klinik atau Rumah Sakit", "Fisioterapis Olahraga", "Praktik Fisioterapi Mandiri", "Tenaga Pendidik", "Bekerja di Dinas Kesehatan"]
      },
      "Kedokteran Hewan": {
        descriptions: "Jurusan yang satu ini cocok banget untuk kamu para pecinta hewan. Kedokteran Hewan mempelajari pengobatan dan pencegahan penyakit pada hewan ternak dan hewan lainnya. Kamu akan mempelajari hubungan antara hewan dengan masyarakat, termasuk cara mengidentifikasi suatu penyakit dan memastikan penyakit tersebut tidak menular ke manusia. Selain itu, bidang studi ini juga mempelajari tentang perkembangbiakan hewan, pengelolaan pengembangbiakan hewan, serta pengolahan produk peternakan.",
        jobs: ["Pegawai Negeri Sipil", "Dokter Hewan", "Pet Salon & Grooming", "Perawat Hewan", "Peternak", "Ahli Bioteknologi", "Dosen", "Chocolatier", "Research and Development"]
      },
      "Pendidikan Kedokteran Gigi": {
        descriptions: "Pendidikan Dokter Gigi merupakan bidang ilmu yang mempelajari berbagai hal untuk jadi “an architect of the smile.” jadi terbayang kan betapa senangnya jika orang lain bisa tersenyum indah karena kamu. Tidak terbatas pada pengobatan penyakit gigi dan mulut dokter gigi juga memiliki peran pada pengobatan lain seperti kanker mulut, merawat dan mempromosikan kesehatan mulut, kerja gigi dan lidah, ludah, serta kesadaran untuk menjaga kesehatan mulut.",
        jobs: ["Bagian Pengendalian Mutu Produk dan kesehatan", "Penyiar", "Jurnalis (Reporter)", "Dosen", "Pekerja Sosial Medis", "Dokter Gigi", "Content Creator", "Wirausaha", "System Analyst"]
      },
      "Biokimia": {
        description: "Biokimia merupakan ilmu pengetahuan dengan konsep dasar kimia dan biologi, landasan ilmu tersebut sebagai penguat bahwa jurusan biokimia mempelajari interaksi molekuler yang terjadi dalam organisme makhluk hidup. Jurusan ini merupakan pengetahuan interdisipliner dalam sains yang mana kamu perlu melakukan analisis data, test lab dan eksperimen suatu organisme hidup untuk memahami kehidupan pada tingkat molekuler. untuk tingkat lanjutnya akan mengeksplorasi topik seperti biologi sel, mikrobiologi dan genetika. Program studi biokimia diharapkan mampu menghubungkan, mendemonstrasikan metode kimia untuk memecahkan masalah di bidang Bioenergetika, Enzimologi, Biokimia medis, Biomolekul dan Biokimia Pertanian untuk dapat diaplikasi di dalam bidang kesehatan, pertanian, industri dan lingkungan.",
        jobs: ["Peneliti di Bidang Penelitian Akademis, Pemerintahan, atau Farmasi", "Teknolog Medis, Apoteker, atau Asisten Dokter", "Analis Kontrol Kualitas", "Spesialis Kimia", "Teknisi Ilmu Forensik", "Ahli Biostatistik", "Ahli Biologi Molekul dan Sel", "Ilmuwan Pangan", "Ahli Toksikologi", "Dosen", "Guru"]
      },
      "Mikrobiologi": {
        description: "Mikrobiologi merupakan ilmu terapan yang memanfaatkan mikroorganisme (mikroba) sebagai alat untuk peningkatan kualitas hidup manusia. Pada awalnya pemanfaatan mikroba hanya berkisar pada industri makanan saja. Seiring dengan berkembangnya ilmu pengetahuan, mikroba pun banyak digunakan untuk kegiatan manusia yang lainnya seperti pengelolaan limbah, pengembangan ilmu pengetahuan di bidang rekayasa genetika dan lain sebagainya. Mikrobiologi adalah studi ilmu terapan yang mempelajari organisme mikroskopis seperti bakteri, virus dan jamur yang dapat berfungsi, berevolusi untuk pemanfaatan kebutuhan hidup manusia. Perkembangan teknologi memungkikan mikroba untuk diisolasi, dibudidayakan dan diidentifikasi sebagai sistem kehidupan individu untuk dimanfaatkan oleh manusia, misalnya mikroba digunakan untuk mengawetkan makanan pada industri makanan. Era modern ahli mikrobiologi dapat merekayasa genetika mikroba untuk dapat berinteraksi, dikendalikan dan dimodifikasi untuk pemanfaat lingkungan dan kemanusian seperti virus menular, membersihkan tumpahan minyak dan limbah beracun yang merusak lingkungan.",
        jobs: ["Instansi Pemerintah: Departemen Pertanian, Kesehatan, Pertambangan dan Perminyakan, BATAN, Biofarma, dan lain sebagainya", "Quality Control", "Research and Development", "Quality Assurance", "Entrepreneur", "Konsultan Lingkungan"]
      },
      "Ilmu Biomedis": {
        description: "Ilmu Biomedis mengkaji tentang fenomena makhluk hidup di tingkat molekul, sel, organ, sampai organisme utuh yang berhubungan dengan penyakit, cara pencegahan, pengobatan, dan pemulihannya. Ilmu Biomedis ini merupakan cabang Ilmu Kedokteran yang berkaitan dengan Biologi, Kimia, dan Fisika. Ilmu Biomedis pun memiliki cakupan yang luas, mulai dari menganalisis sampel biologis, mengembangkan strategi terapeutik; seperti perawatan medis, obat-obatan, dan vaksin di industri swasta maupun pemerintahan, serta melakukan penelitian mengenai penyakit manusia. Selain itu, mahasiswa Jurusan Ilmu Biomedis juga mempelajari mengenai obat-obatan medis modern, seperti melakukan pengecekan jenis darah pasien yang sedang kritis, mengidentifikasi penyakit menular, dan mengawasi pasien kanker. Dengan cakupan yang luas tersebut, di jurusan ini kamu akan belajar mengenai patologi, virologi, anatomi, dan masih banyak lagi.",
        jobs: ["Ahli Bioteknologi", "Dosen", "Teknisi Laboratorium Klinis", "Peneliti"]
      },
      "Ilmu Kelautan": {
        description: "Kelautan merupakan cabang dari ilmu bumi yang mempelajari lautan. Topik pembahasan di jurusan ini antara lain meliputi organisme laut, dinamika ekosistem laut, geologi dasar laut, arus samudera, gelombang, dan dinamika cairan geofisika. Selain itu, bidang ini juga berhubungan dengan atmosfer lho. Tak heran jika nantinya kamu juga akan membahas isu-isu mengenai perubahan iklim, potensi pemanasan global, dan masalah biosfer terkait.",
        jobs: ["Pegawai Negeri Sipil", "Account Officer", "Teknisi Tambang, Minyak, dan Material", "Peternak", "Teknisi Konservasi Lingkungan", "Peneliti Bioteknologi", "Dosen", "Ekonom", "Wirausaha", "Research and Development", "System Analyst"]
      },
      "Ilmu Perikanan": {
        description: "Hidup di negara maritim membuat jurusan yang satu ini menjadi salah satu jurusan yang sangat menjanjikan. Jurusan perikanan merupakan bidang ilmu yang mempelajari ilmu perikanan dari berbagai dimensi mulai dari teknik pengelolaan perikanan, pengolahan produk perikanan, hingga manajemen bisnis perikanan. Kamu juga akan mempelajari penangkapan ikan di laut maupun di perairan darat seperti sungai, danau, dengan perantara nelayan sehingga nantinya dapat membantu kesejahteraan mereka.",
        jobs: ["Pegawai Negeri Sipil", "Pegawai Negeri Sipil Daerah", "Peternak", "teknisi Konservasi Lingkungan", "Dosen", "Chocolatier", "Quality Assurance (QA) & Quality Control (QC)", "System Analyst"]
      },
      "Kimia": {
        description: "Siapa yang di sekolah suka banget sama pelajaran Kimia? Kalau kamu sudah jatuh hati dengan mata pelajaran Kimia, kamu cocok nih untuk melanjutkan pendidikan ke Jurusan Kimia saat kuliah nanti. Saat kuliah di jurusan kimia, tentu kamu akan mempelajari lebih dalam bidang ini daripada yang kamu dapatkan semasa sekolah. Di jurusan Kimia, kamu bakal mempelajari struktur, sifat, dan reaktivitas suatu zat. Terdapat pula materi fisika kimia yang mempelajari sifat-sifat zat di lapangan untuk lebih memfokuskan diri pada senyawa organik, senyawa anorganik, protein, dan sebagainya.",
        jobs: ["Account Officer", "Bagian Operasi dan Logistik", "bagian Pengendalian Mutu Produk dan Kesehatan", "Data Scientist", "Peneliti dan Teknisi Kimia", "Teknisi Tambang, Minyak, dan Material", "Teknisi Konservasi Lingkungan", "Peneliti Bioteknologi", "Bagian Perencanaan, Pengembangan, dan Penelitian Produk Bioteknologi", "Ahli Bioteknologi", "Teknisi Laboratorium Klinis", "Quality Assurance (QA) & Quality Control (QC)", "System Analyst"]
      },
      "Pendidikan Kimia": {
        description: "Jurusan Pendidikan Kimia adalah program studi yang mempelajari konsep teoritis kimia serta kompetensi pedagogik yang profesional sebagai pendidik di bidang kimia bagi siswa, mampu menerapkan dan mengembangan pembelajaran kimia berbasis Teknological Pedagogical and Content Knowledge (TPACK). Ada dua kompetensi yaitu pengetahuan kimia pedagogik dan konsep terioris dalam bidang kimia seperti ilmu kimia, Kimia anorganik, kimia analitik dan kimia fisika yang harus dipahami, selain itu mahasiswa juga diharapkan dapat penelitian pendidikan kimia untuk dapat diimplementasikan dalam pembelajaran. Perbedaan kimia murni dan pendidikan kimia pada kompetensi pedagogik, pada program studi kimia akan mempelajari pengetahuan Pedagogik, membuat kurikulum, manajemen kelas, penilaian dan evaluasi sedangkan di kimia hanya mempelajari bidang kimia saja.",
        jobs: ["Guru", "Dosen", "Teknisi Laboratorium Klinis", "Dan sebagainya"]
      },
      "Teknik Kimia": {
        description: "Jurusan Teknik Kimia merupakan bidang studi yang mempelajari rekayasa untuk menghasilkan suatu produk dengan nilai ekonomis tinggi. Kamu akan mencari dan mengembangkan suatu teknik produksi. Jadi, jurusan ini berbeda dengan program studi kimia atau pendidikan kimia ya. Nah, nantinya kamu akan banyak mengembangkan penelitian terkait desain molekular baru, sintesis, dan reaksi kimia untuk mewujudkan masyarakat ramah lingkungan.",
        jobs: ["Bagian Operasional dan Logistik", "Bagian Pengendalian Mutu Produk dan Kesehatan", "Peneliti dan Teknisi Kimia", "Teknisi Tambang, Minyak, dan Material", "Teknisi dan Operator Pabrik", "Bagian Perencanaan, Pengembangan, dan Penelitian Produk Bioteknologi", "Dosen", "Quality Assurance (QA) & Quality Control (QC), System Analyst"]
      },
      "Teknik Pertambangan": {
        description: "Teknik Pertambangan merupakan bidang ilmu yang mempelajari proses penambangan mineral berharga dan batubara. Fokus dari jurusan Teknik Pertambangan adalah kegiatan eksplorasi, eksploitasi, dan pemrosesan. Jadi, kamu akan belajar banyak soal sifat-sifat mineral yang akan ditambang, kegunaannya, cara menambangnya, sampai proses pengolahannya agar dapat dimanfaatkan oleh manusia. Kamu juga harus memperhitungkan untung-rugi dari proses penambangan itu, lho.",
        jobs: ["Pegawai Negeri Sipil", "Jurnalis", "Teknisi Tambang, Minyak, dan Material", "teknisi Konservasi Lingkungan", "Dosen", "Bartender", "Arsiparis"]
      },
      "Teknik Perminyakan": {
        description: "Salah satu jurusan yang dianggap memiliki prospek kerja menjanjikan adalah Jurusan Teknik Perminyakan. Pada jurusan ini kamu akan diajarkan tentang ilmu eksploitasi dan eksplorasi sumber daya alam. Fokus kajian keilmuan Jurusan Teknik Perminyakan adalah pada tambang minyak bumi, panas bumi, dan gas alam. Hal tersebut tidak terlalu jauh berbeda dengan kajian Jurusan Teknik Pertambangan yakni seputar pengeboran, eksplorasi, dan distribusi. Perbedaan kedua jurusan tersebut adalah pada objeknya. Jurusan Teknik Pertambangan mengkaji tentang penambangan benda padat seperti batu bara, emas, nikel, aspal, dan lain-lain, sementara Jurusan Teknik Perminyakan mengkaji tentang tentang penambangan benda cair (fluida) dan gas.",
        jobs: ["Pegawai Negeri Sipil", "Teknisi Tambang, Minyak, dan Material", "Teknisi dan Operator Pabrik", "Surveyor Tanah", "Kontraktor", "Wirausaha"]
      },
      "Teknik Metalurgi": {
        description: "Pernahkah kamu mendengar Jurusan Teknik Metalurgi? Ini adalah salah satu program studi yang kurang diketahui orang sehingga sampai sekarang peminatnya masih sedikit. Padahal, jurusan teknik yang satu ini cukup penting dan banyak manfaatnya untuk kehidupan sehari-hari. Diambil dari Bahasa Yunani, istilah metalurgi memiliki arti proses ekstraksi logam dari mineral. Seiring berjalannya waktu, metalurgi hanya berkaitan dengan ekstraksi logam serta produksi logam, pengerjaan dan pengolahan logam, hingga logam bisa digunakan. Jurusan ini masuk dalam bidang ilmu keteknikan yang khusus mendalami proses pengolahan mineral, proses ekstraksi serta pembuatan paduan logam, penguatan logam, degradasi logam, juga mempelajari hubungan sifat mekanik logam dengan strukturnya. Intinya, prodi ini mempelajari sifat-sifat kimia yang ada di dalam logam. Meski kurang populer, hampir setiap universitas terkemuka memiliki jurusan ini lho. Pada beberapa universitas terkenal di Indonesia, Teknik Metalurgi digabung dengan Teknik Material dan menjadi satu jurusan. Namun, ada juga yang memisahkan kedua jurusan tadi dan berdiri sendiri.",
        jobs: ["Peneliti dan Teknisi Kimia", "Perancang dan Teknisi Mesin", "Teknisi Tambang, Minyak, dan Material", "Dosen"]
      },
      "Kesejahteraan Sosial": {
        description: "Kesejahteraan Sosial mengajarkan tentang pengetahuan dasar pekerjaan sosial, nilai, prinsip, dan etikanya. Kamu juga akan belajar kebijakan dan pelayanan sosial di tingkat lokal, nasional, dan internasional. Jurusan ini sangat cocok dengan kamu yang memiliki jiwa sosial tinggi dan serius mendalami bidang tersebut, terlebih jika kamu suka kegiatan di luar ruangan untuk berinteraksi dengan masyarakat secara langsung.",
        jobs: ["Pegawai Negeri Sipil", "Account Officer", "Dosen", "Pekerja Sosial Medis", "Social Worker", "Chocolatier", "Research and Development", "System Analyst", "Arsiparis"]
      },
      "Antropologi Sosial": {
        description: "Antropologi merupakan studi yang mempelajari ciri khas dan kesamaan dari suatu masyarakat dan kebudayaan melalui penelitian tentang bahasa dan agama di dunia, hak asasi manusia, upacara, pola pikir, kemasyarakatan, etika, budaya, dan banyak hal lainnya. Jika kamu kuliah di jurusan ini, maka siap-siap ya untuk sering melakukan penelitian lapangan karena kamu akan banyak melakukan observasi langsung.",
        jobs: ["Bagian personalia (HRD)", "Video Editor", "Pustakawan", "Jurnalis", "Event Planner/Event Organizer", "Kurator", "Dosen", "Research and Development", "Peneliti", "Antropolog"]
      },
      "Pendidikan Sosiologi": {
        description: "Jurusan Pendidikan Sosiologi adalah program studi yang menggabungkan antara ilmu sosiologi murni dan ilmu kependidikan. Mahasiswa yang ada di jurusan ini nantinya akan belajar tentang berbagai macam materi teori sosiologi dan ilmu kependidikan termasuk teori-teori pembelajaran, strategi pembelajaran, kurikulum, evaluasi pembelajaran, dan berbagai isu pendidikan yang sedang aktual. Biasanya, di Perguruan Tinggi lain, antara Jurusan Sosiologi dan Jurusan Antropologi akan dibedakan, dimana Sosiologi sendiri dan Antropologi sendiri. Akan tetapi, ada beberapa universitas yang menggabungkan antara kedunya dan nantinya akan dipersiapkan untuk menjadi seorang guru atau pengajar karena masuk ke dalam jurusan pendidikan. Sebenarnya, Jurusan Pendidikan Sosiologi ini sangat dibutuhkan oleh negara multikultural seperti Indonesia yang mempunyai berbagai macam suku, kebudayaan, dan kepercayaan. Karena apabila ilmu-ilmu yang ada di dalam Jurusan Pendidikan Sosiologi ini meresap dan tumbuh di dalam pola pikir masyarakat Indonesia, maka tidak akan terjadi lagi kesenjangan sosial dan juga peperangan antar suku yang selama ini menjadi salah satu pokok permasalahan yang ada di Indonesia.",
        jobs: ["Sosiolog", "Dosen", "Peneliti Survei"]
      },
      "Ilmu Komunikasi": {
        description: "Apa itu Jurusan Ilmu Komunikasi? Sederhananya, jurusan Ilmu Komunikasi adalah studi yang mempelajari proses penyampaian pesan secara efektif dari komunikator (pemberi pesan) kepada komunikan (penerima pesan) melalui berbagai media. Di jurusan ini kamu akan mempelajari komunikasi dalam berbagai tingkatan, mulai dari individu, media, periklanan/publisitas, komunikasi interkultural, hingga komunikasi media sosial. Seperti yang kita rasakan bahwa kehidupan kita tidak pernah lepas dari yang namanya komunikasi. Oleh karena itu, Ilmu komunikasi berhubungan erat dengan masalah fundamental dari hubungan antara manusia dengan sesamanya dalam bermasyarakat.",
        jobs: ["Product Manager", "Bagian Penjualan dan Pelayanan (Customer Service)", "Penyiar", "Video Editor", "Account Executive", "Public Relations", "Jurnalis", "Prosedur TV atau Radio", "Content Creator", "Telemarketer", "Content Writer", "Editor"]
      },
      "Hubungan Internasional": {
        description: "Hubungan Internasional berkaitan erat dengan upaya suatu negara menghadapi tantangan internasional seperti ketidakseimbangan perdagangan dunia, isu keamanan, masalah lingkungan secara global, dan kemiskinan melalui kerja sama antarnegara. Kuliah di jurusan ini memungkinkanmu untuk merasakan atmosfer internasional melalui berbagai simulasi pertemuan-pertemuan penting di dunia, salah satunya sidang PBB. Seru kan? Hubungan antarnegara aja dijaga, apalagi hubungan kita?",
        jobs: ["Pegawai Negeri Sipil", "Politisi", "Eksportir", "Diplomat", "Bagian Tata Usaha (Atase) Perdagangan Luar Negeri", "Konsultan Pendidikan", "Penyiar", "Jurnalis", "Chocolatier", "Editor", "System Analyst", "Arsiparis"]
      },
      "Psikologi": {
        desription: "Jurusan Psikologi adalah salah satu bidang keilmuan yang mempelajari tentang manusia. Manusia yang dimaksud di sini tak sebatas pada perilakunya saja, melainkan mempelajari jiwa yang mempengaruhi tindakan tersebut. Misalnya pada konteks sosial, seperti mempelajari bagaimana manusia berinteraksi dengan lingkungannya, atau dalam konteks industri mempelajari bagaimana seseorang berperilaku terkait dengan posisinya di sebuah perusahaan. Jadi, mahasiswa akan diajak untuk meneliti alur pemikiran seseorang dan mencari tahu alasan yang ada di balik perilakunya. Artinya, mahasiswa akan belajar tentang manusia sebagai individu, dengan memperhatikan setiap latar belakang yang mengikutinya. Seperti yang kita ketahui bahwa manusia adalah makhluk yang unik, bahkan ketika diberi stimulus yang sama pun responnya bisa berbeda tergantung pada pengetahuan, pengalaman, perasaan, harapan, dan banyak faktor penentu lainnya. Terdapat beberapa peminatan yang bisa ditemukan, seperti Psikologi Klinis, Psikologi Pendidikan, Psikologi Sosial, Psikologi Industri dan Organisasi, serta Psikologi Perkembangan. Mata kuliah yang akan dipelajari akan tergantung dengan peminatan yang kamu ambil.",
        jobs: ["Bagian Personalia (HRD)", "Konsultan Pendidikan", "Konsultan Karir", "Dosen", "Perawat Kesehatan Mental", "Psikolog", "Psikolog Klinis", "Content Writer", "Research and Development (RnD)", "Management Trainee"]
      },
      "Ilmu Politik": {
        description: "Ilmu Politik merupakan bidang ilmu yang banyak mengkaji gejala maupun fenomena sosial politik sehingga nantinya mampu menerapkan teori-teori ilmu politik untuk menawarkan solusi dari permasalahan sosial politik. Jurusan ini tidak hanya mempelajari bagaimana politik di Indonesia, tapi juga politik di berbagai negara. Dijamin deh wawasanmu akan semakin luas kalau kuliah di Jurusan Ilmu Politik.",
        jobs: ["Pegawai Negeri Sipil", "Politisi", "Diplomat", "Bagian tata Usaha (Atase) Perdagangan Luar Negeri", "Penyiar", "Jurnalis", "Chocolatier", "Editor", "System Analyst"]
      },
      "Administrasi Publik": {
        description: "Jurusan Administrasi Negara merupakan rumpun ilmu sosial yang mana di beberapa kampus, jurusan ini disebut atau berganti nama menjadi Jurusan Administrasi Publik. Perubahan nama tersebut kemudian memperluas ranah kajian administrasi yang bukan hanya tentang bagaimana negara atau pemerintah melayani rakyat, namun juga mengkaji bagaimana tinjauan administrasi yang berhubungan dengan kebijakan publik serta kegiatan kemasyarakatan. Jadi nggak bingung lagi kan kamu kalau dengar ada jurusan administrasi publik dan jurusan administrasi negara? Di Jurusan Administrasi Negara, mahasiswa akan belajar memahami bagaimana turunan dari setiap hukum/peraturan dan kebijakan yang di keluarkan oleh pemerintah dapat diimplementasikan dengan baik di setiap level, baik tingkat organisasi atau perseorangan. Selain itu, mahasiswa juga dituntut untuk bisa memanfaatkan teknologi dalam proses pengumpulan dan pengolahan data. Sarjana Admnistrasi Negara diharapkan dapat memiliki berbagai kompetensi, di antaranya: memiliki daya saing tinggi; mampu mengidentifikasi, menganalisis, dan menanganai masalah publik berdasarkan landasan metodologis; mampu membuat terobosan yang kreatif dan inovatis dalam memberdayakan peran masyarakat; mamu bekerja secara mandiri dan tim; mampu membangun komunikasi yang baik dengan pakar dari berbagai bidang kelahlian; serta senantiasa mengikuti perkembangan dalam bidang keilmuannya.",
        jobs: ["Pegawai Negeri Sipil", "Politisi", "Tata Usaha (Admin)", "Dosen", "Peneliti"]
      },
      "Kriminologi": {
        description: "Kriminologi adalah ilmu yang mempelajari berbagai aspek tentang kejahatan. Kata kriminologi berasal dari bahasa Latin, yaitu gabungan crimen yang artinya kejahatan dan logos yang artinya ilmu. Mempelajari kriminologi artinya kamu akan mengenali berbagai faktor penyebab timbulnya kejahatan. Maka dari itu, kriminologi memiliki hubungan dengan ilmu-ilmu lainnya mulai dari sosiologi, psikologi, psikiatri, ekonomi, sejarah, biologi, geografi, antropologi, filsafat, politik, hukum, dan bahkan ilmu jurnalistik.",
        jobs: ["Jurnalis", "Dosen", "Peneliti", "Polisi", "Pegawai Negeri di Kejaksaan", "Kriminolog", "Analis Data", "Analis Intelijen", "Penasihat Hukum"]
      },
      "Studi Pembangunan": {
        description: "Jurusan Studi Pembangunan merupakan suatu disiplin ilmu yang memfokuskan pada pemahaman dan analisis tentang berbagai aspek pembangunan, baik dari segi ekonomi, sosial, politik, hingga lingkungan. Mahasiswa jurusan ini akan mempelajari teori-teori dan konsep-konsep yang berkaitan dengan pembangunan serta menganalisis dampaknya terhadap masyarakat, negara, dan lingkungan. Studi ini bersifat interdisipliner, menggabungkan elemen-elemen dari ekonomi, sosiologi, politik, geografi, dan disiplin ilmu lainnya untuk menyelidiki dinamika pembangunan.",
        jobs: ["Manajer program advokasi pembangunan di lembaga pemerintah seperti BAPPENAS, BAPPEDA, BAPPEPROV, atau BAPPEKO", "Tenaga ahli di organisasi nirlaba nasional atau internasional (LSM/NGO/INGO)", "Pendamping atau tenaga ahli pemberdayaan masyarakat", "CSR di perusahaan nasional dan multinasional", "Peneliti pembangunan yang melakukan studi ilmiah untuk memahami tantangan dan potensi dalam proses pembangunan", "Pemerhati lingkungan pembangunan yang mengevaluasi dampak proyek-proyek terhadap lingkungan", "Pengajar yang memberikan pelatihan tentang teori dan praktik pembangunan", "Asisten peneliti yang melakukan berbagai analisis, seperti analisis manajer pembangunan, analis dampak teknologi, atau analis maritim", "Wirausahawan sosial yang mengembangkan bisnis di bidang konsultasi ekonomi, riset pasar, atau pengembangan proyek pembangunan"]
      },
      "Sosiologi": {
        description: "Sosiologi merupakan ilmu yang membahas perilaku sosial antar individu, antar kelompok, maupun antara individu dan kelompok. Di jurusan ini kamu juga akan membicarakan apa itu masyarakat. Kamu akan mempelajari struktur dan karakter masyarakat, problematika masyarakat, fenomena sosial, dan gerakan masyarakat. Selain itu, mempelajari metode survei sosial seperti kuisioner dan statistik, serta metode analisis dari hasil survei.",
        jobs: ["Market Researcher", "Tour Guide", "Jurnalis", "Event Organizer", "Dosen", "Aktivis", "Social Worker", "Sosiolog", "Chocolatier", "Content Writer", "Research and Development (RnD)", "Peneliti"]
      },
      "Pariwisata": {
        description: "Pariwisata di Indonesia sedang mengalami perkembangan yang cukup pesat dan menjadikan bidang ini sebagai salah satu bidang yang sangat menjanjikan di masa depan. Pariwisata nggak sekadar jalan-jalan aja lho, tetapi lebih luas juga membahas manajemen dan strateginya. Ilmu Pariwisata berhubungan erat dengan sejarah, geografi, budaya, ekonomi, dan sebagainya. Bidang ilmu ini mempelajari sumber daya pariwisata, pembangunan kawasan pariwisata, juga manajemen perhotelan. Bekal pengetahuan tersebut sangat berguna ketika kamu bekerja di industri pariwisata seperti agen perjalanan maupun perhotelan.",
        jobs: ["Wedding Organizer", "Pramugara/i", "Staf Maskapai Penerbangan", "Concierge Hotel", "Tour Guide", "Kondektur Transportasi", "Sales Hotel", "Sales Agensi Wisata", "Event Organizer", "Wirausaha", "Research and Development (RnD)"]
      },
      "Perhotelan": {
        description: "Perhotelan merupakan bidang ilmu yang mempelajari pengelolaan hotel serta cara menyeimbangkan aspek wisata dan manajemen bisnis untuk mencapai kesuksesan. Beberapa topik yang akan diajarkan antara lain mengenai pelayanan yang memuaskan bagi pelanggan, melindungi budaya lokal, manfaat ekonomi yang diperoleh bagi masyarakat sekitar serta kesejahteraan karyawan. Selain itu kamu pun akan dibekali dengan pelajaran bahasa asing untuk menghadapi tren wisatawan internasional yang terus meningkat.",
        jobs: ["Wedding Organizer", "Staf Maskapai Penerbangan", "Concierge Hotel", "Sales Hotel", "Event Organizer", "Dosen", "Sommelier (Ahli Mengenai Wine)", "Chef (Koki)", "Patissier (Pembuat Kue)", "Wirausaha"]
      },
      "Tata Boga": {
        description: "Tata Boga adalah ilmu tentang bagaimana teknik untuk menyajikan makanan dengan memperhatikan beberapa faktor yaitu estetika atau keindahan, kualitas rasa masakan, serta nilai kebutuhan gizinya. Ketika kuliah di Jurusan Tata Boga, mahasiswa akan mempelajari bagaimana seni untuk mengolah suatu makanan yang dimulai dari persiapan, tahap pengolahan hingga cara penyajiannya. Selain itu, kuliah di Jurusan Tata Boga bukan hanya sekedar belajar memasak dan mengolah makanan saja lho! Namun, lebih luas lagi kamu akan belajar tentang perencanaan, pengelolaan, dan juga tata cara untuk melakukan evaluasi pada usaha kuliner.",
        jobs: ["Chef (Koki)", "Patissier (Pembuat Kue)", "Content Creator", "Wirausaha", "Bartender", "Vlogger"]
      },
      "Ilmu Ekonomi": {
        description: "Tahukah kamu, jika Maudy Ayunda dan Gita Gutawa adalah lulusan jurusan Ilmu Ekonomi? Apa saja ya yang mereka pelajari selama kuliah? Jika kamu ingin belajar Ilmu Ekonomi, kalian akan fokus pada upaya pengalokasian sumber daya yang terbatas dan memperoleh keuntungan optimal. Selain itu, kamu juga akan mengeksplorasi upaya pemberdayaan ekonomi. Dewasa ini, tren pembelajaran Ilmu Ekonomi mulai banyak yang mengarah pada behavioral economics lho. Selain itu, mulai berkembang pula crime economics, jadi kamu bisa melakukan analisis terhadap permasalahan hukum yang ditinjau dari sisi ekonomi. Menarik kan?",
        jobs: ["Makelar Saham", "Bagian Penjualan (Sales) di Lembaga Keuangan", "Account Officer", "Akuntan", "Pegawai Asuransi", "Bagian Perencanaan dan Pengembangan Real Estate", "Market Research", "Marketing Produk Otomotif", "Dosen"]
      },
      "Ekonomi Pembangunan": {
        description: "Ekonomi Pembangunan merupakan salah satu cabang ilmu Ekonomi yang khusus mengkaji persoalan-persoalan pembangunan baik itu dari sektor bisnis, keuangan, ataupun perbankan. Dan jika kamu berminat untuk kuliah di jurusan ekonomi pembangunan, kamu akan berkutat dengan analisa berbagai isu perekonomian untuk mencari dan menemukan solusi dari berbagai persoalan ekonomi secara kritis, kreatif, dan inovatif. Menarik banget kan? Di program studi ini, kamu dipersiapkan menjadi perencana bidang pembangunan ekonomi yang tentunya juga turut berperan dalam pembangunan negara dan berkontribusi untuk terciptanya kesejahteraan bersama.",
        jobs: ["Pegawai Negeri Sipil", "Akuntan", "Trend Analyst", "Dosen", "Ekonom", "Research and Development", "Peneliti", "System Analyst", "Data Analyst"]
      },
      "Ekonomi Syariah": {
        description: "Jurusan Ekonomi Syariah sering juga disebut Jurusan Ekonomi Islam di beberapa perguruan tinggi. Secara umum, di jurusan ini kamu akan mempelajari subjek-subjek yang kurang lebih sama seperti Jurusan Ekonomi pada umumnya, misalnya pengelolaan sumber daya, kajian prinsip-prinsip ekonomi baik makro maupun mikro, perdagangan internasional, dan lain-lain. Lalu, apa perbedaan antara Jurusan Ekonomi dan Jurusan Ekonomi Syariah? Bedanya adalah, di Jurusan Ekonomi Syariah, kamu akan mengkaji prinsip-prinsip ekonomi tersebut sesuai dengan prinsip syariah Islam yakni berlandaskan Al-Qur’an, hadis, beserta kaidah-kaidah fiqih turunannya. Sekalipun demikian, kamu juga tetap mendapatkan materi perkuliahan yang berhubungan dengan sistem ekonomi konvensional, sehingga kamu bisa mendapatkan kesimpulan utuh terkait sistem ekonomi yang ideal. Menarik bukan?",
        jobs: ["Bagian Penjualan (Sales) di Lembaga Keuangan", "Account Officer", "Pegawai Asuransi", "Dosen", "Ekonom", "Wirausaha", "Finance", "Peneliti"]
      },
      "Akuntansi": {
        description: "Kalian pasti sudah nggak asing dengan Jurusan Akuntansi. Jurusan Akuntansi adalah bidang studi yang mempelajari materi terkait metode pencatatan dan penyusunan laporan keuangan yang berguna membantu pemangku kepentingan dalam proses pengambilan keputusan. Jurusan Akuntansi dikenal sebagai jurusan yang sangat dekat dengan angka, khususnya segala sesuatu yang terkait dengan keuangan. Meskipun begitu, mahasiswa Jurusan Akuntansi tidak hanya belajar tentang cara menghitung uang, termasuk juga tentang manajemen, perpajakan, sistem informasi, hingga pengauditan. Oh iya, Lulusan Akuntansi ternyata dikenal sebagai idaman para pencari pasangan lho! Kegigihan lulusan akuntansi telah dikenal luas lantaran kalau hilang nol satu aja akan dicari sampai ketemu! Nah, kebayang gimana kegigihannya memperjuangkan pasangannya kan?",
        jobs: ["Makelar Saham", "Account Officer", "Akuntan", "Bagian Personalia (HRD)", "Konsultan Pajak", "Pegawai Asuransi", "Dosen", "Bagian Keuangan (Finance)", "Auditor"]
      },
      "Manajemen": {
        description: "Jurusan Manajemen merupakan bidang keilmuan yang mempelajari tentang kegiatan perusahaan atau korporasi, yang masih memiliki keterkaitan dengan ilmu ekonomi dan bisnis. Jika kamu mendalami Ilmu Manajemen maka akan belajar menjadi seorang “pengendali” layaknya tokoh Aang pada serial Avatar. Jika Aang mengendalikan elemen bumi, kamu akan mengendalikan roda perusahaan berupa kegiatan yang meliputi kebijakan manajemen perusahaan, organisasi, strategi bisnis, ketenagakerjaan dan kepegawaian, manajemen produksi, pemasaran, administrasi, hingga organisasi nirlaba. Oleh karena setiap hal memiliki tata cara pengelolaan tertentu yang perlu diperhatikan, membuat ilmu manajemen menjadi terus berkembang dan dipelajari secara lebih spesifik. Berikut adalah macam-macam jurusan manajemen yang bisa kamu temui di Indonesia dari berbagai jenjang.",
        jobs: ["Bagian penjualan (Sales)", "Account Officer", "Bagian Operasional dan Logistik", "Product Manager", "Pegawai Asuransi", "Market Researcher", "Produser TV atau Radio", "Event Organizer", "Dosen", "Wirausaha"]
      },
      "Keuangan dan Perbankan": {
        description: "Pada program studi Keuangan dan Perbankan kamu akan mempelajari ilmu tentang keuangan, khususnya pengelolaan keuangan di sektor perbankan. Di prodi ini kamu juga akan mempelajari operasional perbankan baik bank konvensional maupun syariah, seperti tugas-tugas frontliner (teller dan customer services) dan tugas-tugas backoffice seperti administrasi, akuntansi, dan audit.",
        jobs: ["Perencana Bisnis Berkelanjutan", "Pemeriksa Keuangan", "Auditor", "Analis Keuangan", "Analis Keuangan Kuantitatif", "Penilai (Pajak dan Keuangan)", "Akuntan", "Analis Kredit", "Manajer Keuangan", "Manager Investasi Pemodalan"]
      },
      "Bisnis Internasional": {
        description: "Dilihat dari pengertiannya, bisnis internasional adalah bisnis yang kegiatan-kegiatannya melewati batas-batas negara. Selain berkaitan dengan perdagangan dan pemanufakturan di luar negeri, bisnis internasional juga berhubungan dengan industri jasa di berbagai bidang, mulai dari pariwisata, perbankan, transportasi, perdagangan eceran, dan masih banyak lagi. Dengan demikian, Jurusan Bisnis Internasional merupakan jurusan yang berfokus pada pembelajaran tentang tantangan-tantangan yang dihadapi oleh dunia bisnis di pasar internasional. Makanya, di jurusan ini, kamu akan mempelajari etika dan hukum bisnis dalam skala internasional. Kamu pun akan dilatih untuk bisa berpikir secara global, sehingga dapat menciptakan ide dan solusi yang berkaitan dengan permasalahan ekonomi dan bisnis dalam lingkup internasional. Kamu juga akan dibimbing agar dapat mengambil keputusan dengan tepat dan relevan yang berkaitan dengan aturan perdagangan internasional, investasi di pasar saham asing, maupun transaksi antar negara. Pokoknya lengkap deh!",
        jobs: ["Business Intelligence", "Business Development", "Konsultan Bisnis"]
      },
      "Ekonomi Pertanian": {
        description: "Jurusan Ekonomi Pertanian atau yang disebut juga sebagai Agribisnis adalah program studi yang mempelajari bisnis berbasis bidang pertanian serta bidang pendukung lainnya, seperti perkebunan, peternakan, dan perhutanan. Berdasarkan pengertiannya, maka jurusan ini akan mempelajari berbagai materi perkuliahan terkait ekonomi dan pertanian. Kamu akan belajar mengolah hasil pertanian, manajemen usaha, hingga memasarkan produk.",
        jobs: ["Lulusan dari program studi Ekonomi Pertanian memiliki prospek berkarir di Kementrian Perencanaan Pembangunan Nasional, Perbankan, BUMN, BUlog, Kementrian Perdagangan, Kementrian Kehutanan, Kementrian Pendidikan, Kementrian Koperasi dan UKM,Biro Pusat Statistik, Kementrian Tenaga Kerja, Lembaga Penelitian, Bappeda.", "Kamu juga bisa bekerja secara mandiri sebagai konsultan pertanian atau ekonomi pertanian untuk meningkatkan kesejahteraan petani. Kamu bisa memberikan saran kepada petani atau perusahaan pertanian terkait dengan strategi bisnis, manajemen risiko, dan inovasi teknologi.", "Kamu juga memiliki peluang untuk mengelola bisnis pertanian sendiri, termasuk peternakan, perkebunan, atau usaha agroindustri."]
      },
      "Ekonomi Sumberdaya dan Lingkungan": {
        description: "Ekonomi Sumberdaya dan Lingkungan mempelajari aspek ekonomi dan sosial dalam pengelolaan sumberdaya alam dan mengkaji dampaknya terhadap masyarakat secara keseluruhan, baik pelaku maupun penerima dampak. Ekonomi dan sumberdaya lingkungan sendiri adalah bidang ilmu yang berkaitan dengan isu-isu besar seperti sumberdaya alam, kebijakan lingkungan, serta pengembangan pertanian dalam arti luas.",
        jobs: ["Perencana Bisnis Berkelanjutan", "Manajer Layanan Sosial dan Komunitas", "Pengajar Ekonomi", "Ahli Ekonomi Lingkungan", "Analis Manajemen Bisnis", "Konsultan Bisnis"]
      },
      "Pendidikan Ekonomi Koperasi": {
        description: "Program studi Pendidikan Ekonomi Koperasi adalah program akademik yang mengajarkan prinsip-prinsip dasar dalam pendidikan, akuntansi, ekonomi, dan administrasi perkantoran, serta memberikan keterampilan untuk merencanakan, menganalisis, dan menerapkan pengetahuan tersebut dalam konteks ekonomi koperasi. Selain itu, program ini juga mencakup kegiatan penelitian di bidang pendidikan ekonomi koperasi. Pendidikan Ekonomi Koperasi merupakan salah satu konsentrasi di bawah Pendidikan Ekonomi, seperti yang terdapat di Universitas Negeri Semarang.",
        jobs: ["Guru Ekonomi Koperasi", "Manajer Koperasi", "Konsultan Koperasi", "Peneliti Koperasi", "Pegawai Dinas Koperasi", "Wirausahawan atau Pengelola Bisnis", "Peneliti di Bidang Pendidikan", "Peneliti atau Konsultan di Bidang Keuangan"]
      },
      "Bisnis Digital": {
        description: "Bisnis digital termasuk dalam rumpun ilmu terapan. Pada implementasinya, jurusan ini akan mengajarkan untuk merancang dan menjalankan bisnis yang berbasis digital. Ilmu yang akan diperoleh adalah perpaduan dari manajemen, bisnis, teknik informatika, dan juga sistem informasi. Umumnya, Jurusan Bisnis Digital tersedia pada program D4 atau S1. Jurusan ini berdiri untuk menjawab tantangan bisnis masa depan yang akan didominasi oleh sistem digital sehingga memerlukan kajian terstruktur, mendalam, dan berkelanjutan untuk merumuskan strategi bisnis yang tepat. Bahkan lebih dari itu, lulusan jurusan ini juga diharapkan memiliki keterampilan mumpuni untuk menjadi seorang ahli digital business yang mampu menghadirkan solusi dan rekomendasi dalam berbagai permasalahan bisnis. So, jika kamu merasa memiliki minat yang kuat terhadap dunia bisnis dan ingin memaksimalkan peluang yang ada di era digital saat ini, sepertinya kamu cocok kuliah di jurusan ini! Lalu, memilih kuliah di jurusan ini bisa dikatakan memiliki keuntungan tersendiri. Coba deh lihat kondisi perekonomian di Indonesia bahkan dunia saat ini, hampir semua memanfaatkan marketplace untuk berbisnis bukan? Apalagi dengan adanya social distancing di kala pandemi, maka banyak sekali kegiatan yang memanfaatkan berbagai platform digital.",
        jobs: ["Bagian Penjualan (Sales)", "Product Manajer", "Bagian Penjualan dan Pelayanan (Customer Service)", "Market Researcher", "Dosen", "Digital Marketing", "Wirausaha"]
      },
      "Teknik Industri": {
        description: "Teknik Industri adalah bidang ilmu yang mempelajari bagaimana mengoptimalisasi kegiatan manusia seperti; produksi, pengelolaan dan ekonomi. Lulusan Teknik Industri nantinya bertanggungjawab atas optimalisasi praktis dari sistem produksi pabrik, proposal strategi, serta desain optimal manajemen perusahaan. Di jurusan Teknik Industri, kamu akan banyak melakukan penyelesaian masalah melalui pendekatan matematis.",
        jobs: ["bagian Operasional dan Logistik", "Product Manager", "Bagian Personalia (HRD)", "Bagian Pengendalian Mutu Produk dan Kesehatan", "Market Researcher", "Data Scientist", "Teknisi dan Operator Pabrik", "Dosen", "Quality Assurance (QA) & Quality Control (QC)", "System Analyst"]
      },
      "Sejarah": {
        description: "“Jangan sekali-kali meninggalkan sejarah, jangan sekali-sekali melupakan sejarah” itulah salah satu kutipan Presiden Pertama Indonesia, Presiden Soekarno yang cukup fenomenal. Sejarah sudah menjadi bagian penting bagi kehidupan manusia. Nah, kamu yang tertarik dengan sejarah dan ingin mendalaminya bisa melanjutkan kuliah di Jurusan Ilmu Sejarah. Disini kamu akan mempelajari segala hal yang berkaitan dengan sejarah, mulai dari geografi sejarah, sejarah kerajaan nusantara, sejarah dunia, sejarah Indonesia, dan sebagainya. Ilmu sejarah itu berkaitan erat sama kehidupan manusia, seperti politik, sosial, budaya, bahasa, ekonomi, dan militer. Kalau kamu kuliah di Ilmu Sejarah, bakalan hemat biaya sewa tour guide deh tiap piknik ke tempat bersejarah!",
        jobs: ["Penerjemah Lisan (Interpreter)", "Penerjemah Tulisan (Translator)", "Pemandu Wisata (Tour Guide)", "Penyiar", "Pustakawan", "Jurnalis", "Produser TV atau Radio", "Kurator", "Guru", "Dosen", "Content Writer", "Sejarawan"]
      },
      "Pendidikan Sejarah": {
        description: "Kamu kagum nggak sih dengan guru Sejarah? Kok bisa ya mereka menghafal banyak peristiwa sejarah di dunia? Kira-kira gimana ya caranya? Nah, berbagai hal tersebut bisa kamu pelajari di Jurusan Pendidikan Sejarah. Yup, di jurusan ini, selain mempelajari segala peristiwa yang terjadi di masa lampau, kamu juga akan dibekali dengan ilmu pendidikan, seperti manajemen pendidikan, serta metode dan evaluasi pembelajaran Sejarah. Sementara, untuk yang berkaitan langsung dengan sejarah, kamu akan bertemu dengan pembelajaran mengenai geografi sejarah, sejarah dunia, sejarah kerajaan nusantara, sejarah Indonesia, dan sebagainya. Selain itu, kamu juga akan belajar tentang politik, sosial, budaya, bahasa, ekonomi, dan berbagai hal lainnya yang berkaitan erat dengan kehidupan manusia. Wah, sepertinya seru ya!",
        jobs: ["Pegawai Negeri Sipil", "Penerjemah Lisan (Interpreter)", "Penerjemah Tulisan (Translator)", "Tour Guide", "Jurnalis", "Kuraor", "Dosen", "Content Writer"]
      },
      "Antropologi": {
        description: "Antropologi merupakan studi yang mempelajari ciri khas dan kesamaan dari suatu masyarakat dan kebudayaan melalui penelitian tentang bahasa dan agama di dunia, hak asasi manusia, upacara, pola pikir, kemasyarakatan, etika, budaya, dan banyak hal lainnya. Jika kamu kuliah di jurusan ini, maka siap-siap ya untuk sering melakukan penelitian lapangan karena kamu akan banyak melakukan observasi langsung.",
        jobs: ["Bagian Personalia (HRD)", "Video Editor", "Pustakawan", "Jurnalis", "Event Organizer", "Kurator", "Dosen", "Research and Development", "Peneliti", "Antropolog"]
      },
      "Arkeologi": {
        description: "Kalau kamu sering galau menggali kenangan masa lalu, kayaknya kamu cocok nih masuk jurusan yang satu ini. Jurusan Arkeologi kerap dikaitkan dengan menggali dan mencari peninggalan masa lampau. Arkeologi merupakan ilmu yang mempelajari budaya manusia sepanjang zaman dengan menggabungkan Sejarah dan Geologi. Kamu akan banyak membahas peristiwa di masa lampau, mengaji peninggalan kepurbakalaan, juga mempelajari artefak mulai dari cara menemukan hingga menaksir usia artefak tersebut. Serunya, kuliah di jurusan ini kamu akan mengungkap berbagai fakta peradaban masa lampau dari beraneka ragam budaya. Yang paling penting, akan banyak travelling-nya juga lho!",
        jobs: ["Tour Guide", "Pustakawan", "Jurnalis", "Kurator", "Dosen", "Content Writer", "Research and Development", "Editor", "System Analyst", "Sejarawan"]
      },
      "Sastra dan Bahasa Daerah": {
        description: "Sastra & Bahasa Daerah merupakan bidang ilmu yang mempelajari sastra dan bahasa daerah yang ada di Indonesia. Misalnya Jawa, Sunda, Bali, Melayu, Batak, Minangkabau, Bugis, dan lainnya. Di jurusan ini, kamu akan mempelajari norma dan kaidah dasar pengkajian sastra, bahasa, serta filologi. Kamu pun akan belajar gimana menafsirkan teks dari berbagai variasi zaman dan tradisi masyarakat.",
        jobs: ["Penerjemah Lisan (Interpreter)", "Penerjemah Tulisan (Translator)", "Wedding Organizer", "Tour Guide", "Jurnalis", "Event Organizer", "Guru", "Dosen", "Content Writer", "Editor", "Peneliti", "Sastrawan"]
      },
      "Ilmu Hukum": {
        description: "Jurusan Ilmu Hukum adalah studi yang mempelajari berbagai sistem hukum yang berkaitan dengan kehidupan kemasyarakatan. Di Prodi Ilmu Hukum, mahasiswa juga belajar mengenai perundang-undangan termasuk di dalamnya hukum dasar (konstitusi, hukum perdata, hukum dagang, hukum tata negara, hukum pidana, hukum tata pidana) hingga hukum internasional dengan cakupan yang cukup luas. Pada akhir masa kuliah, biasanya mahasiswa jurusan ini dituntut untuk mengaplikasikan ilmu yang telah diperoleh selama kuliah melalui magang di berbagai firma hukum, lembaga pengadilan, dan juga kantor kejaksaan. Mahasiswa yang telah menuntaskan pendidikan di jurusan ini diharapkan dapat menguasai dengan baik hukum dan sistem hukum di Indonesia, mempunyai keterampilan dan pengetahuan ilmiah untuk mengembangkan hukum, peka terhadap permasalahan keadilan dan masyarakat, mampu mengenali dan menganalisis permasalahan hukum, serta mampu menerapkan hukum dan peraturan perundang-undangan untuk menyelesaikan masalah hukum.",
        jobs: ["Notaris", "Politisi", "Pengacara", "Bagian personalia (HRD)", "Diplomat", "Bagian Tata Usaha (Atase) Perdagangan Luar Negeri", "Dosen", "Aktivis", "Jaksa", "Hakim", "Panitera", "System Analyst", "Management Trainee"]
      },
      "Geografi": {
        description: "Geografi umumnya membahas bentang lahan dan hal-hal terkait fisik bumi. Kamu akan mempelajari topografi, iklim, hingga geografi manusia untuk mencari hubungan antara kondisi alami dan pengumpulan populasi, penggunaan lahan, industri, sejarah, budaya, dan sebagainya. Selain belajar tentang fisik bumi, kamu juga akan dibekali dengan kemampuan untuk memahami perspektif regional dalam berbagai pengembangan wilayah termasuk penguasaan teknologi sistem informasi geografis.",
        jobs: ["Pegawai Negeri Sipil", "Pegawai Negeri Sipil Daerah", "Teknisi dan Operator Pabrik", "Surveyor Tanah", "Tenaga Ahli Prakiraan Cuaca", "Dosen", "Chocolatier", "Ahli Pemetaan (Kartografer)", "System Analyst"]
      },
      "Pendidikan Geografi": {
        description: "Kamu tau nggak sih bedanya Jurusan Geografi dengan Jurusan Pendidikan Geografi? Jurusan Geografi lebih berfokus pada pendalaman ilmu mengenai permukaan bumi beserta proses perubahannya, mulai dari atmosfer, hidrologi, iklim, kualitas air, dan sebagainya. Sementara, di Jurusan Pendidikan Geografi, kamu juga akan mempelajari konsep-konsep untuk menjadi tenaga pendidik profesional untuk mata pelajaran geografi. Jadi, Jurusan Pendidikan Geografi adalah jurusan yang mempelajari ilmu dan kehidupan di bumi serta cara untuk mengajarnya. Konsep-konsep yang akan kamu pelajari jika mengambil jurusan ini meliputi metode pembelajaran Geografi, manajemen pendidikan, serta evaluasi pembelajaran Geografi. Jadi, buat kamu yang tertarik dengan Ilmu Geografi sekaligus dunia pendidikan, bisa banget ambil jurusan ini ya!",
        jobs: ["Pegawai Negeri Sipil", "Pegawai Negeri Sipil Daerah", "Surveyor Tanah", "Tenaga Ahli Prakiraan Cuaca", "Guru", "Dosen", "Ahli Pemetaan (Kartografer)"]
      },
      "Meteorologi": {
        description: "Kamu suka penasaran nggak sih apa yang menyebabkan cuaca sering tiba-tiba berubah, misalnya dari panas menjadi hujan, atau sebaliknya? Nah, hal-hal seperti itu bisa kamu pelajari di Jurusan Meteorologi. Secara umum, Meteorologi adalah ilmu yang mempelajari tentang bumi dan berbagai gejalanya, termasuk tentang penyebab perubahan iklim dan cuaca serta hubungannya terhadap kelangsungan hidup manusia. Selain itu, kamu juga akan mendalami gejala-gejala alam seperti puting beliung, angin topan, dan sebagainya. Kamu pun nggak hanya mempelajari penyebab bencana tersebut bisa terjadi ya, tetapi kamu juga akan mengkaji mengenai solusi untuk menghadapi dan meminimalisir dampak dari berbagai bencana alam.",
        jobs: ["Pegawai Negeri Sipil", "Tenaga Ahli Prakiraan Cuaca", "Dosen"]
      },
      "Oseanografi": {
        description: "Jurusan oseanografi adalah program studi yang mempelajari fenomena fisika, kimia dan geologi dalam ekosistem lautan, kamu akan mempelajari topik seperti dinamika ekosistem: arus laut, gelombang laut, geologi dasar laut dan berbagai zat kimia dan sifat fisik yang terkandung di dalam lautan. Serta semua bentuk kehidupan yang ada di laut. Perubahan iklim cuaca yang terjadi mendorong ahli oseanografi untuk membuat penelitian dan kajian terapan untuk dapat menghasilkan studi yang dapat bagi lingkungan laut dan pesisir, perkembangan teknologi kelautan dan eksplorasi sumber daya laut. Wilayah kelautan indonesia sebagai benua maritim tentu membutuhkan tenaga ahli pada bidang oseanografi baik untuk perusahaan swasta dan pemerintahan untuk dapat melakukan kajian dalam bentuk pengembangan teknologi kelautan, bencana laut dan lingkungan dan sumber energi alternatif dari laut. Secara umum studi oseanografi memiliki 4 cabang spesialisasi keilmuan oseanografi fisik, oseanografi kimia, geologi kelautan, dan ekologi laut. Pendidikan akan didukung oleh teknologi canggih berupa instrumentasi oseanografi, kapal, penginderaan satelit untuk menunjang eksplorasi dan studi.",
        jobs: ["Peneliti", "Konsultan Lingkungan", "Manajer Akuakultur", "Spesialis Konservasi Alam", "Ahli Ekologi", "Metocean Engineer", "Dosen atau Tenaga Pengajar", "Surveyor Hidrografi"]
      },
      "Planologi": {
        description: "Jurusan planologi merupakan sebuah program studi yang mempelajari perencanaan kota dan wilayah dengan menggunakan berbagai aspek. Mulai dari aspek sosial, politik, dan ekonomi dalam sebuah pembangunan. Saat ini, prospek kerja lulusan planologi pun sangat luas",
        jobs: ["Perencana Transportasi", "Jasa Konstruksi", "Arsitek", "Bergabung dengan Instasi Pemerintahan", "Perencana Wilayah dan Kota", "Konsultan"]
      },
      "Ilmu Pengelolaan dan Pemberdayaan Sumber Daya Alam dan Lingkungan": {
        description: "Jurusan Pengelolaan dan Pemberdayaan SDA dan lingkungan adalah Ilmu yang akan mengajarkan bagaimana pemanfaatan, pengaturan dan pemaksimalan Sumber Daya Alam (SDA) bumi yang terbatas serta lingkungan hidup bagi kebutuhan manusia. Jurusan ini akan mempelajari lingkungan dan permasalahannya, serta mencari solusi untuk masalah yang ada, atau memikirkan pencegahan untuk masalah lingkungan yang akan dihadapi di masa depan. Dengan berkuliah di Jurusan ini kamu dapat menstabilkan hubungan antara manusia dan lingkungan dengan melestarikan dan menciptakan suatu lingkungan yang aman dan nyaman bersama-sama dengan makhluk hidup lainnya. Tak hanya ilmu lingkungan, di jurusan ini kamu juga akan mengulik banyak tentang Biologi dan Kimia, seperti pada mata kuliah Ekologi dan Ilmu Lingkungan atau Manajemen Lingkungan. Kamu juga masih mendapat bekal pengetahuan ekonomi dalam mata kuliah Ekonomi Sumberdaya Alam dan Lingkungan. Bahkan, kamu juga akan belajar tentang Hukum Lingkungan.",
        jobs: ["Konsultan Lingkungan", "Marine Scientist", "Pengelola Limbah", "Ahli Ekologi", "Insinyur Energi", "Manajer Pengelolaan Energi", "Manajer Lingkungan", "Pemelihara Kualitas Air", "Petugas Daur Ulang"]
      },
      "Konservasi Sumber Daya Hutan": {
        description: "Jurusan Konservasi Sumber Daya Hutan adalah program studi yang menyajikan dan juga mengembangkan ilmu pengetahuan dan teknologi di bidang perlindungan dan pelestarian ekosistem hutan. Di prodi ini, kamu akan fokus untuk belajar tentang penyelamatan, perlindungan, pengelolaan, dan juga pemanfaatan sumber daya hutan secara bijaksana untuk kelestarian sumber daya hutan sebagai penyangga kehidupan secara berkelanjutan. Bidang ilmu yang akan dipelajari antara lain ekologi dan manajemen satwa liar, rekreasi alam, dan konservasi keanekaragaman tumbuhan.",
        jobs: ["Pengelola Tepat Wisata Alam", "SIG Analisis", "Ahli Pemetaan", "Tenaga Ahli Sertifikasi Hutan", "Pengelola Konservasi", "Pengelola Hasil Hutan", "Pengembang Teknologi Hasil Hutan", "Pengelola Kawasan Ekowisata", "Pengelola Pembangunan Hutan (Silvikultur)", "Logger", "Ahli Konservasi Hutan"]
      },
      "Manajemen Bencana": {
        description: "Jurusan Manajemen Bencana adalah salah satu program studi yang didedikasikan untuk menghasilkan sumber daya manusia yang handal dan berkompeten di bidang manajemen bencana, baik itu sebelum terjadinya bencana atau ketika terjadi bencana dan pasca bencana. Jurusan yang satu ini memfokuskan diri pada penciptaan SDM yang berbudi pekerti luhur dan memiliki kapasitas keilmuan kebencanaan yang komprehensif, baik itu teori ataupun praktis. Harapannya, program studi ini akan menghasilkan lulusan yang memiliki kemampuan manajerial berjiwa kepemimpinan yang baik, bisa mengambil keputusan secara cepat dan juga tepat ketika kondisi sedang krisis dan bisa merencanakan kegiatan pengurangan risiko bencana secara komprehensif.",
        jobs: ["Badan Nasional Penanggulangan Bencana (BNPB)", "TNI", "Polri", "Taruna"]
      },
      "DKV": {
        description: "Jurusan Desain Komunikasi Visual atau DKV adalah bagian dari ilmu desain yang mempelajari tentang konsep komunikasi dan ungkapan kreatif, dengan memanfaatkan elemen visual untuk menyampaikan pesan dengan tujuan tertentu. Karena unsur pesan memiliki peran yang sangat penting, lulusan jurusan DKV diharapkan mampu mengeloah pesan tersebut menjadi sesuatu yang menarik, informatif, dan komunikatif, sehingga bisa disampaikan secara efektif. Mahasiswa jurusan ini bukan hanya dituntut jago gambar, tetapi juga harus mampu menghasilkan karya seni agar dapat mencapai tujuan yang telah ditetapkan, seperti mempengaruhi perilaku seseorang. Sebagai bagian dari cabang ilmu desain, pada jurusan ini mahasiswa akan dibantu untuk bisa mengembangkan bahasa visual dalam bentuk gambar, sekaligus mengolah pesan dalam bentuk kata, agar pesan tersebut mampu diterima oleh sasaran dengan baik.",
        jobs: ["Ilustrator", "Web Designer","Desainer Produk", "Graphic Designer", "Desainer Grafis Game", "Animator"]
      },
      "Seni Rupa": {
        description: "Seni Rupa adalah bidang seni yang bermula dari pemahaman tradisi “fine art”, sebuah wacana dari modernisme yang dikembangkan dalam kesadaran nilai-nilai lokal juga global. Kamu akan diajari cara berekspresi melalui melukis, seni grafis, seni pahat, kerajinan, dan sebagainya. Kuliah di jurusan ini juga akan mempelajari sejarah seni, komposisi, dan tematik dalam karya seni.",
        jobs: ["Ilustrator", "Fotografer", "Kurator", "Desainer Produk", "Display Designer", "Pembatik", "Resepsionis (Front Office)", "Pengrajin Mebel", "Florist (Dekorator Bunga)", "Guru", "Dosen", "Content Creator", "Digital Marketing", "Seniman", "Peneliti"]
      },
      "Seni Kriya": {
        description: "Seni kriya adalah seni kerajinan tangan yang sangat bernilai karena lahir dari kultur budaya dan memperkaya identitas Indonesia sehingga wajib dipelihara keberadaannya. Beberapa contoh karya seni kriya yaitu anyaman, tembikar, dan topeng. Sering diidentikkan dengan kerajinan, sesungguhnya seni kriya sangat berbeda karena produknya bersifat eksklusif. Jurusan Seni Kriya mungkin tidak begitu populer dibanding jurusan seni lainnya. Meski begitu, jurusan ini tak bisa diremehkan begitu saja. Di jurusan ini kamu akan diberikan ilmu seni dan desain untuk menghasilkan suatu karya seni atau produk yang memiliki nilai estetika tetapi tak meninggalkan nilai fungsionalnya. Hal ini terlihat dari produk kriya yang memiliki kualitas desain orisinal yang mengandung pesan filosofi, sehingga tak mengherankan apabila produknya bernilai estetis tinggi dan diagungkan. Produk seni kriya menyerap nilai serta unsur tradisional untuk melestarikan citra tradisi Indonesia. Umumnya, proses pembuatan kriya berlangsung dalam waktu yang lama dan mengandalkan tenaga manusia. Oleh karena itu produknya sulit untuk ditiru dan dibajak sebab memiliki keunikan tersendiri.",
        jobs: ["Pegawai Negeri Sipil", "Kurator", "Dosen", "Seniman", "Wirausaha"]
      },
      "Desain Grafis": {
        description: "Jurusan Desain Grafis ialah jurusan yang mempelajari tentang konsep, bentuk, dan komposisi suatu karya komunikasi visual berupa gambar, garis, maupun elemen grafis lainnya. Hasil dari karya desain diaplikasikan pada berbagai media. Karya desain grafis dapat dijumpai antara lain pada logo, poster, brosur, undangan, hingga kartu nama baik itu dalam bentuk cetak atau digital. Ilmu desain grafis juga dapat diterapkan untuk membuat desain tampilan antarmuka website bahkan aplikasi mobile. Jadi, Jurusan Desain Grafis ini berfokus pada representasi visual yang diambil dari konsep penting dalam metode komunikasi visual. Kemudian untuk belajar desain grafis, memerlukan perangkat lunak atau software yang berhubungan dengan desain. Software yang biasanya dibutuhkan seperti adobe photoshop, corel draw, dan adobe XD.",
        jobs: ["Ilustrator", "UI/UX Designer", "Web Designer", "Desainer Produk", "Graphic Designer", "Animator"]
      },
      "Fotografi": {
        description: "Di Jurusan Fotografi kamu akan mempelajari berbagai hal tentang teknik dan proses merekam gambar dalam berbagai bentuk dan situasi yang bertujuan untuk menciptakan sebuah karya seni. Nah, karena fotografi itu pada dasarnya merupakan sebuah seni, maka foto-foto yang direkam dari sebuah peristiwa ataupun keadaan baik itu kondisinya di-setting ataupun tidak haruslah memenuhi unsur-unsur seni dan mampu mempresentasikan nilai dan pesan tersendiri. Sampai sini kamu bisa paham ya kalau fotografi itu sebenarnya bukan asal jepret? So, di jurusan ini kamu akan dibimbing untuk menghasilkan foto yang bukan hanya sekedar bagus tetapi juga memiliki nilai. Perlu kamu ketahui juga bahwa dunia fotografi itu terbagi ke beberapa bidang, mungkin kita bisa sebut dengan bidang spesialisasi atau keahlian yaitu fotografi jurnalistik, fotografi komersial, dan fotografi ekspresi. Masing-masing spesialisasi ini tentunya menggunakan teknik dan feel yang berbeda, nah semua hal itu nantinya akan kamu dapatkan selama menjalani perkuliahan di Jurusan Fotografi.",
        jobs: ["Fotografer", "Content Creator", "Influencer"]
      },
      "Desain Interior": {
        description: "Ketika kuliah di jurusan desain interior, kamu akan mempelajari tentang perancangan dan perencanaan penataan suatu ruang bangunan. Beberapa hal yang perlu diperhatikan dalam kegiatan perancangan dan perencanaan itu antara lain fungsi, estetika, dan juga mempertimbangkan psikologis dan kenyamanan pengguna ruangan. Meskipun sama-sama mengkaji tentang perancangan dengan memperhatikan unsur estetika, namun jurusan ini sejak awalnya sudah dibedakan dengan jurusan arsitektur ya! Karena objeknya berbeda, yakni jurusan arsitektur mengkaji rancangan keseluruhan bangunan, sedangkan desain interior mengkaji optimalisasi pemanfaatan ruangan.",
        jobs: ["Konsultan Properti", "Graphic Designer", "Kontraktor", "Desainer Interior"]
      },
      "Seni Tari": {
        description: "Kuliah di jurusan Seni Tari nggak hanya membuatmu menjadi seorang penari yang andal tapi juga bisa menciptakan tarian mu sendiri. Tari adalah bidang ilmu yang mengajarkan mu upaya untuk mengungkapkan perasaan dan pikiran dalam gerak tubuh yang menyesuaikan dengan irama. Nggak hanya itu kamu juga akan belajar bagaimana menghayati dan mempelajari filosofi tarian sehingga tarian akan lebih bernyawa saat kamu pentaskan nanti. Dalam seni tari, kamu akan mempelajari bagaimana memadukan berbagai unsur seperti raga, irama, dan rasa. Selain itu, kamu juga akan mempelajari koreografi dari berbagai jenis tarian mulai dari tari tradisional sampai tari modern.",
        jobs: ["Penyiar", "Produser TV atau Radio", "Kurator", "Guru", "Dosen", "Seniman", "Penari", "Koreografer", "Peneliti"]
      },
      "Seni Musik": {
        description: "Siapa sih yang nggak suka mendengarkan musik? Kalau kamu nggak cuma suka mendengarkan tetapi ingin mempelajari musik lebih dalam dan secara serius kamu bisa masuk Jurusan Seni Musik saat kuliah nanti. Di jurusan Musik kamu akan mempelajari bidang ilmu yang mempelajari teori musik dan membekalimu dengan keterampilan praktis seperti instrumen dalam musik, teknik vokal, dan komposisi. Selain itu, kamu juga akan mempelajari berbagai aliran musik seperti jazz, pop, musik tradisional, dan sebagainya. Kapan lagi kan bermain sambil belajar?",
        jobs: ["Penyiar", "Produser TV atau Radio", "Event Organizer", "Produser Rekaman (Produser Musik)", "Penata Musik", "Guru", "Dosen", "Terapis Musik", "Seniman"]
      },
      "Seni Pertunjukan": {
        description: "Jurusan seni pertunjukan adalah jurusan yang mempelajari tentang seni pertunjukan, baik itu seni teater, musik, tari, dan seni pertunjukan lainnya. Lulusan jurusan ini diharapkan memiliki kemampuan dalam berkarya, menampilkan, menginterpretasi, dan mengapresiasi seni pertunjukan.",
        jobs: ["Profesional Seni", "Guru Seni Budaya", "Penyelenggara da Konsultan Kegiatan Seni Pertunjukan", "Programer dan Sutradara di Stasiun televisi", "Aktor atau Aktris Film", "Pegawai pada Lembaga Kebudayaan", "Komposer atau Pengaransemen Musik", "Pelatih di Industri Akting", "PR dan Staf Marketing Teater"]
      },
      "Sinematografi": {
        description: "Jurusan Sinematografi adalah sebuah program studi yang mempelajari seni dan teknik pembuatan film serta media audiovisual lainnya. Jurusan ini berfokus pada bagaimana menciptakan gambar yang mampu menyampaikan cerita secara visual dengan memperhatikan elemen-elemen seperti pencahayaan, framing, pergerakan kamera, dan komposisi visual. Sinematografi juga tidak terbatas pada film, tetapi mencakup produksi video untuk iklan, video musik, dokumenter, dan konten digital.",
        jobs: ["Sinematografer", "Editor Video", "Penata Cahaya", "Sutradara", "Produser Film/Video", "Animator", "Pengembang Konten Media Sosial dan Youtube", "Dosen atau Pengajar", "Jurnalis Video atau Dokumentaris", "Pekerja Freelance di Industri Film"]
      },
      "Animasi": {
        description: "Jurusan Animasi di beberapa perguruan tinggi di Indonesia merupakan bagian dari Program Studi Desain Komunikasi Visual (DKV) dan pada beberapa perguruan tinggi lainya berdiri sendiri sebagai satu program studi. Jurusan ini dibagi menjadi dua jenis berdasarkan keahlian kompetensi animasi, yaitu untuk film animasi dan animasi game (animasi interaktif). Dengan belajar di Jurusan Animasi, kamu akan mengetahui cara dan teknik membuat gambar yang dirancang berurutan sehingga penonton akan merasakan adanya ilusi gerakan (motion) pada gambar yang ditampilkan. Di jurusan ini pula, kamu akan belajar cara membuat karakter 2 dimensi, karakter 3 dimensi, dan juga dapat merancang special effects, membuat story board, dan mengetahui cara menulis skenarionya dengan baik. Selain membuat tampilan visualnya, kamu juga harus mengolah audionya dengan menyambungkan sound effects dan mengisi suara karakter-karakternya. Jadi, kamu juga akan mempelajari tentang audio dan sound effect di jurusan ini secara mendalam. Setelah karya film animasi atau animasi game telah jadi dan siap, maka selanjutnya kamu juga akan belajar bagaimana cara memperkenalkan, memasarkan, dan mendistribusi hasil karyamu pada orang banyak. Jurusan ini akan mengajak kamu untuk mengasah kreativitas dan keahlian untuk menciptakan sesuatu, misalnya cerita, tokoh utama, atau gaya animasi yang unik dan juga menarik. Selain itu, memerlukan konsentrasi tinggi dan juga keahlian untuk menyampaikan ide, pesan dan kesan yang diubah ke dalam bentuk animasi. Gimana, sudah siap jadi kreator animasi handal?",
        jobs: ["game Creator", "Desainer Grafis Game", "Sutradara", "Animator"]
      },
      "Film dan Televisi": {
        description: "Film dan Televisi adalah bidang ilmu yang mempelajari bagaimana menciptakan bentuk-bentuk di dalam audio visual lengkap dengan berbagai prosesnya. Segala hal teknis pembuatan film juga program siaran televisi akan kamu lahap habis! Nggak lupa, bekal manajerial juga akan kamu dapatkan di jurusan ini.",
        jobs: ["Penyiar", "Video Editor", "Jurnalis", "Produser TV atau Radio", "Penata Musik", "Fotografer", "Content Creator", "Sutradara", "Wirausaha", "Animator"]
      },
      "Tata Busana": {
        description: "Program studi Tata Busana sering juga disebut dengan nama Fashion Design di beberapa perguruan tinggi. Pada program studi ini di pelajari teknik mendesain, belajar membuat pola, menjahit, dan seluk beluk produksi busana atau fashion. Nggak Cuma soal produksi, disini kita juga diajarin tentang analisa tren, bagaimana marketing dan manajemen bisnis fashion. Biasanya, di akhir perkuliahannya anak Tata Busana (Fashion Design) akan mengadakan fashion show sebagai tugas final mereka. Seru kan? Biasanya di perguruan tinggi negeri program studi ini bernama program studi Tata Busana, tapi di beberapa perguruan tinggi swasta yang mengadopsi kurikulum internasional program studi ini lebih dikenal dengan nama Fashion Design. Memang artinya sama aja, sih. Mata kuliahnya pun hampir sama aja. Namun di program studi Fashion Design di perguruan tinggi swatsa umumnya, kita akan belajar tentang fashion dari perspektif Paris sebagai kiblat fashion dunia dengan pencampuran budaya Indonesia. Program studi Tata Busana (Fashion Design) umumnya berjenjang pendidikan Diploma 2 (D2), Diploma 3 (D3) dan Diploma 4 (D4) atau setara Strata 1 (S1). Pada perguruan tinggi swasta juga tersedia program kursus untuk yang minat belajar tentang fashion dalam waktu 1 tahun saja, dan di akhir kita akan di beri sertifikat dari perguruan tinggi yang bersangkutan.",
        jobs: ["Fashion Designer", "Fashion Merchandiser", "Visual merchandiser", "Desainer Garmen", "Jurnalis Fashion", "Textile Designer", "Wirausaha"]
      },
      "Sastra Asing": {
        description: "Sastra & Bahasa Asing merupakan bidang ilmu yang mempelajari sastra dan bahasa negara-negara di dunia, antara lain Inggris, Jepang, Korea, Cina, Perancis, Belanda, Jerman, Rusia, Arab, dan sebagainya. Di jurusan ini, kamu juga akan melakukan kajian terhadap kebudayaan, sejarah, maupun perekonomian negara-negara tersebut. Duh terbayang enaknya mendengarkan K-pop atau nonton anime tanpa harus menggunakan subtitle atau dialih suara tapi tetap paham artinya. Nah, supaya makin asyik mendengarkan KPop-nya mengapa nggak sekalian aja mendalami dan belajar bahasanya lewat Jurusan Sastra & Bahasa Asing ini. Seru deh!",
        jobs: ["Eksportir", "Penerjemah Lisan (Interpreter)", "Guru Bahasa Asing", "Penerjemah Tulisan (Translator)", "Konsultan Pendidikan", "Tour Guide", "Jurnalis", "Dosen", "Content Creator", "Editor", "Sastrawan"]
      },
      "Sastra Indonesia": {
        description: "Sastra Indonesia merupakan bidang ilmu yang mempelajari puisi, prosa, cerita, novel, naskah, dan karya sastra lainnya dalam bahasa Indonesia. Kamu akan melakukan berbagai kajian untuk mengetahui latar belakang dari ide dan karya seniman. Ada pula bibliografis yang mempelajari tentang penampilan dan formasi buku. Selain itu, kamu juga akan belajar penulisan kreatif dan penyuntingan lho. Jadi, Jurusan ini sangat cocok untuk kamu yang senang membaca dan menulis.",
        jobs: ["Penerjemah Lisan (Interpreter)", "Penerjemah Tulisan (Translator)", "Penyiar", "Jurnalis", "Produser TV atau Radio", "Dosen", "Sutradara", "Content Writer", "Editor"]
      },
      "Sastra Inggris": {
        description: "Sastra Inggris merupakan bidang ilmu yang mempelajari Bahasa Inggris dari sisi linguistik dan sastra secara mendalam. Jadi jangan heran kalau kamu akan melakukan banyak kajian terhadap berbagai karya, seperti puisi, prosa, novel drama, maupun film. Selain itu, kamu juga akan banyak membahas kebudayaan negara-negara dengan Bahasa Inggris sebagai bahasa ibu.",
        jobs: ["Eksportir", "Penerjemah Lisan (Interpreter)", "Penerjemah Tulisan (Translator)", "Guru Bahasa Asing", "Bagian Tata Usaha (Atase) Perdagangan Luar Negeri", "Konsultan Pendidikan", "Staf Maskapai Penerbangan", "Concierge Hotel", "Tour Guide", "Public Relations", "Jurnalis", "Dosen", "Editor", "Sastrawan"]
      },
      "Pendidikan Bahasa Indonesia": {
        description: "Pendidikan Bahasa & Sastra Indonesia (PBSI) atau dikenal juga dengan Jurusan Pendidikan Bahasa Indonesia merupakan bidang yang mengajarkan keterampilan berbahasa Indonesia dengan baik dan efektif, seperti keterampilan menyimak, berbicara, membaca, dan menulis. Kamu juga akan belajar bagaimana cara yang tepat untuk mengajarkannya. Ada juga lho pembelajaran mengenai morfologi, fonologi, semantik, sintaksis, dan sebagainya. Tak ketinggalan materi bidang kesusastraan mulai dari apresiasi hingga pengkajian karya. Lengkap deh!",
        jobs: ["Penerjemah Lisan (Interpreter)", "Penerjemah Tulisan (Translator)", "Public Realtion", "Jurnalis", "Guru", "Dosen", "Content Writer", "Editor", "Sastrawan"]
      },
      "Pendidikan Bahasa Inggris": {
        description: "Pendidikan Bahasa Inggris fokus pada pembelajaran mendengarkan, berbicara, membaca, menulis juga penggunaan bahasa Inggris dalam berbagai konteks seperti berkomunikasi dalam bisnis, presentasi, penulisan artikel, bahkan pertunjukan drama. Tentu saja kamu juga akan mempelajari tata bahasa juga ya. Selain itu, nggak ketinggalan materi tentang kependidikan, seperti pengembangan kurikulum dan teaching assessment.",
        jobs: ["Penerjemah Lisan (Interpreter)", "Penerjemah Tulisan (Translator)", "Guru Bahasa Asing", "Konsultan Pendidikan", "Staf Maskapai Penerbangan", "Concierge Hotel", "Tour Guide", "Jurnalis", "Guru", "Content Writer", "Editor"]
      },
      "Ilmu Linguistik": {
        description: "Jurusan Ilmu Linguistik merupakan ilmu yang mempelajari tentang bahasa secara ilmiah, baik itu dari segi struktur bahasa, penggunaan bahasa, sampai sejarah perkembangan bahasa. Program studi yang satu ini umumnya mencakup materi seperti fonetik dan fonologi, morfologi, sintaksis, semantik, pragmatik, psikolinguistik, sosiolinguistik, neurolinguistik, dan juga analisis wacana.",
        jobs: ["Ahli Bahasa Komputasi", "Editor", "Penulis Teknis", "Peneliti Linguistik", "Jurnalis", "Penyunting atau Editor", "Penyusun Kamus", "Guru", "Terapis Wicara"]
      },
      "Filsafat": {
        description: "Filsafat merupakan bidang ilmu yang mempelajari cara berpikir. Kamu dilatih untuk mempertanyakan suatu keadaan. Selain itu, juga akan diajarkan bagaimana memformulasikan dan mengokohkan pandanganmu secara merdeka tentang suatu permasalahan di dunia ini. Kamu akan diajak untuk mengenal jenis-jenis kesesatan berpikir, karakteristik ilmu pengetahuan, mengkritik suatu karya seni, pentingnya empati, mengkaji kapan suatu tindakan bisa dikatakan baik dan buruk, dan sebagainya.",
        jobs: ["Jurnalis", "Kurator", "Dosen", "Chocolatier", "Content Writer", "Editor", "Peneliti", "System Analyst", "Arsiparis"]
      },
      "Pendidikan Olahraga": {
        description: "Siapa nih yang suka banget sama pelajaran olahraga? Pelajaran luar ruangan ini memang mengasyikan karena bisa nge-refresh badan dan pikiran, selain itu tentu membuat badan selalu bugar. Kalau kamu suka sama pelajaran olahraga, kenapa nggak mendalaminya secara serius? Saat lulus nanti, kamu bisa melanjutkan pendidikan dengan kuliah di Jurusan Pendidikan Olahraga. Pendidikan Olahraga merupakan bidang ilmu yang fokus mempelajari olahraga dari sudut pandang seorang pengajar. Quipperian akan mempelajari berbagai aturan dalam olahraga, kesehatan mental dan fisik, peningkatan fungsi fisik, olahraga dan nutrisi, metode pelatihan untuk kompetisi, taktik dan strategi, dan metode pengajaran. Kamu pun akan mempelajari hampir seluruh cabang olahraga mulai dari sepak bola, basket, voli, renang, atletik, sampai woodball. Selain itu tentunya pembelajaran mu nggak hanya sebatas teori di dalam kelas lho!",
        jobs: ["Penyiar", "Jurnalis", "Event Organizer", "Guru", "Dosen", "Terapis Fisik (Fisioterapis)", "Pelatih Olahraga", "Guru Pendidikan Jasmani/Guru Olahraga", "Atlet", "Wirausaha"]
      },
      "Ilmu Keolahragaan": {
        description: "Jurusan llmu Keolahragaan mengkaji olahraga dari perspektif kesehatan, terapan, hingga sosial. Tiga cabang ilmu tersebut nantinya bisa kamu pelajari lebih mendalam melalui peminatan ketika sudah menginjak semester 5. Mahasiswa jurusan ini antara lain mempelajari terapi untuk rehabilitasi fisik, manajemen olahraga hingga aktivitas jasmani. Kamu mungkin akan berpikir bahwa jurusan ini hanya akan belajar tentang olahraga saja, tetapi kenyataannya adalah hal itu tidak benar. Kamu juga akan belajar banyak sekali hal seperti anatomi, fisioterapi olahraga, mata kuliah lain di bidang kesehatan, fisiologi, dan beberapa bidang lainnya. Pengetahuan tersebut merupakan ilmu dasar yang harus dimiliki untuk menjadi seorang olahragawan maupun perorangan yang bekerja dalam bidang olahraga. Jurusan lain yang berhubungan dengan olahraga adalah Pendidikan Olahraga. Lulusannya akan mendapatkan gelar S. Pd dan akan fokus pada bidang pendidikan. Lalu selanjutnya adalah Pendidikan Kepelatihan Olahraga, yang mana nantinya kamu akan mendapatkan gelar S. Pd dan lebih fokus untuk jadi pelatih klub olahraga.",
        jobs: ["Dosen", "Pelatih Olahraga/Instruktur Olahraga", "Atlet"]
      },
      "Pendidikan Jasmani, Kesehatan, dan Rekreasi": {
        description: "Jurusan Pendidikan Jasmani, Kesehatan, dan Rekreasi (PJKR) tidak bisa dianggap remeh lho! Ingat, banyak kompetisi yang diselenggarakan di bidang olahraga, bahkan tak sedikit orang yang butuh les privat olahraga untuk mendalaminya. Pada jurusan yang satu ini, kamu akan belajar banyak hal terkait kesehatan fisik maupun mental. Mulai dari aturan dalam berolahraga, peningkatan fungsi fisik, nutrisi, strategi dan taktik, juga metode pengajaran olahraga. Maka ketika berkuliah di Program Studi Pendidikan Jasmani, Kesehatan, dan Rekreasi ini, kamu juga akan menjalani banyak praktik hampir semua jenis olahraga yang ada seperti renang, basket, voli, atletik, woodball, serta sepak bola yang tentunya selalu berada di luar kelas. Meski begitu, kamu juga akan dapat teori di kelas ya. Karena mau bagaimana pun, terdapat pengetahuan seputar olahraga yang perlu didalami.",
        jobs: ["Pelatih Olahraga", "Guru Pendidikan Jasmani/Guru Olahraga", "Atlet", "Wirausaha"]
      },
      "Manajemen Olahraga": {
        description: "Jurusan Manajemen Olahraga bertujuan untuk menghasilkan tenaga kerja terdidik yang memiliki pemahaman mengenai sinergi olahraga, bisnis dan manajemen. Pada umumnya, jurusan ini menawarkan kelas-kelas yang berfokus pada aspek bisnis olahraga, informasi tentang olahraga dan industri olahraga di tingkat perguruan tinggi dan profesional. Para mahasiswa jurusan ini juga akan belajar mengenai sejarah olahraga, etika olahraga, pemasaran olahraga, hukum olahraga, pengelolaan keuangan di industri olahraga, komunikasi olahraga dan pengelolaan fasilitas olahraga. Selain mendapatkan pengetahuan dalam kelas, para mahasiswa dalam jurusan ini akan mendapatkan pengalaman praktik dalam pengelolaan organisasi olahraga dan/atau acara olahraga. Penyampaian semua materi ini tentunya dirancang agar sesuai dengan kebutuhan terkini di industri olahraga serta tren dan teknologi terbaru.",
        jobs: ["Agen Olahraga", "Manajer Fitness", "Ahli Pemasaran Olahraga", "Direktur Atletik", "Perencana Acara Olahraga"]
      },
      "Ilmu Agama Islam": {
        description: "Mendalami ilmu agama juga bisa kamu lakukan sejalan dengan pilihan pendidikan akademis lho! Kuliah di Jurusan Ilmu Agama Islam akan membantumu memahami hukum dan aturan yang berlaku dalam sudut pandang agama Islam. Kamu akan mempelajari berbagai hal dalam hidup berdasarkan Al-Quran dan hadis. Banyak universitas yang juga akan mengajarkan tentang perkembangan Islam, ekonomi Islam, hukum Islam, pendidikan Agama Islam, dan lain-lain.",
        jobs: ["Pegawai Negeri Sipil", "Account Officer", "Video Editor", "Guru", "Dosen", "Content Writer"]
      },
      "Pendidikan Agama Islam": {
        description: "Jurusan Pendidikan Agama Islam atau PAI adalah program studi yang memiliki fokus untuk menghasilkan lulusan-lulusan yang siap untuk menjadi pengajar Agama Islam. Sederhananya, kalau mau jadi Guru Agama di Lembaga Pendidikan, kamu bisa mengambil program studi ini. Jurusan PAI ini jelas berbeda ya dengan Jurusan Ilmu Agama Islam. Jurusan Ilmu Agama Islam hanya akan mempelajari seluk beluk Islam secara mendetail hingga kamu memahami perspektif Islam secara jelas. Sementara untuk prodi PAI, selain harus mendalami Ilmu Keislaman, kamu juga akan belajar bagaimana menjadi pengajar atau pendidik yang baik. Sehingga nantinya Ketika lulus kamu bisa menjadi guru agama, hingga dosen agama Islam. Sebagai negara dengan penduduk muslim terbesar di dunia, pastinya lulusan dari jurusan Pendidikan Agama Islam sangatlah dicari dan dibutuhkan. Jurusan Pendidikan Agama Islam lebih umum ditemukan di perguruan tinggi seperti IAIN atau UIN. Biasanya Prodi PAI berada di bawah naungan Fakultas Agama Islam atau Fakultas Tarbiyah dan Ilmu Keguruan. Namun, setiap universitas bisa saja memiliki aturan yang berbeda terkait penamaan atau penempatan jurusan PAI ini. Saat lulus dari jurusan Pendidikan Agama Islam pada jenjang S1, kamu akan menyandang gelar Sarjana Pendidikan atau S.Pd. Hal ini merujuk pada Peraturan Menteri Agama (PMA) Nomor 33 Tahun 2016 tentang Gelar Akademik Perguruan Tinggi Keagamaan. Sebelum Peraturan Menteri tersebut, dulu lulusan PAI mendapatkan gelar Sarjana Pendidikan Islam atau S.Pd.I.",
        jobs: ["Guru", "Dosen", "Pegawai di Kementrian Agama", "Pegawai Negeri Sipil", "Penulis Buku Agama Islam", "Jurnalis", "Peneliti Sosial yang berkaitan dengan isu-isu agama", "Wirausahawan", "Konsultan Pendidikan", "Pegawai Bank Syariah"]
      },
      "Manajemen Dakwah": {
        description: "Jurusan manajemen dakwah adalah program studi yang mempelajari manajemen dalam dunia dakwah Islam. Jurusan ini mempersiapkan lulusan lebih dari sebatas menjadi penceramah. Jadi kalau kamu berpikir lulusan dari manajemen dakwah hanya menjadi mubaligh yang berdakwah dengan cara ceramah, tidak sepenuhnya tepat ya. Karena di samping mempunyai wawasan agama Islam, lulusan manajemen dakwah akan memiliki kemampuan untuk mengelola lembaga keagamaan. Sesuai namanya, jurusan ini merupakan kombinasi antara ilmu siar agama Islam yakni dakwah dengan ilmu manajemen. Manajemen Dakwah sama halnya dengan jurusan manajemen pada umumnya yang mempelajari cara mengelola suatu organisasi. Serta belajar tentang materi yang berkaitan dengan perencanaan, strategi, dan pengelolaan. Perbedaanya, manajemen dakwah adalah jurusan yang mempelajari ilmu manajemen untuk kepentingan di bidang dakwah. Lulusannya mempunyai peluang bekerja di lembaga keagaman pemerintah dan juga instansi non kedinasan lainnya. Termasuk lembaga amil zakat, biro haji dan umrah, serta dunia usaha dan juga pariwisata. Gimana? Prospek kerja manajemen Dakwah cukup luas kan?",
        jobs: ["Staf di lembaga keagamaan, seperti masjid, pondok pesantren, dan lembaga sosial keagamaan", "Staf di Biro Haji dan Umroh", "PNS di Kementerian Agama", "Pengelola organisasi politik Islam", "Wirausahawan", "Muballigh", "Dewan Kemakmuran Masjid", "Pengelola lembaga keuangan syariah, seperti BMT dan Bank Syariah", "Konsultan dakwah atau trainer dakwah", "Pemandu wisata religi atau umum"]
      },
      "Psikologi Islam": {
        description: "Psikolog Islam adalah program studi yang mempelajari kajian psikologi yaitu memahami kejiwaan dan perilaku manusia dari tinjauan agama berdasarkan konsep tauhid. Pertama-tama, ketahuilah bahwa kajian yang melahirkan Psikologi Islam merupakan suatu hal tergolong baru, karena eksistensinya hanya beberapa dekade yang lalu, lebih tepatnya pada tahun 1960. Dalam sejarahnya, permulaan kajian ini diinisiasi oleh Dr. Zakiah Drajat. Seperti ilmu psikologi-psikologi lainnya, Psikologi Islam mempelajari dan melakukan kajian mengenai perilaku manusia. Namun, ada sisi spesial dari Psikologi Islam yang tidak dipunyai aliran psikologi lainnya, yakni dasaran teori dan konsep yang direlevansikan pada Islam.",
        jobs: ["Psikolog", "Konselor", "HRD", "Wirausaha", "Perancang dan Fasilitator Pengembangan Komunitas"]
      },
      "Sastra Arab": {
        description: "Kalian yang berasal dari Madrasah tentu sudah akrab banget dengan aksara dan pelajaran Bahasa Arab. Nah, kamu yang mau mendalami lebih lanjut bisa lho bergabung dengan Jurusan Sastra Arab saat kuliah nanti. Nggak cuma bagi kamu yang berasal dari pendidikan Madrasah, kamu yang berasal dari SMA ataupun SMK juga bisa kok bergabung! Jurusan ini pastinya dibuka bagi semua orang yang mau belajar dan mendalami Sastra Arab. Sastra Arab sendiri merupakan bidang ilmu yang membekali mahasiswa dengan keterampilan berbicara, menulis, dan mendengarkan dengan bahasa Arab. Kamu juga akan mempelajari sastra, bahasa, maupun kebudayaan Arab secara mendalam. Selain itu, tata bahasa (Nahwu dan Sharaf), terjemahan, kajian terhadap karya sastra (manuskrip, puisi, prosa, syair Arab) kaligrafi, diplomasi, bahkan jurnalistik juga akan kamu pelajari.",
        jobs: ["Penerjemah Lisan (Interpreter)", "Penerjemah Tulisan (Translator)", "Guru Bahasa Asing", "Bagian Tata Usaha (Atase) Perdagangan Luar Negeri", "Konsultan Pendidikan", "Pramugara/i", "Staf Maskapai Penerbangan", "Tour Guide", "Jurnalis", "Dosen", "Content Creator", "Content Writer", "Editor", "Sastrawan"]
      }
    };

    // Tampilkan detail jurusan
    const detailsDiv = document.getElementById('details');
    const data = majorDetails[major];

    if (data) {
      detailsDiv.innerHTML = `
        <h2>${major}</h2>
        <p>${data.description}</p>
        <h3>Prospek Kerja:</h3>
        <ul>${data.jobs.map(job => `<li>${job}</li>`).join('')}</ul>
      `;
    } else {
      detailsDiv.innerHTML = "<p>Data jurusan tidak ditemukan.</p>";
    }
  </script>
</body>
</html>
