# 127_144_153-KAMIS-12.15--Studi-kasus-6#include <iostream>
using namespace std;

class Mahasiswa {
public:
    string nama;
    string nim;
    float alpro, matdis, pweb, aljabar;
    float nilai_akhir;
    char huruf;
    string kelulusan;

    void input(int index) {
        cout << "\nMasukkan Nama Mahasiswa Ke-" << index + 1 << " : ";
        cin.ignore();
        getline(cin, nama);
        cout << "Masukkan NIM " << nama << " : ";
        getline(cin, nim);
        cout << "\nInput Nilai Alpro " << nama << " : ";
        cin >> alpro;
        cout << "Input Nilai Matdis " << nama << " : ";
        cin >> matdis;
        cout << "Input Nilai Pweb " << nama << " : ";
        cin >> pweb;
        cout << "Input Nilai Aljabar " << nama << " : ";
        cin >> aljabar;
        cout << "+==============================+\n";
    }

    void hitungNilai() {
        nilai_akhir = (alpro + matdis + pweb + aljabar) / 4.0;

        if (nilai_akhir >= 85)
            huruf = 'A';
        else if (nilai_akhir >= 75)
            huruf = 'B';
        else if (nilai_akhir >= 65)
            huruf = 'C';
        else if (nilai_akhir >= 50)
            huruf = 'D';
        else
            huruf = 'E';

        kelulusan = (nilai_akhir >= 70) ? "LULUS" : "TIDAK LULUS";
    }

    void tampil() {
        cout << "\n| Nama\t\t\t: " << nama;
        cout << "\n| NIM\t\t\t: " << nim;
        cout << "\n| Nilai Akhir Mahasiswa\t: " << nilai_akhir;
        cout << "\n| Huruf\t\t\t: " << huruf;
        cout << "\n| Kelulusan\t\t: " << kelulusan << "\n";
        cout << "+==============================+\n";
    }
};

int main() {
    const int MAX = 100;
    Mahasiswa mhs[MAX];
    int jumlah;

    cout << "Masukkan jumlah Mahasiswa : ";
    cin >> jumlah;

    int pilihan;
    float total_nilai = 0;

    do {
        cout << "\n+==============================+\n";
        cout << "|            MENU             |\n";
        cout << "+==============================+\n";
        cout << "| 1. Input Nilai              |\n";
        cout << "| 2. Tampilkan Data Nilai     |\n";
        cout << "| 3. Keluar                   |\n";
        cout << "+==============================+\n";
        cout << " Masukkan Pilihan : ";
        cin >> pilihan;

        switch (pilihan) {
        case 1:
           cout << "\n+==============================+\n";
           cout << "|      INPUT NILAI MAHASISWA  |\n";
           cout << "+==============================+\n";
            for (int i = 0; i < jumlah; i++) {
                mhs[i].input(i);
                mhs[i].hitungNilai();
            }
             cout << "+===========================================+\n";
             cout << "|     NILAI MAHASISWA BERHASIL DIINPUT      |\n";
             cout << "+===========================================+\n";
             break;

        case 2:
             cout << "\n+==============================+\n";
             cout << "|     DATA NILAI MAHASISWA     |\n";
             cout << "+==============================+\n";
            total_nilai = 0;
            for (int i = 0; i < jumlah; i++) {
                mhs[i].tampil();
                total_nilai += mhs[i].nilai_akhir;
            }
            cout << "\n| Jumlah Mahasiswa\t: " << jumlah;
            cout << "\n| Total Nilai Mahasiswa\t: " << total_nilai;
            cout << "\n| Rata-rata nilai\t: " << (total_nilai / jumlah) << "\n";
            break;

        case 3:
            cout << "\nTerima Kasih\n";
            break;

        default:
            cout << "\nPilihan tidak valid.\n";
        }

    } while (pilihan != 3);

    return 0;
}

