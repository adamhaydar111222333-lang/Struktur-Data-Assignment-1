# <h1 align="center">ABSTRACT DATA TYPE (ADT)</h1>
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

**pelajaran.h**
```C++
#ifndef PELAJARAN_H
#define PELAJARAN_H

#include <string>
using namespace std;

struct Pelajaran {
    string namaMapel;
    string kodeMapel;
};

Pelajaran createPelajaran(string nama, string kode);

void tampilPelajaran(Pelajaran p);

#endif
}
```

**pelajaran.cpp**
```C++
#include <iostream>
#include "pelajaran.h"
using namespace std;

Pelajaran createPelajaran(string nama, string kode) {
    Pelajaran p;
    p.namaMapel = nama;
    p.kodeMapel = kode;
    return p;
}

void tampilPelajaran(Pelajaran p) {
    cout << "nama pelajaran : " << p.namaMapel << endl;
    cout << "nilai : " << p.kodeMapel << endl;
}
```

**main.cpp**
```C++
#include <iostream>
#include "pelajaran.h"
using namespace std;

int main() {
    string nama = "Struktur Data";
    string kode = "STD";

    Pelajaran pel = createPelajaran(nama, kode);

    tampilPelajaran(pel);

    return 0;
}
```
#### Output:
<img width="986" height="274" alt="Image" src="https://github.com/user-attachments/assets/afdd8fc8-554f-4fce-b851-faacb6acbfe6" />

Kode di atas digunakan untuk membuat dan menampilkan data pelajaran. Program ini menyimpan nama dan kode mata pelajaran menggunakan struktur Pelajaran, lalu menampilkan hasilnya ke layar melalui fungsi tampilPelajaran().

#### Full code Screenshot:
<img width="783" height="898" alt="Image" src="https://github.com/user-attachments/assets/025840d9-3476-43d2-b047-2846143abb5d" />

### 3. [Soal]

```C++
#include <iostream>
using namespace std;

int main() {
    int A[3][3] = {{1,2,3},{4,5,6},{7,8,9}};
    int B[3][3] = {{9,8,7},{6,5,4},{3,2,1}};

    cout << "Array A sebelum ditukar:" << endl;
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            cout << A[i][j] << " ";
        }
        cout << endl;
    }

    cout << "\nArray B sebelum ditukar:" << endl;
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            cout << B[i][j] << " ";
        }
        cout << endl;
    }

    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            int temp = A[i][j];
            A[i][j] = B[i][j];
            B[i][j] = temp;
        }
    }

    cout << "\nSetelah menukar seluruh isi array:" << endl;

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

    return 0;
}

```
#### Output:
<img width="872" height="658" alt="Image" src="https://github.com/user-attachments/assets/dc19730e-938f-4c94-baad-edf1eeb01d70" />

Kode di atas berfungsi untuk menampilkan dua array 2 dimensi (A dan B), kemudian menukar seluruh isi dari kedua array tersebut. Setelah proses pertukaran, program menampilkan hasil akhir dari masing-masing array untuk memperlihatkan perubahan nilainya.

#### Full code Screenshot:
<img width="511" height="1055" alt="Image" src="https://github.com/user-attachments/assets/674afa20-5a95-4790-b09c-51f89d403881" />


## Kesimpulan
Kesimpulannya, praktikum ini menunjukkan bahwa bahasa C++ dapat digunakan untuk mengelola data secara terstruktur menggunakan variabel, fungsi, struct, array, dan pointer, serta memisahkan kode program agar lebih rapi dan mudah dipahami.

## Referensi
[1] I. Holm, Narrator, and J. Fullerton-Smith, Producer, How to Build a Human [DVD]. London: BBC; 2002.
