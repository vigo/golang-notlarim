# Zero Value’ler

Tipler, otomatik olarak, kendi zero value’leri ile `initialize` edilir. Yani;
`var s string` dendiği zaman, `s` otomatik olarak `string`’in zero value’sü olan
`""` değerini alır ve artık `s`’in değeri boş string; `""` olur.

`var` anahtar kelimesini görünce **declare and initialize** oluyor diye
düşünmeli.

| Tip | Zero Value’su |
| --- | ---------: |
| `string` | `""` |
| `int` | `0` |
| `float64` | `0` |
| `rune` | `0` |
| `byte` | `0` |
| `struct{}` | `{}` |
| `[]int` | `[]` |
| `map[string]struct{}` | `map[]` |
| `*int` | `nil` |
| `interface{}` | `nil` |
| `func()` | `nil` |
| `chan struct{}` | `nil` |

Byte cinsinden kapladıkları hafıza alanları:

```go
package main

import (
	"fmt"
	"os"
	"text/tabwriter"
	"unsafe"
)

var (
	s   string
	r   rune
	b   byte
	i   int
	ii  *int
	f   float64
	ff  func()
	eif interface{}
	ss  struct{}
	ch  chan struct{}
	slc []struct{}
	mp  map[string]struct{}
)

func main() {
	w := tabwriter.NewWriter(os.Stdout, 0, 0, 0, ' ', tabwriter.AlignRight|tabwriter.Debug)

	fmt.Fprintf(w, "string\t%v\tbytes\n", unsafe.Sizeof(s))
	fmt.Fprintf(w, "rune\t%v\tbytes\n", unsafe.Sizeof(r))
	fmt.Fprintf(w, "byte\t%v\tbytes\n", unsafe.Sizeof(b))
	fmt.Fprintf(w, "int\t%v\tbytes\n", unsafe.Sizeof(i))
	fmt.Fprintf(w, "*int\t%v\tbytes\n", unsafe.Sizeof(ii))
	fmt.Fprintf(w, "float64\t%v\tbytes\n", unsafe.Sizeof(f))
	fmt.Fprintf(w, "function\t%v\tbytes\tnil?\t%t\n", unsafe.Sizeof(ff), ff == nil)
	fmt.Fprintf(w, "interface{}\t%v\tbytes\tnil?\t%t\n", unsafe.Sizeof(eif), eif == nil)
	fmt.Fprintf(w, "struct{}\t%v\tbytes\n", unsafe.Sizeof(ss))
	fmt.Fprintf(w, "chan struct{}\t%v\tbytes\tnil?\t%t\n", unsafe.Sizeof(ch), ch == nil)
	fmt.Fprintf(w, "[]struct{}\t%v\tbytes\tnil?\t%t\n", unsafe.Sizeof(slc), slc == nil)
	fmt.Fprintf(w, "map[string]struct{}\t%v\tbytes\tnil?\t%t\n", unsafe.Sizeof(mp), mp == nil)

	w.Flush()
}

//              string|16|bytes
//                rune| 4|bytes
//                byte| 1|bytes
//                 int| 8|bytes
//                *int| 8|bytes
//             float64| 8|bytes
//            function| 8|bytes|nil?|true
//         interface{}|16|bytes|nil?|true
//            struct{}| 0|bytes
//       chan struct{}| 8|bytes|nil?|true
//          []struct{}|24|bytes|nil?|true
// map[string]struct{}| 8|bytes|nil?|true
```

## Word Büyüklüğü (*size*)

**Integer** ve **Pointer**’ları hafızaya yerleştirmek için (*memory allocation*)
kullanılan ölçü **word**’dür. Aynı Amiga 68000 assembly’deki gibi; `byte`,
`word`, `long-word` ...

- 32 bit işlemci için `4 byte` tahis edilir.
- 64 bit işlemci için `8 byte` tahis edilir.
