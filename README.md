# README - Praktikum Pemrograman Basis Data

Laporan ini mendokumentasikan implementasi struktur percabangan pada MySQL untuk sistem penilaian mahasiswa.

## Profil Mahasiswa
- **Nama**: Suharnina Aksan
- **NIM**: IK2411001
- **Program Studi**: Informatika
- **Tahun Akademik**: 2025/2026

## Deskripsi Tugas
Membuat *stored procedure* `cek_predikat_mahasiswa` yang secara otomatis menentukan predikat dan status kelulusan berdasarkan nilai input tanpa menggunakan tabel database tambahan.

## Aturan Logika
1. **Predikat**:
   - ≥ 90: Sangat Memuaskan
   - ≥ 80: Memuaskan
   - ≥ 70: Baik
   - ≥ 60: Cukup
   - < 60: Kurang
2. **Status Kelulusan**:
   - ≥ 70: Lulus
   - < 70: Tidak Lulus

## Kode SQL Singkat
```sql
CREATE PROCEDURE cek_predikat_mahasiswa (IN p_nilai INT)
BEGIN
    DECLARE v_predikat VARCHAR(50);
    DECLARE v_status VARCHAR(20);

    -- Logika IF-THEN-ELSE
    IF p_nilai >= 90 THEN SET v_predikat = 'Sangat Memuaskan';
    ELSEIF p_nilai >= 80 THEN SET v_predikat = 'Memuaskan';
    ELSEIF p_nilai >= 70 THEN SET v_predikat = 'Baik';
    ELSEIF p_nilai >= 60 THEN SET v_predikat = 'Cukup';
    ELSE SET v_predikat = 'Kurang';
    END IF;

    IF p_nilai >= 70 THEN SET v_status = 'Lulus';
    ELSE SET v_status = 'Tidak Lulus';
    END IF;

    SELECT p_nilai AS nilai, v_predikat AS predikat, v_status AS status;
END;
Kesimpulan
Prosedur berhasil dijalankan dan diuji dengan nilai 91 (Sangat Memuaskan/Lulus) serta nilai 66 (Cukup/Tidak Lulus). Implementasi ini terbukti akurat dan efisien dalam mengolah data nilai mahasiswa.
