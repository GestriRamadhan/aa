# Koneksi
<?php
$host ="127.0.0.1";
$user ="root";
$pass ="";
$debe ="dbgym";

$db = new mysqli($host,$user,$pass,$debe)or die($db->error);

    function query($query) {
        global $koneksi;
        $result = mysqli_query($koneksi, $query);
        $rows = [];
        while( $row = mysqli_fetch_assoc($result) ) {
            $rows[] = $row;
        }
        return $rows;
    }
//tambahbulanan
$db = new mysqli($host,$user,$pass,$debe)or die($db->error);
function tambahMasuk($dataMasuk) {
        global $koneksi;
        $namalengkap = htmlspecialchars($dataMasuk["nama_member"]);
        $tanggalMasukMember = htmlspecialchars($dataMasuk["tanggal_masuk"]);
        $alamat = htmlspecialchars($dataMasuk["alamat"]);
        $jenisMember = htmlspecialchars($dataMasuk["kls_member"]);

        // query insert data
        $query = "INSERT INTO datamember (nama_member, tanggal_masuk, alamat, kls_member) VALUES NULL ('$namalengkap', '$tanggalMasukMember', '$alamat', '$jenisMember')";
        mysqli_query($koneksi, $query);            
        return mysqli_affected_rows($koneksi);
    }

    //tambahharian
    function tambahKeluar($dataKeluar) {
        global $koneksi;
        $namalengkap = htmlspecialchars($dataMasuk["nama_member"]);
        $tanggalMasukMember = htmlspecialchars($dataMasuk["tanggal_masuk"]);
        $alamat = htmlspecialchars($dataMasuk["alamat"]);
        $jenisMember = htmlspecialchars($dataMasuk["kls_member"]);

        // query insert data
        $query = "INSERT INTO datamemberharian (nama_member, tanggal_masuk, alamat, kls_member) VALUES (NULL, '$namalengkap', '$tanggalMasukMember', '$alamat', '$jenisMember')";
        mysqli_query($koneksi, $query);            
        
        return mysqli_affected_rows($koneksi);
    }

    // tanggal indonesia
    function tgl_indo($tgl) {
        $tanggal = substr($tgl, 8, 2);
        $nama_bulan = array("Jan", "Feb", "Mar", "Apr", "Mei", "Jun", "Jul", "Ags", "Sep", "Okt", "Nov", "Des");
        $bulan = $nama_bulan[substr($tgl, 5, 2) - 1];
        $tahun = substr($tgl, 0, 4);

        return $tanggal.'-'.$bulan.'-'.$tahun;
    }
