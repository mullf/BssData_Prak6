# praktikum-basis-data-8
```
1. Tampilkan data karyawan yang bekerja pada departemen yang sama dengan karyawan yang bernama Dika
2. Tampilkan data karyawan yang gajinya lebih besar dari rata-rata gaji semua  karyawan. urutkan menurun berdasarkan besaran gaji
3. Tampilkan nik dan nama karyawan untuk semua karyawan yang bekerja di  department yang sama dengan karyawan dengan nama yang mengandung  huruf 'K'.
4. Tampilkan data karyawan yang bekerja pada departemen yang ada di  kantor pusat.
5 Tampilkan nik dan nama karyawan untuk semua karyawan yang bekerja di department yang sama dengan karyawan dengan nama yang mengandung huruf 'K'
dan yang gajinya lebih besar dari rata-rata gaji semua karyawan
```

1. Tampilkan data karyawan yang bekerja pada departemen yang sama dengan karyawan yang bernama Dika
```
SELECT 
kr.nik,
kr.nama,
kr.id_departemen
from karyawan kr
WHERE id_departemen = (SELECT id_departemen FROM karyawan WHERE nama = 'dika');
```

<img width="481" alt="p8_1" src="https://github.com/DimasF3009/praktikum-basis-data-8/assets/115356128/12c9605d-4395-485b-adc9-00b153f8b165">


2. Tampilkan data karyawan yang gajinya lebih besar dari rata-rata gaji semua  karyawan. urutkan menurun berdasarkan besaran gaji
```
SELECT 
kr.nik,
kr.nama,
kr.gaji_pokok
from karyawan kr
WHERE gaji_pokok > (SELECT avg(gaji_pokok) FROM karyawan );
```

<img width="370" alt="p8_2" src="https://github.com/DimasF3009/praktikum-basis-data-8/assets/115356128/08b3c825-6d72-4634-8a23-9224ea197348">


3. Tampilkan nik dan nama karyawan untuk semua karyawan yang bekerja di  department yang sama dengan karyawan dengan nama yang mengandung  huruf 'K'.
```
SELECT 
kr.nik,
kr.nama,
kr.id_departemen
from karyawan kr
WHERE id_departemen in (SELECT id_departemen FROM karyawan WHERE nama LIKE '%K%');
```

<img width="493" alt="p8_3" src="https://github.com/DimasF3009/praktikum-basis-data-8/assets/115356128/c0abf2b8-43a7-4add-a4e5-c7ff97965afc">


4. Tampilkan data karyawan yang bekerja pada departemen yang ada di  kantor pusat.
```
SELECT 
d.id_perusahaan,
kr.nik,
kr.nama,
kr.id_departemen
from karyawan kr
LEFT JOIN departemen d on d.id_departemen = kr.id_departemen
WHERE id_perusahaan = 'p01';
```

<img width="381" alt="p8_4" src="https://github.com/DimasF3009/praktikum-basis-data-8/assets/115356128/22eb6870-bf03-40fd-a858-9e7c713e6a3b">


5 Tampilkan nik dan nama karyawan untuk semua karyawan yang bekerja di department yang sama dengan karyawan dengan nama yang mengandung huruf 'K'
dan yang gajinya lebih besar dari rata-rata gaji semua karyawan
```
SELECT 
kr.nik,
kr.nama,
kr.id_departemen,
kr.gaji_pokok
from karyawan kr
WHERE gaji_pokok > (SELECT avg(gaji_pokok) from karyawan) AND nama LIKE '%K%';
```

<img width="479" alt="p8_5" src="https://github.com/DimasF3009/praktikum-basis-data-8/assets/115356128/db02ec4f-e674-43a4-8cdc-342ccf33eed7">
