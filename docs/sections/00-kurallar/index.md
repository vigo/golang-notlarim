# Dil Kuralları

## Unicode

Go, otomatik olarak `UTF-8` karakter dönüşüm formatı kullanıyor. Bu şu anlama
geliyor; kod içinde Türkçe değişken adı (*variable name/identifier*)
kullanılabilir:

```go
kullanıcıAdı := "uğur"
```

tamamen geçerli (*valid*) bir ifade olmasına rağmen kullanılmasa iyi olur. Hangi
tür karakterler kullanılabilir?

- Unicode kampsamındaki tüm karakterler ve `_` karakteri
- `0`’dan `9`’a kadar 10’luk (*decimal*) sayı sistemi için
- `0`’dan `7`’ye kadar 8’lik (*octal*) sayı sistemi için
- `0`’dan `9`’a ve `A`’dan `F`’e kadar 16’lık (*hexadecimal*) sayı sistemi için

kullanılabilir.

Keza kaynak kod da `UTF-8` olarak kaydedilmelidir. Geliştirme yaptığımız `main.go`
dosyasının da karakter tipi (*encoding type*) `UTF-8` olmalıdır.

---

## Anahtar Kelimeler

Toplam **25** tane anahtar kelimeden oluşur.

```go
break        default      func         interface    select
case         defer        go           map          struct
chan         else         goto         package      switch
const        fallthrough  if           range        type
continue     for          import       return       var
```

Bunlara ek olarak;

- Mantıksal sabitler (*boolean constants*) için; `true`, `false`
- Sayısal sabit (*integer constants*) için; `iota`
- Ön tanımlı işaretçi olrak (*predeclared identifier*); `nil`

Tipler için;

```go
int      int8     int16    int32      int64
uint     uint8    uint16   uint32     uint64
uintptr  float32  float64  complex64  complex128
bool     byte     rune     string     error
```

Fonksiyonlar için;

```go
make     len   new   append copy     close
complex  real  imag  panic  recover  delete
```

gibi kelimeler de bulunur.

---

## Operatörler ve Noktalama İşaretleri

Matematik işlemleri, mantık işlemleri, gruplama, bit işlemleri ve benzeri
operasyonlarda kullanabileceğimiz operatör karakterleri:

```go
+    &     +=    &=     &&    ==    !=    (    )
-    |     -=    |=     ||    <     <=    [    ]
*    ^     *=    ^=     <-    >     >=    {    }
/    <<    /=    <<=    ++    =     :=    ,    ;
%    >>    %=    >>=    --    !     ...   .    :
     &^          &^=          ~
```

---

## İşaretçiler (Identifiers)

@wip

---
