#include <stdio.h>
#include <stdlib.h>
#include <string.h>

struct Kitap {
    char ad[50];
    char yazar[50];
    char ISBN[13];
    char kategori[20];
    int stok;
};

struct Kullanici {
    char isim[50];
    char soyisim[50];
    char email[100];
    int id;
};

int kitapEkle(struct Kitap kitaplar[], int kitapSayisi) {
    printf("\nYeni Kitap Ekle:\n");

    printf("Kitap adi: ");
    scanf("%s", kitaplar[kitapSayisi].ad);

    printf("Yazar adi: ");
    scanf("%s", kitaplar[kitapSayisi].yazar);

    printf("ISBN: ");
    scanf("%s", kitaplar[kitapSayisi].ISBN);

    printf("Kategori: ");
    scanf("%s", kitaplar[kitapSayisi].kategori);

    printf("Stok adedi: ");
    scanf("%d", &kitaplar[kitapSayisi].stok);

    return kitapSayisi + 1;
}

int kitapListele(struct Kitap kitaplar[], int kitapSayisi) {
    if (kitapSayisi == 0) {
        printf("\nKayitli kitap yok!\n");
        return kitapSayisi;
    }

    printf("\nKAYITLI KITAPLAR\n");
    for (int i = 0; i < kitapSayisi; i++) {
        printf("\nKitap #%d\n", i + 1);
        printf("Ad: %s\n", kitaplar[i].ad);
        printf("Yazar: %s\n", kitaplar[i].yazar);
        printf("ISBN: %s\n", kitaplar[i].ISBN);
        printf("Kategori: %s\n", kitaplar[i].kategori);
        printf("Stok: %d\n", kitaplar[i].stok);
    }

    return kitapSayisi;
}

int kitapAra(struct Kitap kitaplar[], int kitapSayisi) {
    char aranan[50];
    printf("\nAramak istediginiz kitap adini girin: ");
    scanf("%s", aranan);

    int bulundu = 0;
    for (int i = 0; i < kitapSayisi; i++) {
        if (strcmp(kitaplar[i].ad, aranan) == 0) {
            printf("\nKitap bulundu:\n");
            printf("Ad: %s\n", kitaplar[i].ad);
            printf("Yazar: %s\n", kitaplar[i].yazar);
            printf("ISBN: %s\n", kitaplar[i].ISBN);
            printf("Kategori: %s\n", kitaplar[i].kategori);
            printf("Stok: %d\n", kitaplar[i].stok);
            bulundu = 1;
            break;
        }
    }

    if (!bulundu) {
        printf("\nKitap bulunamadi!\n");
    }

    return kitapSayisi;
}

int kullaniciEkle(struct Kullanici kullanicilar[], int kullaniciSayisi) {
    printf("\nYeni Kullanici Ekle:\n");

    printf("Isim: ");
    scanf("%s", kullanicilar[kullaniciSayisi].isim);

    printf("Soyisim: ");
    scanf("%s", kullanicilar[kullaniciSayisi].soyisim);

    printf("Email: ");
    scanf("%s", kullanicilar[kullaniciSayisi].email);

    kullanicilar[kullaniciSayisi].id = kullaniciSayisi + 1;

    return kullaniciSayisi + 1;
}

int kullaniciListele(struct Kullanici kullanicilar[], int kullaniciSayisi) {
    if (kullaniciSayisi == 0) {
        printf("\nKayitli kullanici yok!\n");
        return kullaniciSayisi;
    }

    printf("\nKAYITLI KULLANICILAR\n");
    for (int i = 0; i < kullaniciSayisi; i++) {
        printf("\nKullanici #%d\n", i + 1);
        printf("Isim: %s\n", kullanicilar[i].isim);
        printf("Soyisim: %s\n", kullanicilar[i].soyisim);
        printf("Email: %s\n", kullanicilar[i].email);
        printf("ID: %d\n", kullanicilar[i].id);
    }

    return kullaniciSayisi;
}

int kitapOduncAl(struct Kitap kitaplar[], int kitapSayisi, struct Kullanici kullanicilar[], int kullaniciSayisi) {
    if (kullaniciSayisi == 0) {
        printf("\nOdunc almak icin kullanici kaydi bulunamadi!\n");
        return kitapSayisi;
    }

    char kitapAdi[50];
    printf("\nOdunc almak istediginiz kitap adini girin: ");
    scanf("%s", kitapAdi);

    int bulundu = 0;
    for (int i = 0; i < kitapSayisi; i++) {
        if (strcmp(kitaplar[i].ad, kitapAdi) == 0) {
            if (kitaplar[i].stok > 0) {
                printf("\nKitap bulundu. Kitabi odunc alacak kullaniciyi secin:\n");
                kullaniciListele(kullanicilar, kullaniciSayisi);
                int kullaniciID;
                printf("Kullanici ID girin: ");
                scanf("%d", &kullaniciID);

                if (kullaniciID > 0 && kullaniciID <= kullaniciSayisi) {
                    kitaplar[i].stok--;
                    printf("\nKitap \"%s\" kullanici \"%s %s\" tarafindan odunc alindi!\n", 
                        kitaplar[i].ad, kullanicilar[kullaniciID - 1].isim, kullanicilar[kullaniciID - 1].soyisim);
                    printf("Kalan stok: %d\n", kitaplar[i].stok);
                } else {
                    printf("\nGecersiz Kullanici ID!\n");
                }
            } else {
                printf("\nStokta yeterli kitap yok!\n");
            }
            bulundu = 1;
            break;
        }
    }

    if (!bulundu) {
        printf("\nKitap bulunamadi!\n");
    }

    return kitapSayisi;
}

int main() {
    struct Kitap kitaplar[100];
    struct Kullanici kullanicilar[100];
    int kitapSayisi = 0;
    int kullaniciSayisi = 0;

    int secim;

    do {
        printf("\nKUTUPHANE YONETIM SISTEMI\n");
        printf("1. Kitap Ekle\n");
        printf("2. Kitaplari Listele\n");
        printf("3. Kitap Ara\n");
        printf("4. Kullanici Ekle\n");
        printf("5. Kullanicilari Listele\n");
        printf("6. Kitap Odunc Al\n");
        printf("0. Cikis\n");
        printf("Seciminizi yapin: ");
        scanf("%d", &secim);

        switch (secim) {
            case 1:
                kitapSayisi = kitapEkle(kitaplar, kitapSayisi);
                break;
            case 2:
                kitapSayisi = kitapListele(kitaplar, kitapSayisi);
                break;
            case 3:
                kitapSayisi = kitapAra(kitaplar, kitapSayisi);
                break;
            case 4:
                kullaniciSayisi = kullaniciEkle(kullanicilar, kullaniciSayisi);
                break;
            case 5:
                kullaniciSayisi = kullaniciListele(kullanicilar, kullaniciSayisi);
                break;
            case 6:
                kitapSayisi = kitapOduncAl(kitaplar, kitapSayisi, kullanicilar, kullaniciSayisi);
                break;
            case 0:
                printf("Program sonlandiriliyor...\n");
                break;
            default:
                printf("Gecersiz secim!\n");
        }
    } while (secim != 0);

    return 0;
}
