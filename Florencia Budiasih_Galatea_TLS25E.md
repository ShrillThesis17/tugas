#include <iostream>
#include <string>
using namespace std;

int main(){
    string kata;
    cout << "Masukin kata: ";
    cin >> kata;

    // cek apakah ada angka
    bool adaAngka = false;
    for(int i=0; i<kata.size(); i++){
        if(kata[i] >= '0' && kata[i] <= '9'){
            adaAngka = true;
            break;
        }
    }

    if(!adaAngka){
        // === MODE ENCODE ===
        string tanpaVokal = "";
        for(int i=0; i<kata.size(); i++){
            char c = tolower(kata[i]);
            if(c!='a' && c!='i' && c!='u' && c!='e' && c!='o'){
                tanpaVokal += kata[i];
            }
        }

        // balik manual
        string dibalik = "";
        for(int i=tanpaVokal.size()-1; i>=0; i--){
            dibalik += tanpaVokal[i];
        }

        // sisip ascii huruf terakhir
        if(dibalik.size() > 0){
            char last = dibalik[dibalik.size()-1];
            int kode = (int)last;
            string angka = to_string(kode);

            int tengah = dibalik.size()/2;
            string hasil = "";
            for(int i=0; i<tengah; i++){
                hasil += dibalik[i];
            }
            hasil += angka;
            for(int i=tengah; i<dibalik.size(); i++){
                hasil += dibalik[i];
            }

            cout << "hasil encode: " << hasil << endl;
        } else {
            cout << "hasil encode: (kosong)" << endl;
        }
    }
    else{
        // === MODE DECODE (sederhana aja) ===
        string tanpaAngka = "";
        for(int i=0; i<kata.size(); i++){
            if(!(kata[i] >= '0' && kata[i] <= '9')){
                tanpaAngka += kata[i];
            }
        }

        // balik manual lagi
        string dibalik = "";
        for(int i=tanpaAngka.size()-1; i>=0; i--){
            dibalik += tanpaAngka[i];
        }

        cout << "decode kira-kira: " << dibalik << endl;
        cout << "(note: vokal ga bisa dipastiin)" << endl;
    }

    return 0;
}
