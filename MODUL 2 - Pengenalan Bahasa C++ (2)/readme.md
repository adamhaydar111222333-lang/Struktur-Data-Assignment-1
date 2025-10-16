# <h1 align="center">Laporan Praktikum Modul Pengenalan Bahasa C++ (1)</h1>
<p align="center">Adam Haydar</p>

## Dasar Teori

Modul ini membahas dasar C++ seperti penggunaan **main()**, **cout**, **cin**, variabel, percabangan, dan perulangan untuk memahami logika serta struktur program dasar.



## Guided 

### 1. MODUL PENGENALAN BAHASA C++ BAGIAN 2


```C++
#include <iostream>

using namespace std;

int main () {
    // array 1 dimensi
    int arrID[5] = {10,20,30,40,50};
    cout << "Array 1 Dimensi" << endl;
    for (int i=0; i<5; i++) {
        cout << "arrID" << i << " = " << arrID[i] << endl; 
        
    }
    cout << endl;

    // array 2 dimensi baris & kolom
    int arr2D[2][3] = {
        {1,2,3},
        {4,5,6}
    };
    cout << "Array 2 Dimensi" << endl;
    for (int i=0; i<2; i++) {
        for (int j=0; j<3; j++) {
            cout << "arr2D[" << i << "}[" << j << "] = " << arr2D[i][j]
            << " ";
        }
        cout << endl;
    }
    cout << endl;
    
    //array multi dimensi (3D)
    int arr3D[2][2][3] = {
    { { 1, 2, 3 }, {4, 5, 6} },
    { { 7, 8, 9} , {10, 11, 12} }   
    };
    cout << "array 3 dimensi" << endl;
    for (int i=0; i<2; i++) {
        for (int j=0; j<2; j++) {
            for (int k=0; k<3; k++) {
                cout << "arr3D[" << i << "][" << j << "]["
                << k << "] = " << arr3D[i][j][k] << endl;
            }
        }
    }

    return 0;
}
```
Kode di atas digunakan untuk menampilkan isi array 1 dimensi, 2 dimensi, dan 3 dimensi ke layar. Setiap elemen array dicetak menggunakan perulangan for dan ditampilkan dengan cout agar hasilnya muncul di layar.


## Unguided 

### 1. [Soal]

```C++
#include <iostream>
using namespace std;

int main() {
    int A[3][3], B[3][3], C[3][3], p;

    cout << "Masukkan elemen matriks A:\n";
    for (int i = 0; i < 3; i++)
        for (int j = 0; j < 3; j++)
            cin >> A[i][j];

    cout << "Masukkan elemen matriks B:\n";
    for (int i = 0; i < 3; i++)
        for (int j = 0; j < 3; j++)
            cin >> B[i][j];

    cout << "Pilih operasi (1=+, 2=-, 3=*): ";
    cin >> p;

    cout << "Hasil:\n";

    if (p == 1) { 
        for (int i = 0; i < 3; i++) {
            for (int j = 0; j < 3; j++)
                cout << A[i][j] + B[i][j] << "\t";
            cout << endl;
        }
    } 
    else if (p == 2) { 
        for (int i = 0; i < 3; i++) {
            for (int j = 0; j < 3; j++)
                cout << A[i][j] - B[i][j] << "\t";
            cout << endl;
        }
    } 
    else if (p == 3) { 
        for (int i = 0; i < 3; i++) {
            for (int j = 0; j < 3; j++) {
                C[i][j] = 0;
                for (int k = 0; k < 3; k++)
                    C[i][j] += A[i][k] * B[k][j];
                cout << C[i][j] << "\t";
            }
            cout << endl;
        }
    } 
    else cout << "Pilihan tidak valid!\n";

    return 0;
}

```
#### Output:
<img width="815" height="409" alt="Image" src="https://github.com/user-attachments/assets/0ce8a7df-1207-4199-a34a-e675a94a5938" />

Kode di atas digunakan untuk menghitung dan menampilkan hasil operasi dua matriks 3×3. Pengguna memasukkan elemen matriks A dan B, lalu memilih operasi (tambah, kurang, atau kali). Hasil perhitungan ditampilkan ke layar dengan cout.



