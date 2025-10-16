# <h1 align="center">Laporan Praktikum Modul Pengenalan Bahasa C++ (1)</h1>
<p align="center">Adam Haydar</p>

## Dasar Teori

Bahasa C++ adalah pengembangan dari C yang mendukung pemrograman prosedural dan berorientasi objek. Program ditulis di Code::Blocks dengan struktur dasar header, fungsi main(), serta perintah cin dan cout untuk input-output.



## Guided 

### 1. Modul Codeblocks IDE & Pengenalan Bahas C++ (1)


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
    float x, y;

    cout << "Masukkan angka pertama : ";
    cin >> x;
    cout << "Masukkan angka kedua   : ";
    cin >> y;

    cout << endl;
    cout << "Penjumlahan = " << (x + y) << endl;
    cout << "Pengurangan = " << (x - y) << endl;
    cout << "Perkalian   = " << (x * y) << endl;

    if(y != 0){
        cout << "Pembagian   = " << (x / y) << endl;
    } else {
        cout << "Pembagian   = tidak bisa (pembagi nol)" << endl;
    }

    return 0;
}
```
#### Output:
<img width="732" height="303" alt="Image" src="https://github.com/user-attachments/assets/1f20ab50-8817-42fe-9306-3e524301a561" />

Kode di atas digunakan untuk menghitung dan menampilkan hasil operasi aritmatika dua angka yang dimasukkan pengguna. Nilai dimasukkan melalui cin, lalu hasil penjumlahan, pengurangan, perkalian, dan pembagian ditampilkan dengan cout.


#### Full code Screenshot:
<img width="913" height="792" alt="Image" src="https://github.com/user-attachments/assets/a545d712-d867-459d-aa57-7698d0c65137" />

### 2. [Soal]

```C++
#include <iostream>
using namespace std;

string ubahTulisan(int n) {
    string satuan[10] = {"", "satu", "dua", "tiga", "empat", "lima", 
                         "enam", "tujuh", "delapan", "sembilan"};
    string belasan[10] = {"sepuluh", "sebelas", "dua belas", "tiga belas", "empat belas",
                          "lima belas", "enam belas", "tujuh belas", "delapan belas", "sembilan belas"};
    string puluhan[10] = {"", "", "dua puluh", "tiga puluh", "empat puluh", 
                          "lima puluh", "enam puluh", "tujuh puluh", "delapan puluh", "sembilan puluh"};

    if (n == 0) return "nol";
    if (n == 100) return "seratus";
    if (n < 10) return satuan[n];
    if (n < 20) return belasan[n - 10];
    
    int p = n / 10;   
    int s = n % 10;   

    if (s == 0) {
        return puluhan[p];
    } else {
        return puluhan[p] + " " + satuan[s];
    }
}

int main() {
    int angka;
    cout << "Masukkan angka (0 - 100) : ";
    cin >> angka;

    if (angka < 0 || angka > 100) {
        cout << "Angka tidak valid!" << endl;
    } else {
        cout << angka << " : " << ubahTulisan(angka) << endl;
    }

    return 0;
}
```
#### Output:
<img width="687" height="312" alt="Image" src="https://github.com/user-attachments/assets/72a76162-4fd5-481e-bb98-36e6d3a9d4b7" />

Kode di atas digunakan untuk mengubah angka yang dimasukkan pengguna menjadi tulisan dalam bahasa Indonesia menggunakan fungsi ubahTulisan(). Hasil konversinya kemudian ditampilkan ke layar dengan perintah cout.

#### Full code Screenshot:
<img width="876" height="844" alt="Image" src="https://github.com/user-attachments/assets/056883ad-db19-431b-a47a-ef0261a9633a" />

### 3. [Soal]

```C++
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Masukkan jumlah angka: ";
    cin >> n;

    cout << "\nOutput:\n\n";

    for (int i = n; i >= 0; i--) {
        for (int s = 0; s < n - i; s++)
            cout << "  ";

        for (int j = i; j >= 1; j--)
            cout << j << " ";

        cout << "* ";

        for (int j = 1; j <= i; j++)
            cout << j << " ";

        cout << endl;
    }

    return 0;
}
```
#### Output:
<img width="711" height="381" alt="Image" src="https://github.com/user-attachments/assets/b25e6a5d-2fd1-4d77-9042-5b85c09b7e91" />

Kode ini membuat pola cermin angka dengan pusat bintang.
Bagian kiri menurun, bagian kanan menaik, dan bentuknya simetris secara vertikal.

#### Full code Screenshot:
<img width="593" height="861" alt="Image" src="https://github.com/user-attachments/assets/8b6f2dee-c447-4217-b86e-c24079c31c87" />


## Kesimpulan
Program ini memperkuat pemahaman tentang perulangan bersarang, logika pengaturan posisi (spasi), dan pola output visual di layar.

## Referensi
Setyawan, R. A., Cahyana, F. M., & St, I. M. J. (2014). Perancangan Program Penghitung Jumlah Kendaraan Di Lintasan Jalan Raya Satu Arah Menggunakan Bahasa Pemrograman C++ Dengan Pustaka Opencv (Doctoral dissertation, Brawijaya University). Programmer Anonim. (2025). Basic_Cpp_Arithmetic (Versi 1.0) [Kode Sumber]. Diakses dari https://github.com/link_ke_repositori
