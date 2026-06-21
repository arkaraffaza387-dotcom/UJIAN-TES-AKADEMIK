<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Belajar Ujian Sekolah & Umum</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdn.jsdelivr.net/npm/font-awesome@4.7.0/css/font-awesome.min.css" rel="stylesheet">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        utama:'#165DFF',
                        sekunder:'#36CFC9',
                        aksen:'#F7BA1E',
                        gelap:'#0F1117',
                        gelapRingan:'#1A1D29',
                        gelapLebihRingan:'#272A36',
                        teksMuda:'#86909C',
                    },
                    fontFamily: {
                        sans: ['Inter', 'system-ui', 'sans-serif'],
                    },
                    boxShadow: {
                        'halus': '0 8px 24px rgba(0,0,0,0.35)',
                        'lembut': '0 4px 12px rgba(0,0,0,0.25)',
                    }
                }
            }
        }
    </script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');
        .kontenTengah{display:grid;place-items:center;}
        .transisi{transition:all 0.3s ease;}
        .bgGradien{background:linear-gradient(135deg,#165DFF,#36CFC9);}
        .hidden{display:none !important;}
        body{font-family:'Inter',sans-serif;}
        .card{border:1px solid rgba(255,255,255,0.08);}
        input,select{background:#1A1D29 !important; border-color:#333842 !important; color:#fff !important;}
        input::placeholder{color:#636974 !important;}
        button:disabled{opacity:0.45;cursor:not-allowed;}
    </style>
</head>
<body class="bg-gelap text-white min-h-screen font-sans">
    <!-- HALAMAN PEMBATASAN JAM MALAM -->
    <div id="halamanIstirahat" class="hidden fixed inset-0 bg-gelap z‑50 flex items‑center justify‑center text‑center p‑6">
        <div>
            <h1 class="text‑3xl md:text‑5xl font‑bold text‑aksen mb‑4">MOHON TIDUR</h1>
            <p class="text‑lg md:text‑2xl text‑teksMuda">INI DEMI KEBAIKAN ANDA</p>
            <p class="mt‑6 text‑sm">Situs dapat digunakan kembali mulai pukul <strong>01.00 dini hari</strong></p>
        </div>
    </div>


    <div class="container mx-auto px-4 py-8 max-w-4xl" id="wadahUtama">
        <!-- TAMPILAN BIASA: SEBELUM 24 JUNI -->
        <div id="halamanBiasa">
            <header class="text-center mb-10">
                <h1 class="text-[clamp(1.5rem,3vw,2.2rem)] font-bold text-utama tracking-tight">📚 Sistem Latihan Belajar</h1>
                <div class="mt-3 text-sm">
                    <a href="#halaman-ujian" class="text-teksMuda hover:text-utama transisi mr-4">Latihan</a>
                    <a href="#halaman-nilai" class="text-teksMuda hover:text-utama transisi">Riwayat Nilai</a>
                </div>
            </header>

            <!-- HALAMAN UJIAN -->
            <section id="halaman-ujian" class="bg-gelapRingan rounded-2xl shadow-halus p-7 mb-10 card">
                <div class="mb-6 p-3 bg-amber-500/10 border border-amber-400/20 rounded-xl text-sm text-amber-300">
                    ⚠️ Hanya untuk latihan pribadi. <strong>Setiap soal benar = 5 poin • Total 100</strong> | Akun berlaku hanya 2 hari
                </div>

                <div id="bagianPilihan">
                    <h2 class="text-xl font-semibold mb-5">Pengaturan Latihan</h2>
                    <div class="grid md:grid-cols-3 gap-5 mb-6">
                        <div>
                            <label class="block mb-2 text-sm text-teksMuda">Tingkat / Kelas</label>
                            <select id="pilihKelas" class="w-full border rounded-lg p-2.5 transisi focus:ring-2 focus:ring-utama/40 focus:outline-none">
                                <option value="">-- Pilih Tingkat --</option>
                                <optgroup label="Sekolah Dasar">
                                    <option>1 SD</option><option>2 SD</option><option>3 SD</option>
                                    <option>4 SD</option><option>5 SD</option><option>6 SD</option>
                                </optgroup>
                                <optgroup label="Sekolah Menengah Pertama">
                                    <option>7 SMP</option><option>8 SMP</option><option>9 SMP</option>
                                </optgroup>
                                <optgroup label="Sekolah Menengah Atas">
                                    <option>10 SMA/SMK</option><option>11 SMA/SMK</option><option>12 SMA/SMK</option>
                                </optgroup>
                                <optgroup label="Perguruan Tinggi">
                                    <option>Semester 1 KULIAH</option><option>Semester 2 KULIAH</option>
                                    <option>Semester 3 KULIAH</option><option>Semester 4 KULIAH</option>
                                    <option>Semester 5 KULIAH</option><option>Semester 6 KULIAH</option>
                                    <option>Semester 7 KULIAH</option><option>Semester 8+ KULIAH</option>
                                </optgroup>
                            </select>
                        </div>
                        <div>
                            <label class="block mb-2 text-sm text-teksMuda">Tingkat Kesulitan</label>
                            <select id="pilihTingkat" class="w-full border rounded-lg p-2.5 transisi focus:ring-2 focus:ring-utama/40 focus:outline-none">
                                <option value="">-- Pilih Tingkat --</option>
                                <option value="mudah">Mudah</option><option value="biasa">Normal</option><option value="susah">Susah</option>
                            </select>
                        </div>
                        <div>
                            <label class="block mb-2 text-sm text-teksMuda">Mata Pelajaran / Bidang</label>
                            <select id="pilihMapel" class="w-full border rounded-lg p-2.5 transisi focus:ring-2 focus:ring-utama/40 focus:outline-none">
                                <option value="">-- Pilih Bidang --</option>
                                <option value="mtk">Matematika</option>
                                <option value="bindo">B. Indonesia</option>
                                <option value="ipa">IPA / Sains</option>
                                <option value="ips">IPS / Sosial</option>
                                <option value="binggris">B. Inggris</option>
                            </select>
                        </div>
                    </div>
                    <button onclick="lanjutAkun()" class="w-full bgGradien text-white py-2.5 rounded-lg font-medium shadow-lembut hover:opacity-90 transisi">Lanjutkan</button>
                </div>

                <div id="bagianAkun" class="hidden">
                    <h2 class="text-xl font-semibold mb-5">Akses / Buat Akun</h2>
                    <div class="grid md:grid-cols-2 gap-8">
                        <div class="p-4 rounded-xl bg-gelapLebihRingan/40">
                            <h3 class="font-medium mb-3 text-teksMuda">Sudah Punya Akun</h3>
                            <input type="text" id="userMasuk" placeholder="Nama Pengguna" class="w-full border rounded-lg p-2.5 mb-3 transisi focus:ring-2 focus:ring-sekunder/40 focus:outline-none">
                            <input type="email" id="emailMasuk" placeholder="Alamat Email Terdaftar" class="w-full border rounded-lg p-2.5 mb-3 transisi focus:ring-2 focus:ring-sekunder/40 focus:outline-none">
                            <input type="password" id="passMasuk" placeholder="Kata Sandi" class="w-full border rounded-lg p-2.5 mb-3 transisi focus:ring-2 focus:ring-sekunder/40 focus:outline-none">
                            <button onclick="prosesMasuk()" class="w-full bg-sekunder/90 hover:bg-sekunder text-white py-2.5 rounded-lg font-medium transisi">Masuk</button>
                        </div>
                        <div class="p-4 rounded-xl bg-gelapLebihRingan/40">
                            <h3 class="font-medium mb-3 text-teksMuda">Buat Akun Baru</h3>
                            <p class="text-xs mb-3 text-teksMuda">Kode Akses: <b class="text-aksen">BELAJAR_GO</b> • Berlaku akun 2 hari</p>
                            <input type="text" id="userBaru" placeholder="Nama Pengguna Baru" class="w-full border rounded-lg p-2.5 mb-3 transisi focus:ring-2 focus:ring-aksen/40 focus:outline-none">
                            
                            <label class="block mb-1 text-sm text-teksMuda">Alamat Email <span class="text-red-400">*</span> <small class="text‑teksMuda/60">(wajib terdaftar sistem)</small></label>
                            <div class="flex gap-2 mb-3">
                                <input type="email" id="emailBaru" placeholder="contoh: sekolahxxx@gmail.com" class="flex‑1 border rounded-lg p-2.5 transisi focus:ring-2 focus:ring-aksen/40 focus:outline-none">
                            </div>
                            <button id="tombolBuatEmail" onclick="buatEmailSekolah()" class="w-full mb-3 border border-dashed border‑aksen/60 text‑aksen/90 py‑2 rounded‑lg hover:bg‑aksen/10 transisi">
                                ✨ Buat Email Sekolah Otomatis <span id="hitunganDetik"></span>
                            </button>
                            <p class="text‑xs text‑teksMuda/70 mb‑3">ℹ️ Email yang dibuat disimpan permanen, tidak bisa diubah/dihapus walau dimuat ulang</p>

                            <input type="password" id="passBaru" placeholder="Kata Sandi Baru" class="w-full border rounded-lg p-2.5 mb-3 transisi focus:ring-2 focus:ring-aksen/40 focus:outline-none">
                            <input type="text" id="kodeAkses" placeholder="Masukkan Kode Akses" class="w-full border rounded-lg p-2.5 mb-3 uppercase transisi focus:ring-2 focus:ring-aksen/40 focus:outline-none">
                            <button onclick="prosesDaftar()" class="w-full bg-aksen hover:bg-aksen/90 text-gelap font-semibold py-2.5 rounded-lg transisi">Buat Akun</button>
                        </div>
                    </div>
                    <div class="mt-6 text-center">
                        <button onclick="kembaliPilihan()" class="text-sm text-teksMuda hover:text-white transisi">&larr; Kembali ke Pengaturan</button>
                    </div>
                </div>

                <div id="bagianUjian" class="hidden">
                    <h2 class="text-xl font-semibold mb-5">Soal Latihan</h2>
                    <div id="wadahSoal" class="space-y-4 mb-6"></div>
                    <button onclick="selesaikanUjian()" class="w-full bg-utama hover:bg-utama/90 text-white py-2.5 rounded-lg font-medium shadow-lembut transisi">✅ Selesaikan Ujian & Hitung Nilai</button>
                </div>

                <div id="bagianSelesai" class="hidden text-center py-10">
                    <div class="text-5xl text-sekunder mb-3"><i class="fa fa-check-circle"></i></div>
                    <h2 class="text-xl font-bold mb-2">Ujian Telah Selesai!</h2>
                    <p class="text-teksMuda mb-4">Nilai tersimpan aman di perangkat • Kirim data otomatis mulai tanggal 24 Juni</p>
                    <a href="#halaman-nilai" onclick="tampilNilai()" class="inline-block text-utama hover:text-sekunder font-medium transisi">Lihat Riwayat Nilai &rarr;</a>
                </div>
            </section>

            <!-- HALAMAN NILAI -->
            <section id="halaman-nilai" class="bg-gelapRingan rounded-2xl shadow-halus p-7 card">
                <h2 class="text-xl font-semibold mb-5">📋 Riwayat Hasil Latihan</h2>
                <div id="daftarNilai"></div>
                <button id="tombolHapusSemua" onclick="hapusSemua()" class="mt-6 w-full bg-red-500/10 text-red-300 border border-red-400/20 py-2.5 rounded-lg hover:bg-red-500/20 transisi">
                    🗑️ Hapus Semua Riwayat
                    <span id="keteranganKunci" class="text-xs ml-2">(Baru aktif mulai 23 Juni)</span>
                </button>
            </section>
        </div>


        <!-- TAMPILAN KHUSUS: MULAI 24 JUNI SAJA -->
        <div id="halamanKhusus" class="hidden text‑center py‑16">
            <div class="max‑w‑md mx‑auto bg‑gelapRingan rounded‑2xl shadow‑halus p‑8 card">
                <h2 class="text‑2xl font‑bold mb‑4 text‑aksen">📤 Pengiriman Data Nilai</h2>
                <p class="text‑teksMuda mb‑6">Sistem berubah fungsi: hanya kirim seluruh hasil ujian ke nomor pusat.</p>
                
                <div class="text‑left space‑y‑3 mb‑6">
                    <div>
                        <label class="text‑sm text‑teksMuda">Nama Akun</label>
                        <input type="text" id="kirimNama" class="w‑full mt‑1">
                    </div>
                    <div>
                        <label class="text‑sm text‑teksMuda">Alamat Email</label>
                        <input type="email" id="kirimEmail" class="w‑full mt‑1">
                    </div>
                    <div>
                        <label class="text‑sm text‑teksMuda">Ringkasan Nilai / Hasil</label>
                        <textarea id="kirimIsi" rows="4" class="w‑full mt‑1"></textarea>
                    </div>
                </div>

                <a id="tautanWA" href="#" target="_blank" class="inline‑block w‑full bg‑green‑600 hover:bg‑green‑700 py‑3 rounded‑xl font‑semibold transisi">
                    📲 Kirim ke WhatsApp Pusat
                </a>
                <p class="text‑xs text‑teksMuda mt‑4">Tujuan: 0858‑8238‑2854</p>
            </div>
        </div>

    </div>


    <script>
        // === PENGATURAN UTAMA ===
        const TANGGAL_UBAH_SISTEM = new Date(2026, 5, 24); // 24 Juni
        const NOMOR_WA_TUJUAN = "6285882382854";
        const TANGGAL_AKTIF_HAPUS = new Date(2026, 5, 23);
        const BATAS_UMUR_AKUN = 2 * 24 * 60 * 60 * 1000; // 2 hari
        const KODE_AKSES = "BELAJAR_GO";

        // Penyimpanan
        function ambilData(k){return JSON.parse(localStorage.getItem(k)||'[]');}
        function simpanData(k,v){localStorage.setItem(k,JSON.stringify(v));}
        let akunSaatIni=null, pengaturan={};


        // ✅ PENYIMPANAN EMAIL PERMANEN: TIDAK BISA DIUBAH / DIHAPUS
        function daftarEmailTerdaftar(){return ambilData('emailTetap');}
        function simpanEmailPermanen(alamat){
            let daftar = daftarEmailTerdaftar();
            if(!daftar.includes(alamat)){
                daftar.push(alamat);
                simpanData('emailTetap', daftar); // disimpan selamanya di penyimpanan lokal
            }
        }
        function cekEmailTerdaftar(alamat){return daftarEmailTerdaftar().includes(alamat.trim().toLowerCase());}


        // ✅ PEMBATASAN JAM MALAM: >22.00 s.d <01.00 = TUTUP
        function cekWaktuIstirahat(){
            const skrg = new Date();
            const jam = skrg.getHours();
            const halIstirahat = document.getElementById('halamanIstirahat');
            const wadahUtama = document.getElementById('wadahUtama');
            if(jam >= 22 || jam < 1){
                halIstirahat.classList.remove('hidden');
                wadahUtama.classList.add('hidden');
            } else {
                halIstirahat.classList.add('hidden');
                wadahUtama.classList.remove('hidden');
            }
        }


        // ✅ BUAT EMAIL ACAK + TUNGGU 7 DETIK + LANGSUNG DISIMPAN PERMANEN
        function buatEmailSekolah(){
            const tombol = document.getElementById('tombolBuatEmail');
            const tampilDetik = document.getElementById('hitunganDetik');
            tombol.disabled = true;
            let sisa = 7;
            tampilDetik.textContent = `(${sisa} dtk)`;
            
            const hitung = setInterval(()=>{
                sisa--;
                tampilDetik.textContent = `(${sisa} dtk)`;
                if(sisa<=0){
                    clearInterval(hitung);
                    tampilDetik.textContent = "";
                    tombol.disabled = false;
                    // Buat acak huruf+angka sesuai permintaan
                    const acakKarakter = () => {
                        const hrf = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789";
                        let hasil = "";
                        for(let i=0;i<5;i++) hasil += hrf[Math.floor(Math.random()*hrf.length)];
                        return hasil;
                    };
                    const alamatBaru = `sekolah${acakKarakter()}@gmail.com`;
                    document.getElementById('emailBaru').value = alamatBaru;
                    simpanEmailPermanen(alamatBaru); // ✅ LANGSUNG DIKUNCI & DISIMPAN
                }
            },1000);
        }


        // Bersihkan akun kedaluwarsa (TAPI DAFTAR EMAIL TETAP DIAM)
        function bersihkanAkunKadaluarsa(){
            let daftar = ambilData('akunSiswa');
            let sekarang = Date.now();
            simpanData('akunSiswa', daftar.filter(a=>sekarang-(a.dibuatPada||sekarang) < BATAS_UMUR_AKUN));
        }

        function cekTombolHapus(){
            const t = new Date(), btn = document.getElementById('tombolHapusSemua'), ket = document.getElementById('keteranganKunci');
            if(t < TANGGAL_AKTIF_HAPUS){ btn.disabled=true; if(ket)ket.textContent="(Baru aktif mulai 23 Juni)"; }
            else { btn.disabled=false; if(ket)ket.textContent=""; }
        }

        function cekPerubahanTanggal(){
            const skrg = new Date();
            const halBiasa = document.getElementById('halamanBiasa');
            const halKhusus = document.getElementById('halamanKhusus');
            if(skrg >= TANGGAL_UBAH_SISTEM){
                halBiasa.classList.add('hidden'); halKhusus.classList.remove('hidden');
                const akun = ambilData('akunSiswa')[0] || {};
                const riwayat = ambilData('catatanNilai');
                document.getElementById('kirimNama').value = akun.user || "";
                document.getElementById('kirimEmail').value = akun.email || "";
                document.getElementById('kirimIsi').value = JSON.stringify(riwayat, null, 2);
                const tautan = document.getElementById('tautanWA');
                tautan.onclick = ()=>{
                    const n=encodeURIComponent(document.getElementById('kirimNama').value),
                          e=encodeURIComponent(document.getElementById('kirimEmail').value),
                          isi=encodeURIComponent(`📝 LAPORAN%0A👤 ${n}%0A📧 ${e}%0A%0A${document.getElementById('kirimIsi').value}`);
                    tautan.href=`https://wa.me/${NOMOR_WA_TUJUAN}?text=${isi}`;
                };
            } else { halBiasa.classList.remove('hidden'); halKhusus.classList.add('hidden'); }
        }


        // === BANK SOAL & FUNGSI UTAMA ===
        const bankSoal={
            mtk:[
                {t:"7 × 6 = ?",j:"42",o:["36","42","48","54"]},
                {t:"25 + 17 = ?",j:"42",o:["32","40","42","52"]},
                {t:"Kelipatan 3 adalah?",j:"12",o:["10","12","14","16"]},
                {t:"½ = ... %",j:"50%",o:["25%","40%","50%","75%"]},
                {t:"Keliling persegi panjang p=10 l=5?",j:"30",o:["15","30","50","100"]},
                {t:"81 ÷ 9 = ?",j:"9",o:["7","8","9","11"]},
                {t:"Pecahan senilai ⅔?",j:"4/6",o:["1/3","4/6","3/4","5/8"]},
                {t:"Sudut siku‑siku besarnya?",j:"90 derajat",o:["45 derajat","60 derajat","90 derajat","180 derajat"]},
                {t:"Faktor dari 12 adalah?",j:"1,2,3,4,6,12",o:["1,2,3,5","1,2,3,4,6,12","2,3,4,6","3,4,6,12"]},
                {t:"0,5 + 0,25 = ?",j:"0,75",o:["0,30","0,55","0,75","1,00"]},
                {t:"Luas persegi sisi 8 cm?",j:"64 cm²",o:["16 cm²","32 cm²","64 cm²","128 cm²"]},
                {t:"KPK dari 4 dan 6 = ?",j:"12",o:["8","12","16","24"]},
                {t:"Bilangan prima antara 1‑10:",j:"2,3,5,7",o:["1,3,5,7","2,3,5,7","2,4,6,8","3,5,7,9"]},
                {t:"20% dari 150 = ?",j:"30",o:["20","25","30","45"]},
                {t:"Jam 07.30 ditambah 45 menit = ?",j:"08.15",o:["07.45","08.00","08.15","08.20"]},
                {t:"Berapa sisi pada segitiga?",j:"3",o:["2","3","4","5"]},
                {t:"⅕ + ⅖ = ?",j:"3/5",o:["2/5","3/5","4/5","5/5"]},
                {t:"3.000 gram sama dengan ... kg",j:"3 kg",o:["0,3 kg","3 kg","30 kg","300 kg"]},
                {t:"FPB dari 12 dan 18 = ?",j:"6",o:["3","6","9","12"]},
                {t:"Urutkan naik: 12, 5, 19, 9",j:"5,9,12,19",o:["19,12,9,5","5,9,12,19","9,5,12,19","5,12,9,19"]}
            ],
            bindo:[
                {t:"Ejaan yang benar adalah?",j:"belajar",o:["blajar","belajar","belajarr","belaar"]},
                {t:"Kata baku dari 'nggak' adalah?",j:"tidak",o:["bukan","tak","tidak","enggak"]},
                {t:"Awal kalimat harus ditulis dengan?",j:"huruf besar",o:["huruf kecil","huruf besar","angka","simbol"]},
                {t:"Kata kerja dalam kalimat: Ayah sedang membaca koran?",j:"membaca",o:["Ayah","sedang","membaca","koran"]},
                {t:"Tanda baca untuk kalimat tanya?",j:"tanda tanya",o:["titik","koma","tanda tanya","seru"]},
                {t:"Sinonim dari kata 'pintar'?",j:"cerdas",o:["rajin","cerdas","sombong","malas"]},
                {t:"Lawan kata dari 'bersih'?",j:"kotor",o:["rapi","kotor","kusam","berdebu"]},
                {t:"Subjek kalimat: Kami berangkat sekolah pagi ini?",j:"Kami",o:["berangkat","sekolah","pagi ini","Kami"]},
                {t:"Kalimat baku yang benar?",j:"Saya sedang makan nasi",o:["Aku lagi makan","Saya sedang makan nasi","Saya makan ni","Saya lagi makan nasi"]},
                {t:"Huruf kapital dipakai untuk?",j:"nama orang/tempat",o:["semua kata","awal nama orang/tempat","kata kerja","kata benda"]},
                {t:"Kata turunan dari 'ajar'?",j:"pengajaran",o:["ajarannya","pengajaran","diajar","ajar‑ajar"]},
                {t:"Kalimat tanya yang tepat?",j:"Kapan kamu pulang?",o:["Kamu pulang kapan","Kapan kamu pulang?","Pulang kamu kapan?","Kapan pulang kamu"]},
                {t:"Fungsi utama tanda koma?",j:"memisah bagian kalimat",o:["akhir kalimat","memisah bagian kalimat","menutup daftar","menandai seruan"]},
                {t:"Contoh kata penghubung?",j:"dan",o:["buku","dan","berlari","indah"]},
                {t:"Penulisan nama orang yang benar?",j:"Budi Santoso",o:["budi santoso","Budi santoso","Budi Santoso","budi Santoso"]},
                {t:"Keterangan tempat: Adik bermain bola di halaman?",j:"di halaman",o:["Adik","bermain bola","di halaman","halaman"]},
                {t:"Kata sifat: Hari ini cuaca sangat cerah?",j:"cerah",o:["hari","cuaca","sangat","cerah"]},
                {t:"Yang bukan kata baku?",j:"foto",o:["fotokopi","foto","telepon","kantor"]},
                {t:"Paragraf biasanya diawali dengan?",j:"dengan menjorok ke dalam",o:["huruf kecil","dengan menjorok ke dalam","tanpa spasi","dengan angka"]},
                {t:"Contoh kalimat perintah?",j:"Tutuplah pintu itu!",o:["Pintu itu ditutup","Tutuplah pintu itu!","Apakah pintu tertutup?","Pintu sudah tertutup"]}
            ],
            ipa:[
                {t:"Alat pernapasan utama manusia?",j:"paru‑paru",o:["jantung","lambung","paru‑paru","ginjal"]},
                {t:"Tumbuhan membuat makanannya sendiri lewat proses?",j:"fotosintesis",o:["respirasi","fotosintesis","penyerapan","penguapan"]},
                {t:"Sumber energi utama bumi?",j:"matahari",o:["api","matahari","batu bara","air"]},
                {t:"Bagian tumbuhan yang menyerap air dan zat hara?",j:"akar",o:["daun","batang","akar","bunga"]},
                {t:"Perubahan air menjadi uap disebut?",j:"penguapan",o:["pengembunan","pembekuan","penguapan","pengendapan"]},
                {t:"Hewan pemakan tumbuhan disebut?",j:"pemakan tumbuhan",o:["pemakan daging","pemakan tumbuhan","pemakan segala","pengurai"]},
                {t:"Jantung berfungsi memompa?",j:"darah",o:["udara","sari makanan","darah","air"]},
                {t:"Benda yang tembus cahaya disebut?",j:"bening",o:["gelap","berwarna","bening","padat"]},
                {t:"Siklus air dimulai dari tahap?",j:"penguapan laut/sungai",o:["hujan","penguapan laut/sungai","aliran air","embun"]},
                {t:"Batu, tanah, pasir termasuk benda berwujud?",j:"padat",o:["cair","gas","padat","berat"]},
                {t:"Contoh hewan yang bertelur?",j:"ayam",o:["kucing","sapi","ayam","kambing"]},
                {t:"Zat penting yang didapat dari makanan?",j:"gizi/nutrisi",o:["warna","gizi/nutrisi","bau","rasa"]},
                {t:"Penyebab terjadinya siang dan malam?",j:"bumi berputar sendiri",o:["matahari bergerak","bumi berputar sendiri","bulan mengelilingi bumi","angin"]},
                {t:"Peran bakteri pengurai di alam?",j:"menguraikan sisa makhluk hidup",o:["membuat sakit","menguraikan sisa makhluk hidup","menghasilkan oksigen","menyerap air"]},
                {t:"Ciri air yang bersih dan sehat?",j:"jernih dan tidak berbau",o:["berwarna","berbau","jernih dan tidak berbau","berasa tawar saja"]},
                {t:"Alat indra untuk mendengar?",j:"telinga",o:["mata","hidung","telinga","kulit"]},
                {t:"Saat membeku, air berubah menjadi?",j:"es padat",o:["uap","es padat","embun","kabut"]},
                {t:"Sinar matahari membantu tumbuhan menghasilkan?",j:"makanan & oksigen",o:["hanya air","makanan & oksigen","hanya bayangan","hanya akar"]},
                {t:"Satuan suhu yang umum dipakai di Indonesia?",j:"derajat Celcius",o:["meter","derajat Celcius","detik","gram"]},
                {t:"Rantai makanan selalu dimulai dari?",j:"tumbuhan",o:["hewan","tumbuhan","pengurai","tanah"]}
            ],
            ips:[
                {t:"Tempat tinggal sekelompok orang disebut?",j:"lingkungan/pemukiman",o:["hutan","lingkungan/pemukiman","sungai","gunung"]},
                {t:"Ibu kota negara Indonesia?",j:"Jakarta",o:["Bandung","Surabaya","Jakarta","Semarang"]},
                {t:"Peta bermanfaat untuk mengetahui?",j:"letak tempat",o:["cuaca","letak tempat","musim","waktu"]},
                {t:"Sungai, danau, laut termasuk bentang alam jenis?",j:"perairan",o:["daratan","perairan","pegunungan","dataran"]},
                {t:"Kerja sama antarwarga memperkuat rasa?",j:"persatuan",o:["perpecahan","persaingan","persatuan","kekayaan"]},
                {t:"Mata pencaharian utama masyarakat di daerah pantai?",j:"nelayan",o:["petani","nelayan","tukang kayu","pedagang"]},
                {t:"Warna bendera negara Indonesia?",j:"merah putih",o:["merah kuning","putih biru","merah putih","kuning hijau"]},
                {t:"Manfaat letusan gunung berapi bagi tanah?",j:"tanah jadi subur",o:["tanah jadi subur","sungai penuh","udara bersih","tanaman mati"]},
                {t:"Sikap yang benar saat bergaul dengan orang lain?",j:"saling menghargai",o:["saling mengejek","saling menghargai","saling memaksa","saling bersaing"]},
                {t:"Jumlah arah mata angin utama?",j:"4",o:["2","3","4","8"]},
                {t:"Contoh hasil pertanian?",j:"padi dan jagung",o:["ikan udang","batu pasir","padi dan jagung","kain baju"]},
                {t:"Tanggal 17 Agustus memperingati hari?",j:"Kemerdekaan RI",o:["Hari Pendidikan","Hari Kemerdekaan RI","Hari Bumi","Hari Guru"]},
                {t:"Mata pencaharian umum di daerah dataran tinggi?",j:"bertani sayur/buah",o:["berlayar","bertani sayur/buah","berdagang laut","menambang"]},
                {t:"Garis batas wilayah antarnegara di darat disebut?",j:"garis batas darat",o:["garis pantai","garis batas darat","garis khatulistiwa","garis waktu"]},
                {t:"Pemimpin wilayah desa atau kelurahan?",j:"kepala desa/lurah",o:["gubernur","bupati","kepala desa/lurah","camat"]},
                {t:"Alat dan benda buatan manusia disebut?",j:"benda budaya/teknologi",o:["benda alam","benda budaya/teknologi","benda cair","benda padat"]},
                {t:"Negara Indonesia terletak di benua?",j:"Asia",o:["Afrika","Asia","Eropa","Australia"]},
                {t:"Musim yang ada di wilayah Indonesia?",j:"hujan dan kemarau",o:["dingin‑panas","hujan‑kemarau","gugur‑semi","angin‑badai"]},
                {t:"Contoh sumber daya alam yang bisa habis?",j:"minyak bumi/batu bara",o:["air angin","minyak bumi/batu bara","cahaya matahari","ombak"]},
                {t:"Sikap yang tepat saat bertamu ke rumah orang lain?",j:"sopan dan tepat waktu",o:["sopan dan tepat waktu","terlambat berisik","mengambil barang sembarangan","berbicara keras"]}
            ],
            binggris:[
                {t:"Bahasa Inggris dari 'kucing'?",j:"cat",o:["dog","cat","bird","fish"]},
                {t:"Bahasa Inggris dari angka 'satu'?",j:"one",o:["two","one","three","four"]},
                {t:"Bahasa Inggris dari warna 'merah'?",j:"red",o:["blue","green","red","yellow"]},
                {t:"Lengkapi: I ... a student",j:"am",o:["is","are","am","have"]},
                {t:"Bahasa Inggris dari hari 'Minggu'?",j:"Sunday",o:["Monday","Sunday","Friday","Tuesday"]},
                {t:"Bahasa Inggris untuk 'terima kasih'?",j:"Thank you",o:["Hello","Goodbye","Thank you","Sorry"]},
                {t:"Bahasa Inggris dari 'buku'?",j:"book",o:["pen","pencil","book","bag"]},
                {t:"Kata ganti untuk 'dia laki‑laki'?",j:"he",o:["she","he","it","we"]},
                {t:"Lengkapi: ... apple",j:"an",o:["a","an","the","‑"]},
                {t:"Bahasa Inggris dari kata kerja 'makan'?",j:"eat",o:["drink","eat","run","read"]},
                {t:"Bahasa Inggris dari angka 'sepuluh'?",j:"ten",o:["eight","nine","ten","eleven"]},
                {t:"Kata tanya untuk menanyakan tempat?",j:"Where",o:["When","Where","Who","What"]},
                {t:"Lawan kata 'besar' dalam bahasa Inggris?",j:"small",o:["big","small","long","short"]},
                {t:"Lengkapi: We ... football",j:"play",o:["plays","play","playing","played"]},
                {t:"Bahasa Inggris dari anggota tubuh 'mata'?",j:"eye",o:["ear","nose","eye","hand"]},
                {t:"Bahasa Inggris musim 'panas'?",j:"summer",o:["winter","autumn","summer","spring"]},
                {t:"Lengkapi: ... the table (di atas meja)",j:"on",o:["in","on","under","between"]},
                {t:"Bahasa Inggris kata penghubung 'dan'?",j:"and",o:["but","or","and","so"]},
                {t:"Bahasa Inggris dari 'kakak perempuan'?",j:"sister",o:["brother","sister","father","mother"]},
                {t:"Lengkapi: Good ... (selamat pagi)",j:"morning",o:["night","afternoon","morning","evening"]}
            ]
        };

        function acakArray(a){return [...a].sort(()=>Math.random()-0.5);}
        function lanjutAkun(){
            const k=document.getElementById('pilihKelas').value,t=document.getElementById('pilihTingkat').value,m=document.getElementById('pilihMapel').value;
            if(!k||!t||!m)return alert("⚠️ Lengkapi semua pilihan terlebih dahulu!");
            pengaturan={kelas:k,tingkat:t,mapel:m};
            document.getElementById('bagianPilihan').classList.add('hidden');
            document.getElementById('bagianAkun').classList.remove('hidden');
        }
        function kembaliPilihan(){
            document.getElementById('bagianAkun').classList.add('hidden');
            document.getElementById('bagianPilihan').classList.remove('hidden');
        }
        function prosesDaftar(){
            const u=document.getElementById('userBaru').value.trim(),
                  e=document.getElementById('emailBaru').value.trim().toLowerCase(),
                  p=document.getElementById('passBaru').value.trim(),
                  kd=document.getElementById('kodeAkses').value.trim().toUpperCase();
            if(!e) return alert("⚠️ Alamat Email WAJIB diisi!");
            if(!cekEmailTerdaftar(e)) return alert("❌ Email ini BELUM terdaftar sistem! Buat dulu pakai tombol ✨ Buat Email Sekolah");
            if(kd !== KODE_AKSES) return alert("❌ Kode akses salah! Gunakan: "+KODE_AKSES);
            if(!u||!p)return alert("⚠️ Nama pengguna & sandi tidak boleh kosong!");
            let d=ambilData('akunSiswa');if(d.find(x=>x.user===u))return alert("⚠️ Nama ini sudah dipakai orang lain!");
            d.push({user:u, email:e, sandi:p, dibuatPada:Date.now()});
            simpanData('akunSiswa',d); akunSaatIni=u;
            alert("✅ Akun berhasil dibuat!"); mulaiUjian();
        }
        function prosesMasuk(){
            const u=document.getElementById('userMasuk').value.trim(),
                  e=document.getElementById('emailMasuk').value.trim().toLowerCase(),
                  p=document.getElementById('passMasuk').value.trim(),
                  d=ambilData('akunSiswa'),
                  x=d.find(i=>i.user===u && i.email===e && i.sandi===p);
            if(!x)return alert("❌ Data tidak cocok atau akun kedaluwarsa / email tidak terdaftar!");
            akunSaatIni=u; mulaiUjian();
        }
        function mulaiUjian(){
            document.getElementById('bagianAkun').classList.add('hidden');
            document.getElementById('bagianUjian').classList.remove('hidden'); tampilkanSoal();
        }
        function tampilkanSoal(){
            const w=document.getElementById('wadahSoal');w.innerHTML="";
            acakArray(bankSoal[pengaturan.mapel]).slice(0,20).forEach((s,i)=>{
                const o=acakArray(s.o),b=document.createElement("div");
                b.className="p‑4 bg‑gelapLebihRingan/50 border border‑white/5 rounded‑xl";
                b.innerHTML=`<p class="font‑medium mb‑3">${i+1}. ${s.t}</p><div class="space‑y‑2 text‑sm">${o.map((opt,ix)=>`<label class="flex items‑center gap‑2 cursor‑pointer hover:bg‑white/5 p‑2 rounded‑lg transisi"><input type="radio" name="soal${i}" value="${opt===s.j?'benar':'salah'}" class="accent‑utama">${String.fromCharCode(65+ix)}. ${opt}</label>`).join('')}</div>`;
                w.appendChild(b);
            });
        }
        function selesaikanUjian(){
            let benar=0; document.querySelectorAll('[name^="soal"]').forEach(g=>{
                const p=document.querySelector(`[name="${g.name}"]:checked`); if(p&&p.value==="benar") benar++;
            });
            let c=ambilData('catatanNilai'); c.push({
                nama:akunSaatIni, waktu:new Date().toLocaleString('id‑ID'), ...pengaturan, benar, nilai:benar*5
            }); simpanData('catatanNilai',c);
            document.getElementById('bagianUjian').classList.add('hidden'); document.getElementById('bagianSelesai').classList.remove('hidden');
        }
        function tampilNilai(){
            const w=document.getElementById('daftarNilai'),d=ambilData('catatanNilai');
            w.innerHTML=!d.length?`<p class="text‑center text‑teksMuda py‑6">Belum ada riwayat.</p>`:
            `<div class="space‑y‑3">${d.map(x=>`<div class="p‑4 rounded‑xl border ${x.nilai>=75?'bg‑emerald‑900/15 border‑emerald‑500/20':'bg‑amber‑900/15 border‑amber‑500/20'}">
                <div class="flex justify‑between font‑medium">${x.mapel} • ${x.kelas} • ${x.tingkat}<strong>${x.nilai}/100</strong></div>
                <div class="text‑sm opacity‑80 mt‑1">👤 ${x.nama} | ✅ Benar: ${x.benar} × 5 poin | 🕒 ${x.waktu}</div>
            </div>`).join('')}</div>`;
        }
        function hapusSemua(){
            if(new Date()<TANGGAL_AKTIF_HAPUS) return alert("🔒 Hanya aktif mulai tanggal 23 Juni");
            if(confirm("Yakin ingin menghapus SEMUA riwayat nilai?")){localStorage.removeItem('catatanNilai'); tampilNilai();}
        }


        // === JALANKAN SEMUA PENGECEKAN OTOMATIS ===
        bersihkanAkunKadaluarsa();
        cekTombolHapus();
        tampilNilai();
        cekPerubahanTanggal();
        cekWaktuIstirahat();
        setInterval(cekWaktuIstirahat, 60000); // cek ulang setiap 1 menit otomatis
    </script>
</body>
</html>
