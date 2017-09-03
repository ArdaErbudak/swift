Bu notlarda Kullanilan Kaynak;

https:developer.apple.com/library/content/documentation/Swift/Conceptual/Swift_Programming_Language/

Oncelikle Swift nedir ondan bahsetmek istiyorum. Swift iOS, macOS, watchOs ve tvOS icin uygulama gelistirmede kullanilan Apple tarafindan gelistirilmis yazilim turudur.
 Swift'in bir cok bolumu C ve Objective-C'de yaptiklarinizdan tanidik gelecektir.


Kodlara ornek vermek icin klasik "Hello World" terimini kullanalim.

print("Hello, world") seklinde yazabiliriz.

Veya String birlestirerek de yazilabilir.

var helloString = "Hello"
var worldString = "World"
var commaString = ", "
print(helloString + commaString + worldString);


Degiskenler ?

Sabit degiskenler (constant) let, degiskenler (variable) var ile tanimlanir. Sabit degiskenlere bir deger atanir ve kodun cesitli yerlerinde kullanilabilir.

var Degisken = 42
Degisken = 50
let SDegisken = 42

Swift’te degiskeni tipini belirtmeden tanimlayabiliyoruz. Derleyici o degiskene atadigimiz ilk degerde o degiskenin tipini belirliyor. var myVariable dedigimizde myVariable‘in tipi belli degildir. myVariable = 50 dedigimizde derleyici myVariable degiskeninin tipini integer olarak ayarlar.

Degiskenin ilk degeri degiskenin tipinin belirlenmesinde yeterli bilgi icermiyorsa asagidaki gibi bir kullanimlar kendimiz ayarlayabiliriz. (Explicit kullanim)

let explicitDouble: Double = 70

explicitDouble sabit degiskeninin tipi Double olarak ayarlaniyor.

Degiskenler Sting icinde \() ile yazilir.(Rubydeki #{} gibi)

let apples = 3
let oranges = 5
let appleSummary = "I have \(apples) apples."
let fruitSummary = "I have \(apples + oranges) pieces of fruit."

Bu koda cikti olarak I have 3 apples ve I haves 8 pieces of fruit seklinde string verecek bize.


Arrayler ve Dictionaryler

Yazarken [] kullaniyoruz/.

Ornek 

var alinacaklar = ["mama", "peceteler", "hoparlor", "fotokopi kagidi"]
alinacaklar[1] = "kolonya"
 
var meslekler = [
    "Enes": "Denizci",
    "Osman": "Reklamci",
]
meslekler["Kerim"] = "Petshop"


alinacaklar[1] = "kolonya" burada kolonya dan kac tane alacagimizi int olarak belirttik.

"Enes": "Denizci",
"Osman": "Reklamci",

Burada Enesi Denizci, Osmani Reklamci olarak tanimladik.

meslekler["Kerim"] = "Petshop" burada yeni eleman ekledik.

Bos array ve dictionary olusturulmasi:

let emptyArray = [String]()
let bosDictionary = Dictionary<String, Float>()

koseli parantez icinde tipini belirtiyoruz.


Temel Array Tipleri

Temel degiskenleri tipini belirterek (explicit) veya belirtmeden (implicit) tanimlayabiliyoruz. Kesirli sayilar icin Double ve Float‘i, boolean degerler icin (true/false olabilir) Bool‘u kullaniyoruz.

Ornek verelim;

let freedom1 = 4.99
let freedom1Explicit: Double = 7.99
 
let freedom3 = 4.99
let freedom4: Float = 4.99
 
let reklamVarMi = true
let reklamVarMiExplicit: Bool = false
 
let sunucu = "KodBilenFamily"
let sunucuExplicit: String = "KodBilenFamily"


Kontrol durumlari

Kontrol durumlarinda if ve switch, dongu icin for-in, for, while, and do-while kullanabiliriz. Parantez kullanimi opsiyonel birakilmis, kume parantezi kullanimi zorunlu.

Ornek;

var skor = 52
var takimSkoru = 0
        
if skor > 50 {
	takimSkoru += 3
} else {
	takimSkoru += 1
}
 
print(takimSkoru);

burada skoru 52 olarak atadik, takim skorunu ise 0 olarak atadik ve sunu dedik;
Eger skor 50'den buyukse takim skorunun mevcut skoru + 3 olarak verdik.
Baska bir durum soz konusu ise (esitlik veya kucuk olmasi gibi{enes tsk}) mevcut sayiya 1 ekleyecek.
En sonda Takim skorunu yazacak. Skoru 52 atadigimiz icin cikti da bize 3 verecek.

Ayni degisken icin birden fazla if kontrolu yapilacagi durumlarda switch tercih edilebilir:

Ornek;

let renk = "turuncu"
var evRengi: String = "";
 
switch renk {
case "mavi":
    evRengi = "It is a blue house."
case "kirmizi", "yesil":
    evRengi = "Bu ev kirmizi"
case let c where c.hasSuffix("low"):
    evRengi = "Bu ev sari"
default:
    evRengi = "Bu ev boyasiz"
}
 
print(evRengi);

--------

interestingNumbers Dictionary tipi icindeki numaralari kontrol ederek en buyuk sayiyi ve o sayinin hangi dizi icinde oldugunu buluyor

let interestingNumbers = [
    "tekli": [2, 3, 5, 7, 11, 13],
    "Fibonacci": [1, 1, 2, 3, 5, 8],
    "cift": [1, 4, 9, 16, 25],
]

var enbuyuk = 0
var serie = ""
for (tur, sayilar) in interestingNumbers {
    for sayi in sayilar {
        if sayi > enbuyuk {
            serie = tur
            enbuyuk = sayi
        }
    }
}

print(serie);
print(sayi);

Burada tekli sayilari, Fibonacci sayi dizisi ve Cift sayilari tanimladik.
en buyuk sayiyi 0 olarak tanimladik ve eger sayi enbuyuk'den buyukse serie turle enbuyuk sayida sayi ile esitlenir. En son olarak serie ve sayi yazdirilir. yani Cift ve 25 yazar. 

while ile do-While dongusu arasindaki fark; kodun while dongusune hic girmeme ihtimali olmasina ragmen, do-While dongusune en az bir kere girecek olmasidir. Bir baska deyisle while dongusunun statement’i false ise kod while dongusune hic girmeden calismaya donguden sonraki statement’tan devam edecektir. Ama do-While dongusunde bir kere dongunun icine girip ondan sonra while statement’ini kontrol edecegi icin en az bir kere donguye girmis olacaktir.

Ornek;

var n = 2
while n < 100 {
    n = n * 2
}
 
var m = 2
do {
    m = m * 2
} while m < 100

Burada n yi 2 ye esitledik. Ardindan n 100 den kucukse n yi n yi ikiyle carpiyor.
Ar

Dongulerin index kullanarak asagidaki gibi bir kullanimi da olabilir. Her iki dongu de aynı isi yapmaktadir.

Ornek;

	var firstForLoop = 0
for i in 0..<4 {
    firstForLoop += i
}
 
var secondForLoop = 0
for var i = 0; i < 4; ++i {
    secondForLoop += i
}

Loop olayini tam anlayamadim ornegi internetten buldum eksik kalmasin diye acikalayamadigim icin ozur dilerim.


3 gunde ogrenebildigim kadarini ogrendim. Umarim dogru anlatmisimdir KodBilen Tesekkurler Okdugun icin Kucuktur Uc.
