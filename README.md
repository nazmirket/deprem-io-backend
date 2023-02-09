# deprem-io-backend

## Nasıl deploy edilir

* Docker dosyasını kullanın
* Env variable olarak MONGOURL kullanın
* Container Portu 8080

## Yardımları listeleme (GET)
istenen yardımları listeler
/yardim 
localhost:8080/yardim?page=1&limit=1

## Yardımiste Ekleme (POST)
Json Yolla
localhost:8080/yardim
* /models/yardimModel.js e bak 
ÖRNEK JSON POSTU
```
{
    "yardimTipi": "İlaç",
    "adSoyad": "John Doe",
    "telefon": "555-555-5555",
    "adres": "123 Main St",
    "adresTarifi": "Apartment 4B",
    "acilDurum": "kritik",
    "fizikiDurum": "Hasar görmüş",
    "tweetLink": "https://twitter.com/example",
    "fields-status": "test-status",
     "fields-yenialan": "ekstrabilgi"

```

## YardımEt ekleme (GET)
insanların sağladığı yardımları listeler
localhost:8080/yardimet

## YardımEt ekleme (POST)
Json Yolla
localhost:8080/yardimet

```
{
    "yardimTipi": "Yolcu Taşıma",
    "adSoyad": "John Doe",
    "telefon": "1234567890",
    "sehir": "Istanbul",
    "hedefSehir": "Ankara",
    "aciklama": "Need transportation to Ankara",
    "fields-status": "test-status",
     "fields-yenialan": "ekstrabilgi"
      }
```

## Fields alanını kullanımı

post olarak fields-{burası aalanı adı}: value şeklinde datayı gönderin onunları fields objesi altında birleştirip db ye kayddedecek

örneğin fiels-yardimalani: "ankara" şu şekilde döner
 ```
fields: {
    yardimalani: "ankara"
}

 ```


## Not
Opsiyonel her türlü yardım isteme ve yardımEt kısmına eklenecek özellikler için
fields alanını kullanın isteidğiniz gibi json objesi post edebilirsiniz 

## Cache i temizleme
/cache/flushall

## cache i görme 

/cache/getstats

## iletisim (POST)

localhost:8080/iletisim
```
{
   
    "adSoyad": "jo2hn",
    "telefon": "123",
    "email": "email@email.com",
    "mesaj": "mesaj"

      }
```

## TODO:

* Yeni data eklenince tüm cache i temizliyor onun düzeltilmesi lazım sadece ilgili cache temizlenecek
* İp logging kısmını biri kontrol etsin
* Filter kısmında yazılan queryi isim, adres telefon gibi tüm yerlerde arıyor ama araya boşluk konup birden fazla paramatere yollarsa çalışmaz
* export scriptlerinde fields kısmında bug var ama acil değil kullanılacaksa bakılır şuan çalışıyor 

## Endpoint Listsi

* /yardim (POST/GET)
* /yardimet (POST/GET)
* /ara-yardimet (/GET)
* /ara-yardim (GET)
* /yardim/:id (GET)
* /yardimet/:id (GET)
* /iletisim (POST)  

## Scripts 

* exportYardimEtCsv.js
`node scripts/exportYardimEtCsv.js`
YardimEt datasını csv export eder 

