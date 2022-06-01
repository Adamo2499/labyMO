### Laboratorium 5 - 24 V 2022
# Zadanie  - Zastosowanie metod bisekcji i fzero()
## Znajdź miejsce zerowe poniższych funkcji przy pomocy napisanego przez siebie algorytmu z poprzednich zajęć oraz przy pomocy polecenia __fzero()__

 a) sin(x) <br>
 b) x^2-3*x-9 <br>
 c) sin(x)+cos(sqrt(3)*x) <br>
 d) x^3-6*(x^2)+4*x+12 <br>
 e) -3*x-5 <br>
 f) (x^2)/2 - 3*x+3 <br>
 g) (x+1)/2 -2*(x^2-1) <br>
 h) x^3+8*(x^2)-5 <br>
 i) sin(x)*e^x <br>
 j) sin(x^2)*cos(x) <br>
 k) x^4-4*x^3 <br>
 l) (x^2-5)(x^2-3)-3 <br>
 m) cos(2*x)+e^x/2 - 5 <br>
 n) log10(x)-3*sin(x) <br>
 o) log10(x)-sin(x^2)+0.75 <br>
 p) log(x)*sin(x)-cos(3*x) <br>

## Cały kod:
```matlab
clear
clc

syms x

a = 1
b = 4;
fun = @funkcja;

odchylka = 0.001;
disp("a)")
disp("Bisekcja:")
x0 = bisekcjaX(funkcja(x));
disp("Fzero:")
opts = optimset('fzero');
opts.ToIX = odchylka
opts.Display = 'iter';
Ffzero = fzero(fun,x0,opts)

% funkcja obliczająca wartość y dla x w zależności od podanej funkcji
function y = funkcja(x)
   y = % tutaj należy zmieniać funkcję na tą, jaka jest nam aktualnie potrzebna
end

% funkcja wyznaczająca miejsca zerowe za pomocą metody bisekcji
function [x0] = bisekcjaX(y)
syms x
f(x) = y;
a = 2;
b = 10;
odchylka = 0.001;
x0 = (a+b)/2;
fx0 = f(x0);
licznikIteracji = 0;
while abs(fx0) > odchylka
    fx0 = f(x0);
    % podpunkt d
    if fx0*f(a) < 0
    b = x0;
    else
       a = x0;
    end
    x0 = (a+b)/2;
    licznikIteracji = licznikIteracji + 1; % licznik iteracji potrzebny do Excela
end
x0
Fx0 = double(f(x0))
licznikIteracji
end


```