### Laboratorium 2 - 04 V 2022
# Zadanie  - Metoda
## Napisz skrypt wyznaczający optymalną wartość funkcji f(x) przy ograniczeniu g(x)
a) Zdefinuj funkcję f(x) = 8x<sub>1</sub><sup>4</sup> -7x<sub>2</sub><sup>3</sup> -2<sub>3</sub> <sup>2</sup> -x<sub>4</sub><sup>2</sup> 
```matlab
syms x1 x2 x3 x4 lambda %zmienne pomocnicze

f(x1,x2,x3,x4) = 8*x1^4-7*x2^3-2*x3^2-1*x4^2
```
b) Zdefinuj funkcję g(x) = 2x<sub>1</sub>+3x<sub>2</sub>-7x<sub>3</sub>-6
```matlab
g(x1,x2,x3,x4) = 2*x1+3*x2-7*x3-6
```
c) Zdefinuj funkcję Lagrange'a L(x,lambda) = f+lambda*g
```matlab
L(x1, x2, x3, x4, lambda) = f + lambda * g
```
d) Oblicz pochodną funkcji L(x,lambda) względem każdej zmiennej występującej w równaniu (wykorzystaj funkcję **diff()**)
```matlab
p1 = diff(L, x1); %pochodna funkcji L względem zmiennej x1
p2 = diff(L, x2);
p3 = diff(L, x3);
p4 = diff(L, x4);
p5 = diff(L, lambda);
```
e) Wyznacz wartości przy poszczególnych niewiadomych równania przy pomocy metody macierzowej
```matlab

A = [
        p1(1, 0, 0, 0, 0) p1(0, 1, 0, 0, 0), p1(0, 0, 1, 0, 0) p1(0, 0, 0, 1, 0) p1(0, 0, 0, 0, 1);
        p2(1, 0, 0, 0, 0) p2(0, 1, 0, 0, 0), p2(0, 0, 1, 0, 0) p2(0, 0, 0, 1, 0) p2(0, 0, 0, 0, 1);
        p3(1, 0, 0, 0, 0) p3(0, 1, 0, 0, 0), p3(0, 0, 1, 0, 0) p3(0, 0, 0, 1, 0) p3(0, 0, 0, 0, 1);
        p4(1, 0, 0, 0, 0) p4(0, 1, 0, 0, 0), p4(0, 0, 1, 0, 0) p4(0, 0, 0, 1, 0) p4(0, 0, 0, 0, 1);
        p5(1, 0, 0, 0, 0) p5(0, 1, 0, 0, 0), p5(0, 0, 1, 0, 0) p5(0, 0, 0, 1, 0) p5(0, 0, 0, 0, 1);
    ] %Macierz współczynników
    B = [0 0 0 0 6]; % Macierz rozwiązań
    b = B' % Transponowanie macierzy
    wynik = A\b % Uzyskanie wartości x1,x2,x3,x4
```
## Cały kod:
```matlab
syms x1 x2 x3 x4 lambda %zmienne pomocnicze

f(x1,x2,x3,x4) = 8*x1^4-7*x2^3-2*x3^2-1*x4^2 %funkcja celu

g(x1,x2,x3,x4) = 2*x1+3*x2-7*x3-6 %funkcja ograniczeń

L(x1, x2, x3, x4, lambda) = f + lambda * g

p1 = diff(L, x1); %pochodna funkcji L względem zmiennej x1
p2 = diff(L, x2);
p3 = diff(L, x3);
p4 = diff(L, x4);
p5 = diff(L, lambda);


A = [
        p1(1, 0, 0, 0, 0) p1(0, 1, 0, 0, 0), p1(0, 0, 1, 0, 0) p1(0, 0, 0, 1, 0) p1(0, 0, 0, 0, 1);
        p2(1, 0, 0, 0, 0) p2(0, 1, 0, 0, 0), p2(0, 0, 1, 0, 0) p2(0, 0, 0, 1, 0) p2(0, 0, 0, 0, 1);
        p3(1, 0, 0, 0, 0) p3(0, 1, 0, 0, 0), p3(0, 0, 1, 0, 0) p3(0, 0, 0, 1, 0) p3(0, 0, 0, 0, 1);
        p4(1, 0, 0, 0, 0) p4(0, 1, 0, 0, 0), p4(0, 0, 1, 0, 0) p4(0, 0, 0, 1, 0) p4(0, 0, 0, 0, 1);
        p5(1, 0, 0, 0, 0) p5(0, 1, 0, 0, 0), p5(0, 0, 1, 0, 0) p5(0, 0, 0, 1, 0) p5(0, 0, 0, 0, 1);
    ] % Macierz współczynników
    B = [0 0 0 0 6]; % Macierz rozwiązań
    b = B' % Transponowanie macierzy
    wynik = A\b % Uzyskanie optymalnych wartości x1,x2,x3,x4

```