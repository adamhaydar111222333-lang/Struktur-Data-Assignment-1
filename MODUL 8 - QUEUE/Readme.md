# <h1 align="center">Laporan Praktikum Modul 8 QUEUE</h1>
<p align="center">Adam Haydar</p>

## Dasar Teori

Queue adalah struktur data seperti antrean yang bekerja dengan prinsip FIFO, di mana data yang masuk pertama diproses lebih dulu, dan dalam praktikum ini diimplementasikan menggunakan linked list dengan operasi insert di belakang dan delete di depan.

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

**queue.h**
```C++
#ifndef QUEUE_H
#define QUEUE_H

#include <iostream>
using namespace std;

typedef int infotype;
#define MAX 5

struct Queue {
    infotype info[MAX];
    int head;
    int tail;
};

void createQueue(Queue &Q);
bool isEmptyQueue(Queue Q);
bool isFullQueue(Queue Q);
void enqueue(Queue &Q, infotype x);
infotype dequeue(Queue &Q);
void printInfo(Queue Q);

#endif

```
**queue.cpp**
```C++
#include "queue.h"

void createQueue(Queue &Q) {
    Q.head = -1;
    Q.tail = -1;
}

bool isEmptyQueue(Queue Q) {
    return (Q.head == -1);
}

bool isFullQueue(Queue Q) {
    return (Q.tail == MAX - 1);
}

void enqueue(Queue &Q, infotype x) {
    if (isFullQueue(Q)) {
        cout << "Queue Full" << endl;
        return;
    }

    if (isEmptyQueue(Q)) {
        Q.head = 0;
        Q.tail = 0;
    } else {
        Q.tail++;
    }
    Q.info[Q.tail] = x;
}

infotype dequeue(Queue &Q) {
    infotype val = -1;

    if (isEmptyQueue(Q)) {
        cout << "Queue Empty" << endl;
        return val;
    }

    val = Q.info[0];

    if (Q.head == Q.tail) {
        createQueue(Q);
    } else {
        for (int i = 0; i < Q.tail; i++) {
            Q.info[i] = Q.info[i + 1];
        }
        Q.tail--;
    }

    return val;
}

void printInfo(Queue Q) {
    cout << Q.head << " - " << Q.tail << " \t| ";

    if (isEmptyQueue(Q)) {
        cout << "empty queue";
    } else {
        for (int i = Q.head; i <= Q.tail; i++) {
            cout << Q.info[i];
            if (i < Q.tail) cout << " ";
        }
    }
    cout << endl;
}
```
**main.cpp**
```C++
#include <iostream>
#include "queue.h"
using namespace std;

int main() {
    cout << "Hello world!" << endl;
    cout << "------------------------" << endl;
    cout << " H - T \t| Queue Info" << endl;
    cout << "------------------------" << endl;

    Queue Q;
    createQueue(Q);

    printInfo(Q);               
    enqueue(Q, 5); printInfo(Q);
    enqueue(Q, 2); printInfo(Q);
    enqueue(Q, 7); printInfo(Q);

    dequeue(Q); printInfo(Q);
    dequeue(Q); printInfo(Q);

    enqueue(Q, 4); printInfo(Q);

    dequeue(Q); printInfo(Q);
    dequeue(Q); printInfo(Q);     
    return 0;
}
```
#### Output:
<img width="794" height="538" alt="image" src="https://github.com/user-attachments/assets/30568e51-4948-478f-8b72-95ada841fa61" />


Program ini memperlihatkan cara kerja antrian FIFO, yaitu data masuk dari belakang, keluar dari depan, dan akhirnya antrian kembali kosong.

#### Full code Screenshot:
<img width="1088" height="902" alt="image" src="https://github.com/user-attachments/assets/50db6840-1d56-4fed-ac30-3f9ec094fef2" />
<img width="638" height="989" alt="image" src="https://github.com/user-attachments/assets/f0c7961f-240c-40b2-b3de-1308e28519b0" />
<img width="1120" height="861" alt="image" src="https://github.com/user-attachments/assets/de2f0ef5-105c-4c2b-bec8-3aa7141728c7" />



## Kesimpulan
queue dapat diimplementasikan dengan cara head tetap di indeks 0, tail bergerak di belakang, dan setiap dequeue menggeser elemen ke kiri sehingga urutan data selalu rapi dan tetap mengikuti prinsip First In First Out.

## Referensi
[1] Dicoding Team. (2024, 15 Maret). Mengenal Struktur Data Queue: Konsep FIFO dan Implementasinya. Dicoding. https://www.dicoding.com/blog/struktur-data-queue/
[2] Akhdan
[3] Ai

