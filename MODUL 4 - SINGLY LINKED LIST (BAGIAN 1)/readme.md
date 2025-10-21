# <h1 align="center">SINGLY LINKED LIST (BAGIAN 1)</h1>
<p align="center">Adam Haydarr</p>

## Dasar Teori
Linked list adalah struktur data yang terdiri dari elemen-elemen yang saling terhubung dan bersifat fleksibel karena dapat bertambah atau berkurang sesuai kebutuhan. Data di dalamnya bisa berupa data tunggal (misalnya nama bertipe *string*) atau data majemuk (misalnya data mahasiswa yang berisi nama, NIM, dan alamat dengan tipe data berbeda).


## Guided 

### 1. [Nama Topik]

```C++
#include <iostream>
using namespace std;

int main() {
    cout << "ini adalah file code guided praktikan" << endl;
    return 0;
}
```
Kode di atas digunakan untuk mencetak teks "ini adalah file code guided praktikan" ke layar menggunakan function cout untuk mengeksekusi nya.

## Unguided 

### 1. [Soal]
**Singlylist.h**
```C++
#ifndef SINGLYLIST_H
#define SINGLYLIST_H

#include <iostream>
using namespace std;

typedef int infotype;

struct ElmList {
    infotype info;
    ElmList* next;
};

typedef ElmList* address;

struct List {
    address First;
};

void createList(List &L);
address alokasi(infotype x);
void dealokasi(address P);
void insertFirst(List &L, address P);
void printInfo(List L);

#endif
```

**Singlylist.cpp**
```C++
#include "Singlylist.h"

void createList(List &L) {
    L.First = nullptr;
}

address alokasi(infotype x) {
    address P = new ElmList;
    if (P != nullptr) {
        P->info = x;
        P->next = nullptr;
    }
    return P;
}

void dealokasi(address P) {
    delete P;
}

void insertFirst(List &L, address P) {
    if (P != nullptr) {
        P->next = L.First;
        L.First = P;
    }
}

void printInfo(List L) {
    address P = L.First;
    while (P != nullptr) {
        cout << P->info << " ";
        P = P->next;
    }
    cout << endl;
}
```

**main.cpp**
```C++
#include "Singlylist.h"

int main() {
    List L;
    address P1, P2, P3, P4, P5;

    createList(L);

    P1 = alokasi(2);
    insertFirst(L, P1);

    P2 = alokasi(0);
    insertFirst(L, P2);

    P3 = alokasi(8);
    insertFirst(L, P3);

    P4 = alokasi(12);
    insertFirst(L, P4);

    P5 = alokasi(9);
    insertFirst(L, P5);

    printInfo(L);

    return 0;
}
```
#### Output:
<img width="1230" height="207" alt="image" src="https://github.com/user-attachments/assets/f748c89e-95e8-4c39-a665-ccdbcad2811a" />


Program ini digunakan untuk membuat dan menampilkan singly linked list yang berisi data integer. Node baru dimasukkan di bagian depan list menggunakan fungsi insertFirst, sehingga urutan data yang tersimpan menjadi terbalik dari urutan input. Hasil akhirnya menampilkan data 9 12 8 0 2 di layar.

#### Full code Screenshot:
<img width="1913" height="1125" alt="image" src="https://github.com/user-attachments/assets/d2988d56-e324-481d-ac67-46701e39e626" />



## Kesimpulan
Ringkasan dan interpretasi pandangan kalia dari hasil praktikum dan pembelajaran yang didapat[1].

## Referensi
[1] I. Holm, Narrator, and J. Fullerton-Smith, Producer, How to Build a Human [DVD]. London: BBC; 2002.

