Bu notlarda Kullanılan Kaynak;

https://developer.apple.com/library/content/documentation/Swift/Conceptual/Swift_Programming_Language/

Öncelikle Swift nedir ondan bahsetmek istiyorum. Swift iOS, macOS, watchOs ve tvOS icin uygulama geliştirmede kullanılan Apple tarafından geliştirilmiş yazılım türüdür.
 Swift'in bir çok bölümü C ve Objective-C'de yaptıklarınızdan tanıdıkk gelecektir.


Kodlara örnek vermek için klasik "Hello World" terimini kullanalım.

print("Hello, world") şeklinde yazabiliriz.

Veya String birlestirerek de yazılabilir.

var helloString = "Hello"
var worldString = "World"
var commaString = ", "
print(helloString + commaString + worldString);


Değişkenler ?

Sabit değişkenler (constant) let, değişkenler (variable) var ile tanımlanır. Sabit değişkenlere bir değer atanır ve kodun çeşitli yerlerinde kullanılabilir.

var Degisken = 42
Değişken = 50
let SDegisken = 42

Swift’te değişkeni tipini belirtmeden tanımlayabiliyoruz. Derleyici o değiskene atadığımız ilk değerde o deiğişkenin tipini belirliyor. var myVariable dediğimizde myVariable‘in tipi belli değildir. myVariable = 50 dediğimizde derleyici myVariable değişkeninin tipini integer olarak ayarlar.

Değişkenin ilk değeri değişkenin tipinin belirlenmesinde yeterli bilgi içermiyorsa aşağıdaki gibi bir kullanımlar kendimiz ayarlayabiliriz. (Explicit kullanım)

let explicitDouble: Double = 70

explicitDouble sabit değişkeninin tipi Double olarak ayarlanıyor.

Değişkenler Sting içinde \() ile yazılır.(Rubydeki #{} gibi)

Örnek;

let apples = 3
let oranges = 5
let appleSummary = "I have \(apples) apples."
let fruitSummary = "I have \(apples + oranges) pieces of fruit."

Bu koda çıktu olarak I have 3 apples ve I haves 8 pieces of fruit seklinde string verecek bize.


Arrayler ve Dictionaryler

Yazarken [] kullanıruz/.

Örnek 

var alinacaklar = ["mama", "peceteler", "hoparlor", "fotokopi kagidi"]
alinacaklar[1] = "kolonya"
 
var meslekler = [
    "Enes": "Denizci",
    "Osman": "Reklamci",
]
meslekler["Kerim"] = "Petshop"


alinacaklar[1] = "mama" burada mama dan kaç tane alacağımızı int olarak belirttik.

"Enes": "Denizci",
"Osman": "Reklamci",

Burada Enesi Denizci, Osmani Reklamci olarak tanımladık.

meslekler["Kerim"] = "Petshop" burada yeni eleman ekledik.

Boş array ve dictionary olusturulması:

let emptyArray = [String]()
let bosDictionary = Dictionary<String, Float>()

köşeli parantez icinde tipini belirtiyoruz.


Temel Array Tipleri

Temel değişkenleri tipini belirterek (explicit) veya belirtmeden (implicit) tanımlayabiliyoruz. Kesirli sayılar için Double ve Float‘i, boolean değerler için (true/false olabilir) Bool‘u kullanıyoruz.

Örnek verelim;

let freedom1 = 4.99
let freedom1Explicit: Double = 7.99
 
let freedom3 = 4.99
let freedom4: Float = 4.99
 
let reklamVarMi = true
let reklamVarMiExplicit: Bool = false
 
let sunucu = "KodBilenFamily"
let sunucuExplicit: String = "KodBilenFamily"


Kontrol durumları

Kontrol durumlarında if ve switch, döngü için for-in, for, while, and do-while kullanabiliriz. Parantez kullanımı opsiyonel bırakılmış, küme parantezi kullanımı zorunlu.

Örnek;

var skor = 52
var takimSkoru = 0
        
if skor > 50 {
	takimSkoru += 3
} else {
	takimSkoru += 1
}
 
print(takimSkoru);

burada skoru 52 olarak atadık, takım skorunu ise 0 olarak atadık ve şunu dedik;
Eğer skor 50'den büyükse takım skorunun mevcut skoru + 3 olarak verdik.
Başka bir durum söz konusu ise (eşitlik veya küçük olması gibi) mevcut sayıya 1 ekleyecek.
En sonda Takım skorunu yazacak. Skoru 52 atadığımız için çıktı da bize 3 verecek.

Aynı değişken icin birden fazla if kontrolu yapılacağı durumlarda switch tercih edilebilir:

Örnek;

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

interestingNumbers Dictionary tipi içindeki numaraları kontrol ederek en büyük sayıyı ve o sayının hangi dizi içinde olduğunu buluyor

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

Burada tekli sayıları, Fibonacci sayı dizisi ve Çift sayılari tanımladık.
en büyük sayıyı 0 olarak tanımladık ve eğer sayı enbuyuk'den buyükse serie turle, enbuyuk sayıda sayı ile eşitlenir. En son olarak serie ve sayi yazdırılır. yani Cift ve 25 yazar. 

while ile do-While döngüsü arasındaki fark; kodun while döngüsüne hiç girmeme ihtimali olmasına ragmen, do-While döngüsüne en az bir kere girecek olmasıdır. Bir baska deyişle while döngüsünün statement’i false ise kod while  hic girmeden çalışmaya döngüden sonraki statement’tan devam edecektir. Ama do-While döngüsünde bir kere döngünün içine girip ondan sonra while statement’ini kontrol edeceğ için en az bir kere döngüye girmiş olacaktır.

Örnek;

var n = 2
while n < 100 {
    n = n * 2
}
 
var m = 2
do {
    m = m * 2
} while m < 100

Burada n yi 2 ye eşitledik. Ardından n 100 den küçükkse n yi n yi ikiyle çarpıyor.

Do kısmında 2 olan m yi m * 2 ye yani 2 * 2 eşitledik taki bu işlem m 100'e eşit olana veya büyüyene kadar.

döngülerin index kullanarak aşağıdaki gibi bir kullanımı da olabilir. Her iki döngü de aynı işi yapmaktadır.

Örnek;

	var firstForLoop = 0
for i in 0..<4 {
    firstForLoop += i
}
 
var secondForLoop = 0
for var i = 0; i < 4; ++i {
    secondForLoop += i
}

Loop olayını tam anlayamadım örneksiz kalmasın diye internetten bir örnek buldum diye açıklayamadığım için özür dilerim.


3 günde öğrenebildiğim kadarını öğrendim. Benim hatamdı senin verdiğin gün başlamadım ödev'e, ciddi olduğunu anlamamıştım özür dilerim bu konu hakkında. Projede kalırsam eğer tüm vaktimi ve dikkatimi ayıracağım. Umarım yeteri kadar doğru anlatmışımdır KodBilen Okduğun için teşekkürler Küçüktür Üç.
