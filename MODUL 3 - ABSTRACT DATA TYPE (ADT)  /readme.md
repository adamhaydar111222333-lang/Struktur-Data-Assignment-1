# <h1 align="center">Laporan Praktikum Modul Pengenalan Bahasa C++ (1)</h1>
<p align="center">Adam Haydar</p>

## Dasar Teori

ADT adalah TYPE dan sekumpulan PRIMITIF (operasi dasar) terhadap TYPE tersebut. Selain itu, dalam 
sebuah ADT yang lengkap, disertakan pula definisi invarian dari TYPE dan aksioma yang berlaku. ADT 
merupakan definisi STATIK. 

## Guided 

### 1. ABSTRACT DATA TYPE (ADT) 

```C++
#include <iostream>
using namespace std;

struct mahasiswa{ 
char nim[10]; 
int nilai1,nilai2;
};
void inputMhs(mahasiswa &m); 
float rata2(mahasiswa m);

int main() 
{ 
mahasiswa mhs; 
inputMhs(mhs); 
cout << “rata-rata = “ << rata2(mhs); 
return 0; 
}


void inputMhs(mahasiswa &m){ 
cout << “input nama = “; 
cin >> m.nim; 
cout << “input nilai = “; 
cin >> m.nilai1; 
cout << “input nilai2 = “;
cin >> m.nilai2; 
} 
float rata2(mahasiswa m){ 
return float(m.nilai1+m.nilai2)/2; 
}

mahasiswa.h
#ifndef MAHASISWA_H_INCLUDED 
#define MAHASISWA_H_INCLUDED 
struct mahasiswa{ 
char nim[10]; 
int nilai1, nilai2; 
};
void inputMhs(mahasiswa &m); 
float rata2(mahasiswa m); 
#endif // MAHASISWA_H_INCLUDED

mahasiswa.cpp
#include “mahasiswa.h” 
void inputMhs(mahasiswa &m){ 
cout << “input nama = “; 
cin >> (m).nim; 
cout << “input nilai = “; 
cin >> (m).nilai1; 
cout << “input nilai2 = “; 
cin >> (m).nilai2;
} 
 
float rata2(mahasiswa m){ 
  return float(m.nilai1+m.nilai2)/2; 
}
}
```
Kode di atas digunakan untuk memasukkan data mahasiswa dan menghitung rata-rata dua nilai yang diinput.

## Unguided 

### 1. [Soal]
```C++
#include <iostream>
using namespace std;

struct Mahasiswa {
    string nama;
    string nim;
    float uts, uas, tugas, nilaiAkhir;
};

float hitungNilaiAkhir(float uts, float uas, float tugas) {
    return 0.3 * uts + 0.4 * uas + 0.3 * tugas;
}

int main() {
    Mahasiswa mhs[10];
    int n;

    cout << "Masukkan jumlah mahasiswa (maks 10): ";
    cin >> n;

    for (int i = 0; i < n; i++) {
        cout << "\nData mahasiswa ke-" << i + 1 << endl;
        cin.ignore();
        cout << "Nama  : ";
        getline(cin, mhs[i].nama);
        cout << "NIM   : ";
        cin >> mhs[i].nim;
        cout << "UTS   : ";
        cin >> mhs[i].uts;
        cout << "UAS   : ";
        cin >> mhs[i].uas;
        cout << "Tugas : ";
        cin >> mhs[i].tugas;

        mhs[i].nilaiAkhir = hitungNilaiAkhir(mhs[i].uts, mhs[i].uas, mhs[i].tugas);
    }

    cout << "\n=== Daftar Nilai Mahasiswa ===\n";
    for (int i = 0; i < n; i++) {
        cout << "\nNama        : " << mhs[i].nama;
        cout << "\nNIM         : " << mhs[i].nim;
        cout << "\nNilai Akhir : " << mhs[i].nilaiAkhir << endl;
    }

    return 0;
}
```
#### Output:
<img width="497" height="938" alt="Image" src="https://github.com/user-attachments/assets/211738cf-215f-4efb-a2e0-54a8615fbc72" />

