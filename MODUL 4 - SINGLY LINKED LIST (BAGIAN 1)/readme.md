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



Program ini dipakai untuk membuat dan menampilkan daftar data sederhana menggunakan singly linked list. Setiap kali ada data baru, datanya dimasukkan di bagian depan, jadi urutannya jadi terbalik dari saat dimasukkan. Hasil akhirnya, program menampilkan angka 9 12 8 0 2 di layar.

#### Full code Screenshot:
<img width="1913" height="1125" alt="image" src="https://github.com/user-attachments/assets/d2988d56-e324-481d-ac67-46701e39e626" />

### 2. [Soal]
**Singlylist.h**
```C++
#ifndef SINGLYLIST_H
#define SINGLYLIST_H

#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
};

struct List {
    Node* head;
};

void createList(List &L);
Node* createNode(int nilai);
void deleteNode(Node* P);
void insertFirst(List &L, Node* P);
void printList(List L);

void deleteFirst(List &L, Node* &P);
void deleteLast(List &L, Node* &P);
void deleteAfter(Node* prec, Node* &P);
int countList(List L);
void deleteAll(List &L);

#endif
```

**Singlylist.cpp**
```C++
#include "Singlylist.h"

void createList(List &L) {
    L.head = nullptr;
}

Node* createNode(int nilai) {
    Node* P = new Node;
    P->data = nilai;
    P->next = nullptr;
    return P;
}

void deleteNode(Node* P) {
    delete P;
}

void insertFirst(List &L, Node* P) {
    if (P != nullptr) {
        P->next = L.head;
        L.head = P;
    }
}

void printList(List L) {
    Node* P = L.head;
    while (P != nullptr) {
        cout << P->data << " ";
        P = P->next;
    }
    cout << endl;
}

void deleteFirst(List &L, Node* &P) {
    if (L.head != nullptr) {
        P = L.head;
        L.head = P->next;
        P->next = nullptr;
    } else {
        P = nullptr;
    }
}

void deleteLast(List &L, Node* &P) {
    if (L.head == nullptr) {
        P = nullptr;
    } else if (L.head->next == nullptr) {
        P = L.head;
        L.head = nullptr;
    } else {
        Node* Q = L.head;
        while (Q->next->next != nullptr) {
            Q = Q->next;
        }
        P = Q->next;
        Q->next = nullptr;
    }
}

void deleteAfter(Node* prec, Node* &P) {
    if (prec != nullptr && prec->next != nullptr) {
        P = prec->next;
        prec->next = P->next;
        P->next = nullptr;
    } else {
        P = nullptr;
    }
}

int countList(List L) {
    int jumlah = 0;
    Node* P = L.head;
    while (P != nullptr) {
        jumlah++;
        P = P->next;
    }
    return jumlah;
}

void deleteAll(List &L) {
    Node* P;
    while (L.head != nullptr) {
        deleteFirst(L, P);
        deleteNode(P);
    }
}
```

**main.cpp**
```C++
#include "Singlylist.h"

int main() {
    List L;
    Node *P, *hapus;

    createList(L);

    insertFirst(L, createNode(2));
    insertFirst(L, createNode(0));
    insertFirst(L, createNode(8));
    insertFirst(L, createNode(12));
    insertFirst(L, createNode(9));

    deleteFirst(L, hapus);
    deleteNode(hapus);

    deleteLast(L, hapus);
    deleteNode(hapus);

    Node* prec = L.head;
    deleteAfter(prec, hapus);
    deleteNode(hapus);

    printList(L);
    cout << "Jumlah node : " << countList(L) << endl;

    deleteAll(L);
    cout << "\n- List Berhasil Terhapus -" << endl;
    cout << "Jumlah node : " << countList(L) << endl;

    return 0;
}
```

#### Output:
<img width="1235" height="311" alt="image" src="https://github.com/user-attachments/assets/36a32c4e-b103-40d6-8d5f-a2e55fe1e1d8" />



Kesimpulannya, program ini digunakan untuk menghapus data dari sebuah **linked list** satu per satu. Pertama, data paling depan (9) dihapus, lalu data paling belakang (2), dan setelah itu data di tengah (8). Hasil akhirnya, list hanya tersisa **12 dan 0**, kemudian semua data dihapus sampai list benar-benar kosong.

#### Full code Screenshot:
<img width="1919" height="1126" alt="image" src="https://github.com/user-attachments/assets/3dee54d9-6833-4194-8bab-a354e4230c11" />




## Kesimpulan
Kesimpulannya, program ini dipakai untuk menambah dan menghapus data secara fleksibel dengan bantuan pointer. Data tersimpan dalam bentuk rantai (node-node) yang saling terhubung, dan bisa dihapus kapan saja. Setelah semua proses selesai, list jadi kosong, menandakan data berhasil dikelola tanpa perlu ukuran tetap seperti array.

## Referensi
Materi Modul 4, Wijoyo, A., Prasetiyo, A. R., Salsabila, A. A., Nife, K., Murni, & Nadapdap, P. B. (2024). Evaluasi Efisiensi Struktur Data Linked List pada Implementasi Sistem Antrian. Jurnal Riset Informatika dan Inovasi, 1(12), 1–9.

