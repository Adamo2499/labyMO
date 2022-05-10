### Laboratorium 3 - 10 V 2022
# Zadanie  - Metoda Newtona - Raphsona
## Napisz skrypt, który znajdzie miejsce zerowej wybranej funkcji
a) Zadeklaruj funkcję (wykorzystaj polecenie __syms__)
```matlab
syms x
```
b) Zadeklaruj miejsce, od którego rozpocznie się poszukiwanie
```matlab
x0 = 2
```
c) Zadeklaruj wartość dokładności obliczeń
```matlab
error = 0.001;
```
d) Oblicz pochodną funkcji
```matlab
df=diff(f,x);
```
e) Sprawdź czy wartość pochodnej funkcji dla miejsca, od którego mają się zacząć poszukiwania jest różna od 0. Jeżeli nie jest, to przerwij w tym momencie program; jeżeli jest, przejdź dalej
```matlab
if diff(f,x) ~= 0
    % dalsza część kodu
else
    return
end
```
f) Wyznacz wartość funkcji w punkcie x
```matlab
    % w pętli po przejściu ifa z kroku e
    f(x) = sin(2*x) * cos(x) % wpisać własną funkcję
```
g) Wyznacz wartość pochodnej funkcji w punkcie x <sub>i</sub>
```matlab
 % w pętli po przejściu ifa z kroku e
    df=diff(f,x);
```
h) Oblicz kolejne przybliżenie rozwiązania:<br> <img src="https://latex.codecogs.com/svg.image?{\color{Red}&space;x_{i}&space;=&space;x_{i}&space;-&space;\frac{f(x_{i})}{f'(x_{i})}&space;}"/> 
```matlab
% w pętli po przejściu ifa z kroku e
            x0 = x0 - (f(x0) /df(x0))
            f(x0)
```

i) Sprawdź czy wartość bezwzględna jest zmierzona od wcześniej zdefiniowanej doładności. Jeżeli tak, to zakończ program; jeżeli nie to potwórz kroki f-i
```matlab
    % warunek pętli while
    while abs(f(x0)) > error
        % tutaj kod z podpunktów f,g,h
```
## Cały kod:
```matlab
clear
clc

syms x
x0 = 2
error = 0.001;
f(x) = ((x+1)/2) - 2*(x^2-1)
    if diff(f,x) ~= 0
        while abs(f(x0)) > error
            df=diff(f,x);
            x0 = x0 - (f(x0) /df(x0))
            f(x0)
    else 
        return
    end
end
X = x0:1:10
F = ((X+1)/2) - 2.*(X.^2-1)
plot(X,F)

```