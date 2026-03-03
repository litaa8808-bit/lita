CREATE DATABASE rs_sehat;

USE rs_sehat;

CREATE TABLE booking (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nama VARCHAR(100),
    tanggal DATE,
    dokter VARCHAR(100),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);<?php include 'koneksi.php'; ?>
<!DOCTYPE html>
<html>
<head>
    <title>RS Sehat Sentosa</title>
    <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-blue-50">

<div class="container mx-auto p-10">
    <h1 class="text-3xl font-bold mb-6">Booking Rumah Sakit</h1>

    <form action="proses_booking.php" method="POST" class="bg-white p-6 rounded shadow-md">
        <input type="text" name="nama" placeholder="Nama" required
            class="w-full mb-4 p-2 border rounded">

        <input type="date" name="tanggal" required
            class="w-full mb-4 p-2 border rounded">

        <select name="dokter" required
            class="w-full mb-4 p-2 border rounded">
            <option value="">Pilih Dokter</option>
            <option>Dr. Andi - Umum</option>
            <option>Dr. Sinta - Anak</option>
            <option>Dr. Budi - Penyakit Dalam</option>
        </select>

        <button type="submit"
            class="bg-blue-700 text-white px-6 py-2 rounded">
            Booking
        </button>
    </form>

    <hr class="my-8">

    <h2 class="text-xl font-bold mb-4">Data Booking</h2>

    <table class="w-full bg-white shadow">
        <tr class="bg-blue-700 text-white">
            <th class="p-2">Nama</th>
            <th class="p-2">Tanggal</th>
            <th class="p-2">Dokter</th>
        </tr>

        <?php
        $result = mysqli_query($conn, "SELECT * FROM booking ORDER BY id DESC");
        while($row = mysqli_fetch_assoc($result)) {
        ?>
        <tr class="text-center border">
            <td class="p-2"><?php echo $row['nama']; ?></td>
            <td class="p-2"><?php echo $row['tanggal']; ?></td>
            <td class="p-2"><?php echo $row['dokter']; ?></td>
        </tr>
        <?php } ?>
    </table>

</div>

</body>
</html>
