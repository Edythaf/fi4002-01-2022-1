# 10219004
Edytha Feodora Christine Manurung


## materi sebelumnya
+ Tuliskan materi-materi sebelumnya yang telah diberikan dalam kuliah ini.
+ Bandul
+ Runge Kutta
+ Euler
+ Monte Carlo
+ Lorenz
+ DFT
+ FFT

## materi paling menarik
+ Tuliskan materi yang paling menarik yang telah diberikan dan jelaskan mengapa menarik.
+Euler karena paling mudah dimengerti 

## materi paling membosankan
+ Tuliskan materi yang telah diberikan yang paling membosankan dan jelaskan alasannya.
+ DFT FFT, ga ngerti banget karena ga pernah belajar 


## materi yang sudah dipami
+ Tuliskan materi-materi yang telah dipahami.
+Monte carlo, Runge Kutta, Euler 


## materi yang belum dipahami
+ Tuliskan materi-materi yang masih belum dipahami dan bagian mana yang belum serta ingin dipahami.
+ DFT, FFT

## contoh program
+ Buat suatu contoh program dalam Python dan sertakan di sini dengan hasil keluarnnya.

```python
import numpy as np 
import matplotlib.pyplot as plt
t = np.arange(0, 30, 0.05)
v_x = -10  * np.sin(t)
v_y = 10 * np.cos(t)

plt.figure()
plt.grid()
plt.plot(t, v_x, 'r', label = '$v_x$')
plt.plot(t, v_y, 'b', label = '$v_y$')
plt.title('Rotasi partikel pada medan magnet berdasarkan teori')
plt.xlabel('Waktu (s)')
plt.ylabel('Kecepatan')
plt.legend(loc = 1)

plt.show()

def rungeKutta(F, t, x, y, h):
    K0 = h * F(t, x, y)
    K1 = h * F(t + h/2.0, x + K0/2.0, y)
    K2 = h * F(t + h/2.0, x + K1/2.0, y)
    K3 = h * F(t + h, x + K2, y)
    return(K0 + 2.0 * K1+ 2.0 * K2 + K3)/6.0

#Fungsi diferensial terkopel
def vx_terkopel(t, vx, vy, q = 1, Bz = 1, m = 1):
    return -q * Bz/m * vy

def vy_terkopel(t, vy, vx, q = 1, Bz = 1, m = 1):
    return q * Bz/m * vx
   
vx0 = 0 
vy0 = 10

t0 = 0 
t_stop = 30

h = 0.005

#deklarasi array untuk menyumpan variabel
vxs=[vx0]
vys=[vy0]
ts=[t0]
while ts[-1] < t_stop:
    h = min(h, t_stop - ts[-1])
    vx = vxs[-1] + rungeKutta(vx_terkopel,ts[-1],vxs[-1],vys[-1],h)
    vy = vys[-1] + rungeKutta(vy_terkopel,ts[-1],vys[-1],vxs[-1],h)
    t = ts[-1] + h
    
    ts.append(t)
    vxs.append(vx)
    vys.append(vy)
    
plt.figure()
plt.grid()
plt.plot(ts, vys, 'r', label = '$v_x$')
plt.plot(ts, vxs, 'b', label = '$v_y$')
plt.title('Rotasi partikel pada medan magnet berdasarkan Runge Kutta')
plt.xlabel('Waktu (s)')
plt.ylabel('Kecepatan')
plt.legend(loc = 1)

plt.show()



# contoh program python
```

Hasilnya adalah
![image](https://user-images.githubusercontent.com/83853217/197976831-827f44b4-94d3-4897-837f-425c20ec47b2.png)


```
```


## cara perkuliahan
+ Tuliskan pendapat Anda mengenai cara perkuliahan selama ini dan cantumkan usulan untuk perkuliahan setelah UTS.


## topik sistem fisis
+ Tuliskan sistem fisis yang menarik bagi Anda untuk dikaji lebih dalam dan jelaskan alasannya mengapa.


## simulasi dan visualisasi
+ Apakah Anda tertarik dengan simulasi dan visualisasi? Jelaskan topik yang ingin Anda simulasikan / visualisasikan serta cantumkan alasannya dan perkiraan pusataka Python yang perlu digunakan.
