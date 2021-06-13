# Akar Persamaan Non-Linier

Persamaan non-linier dapat diartikan sebagai persamaan yang tidak mengandung syarat seperti persamaan linier, sehingga persamaan non-linier dapat merupakan:

1. Persamaan yang memiliki pangkat selain satu (misal: \(x^2\))
2. Persamaan yang mempunyai produk dua variabel (misal: \(xy\))

Dalam penyelesaian persamaan non-linier diperlukan akar-akar persamaan non-linier, dimana akar sebuah persamaan non-linier \(f\left(x\right)=0\) merupakan nilai \(x\) yang menyebabkan nilai \(f\left(x\right)\) sama dengan nol. Dalam hal ini dapat disimpulkan bahwa akar-akar penyelesaian persamaan non-linier merupakan titik potong antara kurva \(f\left(x\right)\) dengan sumbu \(x\).

Ilustrasi penjelasan tersebut ditampilkan pada Gambar [7.1](https://bookdown.org/moh_rosidi2610/Metode_Numerik/rootfinding.html#fig:root).

![Penyelesaian persamaan non-linier.](https://bookdown.org/moh_rosidi2610/Metode_Numerik/images/root.PNG)

Gambar 7.1: Penyelesaian persamaan non-linier.

Contoh sederhana dari penentuan akar persamaan non-linier adalah penentuan akar persamaan kuadratik. Secara analitik penentuan akar persamaan kuadratik dapat dilakukan menggunakan Persamaan [(7.1)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/rootfinding.html#eq:kuadratik).

*x*1,2=−*b*±√*b*2−4*a*2*a*

Untuk masalah yang lebih rumit, penyelesaian analitik sudah tidak mungkin dilakukan. Metode numerik dapat digunakan untuk menyelesaikan masalah yang lebih kompleks. Untuk mengetahui apakah suatu persamaan non-linier memiliki akar-akar penyelesaian atau tidak, diperlukan analisa menggunakan Teorema berikut:

**Teorema 7.1 (root)** Suatu range x=[a,b] mempunyai akar bila f(a) dan f(b) berlawanan tanda atau memenuhi f(a).f(b)<0

Untuk memahami teorema tersebut perhatikan ilustrasi pada Gambar [7.2](https://bookdown.org/moh_rosidi2610/Metode_Numerik/rootfinding.html#fig:Bolzano).

![Ilustrasi teorema Bolzano.](https://bookdown.org/moh_rosidi2610/Metode_Numerik/images/Bolzano.png)

Gambar 7.2: Ilustrasi teorema Bolzano.

Pada Chapter [7](https://bookdown.org/moh_rosidi2610/Metode_Numerik/rootfinding.html#rootfinding) ini, akan dilakukan sejumlah pembahasan antara lain:

- penentuan akar persamaan dengan metode tertutup
- penentuan akar persamaan dengan metode terbuka
- fungsi-fungsi `R` untuk mementukan akar persamaan non-linier
- studi kasus

## 7.1 Metode Tertutup

Metode tertutup disebut juga metode *bracketing*. Disebut sebagai metode tertutup karena dalam pencarian akar-akar persamaan non-linier dilakukan dalam suatu selang [*a*,*b*][a,b].

### 7.1.1 Metode Tabel

Penyelesaian persamaan non-linier menggunakan metode tabel dilakukan dengan membagi persamaan menjadi beberapa area, dimana untuk *x*=[*a*,*b*]x=[a,b] dibagi sebanyak *N*N bagian dan pada masing-masing bagian dihitung nilai *f*(*x*)f(x) sehingga diperoleh nilai *f*(*x*)f(x) pada setian *N*N bagian.

Bila nilai *f*(*x**k*)=0f(xk)=0 atau mendekati nol, dimana *a*≤*k*≤*b*a≤k≤b, maka dikatakan bahwa *x**k*xk adalah penyelesaian persamaan *f*(*x*)f(x). Bila tidak ditemukan, dicari nilai *f*(*x**k*)f(xk) dan *f*(*x**k*+1)f(xk+1) yang berlawanan tanda. Bila tidak ditemukan, maka persamaan tersebut dapat dikatakan tidak mempunyai akar untuk rentang [*a*,*b*][a,b].

Bila akar persamaan tidak ditemukan, maka ada dua kemungkinan untuk menentukan akar persamaan, yaitu:

1. Akar persamaan ditentukan oleh nilai mana yang lebih dekat. Bila *f*(*x**k*)≤*f*(*x**k*+1)f(xk)≤f(xk+1), maka akarnya *x**k*xk. Bila *f*(*x**k*+1)≤*f*(*x**k*)f(xk+1)≤f(xk), maka akarnya *x**k*+1xk+1.
2. Perlu dicari lagi menggunakan rentang *x*=[*x**k*,*x**k*+1]x=[xk,xk+1].

Secara grafis penyelesaian persamaan non-linier menggunakan metode table disajikan pada Gambar [7.3](https://bookdown.org/moh_rosidi2610/Metode_Numerik/rootfinding.html#fig:tabelviz).

![Ilustrasi metode tabel.](https://bookdown.org/moh_rosidi2610/Metode_Numerik/images/tabelviz.PNG)

Gambar 7.3: Ilustrasi metode tabel.

------

**Algoritma Metode Tabel**

1. Definisikan fungsi *f*(*x*)f(x)
2. Tentukan rentang untuk *x*x yang berupa batas bawah *a*a dan batas atas *b*b.
3. Tentukan jumlah pembagi *N*N
4. Hitung step pembagi

*h*=*b*+*a**N*

1. Untuk *i*=0i=0 s/d *N*N, hitung:

*x**i*=*a*+*i*.*h*

*y**i*=*f*(*x**i*)

1. Untuk *i*=0i=0 s/d *N*N, dimana

- Bila *f*(*x*)=0f(x)=0, maka akarnya *x**k*xk
- Bila *f*(*a*)*f*(*b*)<0f(a)f(b)<0, maka:
  - *f*(*x**k*)≤*f*(*x**k*+1)f(xk)≤f(xk+1), maka akarnya *x**k*xk
  - Bila tida, *x**k*+1xk+1 adalah penyelesaian atau dapat dikatakan penyelesaian berada diantara *x**k*xk dan *x**k*+1xk+1.

------

Kita dapat membuat suatu fungsi pada `R` untuk melakukan proses iterasi pada metode Tabel. Fungsi `root_table()` akan melakukan iterasi berdasarkan step algoritma 1 sampai 5. Berikut adalah sintaks yang digunakan:

```
root_table <- function(f, a, b, N=20){
    h <- abs((a+b)/N)
    x <- seq(from=a, to=b, by=h)
    fx <- rep(0, N+1)
    for(i in 1:(N+1)){
      fx[i] <- f(x[i])
    }
    data <- data.frame(x=x, fx=fx)
    return(data)
}
```

### Metode Biseksi

Prinsip metode bagi dua adalah mengurung akar fungsi pada interval x=[a,b]x=[a,b] atau pada nilai xx batas bawah aa dan batas atas bb. Selanjutnya interval tersebut terus menerus dibagi 2 hingga sekecil mungkin, sehingga nilai hampiran yang dicari dapat ditentukan dengan tingkat toleransi tertentu. Untuk lebih memahami metode biseksi, perhatikan visualisasi pada Gambar [7.5](https://bookdown.org/moh_rosidi2610/Metode_Numerik/rootfinding.html#fig:biseksi).

![Ilustrasi metode biseksi.](https://bookdown.org/moh_rosidi2610/Metode_Numerik/images/biseksi.png)

Gambar 7.5: Ilustrasi metode biseksi.

Metode biseksi merupakan metode yang paling mudah dan paling sederhana dibanding metode lainnya. Adapun sifat metode ini antara lain:

1. Konvergensi lambat
2. Caranya mudah
3. Tidak dapat digunakan untuk mencari akar imaginer
4. Hanya dapat mencari satu akar pada satu siklus.

------

**Algoritma Metode Biseksi**

1. Definisikan fungsi f(x)f(x)
2. Tentukan rentang untuk xx yang berupa batas bawah aa dan batas atas bb.
3. Tentukan nilai toleransi ee dan iterasi maksimum NN
4. Hitung f(a)f(a) dan f(b)f(b)
5. Hitung:

x=a+b2(7.5)(7.5)x=a+b2

1. Hitung f(x)f(x)
2. Bila f(x).f(a)<0f(x).f(a)<0, maka b=xb=x dan f(b)=f(x)f(b)=f(x). Bila tidak, a=xa=x dan f(a)=f(x)f(a)=f(x)
3. Bila |b−a|<e|b−a|<e atau iterasi maksimum maka proses dihentikan dan didapatkan akar=xx, dan bila tidak ulangi langkah 6.
4. Jika sudah diperoleh nilai dibawah nilai toleransi, nilai akar selanjutnya dihitung berdasarkan Persamaan [(7.5)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/rootfinding.html#eq:biseksi1) dengan nilai aa dan bb merupakan nilai baru yang diperoleh dari proses iterasi.

------

Berdasarkan algoritma tersebut, kita dapat menyusun suatu fungsi pada `R` yang dapat digunakan untuk melakukan iterasi tersebut. Fungsi `root_bisection()` merupakan fungsi yang telah penulis susun untuk melakukan iterasi menggunakan metode biseksi. Berikut adalah sintaks dari fungsi tersebut:

```
root_bisection <- function(f, a, b, tol=1e-7, N=100){
  iter <- 0
  fa <- f(a)
  fb <- f(b)
  
  while(abs(b-a)>tol){
    iter <- iter+1
    if(iter>N){
      warning("iterations maximum exceeded")
      break
    }
    x <- (a+b)/2
    fx <- f(x)
    if(fa*fx>0){
      a <- x
      fa <- fx
    } else{
      b <- x
      fb <- fx
    }
  }
  
  # iterasi nilai x sebagai return value
  root <- (a+b)/2
  return(list(`function`=f, root=root, iter=iter))
}
```

### Metode Regula Falsi

Metode regula falsi merupakan metode yang menyerupai metode biseksi, dimana iterasi dilakukan dengan terus melakukan pembaharuan rentang untuk memperoleh akar persamaan. Hal yang membedakan metode ini dengan metode biseksi adalah pencarian akar didasarkan pada slope (kemiringan) dan selisih tinggi dari kedua titik rentang. Titik pendekatan pada metode regula-falsi disajikan pada Persamaan [(7.6)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/rootfinding.html#eq:rf).

x=f(b).a−f(a).bf(b)−f(a)(7.6)(7.6)x=f(b).a−f(a).bf(b)−f(a)

Ilustrasi dari metode regula falsi disajikan pada Gambar [7.6](https://bookdown.org/moh_rosidi2610/Metode_Numerik/rootfinding.html#fig:regula).

![Ilustrasi metode regula falsi.](https://bookdown.org/moh_rosidi2610/Metode_Numerik/images/regula.png)

Gambar 7.6: Ilustrasi metode regula falsi.

------

**Algoritma Metode Regula Falsi**

1. Definisikan fungsi f(x)f(x)
2. Tentukan rentang untuk xx yang berupa batas bawah aa dan batas atas bb.
3. Tentukan nilai toleransi ee dan iterasi maksimum NN
4. Hitung f(a)f(a) dan f(b)f(b)
5. Untuk iterasi i=1i=1 s/d NN

- Hitung nilai xx berdasarkan Persamaan [(7.6)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/rootfinding.html#eq:rf)
- Hitung f(x)f(x)
- Hitung error=|f(x)|error=|f(x)|
- Jika f(x).f(a)<0f(x).f(a)<0, maka b=xb=x dan f(b)=f(x)f(b)=f(x). Jika tidak, a=xa=x dan f(a)=f(x)f(a)=f(x).

1. Akar persamaan adalah xx

------

Fungsi `root_rf()` didasarkan pada langkah-langkah di atas. Sintaks fungsi tersebut adalah sebagai berikut:

```
root_rf <- function(f, a, b, tol=1e-7, N=100){
  iter <- 1
  fa <- f(a)
  fb <- f(b)
  x <- ((fb*a)-(fa*b))/(fb-fa)
  fx <- f(x)
  
  while(abs(fx)>tol){
    iter <- iter+1
    if(iter>N){
      warning("iterations maximum exceeded")
      break
    }
    if(fa*fx>0){
      a <- x
      fa <- fx
    } else{
      b <- x
      fb <- fx
    }
    x <- (fb*a-fa*b)/(fb-fa)
    fx <- f(x)
  }
  
  # iterasi nilai x sebagai return value
  root <- x
  return(list(`function`=f, root=root, iter=iter))
}
```

##  Metode Terbuka

Metode terbuka merupakan metode yang menggunakan satu atau dua tebakan awal yang tidak memerlukan rentang sejumlah nilai. Metode terbuka terdiri dari beberapa jenis yaitu metode iterasi titik tetap, metode Newton-Raphson, dan metode Secant.

### Metode Iterasi Titik Tetap

Metode iterasi titik tetap merupakan metode penyelesaian persamaan non-linier dengan cara menyelesaikan setiap variabel xx yang ada dalam suatu persamaan dengan sebagian yang lain sehingga diperoleh x=g(x)x=g(x) untuk masing-masing variabel xx. Sebagai contoh, untuk menyelesaikan persamaan x+ex=0x+ex=0, maka persamaan tersebut perlu diubah menjadi x=exx=ex atau g(x)=exg(x)=ex. Secara grafis metode ini diilustrasikan seperti Gambar [7.7](https://bookdown.org/moh_rosidi2610/Metode_Numerik/rootfinding.html#fig:fixpointiter).

![Ilustrasi metode iterasi titik tetap.](https://bookdown.org/moh_rosidi2610/Metode_Numerik/images/fixpointiter.png)

Gambar 7.7: Ilustrasi metode iterasi titik tetap.

------

**Algoritma Metode Iterasi Titik Tetap**

1. Definisikan f(x)f(x) dan g(x)g(x)
2. Tentukan nilai toleransi ee dan iterasi masimum (N)
3. Tentukan tebakan awal x0x0
4. Untuk iterasi i=1i=1 s/d NN atau f(xiterasi)≥e→xi=g(xi−1)f(xiterasi)≥e→xi=g(xi−1), Hitung f(xi)f(xi)
5. Akar persamaan adalah xx terakhir yang diperoleh

------

FUngsi `root_fpi()` dapat digunakan untuk melakukan iterasi dengan argumen fungsi berupa persamaan non-linier, nilai tebakan awal, nilai toleransi, dan jumlah iterasi maksimum. Berikut adalah sintaks fungsi tersebut:

```
root_fpi <- function(f, x0, tol=1e-7, N=100){
  iter <- 1
  xold <- x0
  xnew <- f(xold)
  
  while(abs(xnew-xold)>tol){
    iter <- iter+1
    if(iter>N){
      stop("No solutions found")
    }
    xold <- xnew
    xnew <- f(xold)
  }
  
  root <- xnew
  return(list(`function`=f, root=root, iter=iter))
}
```

**Contoh 7.4** Selesaikan persamaan non-linier pada Contoh [7.2](https://bookdown.org/moh_rosidi2610/Metode_Numerik/rootfinding.html#exm:biseksexmp) menggunakan metode iterasi titik tetap?

**Jawab**:

Untuk menyelesaikan persamaan non-linier tersebut kita perlu mentransformasi persamaan non-linier tersebut terlebih dahulu.

xe−x+1=0 →x=−1e−xxe−x+1=0 →x=−1e−x

Untuk tebakan awal digunakan nilai x=−1x=−1

x1=−1e1=−2,718282x1=−1e1=−2,718282

Nilai xx tersebut selanjutnya dijadikan nilai input pada iterasi selanjutnya:

x2=−1e2,718282=−0,06598802x2=−1e2,718282=−0,06598802

iterasi terus dilakukan sampai diperoleh |xi+1−xi|≤e|xi+1−xi|≤e.

Untuk mempercepat proses iterasi kita dapat menggunakan bantuan fungsi `root_fpi()`. Berikut adalah sintaks yang digunakan:

```
root_fpi(function(x){-1/exp(-x)}, x0=-1)
## $`function`
## function (x) 
## {
##     -1/exp(-x)
## }
## <bytecode: 0x0000000018c9ee40>
## 
## $root
## [1] -0.5671
## 
## $iter
## [1] 29
```

Berdasarkan hasil iterasi diperoleh nilai x=−0,5671433x=−0,5671433 dengan jumlah iterasi yang diperlukan sebanyak 2929 kali. Jumlah iterasi akan bergantung dengan nilai tebakan awal yang kita berikan. Semakin dekat nilai tersebut dengan akar, semakin cepat nilai akar diperoleh.

###  Metode Newton-Raphson

Metode Newton-Raphson merupakan metode penyelesaian persamaan non-linier dengan menggunakan pendekatan satu titik awal dan mendekatinya dengan memperhatikan slope atau gradien. titik pendekatan dinyatakan pada Persamaan [(7.7)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/rootfinding.html#eq:rootnr).

xn+1=xn−f(xn)f′(xn)(7.7)(7.7)xn+1=xn−f(xn)f′(xn)

Ilustrasi metode Newton-Raphson disajikan pada Gambar [7.8](https://bookdown.org/moh_rosidi2610/Metode_Numerik/rootfinding.html#fig:nrviz).

![Ilustrasi metode Newton-Raphson.](https://bookdown.org/moh_rosidi2610/Metode_Numerik/images/nrviz.png)

Gambar 7.8: Ilustrasi metode Newton-Raphson.

------

**Algoritma Metode Newton-Raphson**

1. Definisikan f(x)f(x) dan f′(x)f′(x)
2. Tentukan nilai toleransi ee dan iterasi masimum (N)
3. Tentukan tebakan awal x0x0
4. Hitung f(x0)f(x0) dan f′(x0)f′(x0)
5. Untuk iterasi i=1i=1 s/d NN atau |f(x)|≥e|f(x)|≥e, hitung xx menggunakan Persamaan [(7.7)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/rootfinding.html#eq:rootnr)
6. Akar persamaan merupakan nilai xixi terakhir yang diperoleh.

------

Fungsi `root_newton()` merupakan fungsi yang dibuat menggunakan algoritma di atas. Fungsi tersebut dituliskan pada sintaks berikut:

```
root_newton <- function(f, fp, x0, tol=1e-7, N=100){
  iter <- 0
  xold<-x0
  xnew <- xold + 10*tol
  
  while(abs(xnew-xold)>tol){
    iter <- iter+1
    if(iter>N){
      stop("No solutions found")
    }
    xold<-xnew
    xnew <- xold - f(xold)/fp(xold)  
  }
  
  root<-xnew
  return(list(`function`=f, root=root, iter=iter))
}
```

**Contoh 7.5** Selesaikan persamaan non-linier x−e−x=0x−e−x=0 menggunakan metode Newton-Raphson?

**Jawab**:

Untuk dapat menggunakan metode Newton-Raphson, terlebih dahulu kita perlu memperoleh turunan pertama dari persamaan tersebut.

f(x)=x−e−x→f′(x)=1+e−xf(x)=x−e−x→f′(x)=1+e−x

Tebakan awal yang digunakan adalah x=0x=0.

f(x0)=0−e−0=−1f(x0)=0−e−0=−1f′(x0)=1+e−0=2f′(x0)=1+e−0=2

Hitung nilai xx baru:

x1=x0−f(x0)f′(x0)=0−−12=0,5x1=x0−f(x0)f′(x0)=0−−12=0,5

Untuk mempercepat proses iterasi, kita dapat menggunakan fungsi `root_newton()`. Berikut adalah sintaks yang digunakan:

```
root_newton(function(x){x-exp(-x)},
            function(x){1+exp(-x)},
              x0=0)
## $`function`
## function (x) 
## {
##     x - exp(-x)
## }
## <bytecode: 0x000000001c59e158>
## 
## $root
## [1] 0.5671
## 
## $iter
## [1] 5
```

Berdasarkan hasil iterasi diperoleh akar penyelesaian persamaan non-linier adalah x=0,5671433x=0,5671433 dengan jumlah iterasi yang diperlukan adalah 55 iterasi.

Dalam penerapannya metode Newton-Raphson dapat mengalami kendala. Kendala yang dihadapi adalah sebagai berikut:

1. titik pendekatan tidak dapat digunakan jika merupakan titik ekstrim atau titik puncak. Hal ini disebabkan pada titik ini nilai f′(x)=0f′(x)=0. Untuk memahaminya perhatikan ilustasi yang disajikan pada Gambar [7.9](https://bookdown.org/moh_rosidi2610/Metode_Numerik/rootfinding.html#fig:nrviz2). Untuk menatasi kendala ini biasanya titik pendekatan akan digeser.

![Ilustrasi titik pendekatan di titik puncak.](https://bookdown.org/moh_rosidi2610/Metode_Numerik/images/nrviz2.png)

Gambar 7.9: Ilustrasi titik pendekatan di titik puncak.

1. Sulit memperoleh penyelesaian ketika titik pendekatan berada diantara 2 titik stasioner. Untuk memahami kendala ini perhatikan Gambar [7.10](https://bookdown.org/moh_rosidi2610/Metode_Numerik/rootfinding.html#fig:nrviz3). Untuk menghindarinya, penentuan titik pendekatan dapat menggunakan bantuan metode tabel.

![Ilustrasi titik pendekatan diantara 2 titik stasioner.](https://bookdown.org/moh_rosidi2610/Metode_Numerik/images/nrviz3.png)

Gambar 7.10: Ilustrasi titik pendekatan diantara 2 titik stasioner.

1. Turunan persamaan sering kali sulit untuk diperoleh (tidak dapat dikerjakan dengan metode analitik).

### Metode Secant

Metode Secant merupakan perbaikan dari metode regula-falsi dan Newton Raphson, dimana kemiringan dua titik dinyatakan secara diskrit dengan mengambil bentuk garis lurus yang melalui satu titik. Persamaan yang dihasilkan disajikan pada Persamaan [(7.8)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/rootfinding.html#eq:secant).

y−y0=m(x−x0)(7.8)(7.8)y−y0=m(x−x0)

Nilai mm merupakan transformasi persamaan tersebut.

mn=f(xn)−f(xn−1)xn−xn−1(7.9)(7.9)mn=f(xn)−f(xn−1)xn−xn−1

Bila y=f(x)y=f(x) dan ynyn dan xnxn diketahui, maka titik ke n+1n+1 adalah:

yn+1−yn=mn(xn+1−xn)(7.10)(7.10)yn+1−yn=mn(xn+1−xn)

Bila titik xn+1xn+1 dianggap akar persamaan maka nilai yn+1=0yn+1=0, sehingga diperoleh:

−yn=mn(xn+1−xn)(7.11)(7.11)−yn=mn(xn+1−xn)

mnxn−ynmn=xn+1(7.12)(7.12)mnxn−ynmn=xn+1

atau

xn+1=xn−yn1mn(7.13)(7.13)xn+1=xn−yn1mn

xn+1=xn−f(xn)xn−xn+1f(xn)−f(xn+1)(7.14)(7.14)xn+1=xn−f(xn)xn−xn+1f(xn)−f(xn+1)

Berdasarkan Persamaan [(7.14)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/rootfinding.html#eq:secant7) diketahui bahwa untuk memperoleh akar persamaan diperlukan 2 buah titik pendekatan. Dalam buku ini akan digunakan titik pendekatan kedua merupakan titik pendekatan pertama ditambah sepuluh kali nilai toleransi.

x1=x0+10∗tol(7.15)(7.15)x1=x0+10∗tol

------

**Algoritma Metode Secant**

1. Definisikan f(x)f(x) dan f′(x)f′(x)
2. Tentukan nilai toleransi ee dan iterasi masimum (N)
3. Tentukan tebakan awal x0x0 dan x1x1
4. Hitung f(x0)f(x0) dan f(x1)f(x1)
5. Untuk iterasi i=1i=1 s/d NN atau |f(x)|≥e|f(x)|≥e, hitung xx menggunakan Persamaan [(7.14)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/rootfinding.html#eq:secant7)
6. Akar persamaan adalah nilai x yang terakhir.

------

Fungsi `root_secant()` merupakan fungsi yang penulis buat untuk melakukan iterasi menggunakan metode Secant. Berikut merupakan sintaks dari fungsi tersebut:

```
root_secant <- function(f, x, tol=1e-7, N=100){
  iter <- 0
  
  xold <- x
  fxold <- f(x)
  x <- xold+10*tol
  
  while(abs(x-xold)>tol){
    iter <- iter+1
    if(iter>N)
      stop("No solutions found")
    
    fx <- f(x)
    xnew <- x - fx*((x-xold)/(fx-fxold))
    xold <- x
    fxold <- fx
    x <- xnew
  }
  
  root<-xnew
  return(list(`function`=f, root=root, iter=iter))
}
```

**Contoh 7.6** Selesaikan persamaan non-linier pada Contoh [7.5](https://bookdown.org/moh_rosidi2610/Metode_Numerik/rootfinding.html#exm:newtonraphsonexmp) menggunakan metode Secant?

**Jawab**:

Untuk menyelesaikan persamaan tersebut digunakan nilai pendekatan awal x0=0x0=0 dan x1=0+10∗10−7=10−6x1=0+10∗10−7=10−6.

f(x0)=0−e−0=−1f(x0)=0−e−0=−1

f(x1)=10−6−e−10−6=−0,999998f(x1)=10−6−e−10−6=−0,999998

Hitung nilai x2x2 dan f(x2)f(x2).

x2=0+0,99999810−6−0−0,999998+1=0,499999x2=0+0,99999810−6−0−0,999998+1=0,499999

Untuk mempercepat proses iterasi kita dapat menggunakan fungsi `root_secant()` pada `R`. Berikut sintaks yang digunakan:

```
root_secant(function(x){x-exp(-x)}, x=0)
## $`function`
## function (x) 
## {
##     x - exp(-x)
## }
## <bytecode: 0x000000001b4fc6b0>
## 
## $root
## [1] 0.5671
## 
## $iter
## [1] 6
```

Berdasarkan hasil iterasi diperoleh nilai akar penyelesaian adalah x=0,5671433x=0,5671433 dengan iterasi dilakukan sebanyak 66 kali.

Secara umum metode Secant menawarkan sejumlah keuntungan dibanding metode lainnya. Pertama, seperti metode Newton-Raphson dan tidak seperti metode tertutup lainnya, metode ini tidak memerlukan rentang pencarian akar penyelesaian. Kedua, tidak seperti metode Newton-Raphson, metode ini tidak memerlukan pencarian turunan pertama persamaan non-linier secara analitik, dimana tidak dapat dilakukan otomasi pada setiap kasus.

Adapun kerugian dari metode ini adalah berpotensi menghasilkan hasil yang tidak konvergen sama seperti metode terbuka lainnya. Selain itu, kecepatan konvergensinya lebih lambat dibanding metode Newton-Raphson.

## Penyelesaian Persamaan Non-Linier Menggunakan Fungsi `uniroot` dan `uniroot.all`

Paket `base` pada `R` menyediakan fungsi `uniroot()` untuk mencari akar persamaan suatu fungsi pada rentang spesifik. Fungsi ini menggunakan metode Brent yaitu kombinasi antara *root bracketing*, biseksi, dan interpolasi invers kuadrat. Format fungsi tersebut secara sederhana adalah sebagai berikut:

```
uniroot(f, interval, tol=.Machine$double.eps^0.25, 
        maxiter=1000)
```

> **Catatan**:
>
> - **f**: persamaan non-linier
> - **interval**: vektor interval batas bawah dan atas
> - **tol**: nilai toleransi
> - **maxiter**: iterasi maksimum

Berikut adalah contoh penerapan fungsi `uniroot()`:

```
uniroot(function(x){x*exp(-x)+1},
        interval=c(-1,0), tol=1e-7)
## $root
## [1] -0.5671
## 
## $f.root
## [1] 1.533e-08
## 
## $iter
## [1] 7
## 
## $init.it
## [1] NA
## 
## $estim.prec
## [1] 5e-08
```

Berdasarkan hasil iterasi diperoleh akar persamaan tersebut adalah −0,5671433−0,5671433 dengan jumlah iterasi sebanyak 77 iterasi dan tingkat presisi sebesar 5e−085e−08.

Fungsi lain yang dapat digunakan untuk mencari akar persamaan adalah `uniroot.all()` dari paket `rootSolve`. Fungsi ini mengatasi kelemahan dari `uniroot()`, dimana `uniroot()` tidak bekerja jika fungsi hanya menyentuh dan tidak melewati sumbu nol y=0y=0. Untuk memahaminya perhatikan contoh berikut:

```
uniroot(function(x){sin(x)+1}, c(-pi,0))
```

Bandingkan dengan sintaks berikut:

```
uniroot(function(x){sin(x)+1}, c(-pi,-pi/2))
## $root
## [1] -1.571
## 
## $f.root
## [1] 0
## 
## $iter
## [1] 0
## 
## $init.it
## [1] NA
## 
## $estim.prec
## [1] 0
```

Untuk menggunakan fungsi `uniroot.all()`, jalankan sintaks berikut:

```
library(rootSolve)
```

Jalankan kembali fungsi dan rentang di mana `uniroot()` tidak dapat bekerja:

```
uniroot.all(function(x){sin(x)+1}, c(-pi,0))
## [1] -1.571
```

## Akar Persamaan Polinomial Menggunakan Fungsi `polyroot`

Fungsi `polyroot()` pada paket `base` dapat digunakan untuk memperoleh akar dari suatu polinomial. Algortima yang digunakan dalam fungsi tersebut adalah algoritma Jenkins dan Traub.

Untuk dapat menggunakannya kita hanya perlu memasukkan vektor koefisien dari polinomial. Pengisian elemen dalam vektor dimulai dari variabel dengan pangkat tertinggi menuju variabel dengan pangkat terendah. Berikut adalah contoh bagaimana fungsi `polyroot()` digunakan untuk mencari akar polinomial f(x)=x2+1f(x)=x2+1:

```
polyroot(c(1,0,1))
## [1] 0+1i 0-1i
```

Contoh lainnya adalah mencari akar polinomial f(x)=4x2+5x+6f(x)=4x2+5x+6:

```
polyroot(c(4,5,6))
## [1] -0.4167+0.7022i -0.4167-0.7022i
```

Pembaca dapat mencoba membuktikan hasil yang diperoleh tersebut menggunakan metode analitik.

## Studi Kasus

Penerapan penyelesaian sistem persamaan non-linier banyak dijumpai dalam berbagai kasus di bidang lingkungan. Pada bagian ini penulis tidak akan menjelaskan seluruhnya. Penulis hanya akan menjelaskan penerapannya pada sebuah persamaan yaitu Hukum Bernoulli.

### Persamaan Van Der Walls

### 7.5.2 Hukum Bernoulli

Misalkan terdapat sebuah saluran dengan penampang sesuai dengan Gambar [7.11](https://bookdown.org/moh_rosidi2610/Metode_Numerik/rootfinding.html#fig:bernoulli).

![Aliran fluida pada sebuah pipa.](https://bookdown.org/moh_rosidi2610/Metode_Numerik/images/bernoulli.jpeg)

Gambar 7.11: Aliran fluida pada sebuah pipa.

Berdasarkan hukum Bernoulli, maka diperoleh persamaan berikut:

Q22gb2h20+h0=Q22gb2h2+h+H(7.16)(7.16)Q22gb2h02+h0=Q22gb2h2+h+H

Persamaan tersebut dapat dilakukan transformasi menjadi persamaan berikut:

f(h)=h3+(H−Q22gb2h20−h0)h2+Q22gb2=0(7.17)(7.17)f(h)=h3+(H−Q22gb2h02−h0)h2+Q22gb2=0

Data-data terkait saluran tersebut adalah sebagai berikut:

- Q=1,2 m3det Q=1,2 m3det = volume aliran fluida tiap satuan waktu
- g=9,81 ms2g=9,81 ms2 =percepatan gravitasi
- b=1,8 mb=1,8 m =lebar pipa
- h0=0,6 mh0=0,6 m =ketinggian air maksimum
- H=0,075 mH=0,075 m =tinggi pelebaran pipa
- hh = ketinggian air

Kita dapat menggunakan pendekatan numerik untuk menentukan hh. Pada studi kasus ini tidak dijelaskan lokasi dimana akar penyelesaian berada, sehingga metode terbuka seperti Secant cukup sesuai untuk menyelesaikannya:

Berikut adalah persamaan yang baru setelah seluruh data dimasukkan kedalam tiap variabelnya:

f(h)=h3+(0,075−1,222×9,81×1,82×0,62−0,6)h2+1,222×9,81×1,82=0f(h)=h3+(0,075−1,222×9,81×1,82×0,62−0,6)h2+1,222×9,81×1,82=0

Untuk penyelesaiannya penulis akan memberikan tebakan awal nilai h=h0=0,6h=h0=0,6. Berikut adalah sintaks penyelesaian menggunakan metode secant:

```
f <- function(h){
  (h^3) + ((0.075-((1.2^2)/(2*9.81*(1.8^2)*(0.6^2))))*h^2)+ (1.2^2/(2*9.81*(1.8^2)))
}
root_secant(f, 0.6)
## $`function`
## function (h) 
## {
##     (h^3) + ((0.075 - ((1.2^2)/(2 * 9.81 * (1.8^2) * (0.6^2)))) * 
##         h^2) + (1.2^2/(2 * 9.81 * (1.8^2)))
## }
## <bytecode: 0x000000001d1483f0>
## 
## $root
## [1] -0.287
## 
## $iter
## [1] 26
```

Berdasarkan hasil perhitungan diperoleh nilai h=−0,2870309h=−0,2870309 atau ketinggian air sekitar 0,3 m0,3 m dengan jumlah iterasi sebanyak 2626 kali.

Pembaca dapat mencoba menggunakan metode lain seperti metode tertutup. Untuk dapat melakukannya, pembaca perlu memperoleh rentang lokasi akar persamaan tersebut berada menggunakan metode tabel.

# Sistem Persamaan Linier 

menjelaskan mengenai cara untuk menyelesaikan sistem persamaan linier. Adapun yang akan dibahas pada *chapter* ini antara lain:

- operasi Vektor dan matriks
- Metode Eliminasi Gauss
- Metode Dekomposisi matriks

### Operasi Vektor

Misalkan saja diberikan vektor uu dan vv yang ditunjukkan pada Persamaan [(6.1)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/linearaljabar.html#eq:vectoruv).

u=⎡⎢ ⎢ ⎢ ⎢ ⎢ ⎢⎣u1u2⋮un⎤⎥ ⎥ ⎥ ⎥ ⎥ ⎥⎦dan v =⎡⎢ ⎢ ⎢ ⎢ ⎢ ⎢⎣v1v2⋮vn⎤⎥ ⎥ ⎥ ⎥ ⎥ ⎥⎦(6.1)(6.1)u=[u1u2⋮un]dan v =[v1v2⋮vn]

Jika kita menambahkan atau mengurangkan nilai elemen vektor dengan suatu skalar (konstanta yang hanya memiliki besaran), maka operasi penjumlahan/pengurangan akan dilakukan pada setiap elemen vektor.

u±x=⎡⎢ ⎢ ⎢ ⎢ ⎢ ⎢⎣u1u2⋮un⎤⎥ ⎥ ⎥ ⎥ ⎥ ⎥⎦±x=⎡⎢ ⎢ ⎢ ⎢ ⎢ ⎢⎣u1±xu2±x⋮un±x⎤⎥ ⎥ ⎥ ⎥ ⎥ ⎥⎦(6.2)(6.2)u±x=[u1u2⋮un]±x=[u1±xu2±x⋮un±x]

Jika kita melakukan penjumlahan pada vektor uu dan vv, maka operasi akan terjadi pada masing-masing elemen dengan indeks yang sama.

u±v=⎡⎢ ⎢ ⎢ ⎢ ⎢ ⎢⎣u1u2⋮un⎤⎥ ⎥ ⎥ ⎥ ⎥ ⎥⎦±v =⎡⎢ ⎢ ⎢ ⎢ ⎢ ⎢⎣v1v2⋮vn⎤⎥ ⎥ ⎥ ⎥ ⎥ ⎥⎦=⎡⎢ ⎢ ⎢ ⎢ ⎢ ⎢⎣u1±v1u2±v2⋮un±vn⎤⎥ ⎥ ⎥ ⎥ ⎥ ⎥⎦(6.3)(6.3)u±v=[u1u2⋮un]±v =[v1v2⋮vn]=[u1±v1u2±v2⋮un±vn]

Untuk lebih memahami operasi tersebut, berikut penulis berikan contoh penerapannya pada `R`:

```
u <- seq(1,5)
v <- seq(6,10)

# penjumlahan
u+v
## [1]  7  9 11 13 15
# penguranga
u-v
## [1] -5 -5 -5 -5 -5
```

Bagaimana jika kita melakukan operasi dua vektor, dimaana salah satu vektor memiliki penjang yang berbeda?. Untuk memnjawab hal tersebut, perhatikan sintaks berikut:

```
x <- seq(1,2)
u+x
## Warning in u + x: longer object length is not a
## multiple of shorter object length
## [1] 2 4 4 6 6
```

Berdasarkan contoh tersebut, `R` akan mengeluarkan peringatan yang menunjukkan operasi dilakukan pada vektor dengan panjang berbeda. `R` akan tetap melakukan perhitungan dengan menjumlahkan kembali vektor uu yang belum dijumlahkan dengan vektor xx sampai seluruh elemen vektor uu dilakukan operasi penjumlahan.

Operasi lain yang dapat dilakukan pada vektor adalah menghitung *inner product* dan panjang vektor. Inner product dihitung menggunakan Persamaan [(6.4)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/linearaljabar.html#eq:innerproduct).

u.v=n∑i=1u1v1+u2v2+⋯+unvn(6.4)(6.4)u.v=∑i=1nu1v1+u2v2+⋯+unvn

Panjang vektor atau vektor yang telah dinormalisasi dihitung menggunakan Persamaan [(6.5)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/linearaljabar.html#eq:panjangvektor)

|u|=√u21+u22+⋯+u2n(6.5)(6.5)|u|=u12+u22+⋯+un2

Berikut adalah contoh bagaimana cara menghitung `inner product` dan panjang vektor menggunakan `R`:

```
# inner product
u%*%v
##      [,1]
## [1,]  130
# panjang vektor u
sqrt(sum(u*u))
## [1] 7.416
```

### Operasi matriks

Misalkan kita memiliki 2 buah matriks AA dan BB.

A=⎡⎢ ⎢ ⎢ ⎢ ⎢ ⎢⎣a1.1a1.2⋯a1.na2.1a2.2⋯a2.n⋮⋮⋱⋮am.1am.2⋯am.n⎤⎥ ⎥ ⎥ ⎥ ⎥ ⎥⎦dan B=⎡⎢ ⎢ ⎢ ⎢ ⎢ ⎢⎣b1.1b1.2⋯b1.nb2.1b2.2⋯b2.n⋮⋮⋱⋮bm.1bm.2⋯bm.n⎤⎥ ⎥ ⎥ ⎥ ⎥ ⎥⎦(6.6)(6.6)A=[a1.1a1.2⋯a1.na2.1a2.2⋯a2.n⋮⋮⋱⋮am.1am.2⋯am.n]dan B=[b1.1b1.2⋯b1.nb2.1b2.2⋯b2.n⋮⋮⋱⋮bm.1bm.2⋯bm.n]

Jika salah satu matriks tersebut dijumlahkan atau dikurangkan dengan skalar.

A±x=⎡⎢ ⎢ ⎢ ⎢ ⎢ ⎢⎣a1.1a1.2⋯a1.na2.1a2.2⋯a2.n⋮⋮⋱⋮am.1am.2⋯am.n⎤⎥ ⎥ ⎥ ⎥ ⎥ ⎥⎦±x=⎡⎢ ⎢ ⎢ ⎢ ⎢ ⎢⎣a1.1±xa1.2±x⋯a1.n±xa2.1±xa2.2±x⋯a2.n±x⋮⋮⋱⋮am.1±xam.2±x⋯am.n±x⎤⎥ ⎥ ⎥ ⎥ ⎥ ⎥⎦(6.7)(6.7)A±x=[a1.1a1.2⋯a1.na2.1a2.2⋯a2.n⋮⋮⋱⋮am.1am.2⋯am.n]±x=[a1.1±xa1.2±x⋯a1.n±xa2.1±xa2.2±x⋯a2.n±x⋮⋮⋱⋮am.1±xam.2±x⋯am.n±x]

Jika kedua matriks AA dan BB saling dijumlahkan atau dikurangkan. Perlu diperhatikan bahwa penjumlahan dua buah matriks hanya dapat dilakukan pada matriks dengan ukuran yang seragam.

A±B=⎡⎢ ⎢ ⎢ ⎢ ⎢ ⎢⎣a1.1a1.2⋯a1.na2.1a2.2⋯a2.n⋮⋮⋱⋮am.1am.2⋯am.n⎤⎥ ⎥ ⎥ ⎥ ⎥ ⎥⎦±⎡⎢ ⎢ ⎢ ⎢ ⎢ ⎢⎣b1.1b1.2⋯b1.nb2.1b2.2⋯b2.n⋮⋮⋱⋮bm.1bm.2⋯bm.n⎤⎥ ⎥ ⎥ ⎥ ⎥ ⎥⎦=⎡⎢ ⎢ ⎢ ⎢ ⎢ ⎢⎣a1.1±b1.1a1.2±b1.2⋯a1.n±b1.na2.1±b2.1a2.2±b2.2⋯a2.n±b2.n⋮⋮⋱⋮am.1±bm.1am.2±bm.2⋯am.n±bm.n⎤⎥ ⎥ ⎥ ⎥ ⎥ ⎥⎦(6.8)(6.8)A±B=[a1.1a1.2⋯a1.na2.1a2.2⋯a2.n⋮⋮⋱⋮am.1am.2⋯am.n]±[b1.1b1.2⋯b1.nb2.1b2.2⋯b2.n⋮⋮⋱⋮bm.1bm.2⋯bm.n]=[a1.1±b1.1a1.2±b1.2⋯a1.n±b1.na2.1±b2.1a2.2±b2.2⋯a2.n±b2.n⋮⋮⋱⋮am.1±bm.1am.2±bm.2⋯am.n±bm.n]

Untuk lebih memahaminya, berikut disajikan contoh operasi penjumlahan pada matriks:

```
A <- matrix(1:9,3)
B <- matrix(10:18,3)
C <- matrix(1:6,3)

# penjumlahan dengan skalar
A+1
##      [,1] [,2] [,3]
## [1,]    2    5    8
## [2,]    3    6    9
## [3,]    4    7   10
# penjumlahan A+B
A+B
##      [,1] [,2] [,3]
## [1,]   11   17   23
## [2,]   13   19   25
## [3,]   15   21   27
# penjumlahan
A+C
```

Operasi pehitungan lain yang penting pada matriks adalah operasi perkalian matriks. Perlu diperhatikan bahwa untuk perkalian matriks, jumlah kolom matriks sebelah kiri harus sama dengan jumlah baris pada matriks sebelah kanan. Perkalian antara dua matriks disajikan pada Persamaan [(6.9)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/linearaljabar.html#eq:kalimatrik).

Am.n×Bn.r=ABm.r(6.9)(6.9)Am.n×Bn.r=ABm.r

Pada `R` perkalian matriks dilakukan menggunakan operator `%*%`. Berikut adalah contoh perkalian matriks pada `R`:

```
# Perkalian matriks
A%*%B
##      [,1] [,2] [,3]
## [1,]  138  174  210
## [2,]  171  216  261
## [3,]  204  258  312
```

## Operasi Baris Elementer

Terdapat tiga buah operasi dasar pada baris matriksoperasi baris elementer. Ketiga operasi ini akan menjadi dasar operasi *sub-chapter* selanjutnya. Ketiga operasi dasar tersebut antara lain:

1. ***Row Scalling\***. Mengalikan baris matriks dengan konstanta bukan nol.
2. ***Row Swaping\***. Menukar urutan baris pada sebuah matriks (contoh: menukar baris 1 dengan baris 2 dan sebaliknya).
3. ***Row Replacement\***. Baris matriks diganti dengan hasil penjumlahan atau pengurangan baris matriks tersebut dengan baris matriks lainnya, dimana baris matriks lainnya yang akan dijumlahkan/dikurangkan dengan matriks tersebut telah dilakukan proses *row scalling*. Luaran yang diperoleh pada umumnya adalah nilai nol pada baris matriks awal atau akhir.

Ketiga proses tersebut akan terjadi secara berulang, khusunya jika kita hendak mengerjakan sistem persamaan linier menggunakan algoritma eliminasi Gauss. Untuk mempermudah proses tersebut, kita dapat membuat masing-masing fungsi untuk masing-masing operasi tersebut. Algoritma fungsi-fungsi tersebut selanjutnya menjadi dasar penyusunan algoritma fungsi-fungsi eliminasi Gauss dan dekomposisi matriks yang akan dijelaskan pada *chapter* selanjutnya.

Fungsi *row scalling* pada `R` dapat dituliskan pada sintaks berikut:

```
scale_row <- function(m, row, k){
 m[row, ] <- m[row, ]*k
 return(m)
}
```

Berikut adalah contoh penerapannya:

```
# membuat matriks A
(A <- matrix(1:15, nrow=5))
##      [,1] [,2] [,3]
## [1,]    1    6   11
## [2,]    2    7   12
## [3,]    3    8   13
## [4,]    4    9   14
## [5,]    5   10   15
# lakukan scaling pada row 2 dengan nilai 10
scale_row(m=A, row=2, 10)
##      [,1] [,2] [,3]
## [1,]    1    6   11
## [2,]   20   70  120
## [3,]    3    8   13
## [4,]    4    9   14
## [5,]    5   10   15
```

### Eliminasi Gauss-Jordan

etode eliminasi Gauss-Jordan membentuk matriks menjadi bentuk *reduced row echelon form*. Metode ini merupakan pengembangan metode eliminasi Gauss, dimana matriks sebelah kiri *augmented matrix* diubah menjadi matriks diagonal (lihat Persamaan [(6.17)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/linearaljabar.html#eq:gaussjordan)).

⎡⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢⎣a1,1a1,2a1,3⋯a1,nb1a2,1a2,2a2,3⋯a2,nb2a3,1a3,2a3,3⋯a3,nb3⋮⋮⋮⋱⋮am,1am,2am,3⋯am,nbn⎤⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥⎦⟹⎡⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢⎣100⋯0d1010⋯0d2001⋯0d3⋮⋮⋮⋱⋮000⋯1dn⎤⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥⎦(6.17)(6.17)[a1,1a1,2a1,3⋯a1,nb1a2,1a2,2a2,3⋯a2,nb2a3,1a3,2a3,3⋯a3,nb3⋮⋮⋮⋱⋮am,1am,2am,3⋯am,nbn]⟹[100⋯0d1010⋯0d2001⋯0d3⋮⋮⋮⋱⋮000⋯1dn]

Sehingga penyelesaian persamaan linier tersebut adalah nilai d1,d2,d3,…,dnd1,d2,d3,…,dn dan atau:

x1=d1x2=d2x3=d3⋯⋯⋯⋯⋯⋯⋯⋯xn=dn(6.18)(6.18)x1=d1x2=d2x3=d3⋯⋯⋯⋯⋯⋯⋯⋯xn=dn

**Contoh 6.3** Selesaikan sistem persamaan berikut:

x1+x2=32x1+4x2=8x1+x2=32x1+4x2=8

**Jawab**:

*Augmented matrix* dari persamaan linier tersebut adalah sebagai berikut:

[113248][113248]

Operasi baris elementer selanjutnya dilakukan pada matriks tersebut.

[113248]B2−2B1⟹[113022][113248]B2−2B1⟹[113022]

[113022]B22⟹[113011][113022]B22⟹[113011]

[113011]B1−B2⟹[102011][113011]B1−B2⟹[102011]

Penyelesaian persamaan linier tersebut adalah sebagai berikut:

x1=2 dan x2=1x1=2 dan x2=1

------

**Algoritma Metode Eliminasi Gauss-Jordan**

1. Masukkan matriks AA dan vektor BB beserta ukurannya nn
2. Buat *augmented matrix* [A|B][A|B] namakan dengan AA
3. Untuk baris ke-ii dimana i=1i=1 s/d nn

- Perhatikan apakah nilai ai.iai.i sama dengan nol:
  - **Bila ya**: pertukakan baris ke-ii dan baris ke-i+k≤ni+k≤n, dimana ai+k.iai+k.i tidak sama dengan nol, bila tidak ada berarti perhitungan tidak bisa dilanjutkan dan proses dihentikan dengan tanpa penyelesaian.
  - **Bila tidak**: lanjutkan
- Jadikan nilai diagonalnya menjadi satu dengan cara untuk setiap kolom kk dimana k=1k=1 s/d n+1n+1, hitung ai.k=ai.kai.iai.k=ai.kai.i

1. Untuk baris ke-jj, dimana j=i+1j=i+1 s/d nn. Lakukan operasi baris elementer untuk kolom kk dimana k=1k=1 s/d nn.

- Hitung c=aj.ic=aj.i
- Hitung aj.k=aj.k−c.ai.kaj.k=aj.k−c.ai.k

1. Penyelesaian untuk i=ni=n s/d 1 disajikan pada Persamaan [(6.18)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/linearaljabar.html#eq:gaussjordansolution).

------

Dari algoritma tersebut, kita dapat membangun sebuah fungsi menggunakan `R`. Fungsi tersebut adalah sebagai berikut:

```
gauss_jordan <- function (a){
    m <- nrow (a)
    n <- ncol (a)
    piv <- 1
    
# cek elemen diagonal utama apakah bernilai nol
    for(row_curr in 1:m){
        if(piv <= n){
            i <- row_curr
            while(a[i, piv] == 0 && i < m){
                i <- i + 1
                if(i > m){
                    i <- row_curr
                    piv <- piv + 1
                    if(piv > n)
                        return (a)
                }
            }

# jika diagonal utama bernilai nol,lakukan row swapping
            if(i != row_curr)
                a <- swap_row(a, i, row_curr)
            
# proses pembentukan matriks reduced row echelon form
            piv_val <- a[row_curr , piv]
            a <- scale_row (a, row_curr , 1 / piv_val)
            for(j in 1: m){
                if(j != row_curr){
                    k <- a[j, piv]/a[row_curr, piv]
                    a <- replace_row (a, row_curr, j, -k)
                }
            }
            piv <- piv + 1
        }
    }
    return (a)
}
```

### Matrik Tridiagonal

Metode eliminasi Gauss merupakan metode yang sederhana untuk digunakan khususnya jika semua koefisien bukan nol berkumpul pada diagonal utama dan beberapa diagonal sekitarnya. Suatu sistem yang bersifat demikian disebut sebagai *banded* dan banyaknya diagonal yang memuat koefisien bukan nol disebut sebagai *bandwidth*. Contoh khusus yang sering dijumpai adalah matriks tridiagonal yang memiliki *bandwidth* tiga.

Proses eliminasi untuk matriks tridiagonal bersifat trivial karena dengan membentuk sebuah subdiagonal tambahan, proses substitusi mundur segera dapat dilakukan. Bentuk matriks tridiagonal disajikan pada Persamaan [(6.19)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/linearaljabar.html#eq:matrikstridiagonal).

⎡⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢⎣a1,1a1,20⋯0a2,1a2,2a2,3⋯00a3,2a3,3⋯0⋮⋮⋮⋱⋮000⋯am,n⎤⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥⎦⎡⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢⎣x1x2x3⋯xn⎤⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥⎦=⎡⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢⎣b1b2b3⋯bn⎤⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥⎦(6.19)(6.19)[a1,1a1,20⋯0a2,1a2,2a2,3⋯00a3,2a3,3⋯0⋮⋮⋮⋱⋮000⋯am,n][x1x2x3⋯xn]=[b1b2b3⋯bn]

Penyelesaian persamaan tersebut disajikan pada Persamaan [(6.20)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/linearaljabar.html#eq:solusimatrikstridiagonal).

xn=bnam.n; xi=bi−ai,j+1xi+1ai,j(6.20)(6.20)xn=bnam.n; xi=bi−ai,j+1xi+1ai,j

dimana i=n−1,n−2,…,1i=n−1,n−2,…,1.

Pada beberapa *textbook*, diagonal matriks sering dilambangkan dengan ll(diagonal bawah), dd(diagonal tengah), dan uu (diagonal atas). Bentuk matriksnya disajikan pada Persamaan [(6.21)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/linearaljabar.html#eq:matrikstridiagonal2).

⎡⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢⎣d1u20⋯0l2d2u3⋯00l3d3⋯0⋮⋮⋮⋱⋮000⋯dn⎤⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥⎦⎡⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢⎣x1x2x3⋯xn⎤⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥⎦=⎡⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢⎣b1b2b3⋯bn⎤⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥⎦(6.21)(6.21)[d1u20⋯0l2d2u3⋯00l3d3⋯0⋮⋮⋮⋱⋮000⋯dn][x1x2x3⋯xn]=[b1b2b3⋯bn]

------

**Algoritma Penyelesaian Matrik Tridiagonal**

1. Bentuk sistem persamaan linier menjadi matriks pada Persamaan [(6.21)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/linearaljabar.html#eq:matrikstridiagonal2).
2. Lakukan *foward sweep*. Setiap elemen diagonal ll dieliminasi menggunakan reduksi baris.

- Untuk i=1i=1
  - Hitung u1=u1d1u1=u1d1
  - Hitung b1=b1d1b1=b1d1
- Untuk i=2i=2 s/d n−1n−1
  - Hitung ui=uidi−li×ui−1ui=uidi−li×ui−1
  - Hitung bi=bi−li×ui−1di−li×ui−1bi=bi−li×ui−1di−li×ui−1
- Hitung bn=bn−ln×un−1dn−ln×un−1bn=bn−ln×un−1dn−ln×un−1

1. Lakukan *backward sweep*. Setiap elemen diagonal uu dilakukan eliminasi.

- Untuk i=n−1i=n−1 s/d 11
  - Hitung xn=bi−ui×xi+1xn=bi−ui×xi+1
- Hitung xn=bnxn=bn

------

Berdasarkan algoritma tersebut, kita dapat membangun sebuah fungsi pada `R`. Fungsi penyelesaian matriks tridiagonal disajikan sebagai berikut:

```
tridiagmatrix <- function (L, D, U, b){
  n <- length (D)
  L <- c(NA , L)
  
  ## forward sweep
  U[1] <- U[1] / D[1]
  b[1] <- b[1] / D[1]
  for(i in 2:(n - 1)){
      U[i] <- U[i] / (D[i] - L[i] * U[i - 1])
      b[i] <- (b[i] - L[i] * b[i - 1]) /
      (D[i] - L[i] * U[i - 1])
  }
  b[n] <- (b[n] - L[n] * b[n - 1])/(D[n] - L[n] * U[n - 1])
  
  ## backward sweep
  x <- rep.int (0, n)
  x[n] <- b[n]
  for(i in (n - 1) :1)
      x[i] <- b[i] - U[i] * x[i + 1]
  return (x)
}
```

### Penyelesaian Sistem Persamaan Linier Menggunakan Fungsi `solve()`

`R` menyediakan fungsi bawaan `solve()` untuk menyelesaiakan sistem persamaan linier. Format fungsi `solve()` adalah sebagai berikut:

```
solve(a,b)
```

> **Catatan**:
>
> - **a**: matriks koefisien atau matriks segiempat
> - **b**: vektor konstanta

Berikut adalah contoh penerapan fungsi `solve()` pada sistem persamaan linier yang disajikan pada Contoh [6.2](https://bookdown.org/moh_rosidi2610/Metode_Numerik/linearaljabar.html#exm:refexm2):

```
# memecah matriks m menjadi matriks koefisien dan vektor konstanta
a <- matrix(c(2,3,1,1,2,-5,-1,-2,4),nrow=3)
b <- c(1,1,3)

solve(a,b)
## [1] 1 2 3
```

Jika kita hanya memasukkan matriks persegi, maka output yang akan dihasilkan adalah invers dari matriks yang kita masukkan.

```
solve(a)
##      [,1] [,2]       [,3]
## [1,]    2   -1  7.401e-17
## [2,]   14   -9 -1.000e+00
## [3,]   17  -11 -1.000e+00
```

Jika kita mengalikan invers dengan matriks semula, maka akan dihasilkan output berupa matriks identitas.

```
a%*%solve(a)
##      [,1] [,2] [,3]
## [1,]    1    0    0
## [2,]    0    1    0
## [3,]    0    0    1
```

###  Penyelesaian Sistem Persamaan Linier Menggunakan Fungsi ’Solve.tridiag()`

Penyelesaian matriks tridiagonal selain menggunakan fungsi `solve()`, juga dapat menggunakan fungsi `Solve.tridiag()` dari Paket `limSolve`. Untuk menginstall dan mengaktifkan Paket tersebut, jalankan sintaks berikut:

```
install.packages("limSolve")
library(limSolve)
```

Fungsi `Solve.tridiag()` memiliki format sebagai berikut:

```
Solve.tridiag ( diam1, dia, diap1, B=rep(0,times=length(dia)))
```

> **Catatan**:
>
> - **diam1**: vektor bukan nol di bawah diagonal matriks
> - **dia**: vektor bukan nol pada diagonal matriks
> - **diap1**: vektor bukan nol di atas diagonal matriks
> - **B**: vektor konstanta

Untuk memahami penerapannya, kita akan menggunakan kembali matriks yang ada pada Contoh [6.5](https://bookdown.org/moh_rosidi2610/Metode_Numerik/linearaljabar.html#exm:tridiagexm).

```
l <- u <- c(4, 2, 3); d <- c(3, 5, 5, 5)
b <- c(20, 28, 18, 18)
Solve.tridiag(diam1=l, dia=d, diap1=u, B=b)
##      [,1]
## [1,]    4
## [2,]    2
## [3,]    1
## [4,]    3
```

### Interpolasi Polinomial 

### Interpolasi Polinomial Orde Tinggi

Dengan menggunakan dua titik, kita dapat membentuk garis lurus (linier) yang tepat pada dua titik tersebut. Masalah timbul jika selisih nilai xx kedua titik tersebut sangat kecil atau kedua titik tersebut memiliki nilai xx yang sama. Hal ini akan menyebabkan slope yang dihasilkan menjadi tidak terhingga atau garis yang terbentuk adalah garis vertikal tegak lurus.

Bagaimana jika terdapat tiga buah titik? apakah kita masih bisa menggunakan interpolasi linie?. Ya, asalkan ketiga titik tersebut membentuk pola linier atau terletak pada satu garis yang sama. Pada kenyatannya kondisi tersebut jarang terjadi, sehingga pendekatan menggunakan polinomial orde lebih tinggi diperlukan. Persamaan kuadratik (polinomial orde dua) dapat digunakan untuk membentuk persamaan polinomial pada ketiga titik tersebut, sehingga iterasi dapat dilakukan. Untuk 4 buah titik data, polinomial orde tiga dapat digunakan untuk melakukan interpolasi. Secara umum berdasarkan penjelasan tersebut, untuk nn titik data interpolasi dapat dilakukan menggunakan persamaan polinomial orde n−1n−1.

Diberikan set data berpasangan yang telah diurutkan (xi,yi)(xi,yi), fungsi interpolasi harus memenuhi persyaratan berikut:

p(xi)=yi(8.6)(8.6)p(xi)=yi

Untuk setiap ii. Sebagai tambahan, fungsi interpolasi berupa fungsi polinomial dengan bentuk umum sebagai berikut:

yi=βnxni+βn−1xn−1i+⋯+β1xi+β0(8.7)(8.7)yi=βnxin+βn−1xin−1+⋯+β1xi+β0

Persamaan [(8.7)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#eq:hointereq2) dapat dituliskan kedalam bentuk matriks yang ditampilkan pada Persamaan [(8.8)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#eq:hointereq3).

⎡⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢⎣xn1xn−11⋯x11xn2xn−12⋯x21⋮⋮⋮⋱⋮xnnxn−1n⋯xn1⎤⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥⎦⎡⎢ ⎢ ⎢ ⎢ ⎢ ⎢⎣βnβn−1⋮β0⎤⎥ ⎥ ⎥ ⎥ ⎥ ⎥⎦=⎡⎢ ⎢ ⎢ ⎢ ⎢ ⎢⎣y1y2⋮yn⎤⎥ ⎥ ⎥ ⎥ ⎥ ⎥⎦(8.8)(8.8)[x1nx1n−1⋯x11x2nx2n−1⋯x21⋮⋮⋮⋱⋮xnnxnn−1⋯xn1][βnβn−1⋮β0]=[y1y2⋮yn]

Persamaan matrik tersebut dapat dituliskan sebagai Xβ=yXβ=y. Untuk menyelesaikan persamaan tersebut (memperoleh nilai ββ), pembaca dapat membaca kembali Chapter [6](https://bookdown.org/moh_rosidi2610/Metode_Numerik/linearaljabar.html#linearaljabar). Matriks XX disebut sebagai matriks Vandemonde dan matriks tersebut mengandung sejumlah nilai xx dengan pangkat sampai dengan nn.

------

**Algoritma Interpolasi Polinomial Orde Tinggi**

1. Tentukan set titik berpasangan (x,y)(x,y) yang telah diurutkan.
2. Bentuk matriks Vandermonde sesuai dengan Persamaan [(8.8)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#eq:hointereq3).
3. Definiskan persamaan matriks Xβ=yXβ=y
4. Selesaikan persamaan matriks pada poin 3 untuk memperoleh nilai ββ
5. Definisikan persamaan polinomial berdasarkan koefisien ββ yang diperoleh
6. Lakukan substitusi xx persamaan polinomial pada poin 5 untuk memperoleh nilai yy

------

Berdasarkan algoritma poin 1 sampai 5, kita dapat membentuk suatu fungsi untuk membentuk persamaan polinomial berdasarkan Persamaan [(8.8)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#eq:hointereq3). Berikut adalah sintaks fungsi tersebut:

```
poly_inter <- function(x, y){
  if(length(x) != length(y))
    stop("Lenght of x and y vectors must be the same")
  
  n <- length(x)-1
  vandermonde <- rep(1, length(x))
  for(i in 1:n){
    xi <- x^i
    vandermonde <- cbind(vandermonde, xi)
  }
  beta <- solve(vandermonde, y)
  
  names(beta) <- NULL
  return(beta)
}
```

Diketahui koordinat 3 buah titik yaitu (-1,-2), (1,2) dan (0,1). Jika diketahui titik keempat memiliki koordinat sumbu xx sebesar -2. Lakukan interpolasi untuk menentukan koordinat sumbu yy titik keempat tersebut!

**Jawab**:

Untuk menyelesaiakn contoh soal tersebut, kita perlu terlebih dahulu membentuk matriks sesuai dengan Persamaan [(8.8)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#eq:hointereq3). Berdasarkan soal tersebut, terdapat tiga buah titik data yang diketahui, sehingga polinomial yang hendak dibentuk selanjutnya adalah polinomial berderajat 2.

⎡⎢ ⎢ ⎢⎣−12−1111211102011⎤⎥ ⎥ ⎥⎦⎡⎢ ⎢⎣β2β1β0⎤⎥ ⎥⎦=⎡⎢ ⎢⎣−221⎤⎥ ⎥⎦[−12−1111211102011][β2β1β0]=[−221]

Setelah matriks tersebut terbentuk, pembaca dapat menyelesaikannya menggunakan berbagai metode yang telah penulis jelaskan pada Chapter [6](https://bookdown.org/moh_rosidi2610/Metode_Numerik/linearaljabar.html#linearaljabar) untuk memperoleh nilai ββ.

Untuk menyelesaikan contoh soal tersebut pada `R`, kiat perlu membentuk matriks xx dan yy terlebih dahulu.

```
x <- c(-1, 1, 0)
y <- c(-2, 2, -1)
```

Koefisien persamaan polinomial dihitung menggunakan fungsi `poly_inter()`.

```
(coeff <- poly_inter(x, y))
## [1] -1  2  1
```

Berdasarkan hasil perhitungan, diperoleh nilai ββ. Nilai tersebut selanjutnya digunakan untuk membentuk persamaan polinomial. Berikut merupakan persamaan polinomial yang terbentuk:

f(x)=1x2+2x−1f(x)=1x2+2x−1

Fungsi `horner_poly()` selanjutnya digunakan untuk mengevaluasi polinomial tersebut. Berikut adalah hasil substitusi xx pada persamaan tersebut:

```
horner_poly(-2, coeff)
## [1] -1
```

Hasil yang diperoleh terlihat cukup sesuai jika kita perhatikan visualisasi ketiga titik tersebut pada Gambar [8.2](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#fig:hopoliviz).

![Interpolasi kuadratik tiga titik  (Sumber:Howard, 2017).](https://bookdown.org/moh_rosidi2610/Metode_Numerik/images/hopoliviz.png)

Gambar 8.2: Interpolasi kuadratik tiga titik (Sumber:Howard, 2017).

**Contoh 8.6** Dengan menggunakan data pada Contoh [8.4](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#exm:linterpexmp), lakukan proses perhitungan untuk membentuk persamaan polinomial menggunakan fungsi `poly_inter()`

**Jawab**:

Berdasarkan data pada Contoh [8.4](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#exm:linterpexmp), polinomial yang terbentuk merupakan polinomial derajat 1 (linier). Berikut adalah nilai koefisien yang dihasilkan dari perhitungan menggunakan fungsi `poly_inter()`.

```
x <- c(2, 0)
y <- c(3, -1)
poly_inter(x, y)
## [1] -1  2
```

Meskipun proses perhitungan menggunakan fungsi `poly_inter()` lebih rumit dibandingkan dengan fungsi `linear_poly()`, hasil perhitungan keduanya menggunakan data pada Contoh [8.4](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#exm:linterpexmp) menghasilkan hasil yang sama.

## Interpolasi Piecewise

Interpolasi dengan polinomial sering memberikan hasil yang tidak dapat diterima. Interpolasi polinomial yang dihasilkan dari sejumlah besar data titik biasanya berderajat tinggi. Polinomial berderajat tinggi pada umumnya bersifat osilatif (grafiknya naik turun secara cepat). Akibatnya, perubahan data pada interval kecil dapat menyebabkan fluktuasi besar pada keseluruhan interval. Karena alasan ini, biasanya interpolasi hanya menggunakan polinomial berderajat rendah.

Interpolasi piecewise menawarkan alternatif lain. Pada interpolasi piecewise, pada titik yang berbeda sepanjang kurva, nilai fungsi lebih mungkin lebih baik didekati menggunakan dua atau lebih interpolasi. Pada metode ini kita akan membuat fungsi interpolasi ditiap antara dua titik observasi.

Pada sub-Chapter ini akan dijelaskan 2 buah metode interpolasi piecewise, yaitu: interpolasi linier piecewise dan interpolasi kubik spline. Interpolasi pertama dilakukan menggunakan persamaan linier, sehingga kurva yang terbentuk bukan merupakan kurva kontinu. Interpolasi selanjutnya dilakukan menggunakan persamaan polinomial berderajat tinggi sehingga kurva yang dihasilkan lebih halus (tidak ada sudut siku pada setiap titik).

### Interpolasi Linier Piecewise

Interpolasi linier piecewise merupakan interpolasi yang menggunakan pendekatan interpolasi linier. Fungsi linier akan dibentuk pada setiap dua titik observasi. Untuk lebih memahaminya perhatikan kembali Gambar [8.2](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#fig:hopoliviz). Pada gambar tersebut sebelumnya kita telah membentuk persamaan kudratik untuk menghubungkan titik-titik tersebut. Dibanding menggunakan persamaan polinomial seperti kuadratik tersebut, interpolasi piecewise akan menghubungkan tiap dua titik observasi tersebut dengan garis lurus.

------

**Algoritma Interpolasi Linier Piecewise**

1. Tentukan set titik berpasangan (x,y)(x,y) yang telah diurutkan berdasarkan nilai sumbu xx.
2. Hitung mm pada setiap dua titik berdekatan menggunakan Persamaan [(8.4)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#eq:lineinter)
3. Hitung bb pada setiap dua titik berdekatan menggunakan Persamaan [(8.5)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#eq:lineinter2)
4. Definiskan fungsi linier berdasarkan nilai mm dan bb
5. Hitung yy dengan cara substitusi nilai xx pada persamaan linier untuk melakukan interpolasi nilai yy yang ingin dicari.
6. Untuk melakukan ekstrapolasi dengan titik observasi diluar rentang titik diketahui, gunakan persamaan linier yang berada pada bagian ujung terdekat dengan nilai xx yang hendak dicari nilai yy-nya.

------

Berdasarkan algoritma tersebut, kita dapat menyusun fungsi pada `R` untuk membentuk persamaan linier piecewise. Berikut adalah sintaks yang digunakan:

```
pwise_linterp <- function(x, y){
  n <- length(x)-1
  
  y <- y[order(x)]
  x <- x[order(x)]
  
  m_vec <- b_vec <- c()
  
  for(i in 1:n){
    m <- (y[i+1]-y[i]) / (x[i+1]-x[i])
    b <- y[i+1] - m*x[i+1]
    m_vec <- c(m_vec, m)
    b_vec <- c(b_vec, b)
  }
  
  return(list(b = b_vec, m = m_vec))
}
```

### Interpolasi Spline Kubik

Jika menggunakan interpolasi polinomial berderajat satu (sebuah garis) lebih dari beberapa interval merupakan peningkatan dari satu baris interpolasi, dan jika menggunakan polinomial berderajat tinggi juga merupakan peningkatan dari satu garis interpolasi tunggal, maka dapat disimpulkan bahwa penggunaan polinomial berderajat tinggi pada selang beberapa interval juga akan menjadi peningkatan dalam proses interpolasi. Dalam beberapa kasus, hal tersebut benar, tetapi kita masih menghadapi sudut tajam di mana masing-masing kurva interpolasi tergabung (interpolasi linier piecewise). Sudut tajam ini mencegah diferensiasi dan pada prakteknya tidak dapat digunakan untuk memodelkan beberapa fungsi di dunia nyata, seperti *roller coaster span*.

Interpolasi spline kubik memecahkan masalah ini. Interpolasi ini akan memberikan kurva tergabung yang halus. Hal tersebut juga membuat spline terintegrasi. Karena setiap bagian individu diwakili oleh kurva kubik (polinomial derajat 3), maka masing-masing bagian individu juga dapat dianalisis sebagai kurva kubik. Dengan asumsi ada nn titik data untuk interpolasi, kita akan mendefinisikan SiSi sebagai fungsi polinomial kubik yang mewakili kurva pada domain [xi;xi+1][xi;xi+1]. Kemudian untuk nn titik observasi, ada n−1n−1 interpolasi polinomial kubik.

Bentuk umum seri polinomial dituliskan pada Persamaan [(8.9)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#eq:pwisequb).

Si=di(x−xi)3+ci(x−xi)2+bi(x−xi)+ai(8.9)(8.9)Si=di(x−xi)3+ci(x−xi)2+bi(x−xi)+ai

Ini mengarah ke 4 nilai yang tidak diketahui tidak diketahui, yaitu: aiai, bibi, cici, dan didi pada setiap Persamaan [(8.9)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#eq:pwisequb). Oleh karena itu, ada 4(n−1)=4n−44(n−1)=4n−4 nilai yang tidak diketahui. Karena kita ingin spline membentuk garis kontinu dan dapat didiferensiasi, ada satu set persamaan yang menentukan spline kubik:

Si(xi)=yi,     i=1,……,n−1(8.10)(8.10)Si(xi)=yi,     i=1,……,n−1

Si(xi+1)=yi+1,     i=1,……,n−1(8.11)(8.11)Si(xi+1)=yi+1,     i=1,……,n−1

S′i(xi+1)=S′i+1(xi),     i=1,……,n−2(8.12)(8.12)Si′(xi+1)=Si+1′(xi),     i=1,……,n−2

S′′i(xi+1)=S′′i+1(xi),     i=1,……,n−2(8.13)(8.13)Si″(xi+1)=Si+1″(xi),     i=1,……,n−2

Persamaan [(8.10)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#eq:pwisequb2) dan [(8.11)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#eq:pwisequb3) sudah cukup jelas. Persyaratan ini memastikan bahwa jika kita mengevaluasi spline di salah satu node internal, hasil yang akan kita peroleh merupakan jawaban yang telah ditentukan, yaitu spline yang dievaluasi pada xixi untuk beberapa ii adalah yiyi, dan setiap komponen spline bergabung dengan rapi. Persamaan [(8.12)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#eq:pwisequb4) memastikan bahwa kita memiliki turunan pertama yang berkelanjutan di setiap simpul internal. Ini mencegah terbentuknya sudut tajam pada tiap node. Persamaan [(8.13)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#eq:pwisequb5) memastikan turunan kedua juga kontinu, dimana kondisi ini menguntungkan karena itu berarti turunan pertama itu sendiri dapat didiferensiasi juga.

Kondisi ini menyebabkan ada 4n−64n−6 kondisi yang harus kita penuhi. Jika 4n−44n−4 kita yang tidak diketahui dipecahkan sebagai sebuah matriks, dan akhirnya matriks tersebut akan terpecahkan, matriks akan menjadi kurang ditentukan. Kita dapat menyelesaikan kondisi tersebut dengan memasukkan dua ketentuan tambahan. Dengan splines kubik, secara normal adalah menentukan akhir di kedua ujung untuk mencapai dua kondisi tambahan. Untuk contoh ini, dua kondisi yang akan kita tambahkan adalah S′′i(xi)=0Si″(xi)=0 dan S′′i(xn)=0Si″(xn)=0. Kedua kondisi ini memastikan bahwa pada titik akhir, turunan pertamanya linier dan oleh karena itu fungsi spline berlanjut ke arah yang sudah berjalan. Interpolasi spline kubik ini disebut juga sebagai “natural spline”.

Awalnya, kita dapat melihat bahwa setiap polinomial kubik SiSi digeser ke kanan oleh unit xixi atau bergeser ke kiri jika xixi negatif. Pada xixi nilai fungsi adalah aiai yang berarti ai=yiai=yi untuk setiap nilai ii. Menyelesaikan sisa koefisien yang ada akan lebih kompleks, tetapi sekarang 3n3n tidak diketahui dengan 3n3n kondisi. Derivasi penuh tersedia dari berbagai sumber, tetapi secara garis besar dari Persamaan [(8.12)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#eq:pwisequb4) kita mendapatkan S′i(xi+1)=S′i+1Si′(xi+1)=Si+1′, kemudian S′i+1−S′i(x)=0Si+1′−Si′(x)=0, dan kita dapat mensubstitusi Persamaan [(8.9)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#eq:pwisequb) ke dalam kedua komponen, pemecahan untuk didi dalam hal ini xixi, yiyi, dan cici. Proses yang sama dapat direplikasi dengan Persamaan [(8.13)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#eq:pwisequb5) dan bibi. Hasilnya adalah matriks tridiagonal, seperti yang ada pada Chapter [6.3.3](https://bookdown.org/moh_rosidi2610/Metode_Numerik/linearaljabar.html#matriktridiagonal), yang dapat dipecahkan untuk menemukan koefisien. Terdapat sebuah matriks, A, sedemikian rupa sehingga,

AC=V(8.14)(8.14)AC=V

dimana AA merupakan matriks tridiagonal. Pada matriks tridiagonal ini (u1,u2,…,un−1)(u1,u2,…,un−1) merupakan vektor UU, dan vektor MM, LL, dan VV ditentukan dengan cara serupa. Matriks ini sedemikian rupa,

ui=li=xi+1−xi(8.15)(8.15)ui=li=xi+1−xi

kecuali pada u0=lnu0=ln. Lebih jauh, diagonal utama DD ditentukan menggunakan Persamaan [(8.16)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#eq:pwisequb8).

mi=2(xi+1−xi+xi−xi−1)(8.16)(8.16)mi=2(xi+1−xi+xi−xi−1)

kecuali pada d0=dn=1d0=dn=1. Akhirnya vektor VV ditentukan dengan Persamaan [(8.17)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#eq:pwisequb9).

vi=3(yi+1−yixi+1−xi−yi−yi−1xi−xi−1)(8.17)(8.17)vi=3(yi+1−yixi+1−xi−yi−yi−1xi−xi−1)

kecuali pada v0=vn=0v0=vn=0. Sehingga,

⎡⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢⎣m1u1000l1m2u2000l2⋱⋱000⋱⋱un−1000ln−1mn⎤⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥⎦C=⎡⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢ ⎢⎣v1v2⋮⋮vn⎤⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥ ⎥⎦(8.18)(8.18)[m1u1000l1m2u2000l2⋱⋱000⋱⋱un−1000ln−1mn]C=[v1v2⋮⋮vn]

Penyelesaian Persamaan [(8.18)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#eq:pwisequb10) akan menghasilkan vektor koefisien cc, sehingga koefisien bb dapat dihitung menggunakan Persamaan [(8.19)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#eq:pwisequb11).

bi=yi+1−yixi+1−xi−xi+1−xi3(2ci+ci+1)(8.19)(8.19)bi=yi+1−yixi+1−xi−xi+1−xi3(2ci+ci+1)

Dengan menggunakan vektor CC yang sudah diketahui, koefisien dd dapat dihitung menggunakan Persamaan [(8.20)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#eq:pwisequb12).

di=ci+1−ci3(xi+1−xi)(8.20)(8.20)di=ci+1−ci3(xi+1−xi)

------

**Algoritma Interpolasi Spline Kubik**

1. Tentukan set titik berpasangan (x,y)(x,y).
2. Tentukan koefisien aiai menggunakan Persamaan [(8.10)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#eq:pwisequb2), dimana ai=yiai=yi.
3. Hitung elemen diagonal bawah (lili) dan elemen diagonal atas (uiui) matriks tridiagonal menggunakan Persamaan [(8.15)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#eq:pwisequb7), dimana u0=ln=0u0=ln=0.
4. Hitung elemen diagonal utama (mimi) menggunakan Persamaan [(8.16)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#eq:pwisequb8), dimana d0=dn=1d0=dn=1.
5. Hitung elemen vektor VV menggunakan Persamaan [(8.17)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#eq:pwisequb9), dimana v0=vn=0v0=vn=0.
6. Susunlah elemen lili, uiui, dan mimi menjadi matriks tridiagonal AA.
7. Deifinisikan persamaan linier seperti pada Persamaan [(8.14)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#eq:pwisequb6)
8. Selesaikan sistem persamaan linier pada Persamaan [(8.14)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#eq:pwisequb6) sehingga diperoleh vektor CC yang merupakan kumpulan koefisien cc.
9. Hitung koefisien bibi menggunakan Persamaan [(8.19)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#eq:pwisequb11)
10. Hitung koefisien didi menggunakan Persamaan [(8.20)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/interpolation.html#eq:pwisequb12).
11. Bentuk seri persamaan polinomial menggunakan elemen koefisien aa, bb, cc, dan dd yang telah dihitung.
12. Untuk melakukan ekstrapolasi dengan titik observasi diluar rentang titik diketahui, gunakan persamaan polinomial yang berada pada bagian ujung terdekat dengan nilai xx yang hendak dicari nilai yy-nya.

------

Berdasarkan algoritma tersebut, kita dapat menyusun suatu fungsi pada `R` untuk mencari seri persamaan polinomial derajat tiga. Fungsi tersebut adalah sebagai berikut:

```
cubic_spline <- function(x, y){
  n <- length(x)
  d_vec <- b_vec <- a_vec <- rep(0, n-1)
  vec <- rep(0, n)
  delta_x <- delta_y <- rep(0, n-1)
  
  ## Menghitung nilai selisih dan vektor A
  for(i in 1:(n-1)){
    a_vec[i] <- y[i]
    delta_x[i] <- x[i+1] - x[i]
    delta_y[i] <- y[i+1] - y[i]
  }
  
  ## Menyusun matriks tridiagona
  Au <- c(0, delta_x[2:(n-1)])
  Am <- c(1, 2*(delta_x[1:(n-2)]+delta_x[2:(n-1)]), 1)
  Al <- c(delta_x[1:(n-2)], 0)
  
  vec[0] <- vec[n] <- 0
  for(i in 2:(n-1))
    vec[i] <- 3 * (delta_y[i]/delta_x[i] - 
                   delta_y[i-1]/delta_x[i-1])
  
  ## penyelesaian tridiagonal matriks
  nm <- length(Am)
  Al <- c(NA , Al)
  
  ### forward sweep
  Au[1] <- Au[1] / Am[1]
  vec[1] <- vec[1] / Am[1]
  for(i in 2:(n - 1)){
      Au[i] <- Au[i] / (Am[i] - Al[i] * Au[i - 1])
      vec[i] <- (vec[i] - Al[i] * vec[i - 1]) /
                (Am[i] - Al[i] * Au[i - 1])
  }
  vec[n] <- (vec[n] - Al[n] * vec[n - 1])/
            (Am[n] - Al[n] * Au[n - 1])
  
  ### backward sweep
  c_vec <- rep.int (0, n)
  c_vec[n] <- vec[n]
  for(i in (n - 1) :1)
      c_vec[i] <- vec[i] - Au[i] * c_vec[i + 1]
  
 ## Hitung vektor B dan D dari vektor C
 for(i in 1:(n-1)){
   b_vec[i] <- (delta_y[i]/delta_x[i])-
               (delta_x[i]/3)*(2*c_vec[i]+c_vec[i+1])
   d_vec[i] <- (c_vec[i+1]-c_vec[i]) / (3*delta_x[i])
 }
  
 return(list(a = a_vec, b = b_vec, c = c_vec[-n], d = d_vec))
}
```

# Persamaan Diferensial

Persamaan diferensial merupakan persoalan matematis yang sering dijumpai dalam bidang teknik lingkungan. Sering kali suatu persamaan diferensial tidak dapat diselesaikan secara analitik sehingga diperlukan metode numerik untuk menyelesaikannya. Pada Chapter [10](https://bookdown.org/moh_rosidi2610/Metode_Numerik/diffeq.html#diffeq), kita akan membahas masalah-masalah dalam persamaan diferensial dan metode penyelesaiannya. Adapun yang akan dibahas pada Chapter [10](https://bookdown.org/moh_rosidi2610/Metode_Numerik/diffeq.html#diffeq) kali ini antara lain:

- *Initial value problems*
- Sistem persamaan diferensial
- Persamaan diferensial parsial

## 10.1 *Initial value problems*

*Initial value problems* merupakan permasalahan yang sering ditemukan pada proses dekomposisi zat kimia atau polutan dalam reaktor. Penyelesaiaan persamaan diferensial biasanya dipersulit dengan tidak tersedianya informasi yang cukup untuk menyelesaikannya.Sebuah persamaan diferensial \(f'\left(x,\dots\right)\) merupakan hasil diferensiasi beberapa fungsi \(f\left(x,\dots\right)\). Proses penyelesaian persamaan diferensial, dan menemukan nilai \(f \left(x,\dots\right)\) untuk beberapa nilai x,… tidak dimungkinkan karena integral dari \(f'\left(x,\dots\right)\) hanya digambarkan bentuk umum. Pergeseran vertikal, atas atau bawah, tidak diketahui. Pergeseran vertikal ini menghasilkan konstanta integrasi.

Selama proses diferensiasi, nilai apapun dari proses pergeseran vertikal (integrasi) akan hilang sebagai akibat dari eliminasi konstanta yang memiliki turunan 0. Kita biasa melakukannya ketika mengintegrasikan fungsi dengan menambahkan konstanta \(+ C\) pada proses integrasi ke integral yang tidak terbatas. Hal ini terkadang bukan menjadi permasalahan sebab jika menemukan nilai integrasi pada suatu batas tertentu syarat \(+ C\) dibatalkan dan konstanta integrasi tidak diperlukan.

Untuk persamaan diferensial biasa, tidak ada pembatalan yang nyaman, yang mengarah ke *initial value problems*. *Initial value problems* memberikan nilai \(f\left(x_0,\dots\right)\), di mana \(x_0\) biasanya bernilai 0, meski tidak diharuskan. Nilai awal ini memberikan informasi yang cukup untuk menyelesaikan persamaan dan menemukan nilai aktual dari \(f\left(x,\dots\right)\) untuk sejumlah nilai \(x\). Terdapat beberapa metode yang akan dibahas pada Chapter [10.1](https://bookdown.org/moh_rosidi2610/Metode_Numerik/diffeq.html#ivp), antara lain:

- Metode Euler
- Metode Heun
- Metode Titik Tengah
- Metode Runge-Kutta Orde 4
- Metode multistep linier

###  Metode Euler

Metode Euler merupakan metode paling sederhana yang diturunkan dari deret Taylor. Penyelesaian *initial value problems* menggunakan metode Euler dilakukan melalui Persamaan [(10.1)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/diffeq.html#eq:euler).

\[\begin{equation} y_{i+1}=y_i+f\left(x_i,y_i\right)h \tag{10.1} \end{equation}\]

dimana \(i\) merupakan tahapan iterasi.

------

**Algoritma Metode Euler**

1. Tentukan titik awal integrasi \(x_0\) dan \(y_0\).
2. Tentukan jumlah iterasi \(n\) dan *step size* \(h\) yang digunakan.
3. Lakukan integrasi menggunakan Persamaan [(10.1)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/diffeq.html#eq:euler).

------

Algoritma tersebut, selanjutnya dapat disusun ke dalam sebuah fungsi `R`. Fungsi tersebut adalah sebagai berikut:

```
euler <- function(f, x0, y0, h, n){
  x <- x0
  y <- y0
  
  for(i in 1:n){
    y0 <- y0 + h*f(x0, y0)
    x0 <- x0 + h
    x <- c(x,x0)
    y <- c(y, y0)
  }
  
  return(data.frame(x=x, y=y))
}
```

### Metode Heun

Metode Heun merupakan salah satu peningkatan dari metode Euler. Metode ini melibatkan 2 buah persamaan. Persamaan pertama disebut sebagai persamaan prediktor yang digunakan untuk memprediksi nilai integrasi awal (Persamaan [(10.2)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/diffeq.html#eq:heun1)). Persamaan kedua disebut sebagai persamaan korektor yang mengoreksi hasil integrasi awal (Persamaan [(10.3)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/diffeq.html#eq:heun2)). Metode Heun pada *Chapter* ini merupakan metode prediktor-korektor satu tahapan. Akurasi integrasi dapat ditingkatkan dengan melakukan koreksi ulang terhadap nilai koreksi semula menggunakan persamaan kedua.

\[\begin{equation} y_{i+1}^{0}=y_i+f\left(x_i,y_i\right)h \tag{10.2} \end{equation}\]

\[\begin{equation} y_{i+1}=y_i+\frac{f\left(x_i,y_i\right)+f\left(x_{i+1},y_{i+1}^0\right)}{2}h \tag{10.3} \end{equation}\]

------

**Algoritma Metode Heun**

1. Tentukan titik awal integrasi \(x_0\) dan \(y_0\).
2. Tentukan jumlah iterasi \(n\) dan *step size* \(h\) yang digunakan.
3. Lakukan prediksi nilai awal dengan Persamaan [(10.2)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/diffeq.html#eq:heun1).
4. Lakukan koreksi nilai awal menggunakan Persamaan [(10.3)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/diffeq.html#eq:heun2).
5. Lakukan koreksi terhadap nilai koreksi yang dihasilkan sebelumnya menggunakan Persamaan [(10.3)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/diffeq.html#eq:heun2).

------

Kita dapat membangun sebuah fungsi yang dapat melakukan proses integrasi menggunakan metode Heun. Berikut adalah sintaks yang digunakan:

```
heun <- function(f, x0, y0, h, n, iter=1){
  x <- x0
  y <- y0
  
  for(i in 1:n){
    ypred0 <- f(x0,y0)
    ypred1 <- y0 + h*ypred0
    ypred2 <- f(x0+h,ypred1)
    ykor <- y0 + h*(ypred0+ypred2)/2
    if(iter!=1){
      for(i in 1:iter){
        ykor <- y0 + h*(ypred0+f(x0+h,ykor))/2
      }
    }
    y0 <- ykor
    x0 <- x0 + h
    x <- c(x, x0)
    y <- c(y, y0)
  }
  
  return(data.frame(x=x,y=y))
}
```

### Metode Titik Tengah

Metode titik tengah menggunakan setengah *step size* pada metode Euler untuk melakukan estimasi terhadap integral suatu persamaan diferensial. Metode ini melakukan perhitungan melalui dua tahapan yaitu: menghitung nilai estimasi integral pada setengah *step size*(Persamaan [(10.4)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/diffeq.html#eq:mid1)) dan menghitung nilai integral menggunkan hasil perhitungan setengah *step size* sebelumnya (Persamaan [(10.5)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/diffeq.html#eq:mid2)).

\[\begin{equation} y_{i+\frac{1}{2}}=y_i+f\left(x_i,y_i\right)\frac{h}{2} \tag{10.4} \end{equation}\]

\[\begin{equation} y_{i+1}=y_i+f\left(x_{i+\frac{1}{2}},y_{i,\frac{1}{2}}\right)h \tag{10.5} \end{equation}\]

------

**Algoritma Metode Tengah**

1. Tentukan titik awal integrasi \(x_0\) dan \(y_0\).
2. Tentukan jumlah iterasi \(n\) dan *step size* \(h\) yang digunakan.
3. Lakukan integrasi pada setengah tahapan iterasi menggunakan Persamaan [(10.4)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/diffeq.html#eq:mid1).
4. Lakukan iterasi pada setengah tahapan selanjutnya menggunakan Persamaan [(10.5)](https://bookdown.org/moh_rosidi2610/Metode_Numerik/diffeq.html#eq:mid2).

------

Berdasarkan algoritma tersebut, kita dapat membangun sebuah fungsi pada `R` yang adapat digunakan untuk menyelesaikan persamaan diferensial menggunakan metode titik tengah. Berikut adalah sintaks yang digunakan:

```
midpt <- function(f, x0, y0, h, n){
  x <- x0
  y <- y0
  
  for(i in 1:n){
    s1 <- y0 + f(x0,y0) * h/2
    s2 <- h * f(x0+h/2,s1)
    y0 <- y0 + s2
    x0 <- x0 + h
    x <- c(x, x0)
    y <- c(y, y0)
  }
  
  return(data.frame(x=x,y=y))
}
```

