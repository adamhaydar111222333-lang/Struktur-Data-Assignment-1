# <h1 align="center">DOUBLYLINKEDLIST(BAGIANPERTAMA)</h1>
<p align="center">Adam Haydar</p>
 
## Dasar Teori

Doubly Linked List adalah struktur data di mana setiap elemen memiliki dua penunjuk: satu menunjuk ke elemen sebelumnya (prev) dan satu lagi menunjuk ke elemen setelahnya (next).

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
**Doublylist.h**
```C++
#ifndef DOUBLYLIST_H
#define DOUBLYLIST_H
#include <string>
#include <iostream>

using namespace std;

struct infotype {
    string nopol;
    string warna;
    int thnBuat;
};

typedef struct elmlist *address;

struct elmlist {
    infotype info;
    address next;
    address prev;
};

struct List {
    address first;
    address last;
};

void CreateList(List &L);
address alokasi(infotype x);
void printfInfo(List L);
void insertLast(List &L, address P);
address findElm(List L, string nopol);
void deleteFirst(List &L, address &P);
void deleteLast(List &L, address &P);
void deleteAfter(address Prec, address &P);
void deleteByNopol(List &L, string nopol);

#endif
}
```

**Doublylist.cpp**
```C++
#include "Doublylist.h"
#include <iostream>

using namespace std;

void CreateList(List &L) {
    L.first = NULL;
    L.last = NULL;
}

address alokasi(infotype x) {
    address P = new elmlist;
    P->info = x;
    P->next = NULL;
    P->prev = NULL;
    return P;
}

void printfInfo(List L) {
    cout << "\nDATA LIST 1\n";
    
    if (L.first == NULL) {
        cout << "List kosong!\n";
        return;
    }
    
    address P = L.first;
    while (P != NULL) {
        cout << "no polisi : " << P->info.nopol << endl;
        cout << "warna     : " << P->info.warna << endl;
        cout << "tahun     : " << P->info.thnBuat << endl;
        if (P->next != NULL) cout << endl; // Beri jarak antar data
        P = P->next;
    }
}

void insertLast(List &L, address P) {
    if (L.first == NULL) {
        L.first = P;
        L.last = P;
    } else {
        L.last->next = P;
        P->prev = L.last;
        L.last = P;
    }
}

address findElm(List L, string nopol) {
    address P = L.first;
    while (P != NULL) {
        if (P->info.nopol == nopol) {
            return P;
        }
        P = P->next;
    }
    return NULL;
}

void deleteFirst(List &L, address &P) {
    if (L.first == NULL) return;
    
    P = L.first;
    if (L.first == L.last) {
        L.first = NULL;
        L.last = NULL;
    } else {
        L.first = L.first->next;
        L.first->prev = NULL;
    }
    P->next = NULL;
}

void deleteLast(List &L, address &P) {
    if (L.first == NULL) return;
    
    P = L.last;
    if (L.first == L.last) {
        L.first = NULL;
        L.last = NULL;
    } else {
        L.last = L.last->prev;
        L.last->next = NULL;
    }
    P->prev = NULL;
}

void deleteAfter(address Prec, address &P) {
    if (Prec == NULL || Prec->next == NULL) return;
    
    P = Prec->next;
    Prec->next = P->next;
    if (P->next != NULL) {
        P->next->prev = Prec;
    }
    P->next = NULL;
    P->prev = NULL;
}

void deleteByNopol(List &L, string nopol) {
    address P = findElm(L, nopol);
    
    if (P == NULL) {
        cout << "Data dengan nomor polisi " << nopol << " tidak ditemukan!\n";
        return;
    }
    
    if (P == L.first) {
        deleteFirst(L, P);
    } else if (P == L.last) {
        deleteLast(L, P);
    } else {
        deleteAfter(P->prev, P);
    }
    
    delete P;
    cout << "Data dengan nomor polisi " << nopol << " berhasil dihapus.\n";
}
```

**main.c**
```C++
#include <iostream>
#include "Doublylist.h"

using namespace std;

int main() {
    List L;
    CreateList(L);
    
    cout << "masukkan nomor polisi: ";
    string nopol, warna;
    int tahun;
    
    cin >> nopol;
    cout << "masukkan warna kendaraan: ";
    cin >> warna;
    cout << "masukkan tahun kendaraan: ";
    cin >> tahun;
    
    infotype k1 = {nopol, warna, tahun};
    address p1 = alokasi(k1);
    insertLast(L, p1);
    cout << endl;
    
    cout << "masukkan nomor polisi: ";
    cin >> nopol;
    cout << "masukkan warna kendaraan: ";
    cin >> warna;
    cout << "masukkan tahun kendaraan: ";
    cin >> tahun;
    
    infotype k2 = {nopol, warna, tahun};
    address p2 = alokasi(k2);
    insertLast(L, p2);
    cout << endl;
    
    cout << "masukkan nomor polisi: ";
    cin >> nopol;
    if (findElm(L, nopol) != NULL) {
        cout << "masukkan warna kendaraan: ";
        cin >> warna;
        cout << "masukkan tahun kendaraan: ";
        cin >> tahun;
        cout << "nomor polisi sudah terdaftar\n" << endl;
    }
    
    cout << "masukkan nomor polisi: ";
    cin >> nopol;
    cout << "masukkan warna kendaraan: ";
    cin >> warna;
    cout << "masukkan tahun kendaraan: ";
    cin >> tahun;
    
    infotype k4 = {nopol, warna, tahun};
    address p4 = alokasi(k4);
    insertLast(L, p4);
    cout << endl;
    
    printfInfo(L);
    
    cout << "\n\nNasukkan Nomor Polisi yang dicari : ";
    cin >> nopol;
    
    address found = findElm(L, nopol);
    if (found != NULL) {
        cout << "Nomor Polisi : " << found->info.nopol << endl;
        cout << "warna        : " << found->info.warna << endl;
        cout << "Tahun        : " << found->info.thnBuat << endl;
    }
    
    cout << "\n\nMasukkan Nomor Polisi yang akan dihapus : ";
    cin >> nopol;
    deleteByNopol(L, nopol);
    
    printfInfo(L);
    
    return 0;
}
```
#### Output:
<img width="405" height="860" alt="image" src="https://github.com/user-attachments/assets/46d5e914-404a-45fc-b4fc-e802b1bf08f0" />
    
Doubly linked list lebih powerful daripada singly linked list karena bisa navigasi dua arah, membuat operasi insert/delete lebih efisien, terutama untuk operasi yang membutuhkan akses elemen sebelumnya.

#### Full code Screenshot:
<img width="791" height="878" alt="image" src="https://github.com/user-attachments/assets/45d796ef-06a3-430e-a816-80194d40fd4a" />
<img width="487" height="1032" alt="image" src="https://github.com/user-attachments/assets/158a5cb6-0964-4d32-93bf-64522937db4d" />
<img width="975" height="1033" alt="image" src="https://github.com/user-attachments/assets/df925077-499b-465b-89ae-8a6e98a05dc9" />


## Kesimpulan
Doubly Linked List memberikan solusi yang lebih powerful dibandingkan Singly Linked List untuk kasus-kasus yang membutuhkan akses dua arah, meskipun membutuhkan memori lebih besar untuk menyimpan pointer tambahan. Struktur data ini sangat efektif untuk aplikasi yang memerlukan operasi insert dan delete yang pada berbagai posisi dalam list.

## Referensi
[1] I. Holm, Narrator, and J. Fullerton-Smith, Producer, How to Build a Human [DVD]. London: BBC; 2002.
