# <h1 align="center">GRAPH</h1>
<p align="center">Adam Haydar</p>

## Dasar Teori

Graph adalah kumpulan titik dan garis penghubung. Contohnya, tempat kost dan Common Lab adalah titik, sedangkan jalan yang menghubungkannya adalah garis penghubung.

## Guided 

### 1. [Nama Topik]

Kode di atas digunakan untuk mencetak teks "ini adalah file code guided praktikan" ke layar menggunakan function cout untuk mengeksekusi nya.

## Unguided 

### 1. [Soal]
**graph.h**
```C++
**graph.h**
```C++
#ifndef GRAPH_H
#define GRAPH_H

#include <iostream>
using namespace std;

typedef char infoGraph;
typedef struct ElmNode *adrNode;
typedef struct ElmEdge *adrEdge;

struct ElmEdge {
    adrNode node;
    adrEdge next;
};

struct ElmNode {
    infoGraph info;
    int visited;
    adrEdge firstEdge;
    adrNode next;
};

struct Graph {
    adrNode first;
};

void CreateGraph(Graph &G);
void InsertNode(Graph &G, infoGraph X);
void ConnectNode(adrNode N1, adrNode N2);
adrNode FindNode(Graph G, infoGraph X);
void PrintInfoGraph(Graph G);
void PrintDFS(Graph G, adrNode N);
void PrintBFS(Graph G, adrNode N);

#endif
```
**graph.cpp**
```C++
#include "graph.h"

void CreateGraph(Graph &G) {
    G.first = NULL;
}

adrNode FindNode(Graph G, infoGraph X) {
    adrNode P = G.first;
    while (P != NULL) {
        if (P->info == X) return P;
        P = P->next;
    }
    return NULL;
}

void InsertNode(Graph &G, infoGraph X) {
    adrNode N = new ElmNode{X,0,NULL,NULL};
    if (G.first == NULL) G.first = N;
    else {
        adrNode P = G.first;
        while (P->next != NULL) P = P->next;
        P->next = N;
    }
}

void ConnectNode(adrNode N1, adrNode N2) {
    adrEdge E1 = new ElmEdge{N2, NULL};
    if (N1->firstEdge == NULL)
        N1->firstEdge = E1;
    else {
        adrEdge P = N1->firstEdge;
        while (P->next != NULL) P = P->next;
        P->next = E1;
    }

    adrEdge E2 = new ElmEdge{N1, NULL};
    if (N2->firstEdge == NULL)
        N2->firstEdge = E2;
    else {
        adrEdge P = N2->firstEdge;
        while (P->next != NULL) P = P->next;
        P->next = E2;
    }
}

void PrintInfoGraph(Graph G) {
    adrNode P = G.first;
    while (P != NULL) {
        cout << P->info << " : ";
        adrEdge E = P->firstEdge;
        while (E != NULL) {
            cout << E->node->info << " ";
            E = E->next;
        }
        cout << endl;
        P = P->next;
    }
}

void PrintDFS(Graph G, adrNode N) {
    if (N == NULL || N->visited) return;
    cout << N->info << " ";
    N->visited = 1;
    for (adrEdge E = N->firstEdge; E != NULL; E = E->next)
        PrintDFS(G, E->node);
}

void PrintBFS(Graph G, adrNode N) {
    adrNode Q[50];
    int f=0, r=0;
    Q[r++] = N;
    N->visited = 1;

    while (f < r) {
        adrNode P = Q[f++];
        cout << P->info << " ";
        for (adrEdge E = P->firstEdge; E != NULL; E = E->next)
            if (!E->node->visited) {
                E->node->visited = 1;
                Q[r++] = E->node;
            }
    }
}
```
**main.cpp**
```C++
#include "graph.h"

int main() {
    Graph G;
    CreateGraph(G);

    char node[] = {'A','B','C','D','E','F','G','H'};
    for (char c : node) InsertNode(G,c);

    ConnectNode(FindNode(G,'A'), FindNode(G,'B'));
    ConnectNode(FindNode(G,'A'), FindNode(G,'C'));
    ConnectNode(FindNode(G,'B'), FindNode(G,'D'));
    ConnectNode(FindNode(G,'B'), FindNode(G,'E'));
    ConnectNode(FindNode(G,'C'), FindNode(G,'F'));
    ConnectNode(FindNode(G,'C'), FindNode(G,'G'));
    ConnectNode(FindNode(G,'D'), FindNode(G,'H'));
    ConnectNode(FindNode(G,'E'), FindNode(G,'H'));
    ConnectNode(FindNode(G,'F'), FindNode(G,'H'));
    ConnectNode(FindNode(G,'G'), FindNode(G,'H'));

    cout << "DFS: ";
    PrintDFS(G, FindNode(G,'A'));

    adrNode P = G.first;
    while (P) { P->visited = 0; P = P->next; }

    cout << "\nBFS: ";
    PrintBFS(G, FindNode(G,'A'));

    return 0;
}
```
```
#### Output:
![240302_00h00m06s_screenshot](https://github.com/suxeno/Struktur-Data-Assignment/assets/111122086/6d1727a8-fb77-4ecf-81ff-5de9386686b7)

Kode di atas digunakan untuk mencetak teks "ini adalah file code guided praktikan" ke layar menggunakan function cout untuk mengeksekusi nya.

#### Full code Screenshot:
![240309_10h21m35s_screenshot](https://github.com/suxeno/Struktur-Data-Assignment/assets/111122086/41e9641c-ad4e-4e50-9ca4-a0215e336b04)


## Kesimpulan
Ringkasan dan interpretasi pandangan kalia dari hasil praktikum dan pembelajaran yang didapat[1].

## Referensi
[1] Renaldi, R. (2014). IMPLEMENTASI MEDIA ANIMASI ROTOSCOPING GUNA MENINGKATKAN PEMAHAMAN MATERI GRAPH PADA MATA KULIAH STRUKTUR DATA (Doctoral dissertation, Universitas Pendidikan Indonesia).
[2] Teman sekelas
[3] Ai
