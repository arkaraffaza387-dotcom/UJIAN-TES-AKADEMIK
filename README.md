<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Belajar Ujian Sekolah SD</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdn.jsdelivr.net/npm/font-awesome@4.7.0/css/font-awesome.min.css" rel="stylesheet">
    <script>
        tailwind.config = {
            theme: { extend: { colors: { utama:'#0F4C81', sekunder:'#165DFF', aksen:'#F59E0B', gelap:'#1E293B' }}}
        }
    </script>
    <style>
        .kontenTengah{display:grid;place-items:center;}
        .transisi{transition:all 0.3s ease;}
        .bgGradien{background:linear-gradient(135deg,#0F4C81,#165DFF);}
    </style>
</head>
<body class="bg-slate-50 font-sans min-h-screen">
    <div class="container mx-auto px-4 py-6 max-w-4xl">
        <header class="text-center mb-8">
            <h1 class="text-2xl font-bold text-utama">📚 Sistem Latihan Ujian SD</h1>
            <div class="mt-2">
                <a href="#halaman‑ujian" class="text-sm text-blue-600 hover:underline mr-4">Latihan</a>
                <a href="#halaman‑nilai" class="text-sm text-blue-600 hover:underline">Riwayat Nilai</a>
            </div>
        </header>

        <!-- HALAMAN UJIAN -->
        <section id="halaman‑ujian" class="bg-white rounded-xl shadow p-6 mb-10">
            <div class="mb-4 p-2 bg-amber-50 border border-amber-200 rounded text-sm text-amber-800">
                ⚠️ Hanya untuk latihan pribadi, bukan soal resmi.
            </div>

            <div id="bagianPilihan">
                <h2 class="text-xl font-semibold mb-4">Pengaturan</h2>
                <div class="grid md:grid-cols-3 gap-4 mb-4">
                    <div>
                        <label class="block mb-1 text-sm">Kelas</label>
                        <select id="pilihKelas" class="w-full border rounded p-2">
                            <option value="">-- Pilih --</option>
                            <option>1</option><option>2</option><option>3</option><option>4</option><option>5</option><option>6</option>
                        </select>
                    </div>
                    <div>
                        <label class="block mb-1 text-sm">Tingkat</label>
                        <select id="pilihTingkat" class="w-full border rounded p-2">
                            <option value="">-- Pilih --</option>
                            <option value="mudah">Mudah</option><option value="biasa">Normal</option><option value="susah">Susah</option>
                        </select>
                    </div>
                    <div>
                        <label class="block mb-1 text-sm">Mapel</label>
                        <select id="pilihMapel" class="w-full border rounded p-2">
                            <option value="">-- Pilih --</option>
                            <option value="mtk">Matematika</option>
                            <option value="bindo">B. Indonesia</option>
                            <option value="ipa">IPA</option>
                            <option value="ips">IPS</option>
                            <option value="binggris">B. Inggris</option>
                        </select>
                    </div>
                </div>
                <button onclick="lanjutAkun()" class="w-full bgGradien text-white py-2 rounded">Lanjutkan</button>
            </div>

            <div id="bagianAkun" class="hidden">
                <h2 class="text-xl font-semibold mb-4">Masuk / Daftar</h2>
                <div class="grid md:grid-cols-2 gap-6">
                    <div>
                        <h3 class="font-medium mb-2">Sudah Punya Akun</h3>
                        <input type="text" id="userMasuk" placeholder="Nama" class="w-full border rounded p-2 mb-2">
                        <input type="password" id="passMasuk" placeholder="Sandi" class="w-full border rounded p-2 mb-2">
                        <button onclick="prosesMasuk()" class="w-full bg-sekunder text-white py-2 rounded">Masuk</button>
                    </div>
                    <div>
                        <h3 class="font-medium mb-2">Buat Akun Baru</h3>
                        <p class="text-xs mb-2">Kode: <b>BELAJAR‑2026</b></p>
                        <input type="text" id="userBaru" placeholder="Nama baru" class="w-full border rounded p-2 mb-2">
                        <input type="password" id="passBaru" placeholder="Sandi baru" class="w-full border rounded p-2 mb-2">
                        <input type="text" id="kodeAkses" placeholder="Kode" class="w-full border rounded p-2 mb-2">
                        <button onclick="prosesDaftar()" class="w-full bg-aksen text-white py-2 rounded">Buat</button>
                    </div>
                </div>
                <div class="mt-4 text-center">
                    <button onclick="kembaliPilihan()" class="text-sm text-slate-500">&larr; Kembali</button>
                </div>
            </div>

            <div id="bagianUjian" class="hidden">
                <h2 class="text-xl font-semibold mb-4">Soal Latihan</h2>
                <div id="wadahSoal" class="space-y-4 mb-4"></div>
                <button onclick="selesaikanUjian()" class="w-full bg-utama text-white py-2 rounded">✅ Selesai</button>
            </div>

            <div id="bagianSelesai" class="hidden text-center py-6">
                <div class="text-4xl text-green-600 mb-2"><i class="fa fa-check-circle"></i></div>
                <h2 class="text-xl font-bold mb-2">Selesai! Nilai tersimpan.</h2>
                <a href="#halaman‑nilai" class="text-blue-600 hover:underline">Lihat Riwayat Nilai</a>
            </div>
        </section>


        <!-- HALAMAN NILAI DALAM SATU BERKAS -->
        <section id="halaman‑nilai" class="bg-white rounded-xl shadow p-6">
            <h2 class="text-xl font-semibold mb-4">📋 Riwayat Hasil</h2>
            <div id="daftarNilai"></div>
            <button onclick="hapusSemua()" class="mt-4 w-full bg-red-50 text-red-600 border border-red-200 py-2 rounded hover:bg-red-100">🗑️ Hapus Semua</button>
        </section>
    </div>


    <script>
        function ambilData(k){return JSON.parse(localStorage.getItem(k)||'[]');}
        function simpanData(k,v){localStorage.setItem(k,JSON.stringify(v));}
        let akunSaatIni=null, pengaturan={};

        const bankSoal={
            mtk:[
                {t:"7 × 6 = ?",j:"42",o:["36","42","48","54"]},
                {t:"25 + 17 = ?",j:"42",o:["32","40","42","52"]},
                {t:"Kelipatan 3 adalah?",j:"12",o:["10","12","14","16"]},
                {t:"½ = ... %",j:"50%",o:["25%","40%","50%","75%"]},
                {t:"Keliling p=10 l=5?",j:"30",o:["15","30","50","100"]},
                {t:"81 ÷ 9 = ?",j:"9",o:["7","8","9","11"]},
                {t:"Pecahan senilai ⅔?",j:"4/6",o:["1/3","4/6","3/4","5/8"]},
                {t:"Sudut siku‑siku = ?",j:"90 derajat",o:["45 derajat","60 derajat","90 derajat","180 derajat"]},
                {t:"Faktor dari 12?",j:"1,2,3,4,6,12",o:["1,2,3,5","1,2,3,4,6,12","2,3,4,6","3,4,6,12"]},
                {t:"0,5 + 0,25 = ?",j:"0,75",o:["0,30","0,55","0,75","1,00"]},
                {t:"Luas sisi 8 cm?",j:"64 cm²",o:["16 cm²","32 cm²","64 cm²","128 cm²"]},
                {t:"KPK 4 & 6 = ?",j:"12",o:["8","12","16","24"]},
                {t:"Bilangan prima 1‑10:",j:"2,3,5,7",o:["1,3,5,7","2,3,5,7","2,4,6,8","3,5,7,9"]},
                {t:"20% dari 150 = ?",j:"30",o:["20","25","30","45"]},
                {t:"07.30 + 45 menit = ?",j:"08.15",o:["07.45","08.00","08.15","08.20"]},
                {t:"Sisi segitiga = ?",j:"3",o:["2","3","4","5"]},
                {t:"⅕ + ⅖ = ?",j:"3/5",o:["2/5","3/5","4/5","5/5"]},
                {t:"3.000 gram = ... kg",j:"3 kg",o:["0,3 kg","3 kg","30 kg","300 kg"]},
                {t:"FPB 12 & 18 = ?",j:"6",o:["3","6","9","12"]},
                {t:"Urut naik:12,5,19,9",j:"5,9,12,19",o:["19,12,9,5","5,9,12,19","9,5,12,19","5,12,9,19"]}
            ],
            bindo:[
                {t:"Ejaan benar?",j:"belajar",o:["blajar","belajar","belajarr","belaar"]},
                {t:"Baku dari 'nggak'?",j:"tidak",o:["bukan","tak","tidak","enggak"]},
                {t:"Awal kalimat pakai?",j:"huruf besar",o:["huruf kecil","huruf besar","angka","simbol"]},
                {t:"Kata kerja: Ayah membaca koran?",j:"membaca",o:["Ayah","sedang","membaca","koran"]},
                {t:"Tanda untuk pertanyaan?",j:"tanda tanya",o:["titik","koma","tanda tanya","seru"]},
                {t:"Sinonim pintar?",j:"cerdas",o:["rajin","cerdas","sombong","malas"]},
                {t:"Lawan bersih?",j:"kotor",o:["rapi","kotor","kusam","berdebu"]},
                {t:"Subjek: Kami berangkat sekolah?",j:"Kami",o:["berangkat","sekolah","pagi ini","Kami"]},
                {t:"Kalimat baku benar?",j:"Saya sedang makan nasi",o:["Aku lagi makan","Saya sedang makan nasi","Saya makan ni","Saya lagi makan nasi"]},
                {t:"Huruf kapital untuk?",j:"nama orang/tempat",o:["semua kata","awal nama orang/tempat","kata kerja","kata benda"]},
                {t:"Turunan dari 'ajar'?",j:"pengajaran",o:["ajarannya","pengajaran","diajar","ajar‑ajar"]},
                {t:"Tanya yang tepat?",j:"Kapan kamu pulang?",o:["Kamu pulang kapan","Kapan kamu pulang?","Pulang kamu kapan?","Kapan pulang kamu"]},
                {t:"Fungsi tanda koma?",j:"memisah bagian kalimat",o:["akhir kalimat","memisah bagian kalimat","menutup daftar","menandai seruan"]},
                {t:"Kata penghubung?",j:"dan",o:["buku","dan","berlari","indah"]},
                {t:"Penulisan nama benar?",j:"Budi Santoso",o:["budi santoso","Budi santoso","Budi Santoso","budi Santoso"]},
                {t:"Keterangan tempat: Adik main bola di halaman?",j:"di halaman",o:["Adik","bermain bola","di halaman","halaman"]},
                {t:"Kata sifat: Cuaca cerah?",j:"cerah",o:["hari","cuaca","sangat","cerah"]},
                {t:"Bukan kata baku?",j:"foto",o:["fotokopi","foto","telepon","kantor"]},
                {t:"Paragraf diawali?",j:"dengan menjorok ke dalam",o:["huruf kecil","dengan menjorok ke dalam","tanpa spasi","dengan angka"]},
                {t:"Kalimat perintah?",j:"Tutuplah pintu itu!",o:["Pintu itu ditutup","Tutuplah pintu itu!","Apakah pintu tertutup?","Pintu sudah tertutup"]}
            ],
            ipa:[
                {t:"Alat napas utama manusia?",j:"paru‑paru",o:["jantung","lambung","paru‑paru","ginjal"]},
                {t:"Tumbuhan buat makan lewat?",j:"fotosintesis",o:["respirasi","fotosintesis","penyerapan","penguapan"]},
                {t:"Sumber energi utama bumi?",j:"matahari",o:["api","matahari","batu bara","air"]},
                {t:"Bagian serap air?",j:"akar",o:["daun","batang","akar","bunga"]},
                {t:"Air jadi uap disebut?",j:"penguapan",o:["pengembunan","pembekuan","penguapan","pengendapan"]},
                {t:"Pemakan tumbuhan disebut?",j:"pemakan tumbuhan",o:["pemakan daging","pemakan tumbuhan","pemakan segala","pengurai"]},
                {t:"Jantung memompa?",j:"darah",o:["udara","sari makanan","darah","air"]},
                {t:"Benda tembus cahaya?",j:"bening",o:["gelap","berwarna","bening","padat"]},
                {t:"Siklus air mulai dari?",j:"penguapan laut/sungai",o:["hujan","penguapan laut/sungai","aliran air","embun"]},
                {t:"Batu/tanah/pasir benda?",j:"padat",o:["cair","gas","padat","berat"]},
                {t:"Hewan bertelur?",j:"ayam",o:["kucing","sapi","ayam","kambing"]},
                {t:"Zat penting dari makanan?",j:"gizi/nutrisi",o:["warna","gizi/nutrisi","bau","rasa"]},
                {t:"Penyebab siang‑malam?",j:"bumi berputar sendiri",o:["matahari bergerak","bumi berputar sendiri","bulan mengelilingi bumi","angin"]},
                {t:"Fungsi bakteri pengurai?",j:"menguraikan sisa makhluk hidup",o:["membuat sakit","menguraikan sisa makhluk hidup","menghasilkan oksigen","menyerap air"]},
                {t:"Air bersih cirinya?",j:"jernih dan tidak berbau",o:["berwarna","berbau","jernih dan tidak berbau","berasa tawar saja"]},
                {t:"Alat pendengar?",j:"telinga",o:["mata","hidung","telinga","kulit"]},
                {t:"Air beku jadi?",j:"es padat",o:["uap","es padat","embun","kabut"]},
                {t:"Sinar matahari bantu tumbuhan hasilkan?",j:"makanan & oksigen",o:["hanya air","makanan & oksigen","hanya bayangan","hanya akar"]},
                {t:"Satuan suhu umum?",j:"derajat Celcius",o:["meter","derajat Celcius","detik","gram"]},
                {t:"Rantai makanan mulai dari?",j:"tumbuhan",o:["hewan","tumbuhan","pengurai","tanah"]}
            ],
            ips:[
                {t:"Tempat tinggal kelompok?",j:"lingkungan/pemukiman",o:["hutan","lingkungan/pemukiman","sungai","gunung"]},
                {t:"Ibu kota RI?",j:"Jakarta",o:["Bandung","Surabaya","Jakarta","Semarang"]},
                {t:"Peta untuk?",j:"letak tempat",o:["cuaca","letak tempat","musim","waktu"]},
                {t:"Sungai/danau/laut = bentang?",j:"perairan",o:["daratan","perairan","pegunungan","dataran"]},
                {t:"Kerja sama bikin?",j:"persatuan",o:["perpecahan","persaingan","persatuan","kekayaan"]},
                {t:"Pekerjaan di pantai?",j:"nelayan",o:["petani","nelayan","tukang kayu","pedagang"]},
                {t:"Warna bendera RI?",j:"merah putih",o:["merah kuning","putih biru","merah putih","kuning hijau"]},
                {t:"Gunung meletus bawa manfaat?",j:"tanah jadi subur",o:["tanah jadi subur","sungai penuh","udara bersih","tanaman mati"]},
                {t:"Sikap baik bergaul?",j:"saling menghargai",o:["saling mengejek","saling menghargai","saling memaksa","saling bersaing"]},
                {t:"Jumlah arah utama?",j:"4",o:["2","3","4","8"]},
                {t:"Contoh hasil tani?",j:"padi dan jagung",o:["ikan udang","batu pasir","padi dan jagung","kain baju"]},
                {t:"17 Agustus memperingati?",j:"Kemerdekaan RI",o:["Hari Pendidikan","Hari Kemerdekaan RI","Hari Bumi","Hari Guru"]},
                {t:"Masyarakat dataran tinggi umumnya?",j:"bertani sayur/buah",o:["berlayar","bertani sayur/buah","berdagang laut","menambang"]},
                {t:"Garis batas antarnegara darat?",j:"garis batas darat",o:["garis pantai","garis batas darat","garis khatulistiwa","garis waktu"]},
                {t:"Pemimpin desa/kelurahan?",j:"kepala desa/lurah",o:["gubernur","bupati","kepala desa/lurah","camat"]},
                {t:"Alat buatan manusia disebut?",j:"benda budaya/teknologi",o:["benda alam","benda budaya/teknologi","benda cair","benda padat"]},
                {t:"Indonesia di benua?",j:"Asia",o:["Afrika","Asia","Eropa","Australia"]},
                {t:"Musim di Indonesia ada?",j:"hujan dan kemarau",o:["dingin‑panas","hujan‑kemarau","gugur‑semi","angin‑badai"]},
                {t:"SDA bisa habis contoh?",j:"minyak bumi/batu bara",o:["air angin","minyak bumi/batu bara","cahaya matahari","ombak"]},
                {t:"Sikap bertamu?",j:"sopan dan tepat waktu",o:["sopan dan tepat waktu","terlambat berisik","mengambil barang sembarangan","berbicara keras"]}
            ],
            binggris:[
                {t:"'kucing' Inggris?",j:"cat",o:["dog","cat","bird","fish"]},
                {t:"'satu' Inggris?",j:"one",o:["two","one","three","four"]},
                {t:"'merah' Inggris?",j:"red",o:["blue","green","red","yellow"]},
                {t:"I ... a student",j:"am",o:["is","are","am","have"]},
                {t:"'Minggu' Inggris?",j:"Sunday",o:["Monday","Sunday","Friday","Tuesday"]},
                {t:"Terima kasih = ?",j:"Thank you",o:["Hello","Goodbye","Thank you","Sorry"]},
                {t:"'buku' Inggris?",j:"book",o:["pen","pencil","book","bag"]},
                {t:"'dia laki‑laki' = ?",j:"he",o:["she","he","it","we"]},
                {t:"... apple",j:"an",o:["a","an","the","‑"]},
                {t:"'makan' Inggris?",j:"eat",o:["drink","eat","run","read"]},
                {t:"'sepuluh' Inggris?",j:"ten",o:["eight","nine","ten","eleven"]},
                {t:"Tanya tempat pakai?",j:"Where",o:["When","Where","Who","What"]},
                {t:"Lawan 'besar' = ?",j:"small",o:["big","small","long","short"]},
                {t:"We ... football",j:"play",o:["plays","play","playing","played"]},
                {t:"'mata' Inggris?",j:"eye",o:["ear","nose","eye","hand"]},
                {t:"'panas/musim' Inggris?",j:"summer",o:["winter","autumn","summer","spring"]},
                {t:"'di atas meja' = ... the table",j:"on",o:["in","on","under","between"]},
                {t:"'dan' Inggris?",j:"and",o:["but","or","and","so"]},
                {t:"'kakak perempuan' Inggris?",j:"sister",o:["brother","sister","father","mother"]},
                {t:"Selamat pagi = Good ...",j:"morning",o:["night","afternoon","morning","evening"]}
            ]
        };

        function acakArray(a){return [...a].sort(()=>Math.random()-0.5);}
        function lanjutAkun(){
            const k=document.getElementById('pilihKelas').value,t=document.getElementById('pilihTingkat').value,m=document.getElementById('pilihMapel').value;
            if(!k||!t||!m)return alert("Lengkapi semua pilihan!");
            pengaturan={kelas:k,tingkat:t,mapel:m};
            document.getElementById('bagianPilihan').classList.add('hidden');
            document.getElementById('bagianAkun').classList.remove('hidden');
        }
        function kembaliPilihan(){
            document.getElementById('bagianAkun').classList.add('hidden');
            document.getElementById('bagianPilihan').classList.remove('hidden');
        }
        function prosesDaftar(){
            const u=document.getElementById('userBaru').value.trim(),p=document.getElementById('passBaru').value.trim(),kd=document.getElementById('kodeAkses').value.trim();
            if(kd!=="BELAJAR‑2026")return alert("Kode salah!");if(!u||!p)return alert("Isi nama & sandi!");
            let d=ambilData('akunSiswa');if(d.find(x=>x.user===u))return alert("Sudah dipakai!");
            d.push({user:u,sandi:p});simpanData('akunSiswa',d);akunSaatIni=u;alert("Sukses!");mulaiUjian();
        }
        function prosesMasuk(){
            const u=document.getElementById('userMasuk').value.trim(),p=document.getElementById('passMasuk').value.trim(),d=ambilData('akunSiswa'),x=d.find(i=>i.user===u&&i.sandi===p);
            if(!x)return alert("Salah atau belum ada!");akunSaatIni=u;mulaiUjian();
        }
        function mulaiUjian(){
            document.getElementById('bagianAkun').classList.add('hidden');
            document.getElementById('bagianUjian').classList.remove('hidden');
            tampilkanSoal();
        }
        function tampilkanSoal(){
            const w=document.getElementById('wadahSoal');w.innerHTML="";
            let d=acakArray(bankSoal[pengaturan.mapel]).slice(0,20);
            d.forEach((s,i)=>{
                const o=acakArray(s.o),b=document.createElement("div");
                b.className="p-3 bg-slate‑50 border rounded";
                b.innerHTML=`<p class="font-medium mb-2">${i+1}. ${s.t}</p><div class="space‑y‑1 text-sm">${o.map((opt,idx)=>`<label class="flex items‑center gap‑2"><input type="radio" name="soal${i}" value="${opt===s.j?'benar':'salah'}">${String.fromCharCode(65+idx)}. ${opt}</label>`).join('')}</div>`;
                w.appendChild(b);
            });
        }
        function selesaikanUjian(){
            let b=0;document.querySelectorAll('[name^="soal"]').forEach(g=>{const p=document.querySelector(`[name="${g.name}"]:checked`);if(p&&p.value==="benar")b++;});
            const n=Math.round((b/20)*100);let c=ambilData('catatanNilai');
            c.push({nama:akunSaatIni,waktu:new Date().toLocaleString('id‑ID'),kelas:pengaturan.kelas,mapel:pengaturan.mapel.toUpperCase(),tingkat:pengaturan.tingkat,nilai:n});
            simpanData('catatanNilai',c);
            document.getElementById('bagianUjian').classList.add('hidden');
            document.getElementById('bagianSelesai').classList.remove('hidden');
        }
        function tampilNilai(){
            const w=document.getElementById('daftarNilai'),d=ambilData('catatanNilai');
            if(!d.length){w.innerHTML=`<p class="text‑center text‑slate‑500 py‑4">Belum ada riwayat.</p>`;return;}
            w.innerHTML=`<div class="space‑y‑2">${d.map(x=>`<div class="p‑3 border rounded ${x.nilai>=75?'bg‑green‑50':'bg‑orange‑50'}"><div class="flex justify‑between font‑medium">${x.mapel} • Kelas ${x.kelas} • ${x.tingkat}<b>${x.nilai}/100</b></div><div class="text‑sm text‑slate‑600">👤 ${x.nama} | 🕒 ${x.waktu}</div></div>`).join('')}</div>`;
        }
        function hapusSemua(){if(confirm("Yakin hapus SEMUA?")){localStorage.removeItem('catatanNilai');tampilNilai();}}
        tampilNilai();
    </script>
</body>
</html>
