# Rune ile Byte

- `rune` aslında `int32`’nin takma adı (*alias’ı*).
- `byte` aslında `uint8`’in takma adı.

| Tip | Değer |
| --- | -----:|
| `int32` | `-2147483648` ile `2147483647` arasında değer taşır. |
| `uint8` | `0` ile `255` arasında değer taşır. |

`uğur` 4 harfli bir isim. `ğ` ise aslında `8 bit` için `2 byte`’lık bir değer.
Halbuki `rune` ile `32 bit`’lik değer taşıyabildiğimiz için yani içinde `32 bit`’lik
değerler tutan bir **slice** olduğu için, `rune` olarak **4 karakter** olan isim,
`byte` olarak **5 karakter** olur :)

```go
package main

import "fmt"

func main() {
	s := "uğur" // ğ önemli

	fmt.Printf("%10T %[1]v\n", s)
	fmt.Printf("%10T %[1]v\n", []rune(s))
	fmt.Printf("%10T %[1]v\n", []byte(s))
}

//  string uğur
// []int32 [117 287 117 114]     // 4 karakter
// []uint8 [117 196 159 117 114] // 5 karakter
```