#### Full code Screenshot:
<img width="517" height="1027" alt="Image" src="https://github.com/user-attachments/assets/9d1b7ae1-0f4c-40cd-a32e-ee1a64eea660" />

### 2. [Soal]

```C++
#include <iostream>
using namespace std;

void tukarReference(int &a, int &b, int &c) {
    int temp = a;
    a = b;
    b = c;
    c = temp;
}

int main() {
    int x = 10, y = 20, z = 30;
    cout << "Sebelum: x=" << x << ", y=" << y << ", z=" << z << endl;
    tukarReference(x, y, z);
    cout << "Sesudah: x=" << x << ", y=" << y << ", z=" << z << endl;
}

```
#### Output:
<img width="712" height="228" alt="Image" src="https://github.com/user-attachments/assets/f363b0be-515b-4011-a489-acfc3988c4d2" />

Kode ini menukar nilai tiga variabel secara berurutan menggunakan referensi.
Nilai awal ditampilkan, kemudian fungsi tukarReference memindahkan nilai x → y, y → z, dan z → x, lalu hasilnya ditampilkan kembali.

#### Full code Screenshot:
<img width="927" height="579" alt="Image" src="https://github.com/user-attachments/assets/4772d20a-3477-4d31-b572-9d22978de873" />

### 3. [Soal]

```C++
#include <iostream>
using namespace std;

int cariMaks(int a[], int n) {
    int maks = a[0];
    for (int i = 1; i < n; i++)
        if (a[i] > maks) maks = a[i];
    return maks;
}

int cariMin(int a[], int n) {
    int min = a[0];
    for (int i = 1; i < n; i++)
        if (a[i] < min) min = a[i];
    return min;
}

void rataRata(int a[], int n) {
    float total = 0;
    for (int i = 0; i < n; i++)
        total += a[i];
    cout << "Rata-rata: " << total / n << endl;
}

int main() {
    int arr[] = {11, 8, 5, 7, 12, 26, 3, 54, 33, 55};
    int n = sizeof(arr) / sizeof(arr[0]);
    int pilih;

    do {
        cout << "\n--- Menu Array ---\n";
        cout << "1. Tampilkan array\n";
        cout << "2. Nilai maksimum\n";
        cout << "3. Nilai minimum\n";
        cout << "4. Nilai rata-rata\n";
        cout << "5. Keluar\n";
        cout << "Pilih: ";
        cin >> pilih;

        switch (pilih) {
            case 1:
                for (int i = 0; i < n; i++) cout << arr[i] << " ";
                cout << endl;   
                break;
            case 2:
                cout << "Maksimum: " << cariMaks(arr, n) << endl;
                break;
            case 3:
                cout << "Minimum: " << cariMin(arr, n) << endl;
                break;
            case 4:
                rataRata(arr, n);
                break;
            case 5:
                cout << "Selesai.\n";
                break;
            default:
                cout << "Pilihan salah!\n";
        }
    } while (pilih != 5);
}
```
#### Output:
<img width="1196" height="888" alt="Image" src="https://github.com/user-attachments/assets/abbf036c-4aa6-429d-af3a-3c02b4bc787d" />

Kode ini menyediakan menu interaktif untuk mengolah sebuah array: tampilkan isi, cari maksimum, minimum, atau hitung rata-rata.
Setiap operasi dikerjakan oleh fungsi terpisah, dan program berulang sampai pengguna memilih keluar.

#### Full code Screenshot:
<img width="561" height="1058" alt="Image" src="https://github.com/user-attachments/assets/e6693e34-e0d7-47c3-9ec2-8f09136a8ac0" />


## Kesimpulan
Ketiga program C++ ini secara bersama-sama menunjukkan dasar-dasar dalam pemrograman C++, mulai dari mengolah data yang rumit seperti matriks, sampai trik mengubah nilai variabel dengan fungsi.

## Referensi
Putra, M. T. D., Munawir, M., & Yuniarti, A. R. (2023). BELAJAR PEMROGRAMAN LANJUT DENGAN C++. (A.Pratama, komunikasi pribadi, 9 Oktober 2025).












