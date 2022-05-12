# lineer-regresyon

import pandas as pd
import matplotlib.pyplot as plt

data=pd.read_csv('veriler.csv')


X=data.iloc[:,0]
print(X)
Y=data.iloc[:,1]
print(Y)

m = 0
c = 0

L = 0.0001
epochs = 1000

n = float(len(X))


for i in range(epochs):
    Y_pred = m*X + c
    D_m = (-2/n) * sum(X * (Y - Y_pred))
    D_c = (-2/n) * sum(Y - Y_pred)
    m = m - L * D_m
    c = c - L * D_c


print (m, c)

Y_pred = m*X + c

plt.scatter(X, Y)
plt.plot([min(X), max(X)], [min(Y_pred), max(Y_pred)], color='red')
plt.show()


for X in X:

    Y_Pred = m*X+c
    print(Y_Pred)


from sklearn.metrics import r2_score

print("Başarı Oranı:")
print(r2_score(Y, Y_pred))

z=int(input("Satış Tahmininde Bulunmak İstediğiniz Ayı Girin: "))
tahmin = m*z+c
print(str(z) + ". Ayın Sonundaki Toplam Satış Miktarı Tahmini Olarak = " + str(int(tahmin)) + "'dir.")

"""hata kareleri toplamı = Topla (yi-yi')^2
Ort fark toplamı =Topla (yi-yort)^2
R^2=1- HKT/OFT """

![Ekran Alıntısı](https://user-images.githubusercontent.com/99281922/168000805-70fd0e15-7d92-4d5f-9a7e-615494eaf0ea.PNG)

![Figure 2022-05-12 083615](https://user-images.githubusercontent.com/99281922/167999207-ef2fab96-bd95-4da8-8020-f0105341ef0f.png)