Kode di atas digunakan untuk menyimpan dan menampilkan data mahasiswa sebanyak maksimal 10 orang.
Program ini menggunakan struct Mahasiswa untuk menyimpan data seperti nama, NIM, nilai UTS, UAS, dan tugas.

#### Full code Screenshot:
<img width="757" height="943" alt="Image" src="https://github.com/user-attachments/assets/8098dd23-b43f-4b05-9c30-66576bb7e8ad" />

### 2. [Soal]

```C++
#include <iostream>
using namespace std;

struct pelajaran {
    string namaMapel;
    string kodeMapel;
};

pelajaran create_pelajaran(string nama, string kode) {
    pelajaran p;
    p.namaMapel = nama;
    p.kodeMapel = kode;
    return p;
}

void tampil_pelajaran(pelajaran pel) {
    cout << "nama pelajaran : " << pel.namaMapel << endl;
    cout << "nilai : " << pel.kodeMapel << endl;
}

int main() {
    string namapel = "Struktur Data";
    string kodepel = "STD";

    pelajaran pel = create_pelajaran(namapel, kodepel);
    tampil_pelajaran(pel);

    return 0;
}
```
#### Output:
<img width="834" height="682" alt="Image" src="https://github.com/user-attachments/assets/55b39664-1c77-4454-b5f2-89fc182b5e44" />

Kode di atas digunakan untuk menampilkan isi dua array, menukar salah satu elemen antar array, dan menukar nilai dua variabel melalui pointer, lalu hasilnya dicetak ke layar menggunakan cout untuk mengeksekusinya.

#### Full code Screenshot:
<img width="783" height="898" alt="Image" src="https://github.com/user-attachments/assets/025840d9-3476-43d2-b047-2846143abb5d" />

### 3. [Soal]

```C++
#include <iostream>
using namespace std;

int main() {
    int A[3][3] = {{1,2,3},{4,5,6},{7,8,9}};
    int B[3][3] = {{9,8,7},{6,5,4},{3,2,1}};
    int *p1, *p2;
    int x = 10, y = 20;
    p1 = &x;
    p2 = &y;

    cout << "Array A:" << endl;
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            cout << A[i][j] << " ";
        }
        cout << endl;
    }

    cout << "\nArray B:" << endl;
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            cout << B[i][j] << " ";
        }
        cout << endl;
    }

    int temp = A[1][1];
    A[1][1] = B[1][1];
    B[1][1] = temp;

    cout << "\nSetelah elemen [1][1] ditukar:" << endl;
    cout << "Array A:" << endl;
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            cout << A[i][j] << " ";
        }
        cout << endl;
    }

    cout << "\nArray B:" << endl;
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            cout << B[i][j] << " ";
        }
        cout << endl;
    }

    cout << "\nSebelum tukar pointer: x = " << x << ", y = " << y << endl;
    int temp2 = *p1;
    *p1 = *p2;
    *p2 = temp2;
    cout << "Sesudah tukar pointer: x = " << x << ", y = " << y << endl;

    return 0;
}

```
#### Output:
![240302_00h00m06s_screenshot](https://github.com/suxeno/Struktur-Data-Assignment/assets/111122086/6d1727a8-fb77-4ecf-81ff-5de9386686b7)

Kode di atas digunakan untuk mencetak teks "ini adalah file code guided praktikan" ke layar menggunakan function cout untuk mengeksekusi nya.

#### Full code Screenshot:
<img width="401" height="1076" alt="Image" src="https://github.com/user-attachments/assets/827e646b-4b5e-4b82-ab82-78e18a13c269" />


## Kesimpulan
Ringkasan dan interpretasi pandangan kalia dari hasil praktikum dan pembelajaran yang didapat[1].

## Referensi
[1] I. Holm, Narrator, and J. Fullerton-Smith, Producer, How to Build a Human [DVD]. London: BBC; 2002.
