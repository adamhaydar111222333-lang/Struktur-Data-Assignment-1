# <h1 align="center">TREE (BAGIAN PERTAMA)</h1>
<p align="center">Adam Haydar</p>

## Dasar Teori

Rekursif itu proses di mana suatu fungsi atau prosedur memanggil dirinya sendiri, dan pemakaiannya dalam sub program bikin kode lebih rapi, terbagi-bagi, dan bisa dipakai ulang tanpa nulis perintah yang sama berkali-kali.

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

**bstree.h**
```C++
#ifndef BSTREE_H
#define BSTREE_H 

#include <iostream>
using namespace std;

#define Nil NULL

typedef int infotype;
typedef struct Node* address;

struct Node {
    infotype info;
    address left;
    address right;
};

address alokasi(infotype x);

void insertNode(address &root, infotype x);

void printInOrderStrip(address root);

int hitungJumlahNode(address root);
int hitungTotalInfo(address root);
int hitungKedalaman(address root);

#endif
}
```
**bstree.cpp**
```C++
#include "bstree.h"

address alokasi(infotype x) {
    address P = new Node;
    if (P != Nil) {
        P->info = x;
        P->left = Nil;
        P->right = Nil;
    }
    return P;
}

void insertNode(address &root, infotype x) {
    if (root == Nil) {
        root = alokasi(x);
        return;
    }

    if (x < root->info) {
        insertNode(root->left, x);
    } else if (x > root->info) {
        insertNode(root->right, x);
    }
}

void printInOrderStrip(address root) {
    if (root == Nil) return;
    printInOrderStrip(root->left);
    cout << root->info << " - ";
    printInOrderStrip(root->right);
}

int hitungJumlahNode(address root) {
    if (root == Nil) return 0;
    return 1 + hitungJumlahNode(root->left) + hitungJumlahNode(root->right);
}

int hitungTotalInfo(address root) {
    if (root == Nil) return 0;
    return root->info + hitungTotalInfo(root->left) + hitungTotalInfo(root->right);
}

int hitungKedalaman(address root) {
    if (root == Nil) return 0;
    int kiri = hitungKedalaman(root->left);
    int kanan = hitungKedalaman(root->right);
    if (kiri > kanan) return kiri + 1;
    else return kanan + 1;
}
```
**main.cpp**
```C++
#include <iostream>
#include "bstree.h"
using namespace std;

int main() {
    cout << "Hello world!" << endl;

    address root = Nil;

    int data[] = {1, 2, 6, 4, 5, 3, 6, 7};
    int n = 8;

    for (int i = 0; i < n; i++) {
        insertNode(root, data[i]);
    }

    printInOrderStrip(root);
    cout << endl;

    cout << "kedalaman : " << hitungKedalaman(root) << endl;
    cout << "jumlah node : " << hitungJumlahNode(root) << endl;
    cout << "total : " << hitungTotalInfo(root) << endl;

    return 0;
}
```
#### Output:
<img width="696" height="297" alt="image" src="https://github.com/user-attachments/assets/01d98a62-ab9e-4d45-80ef-cef44d07ee10" />

Program ini bikin dan ngolah Binary Search Tree (BST) dari data 1, 2, 6, 4, 5, 3, 6, 7, lalu menampilkan isi tree secara inorder (jadi urut: 1 - 2 - 3 - 4 - 5 - 6 - 7 -), sambil menghitung kedalaman pohon, jumlah node, dan total semua nilai di dalam tree.

#### Full code Screenshot:
<img width="1103" height="1027" alt="image" src="https://github.com/user-attachments/assets/0a9ef4a9-cf6b-409e-ad74-dbe189bc8b6c" />
<img width="1051" height="1089" alt="image" src="https://github.com/user-attachments/assets/40215a8b-6282-4549-9eff-f43946cf0ea6" />
<img width="1271" height="923" alt="image" src="https://github.com/user-attachments/assets/278d147c-18f4-4bc0-b459-492fa58534ef" />


## Kesimpulan
Ringkasan dan interpretasi pandangan kalia dari hasil praktikum dan pembelajaran yang didapat[1].

## Referensi
[1] Azwanti, N., & Putria, N. E. (2024). Analisis Kepuasan Customer pada Sdtechnology Computer dengan Algoritma Decision Tree. Jurnal Desain Dan Analisis Teknologi, 3(2), 137-148.
[2] Teman sekelas
[3] Ai

