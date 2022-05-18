### Laboratorium 4 - 17 V 2022
# Zadanie  - Metoda Bisekcji
## Napisz skrypt, który znajdzie miejsce zerowej wybranej funkcji
a) Sprawdź, czy w podanym przedziale mogą znajdować się miejsca zerowe. Jeżeli nie, zmień zakres.
```matlab
% Dodatkowe zmienne potrzebne później
syms x;
odchylka = 0.001; % odchyłka wyniku
x1 = 2; % wartość minimalna
x2 = 10; % wartość maksymalna
f(x) = ; % tutaj trzeba wpisać swoją funkcję
% Koniec sekcji dla dodatkowych zmiennych

x0 = (a+b)/2;
if f(x0) ~= 0
    % Wylosuj inne a i b
end
```
b) Oblicz początkową wartość x0
```matlab
x0 = (a+b)/2;
```
c) Oblicz wartość funkcji w punkcie x0
```matlab
    fx0 = f(x0)
```
d) Sprawdź czy f(x0) * f(x1) < 0, Jeżeli tak to za x2 przyjmij x0, w przeciwnym przypadku x1 = x0;
```matlab
if fx0*f(x1) < 0
    x2 = x0;
    else
       x1 = x0;
    end
```
e) Oblicz wartość f(x0) i sprawdż czy jest mniejsza od zadeklarowanej wartości odchyłki. Jeżeli tak, to zakończ działanie skryptu, w przeciwnym wypadku powróć do punktu a
```matlab
while abs(fx0) > odchylka
    % kod z podpuntków c,d,e
end
```
## Cały kod:
```matlab
clear
clc

syms x
% poczatkowy przedzial
x1 = 2
x2 = 10
% rownanie
f(x) = x.^2-3*x-9
% odchylka
odchylka = 0.001;
% podpunkt b
x0 = (a+b)/2;
% podpunkt c
fx0 = f(x0);
% podpunkt e
while abs(fx0) > odchylka
    fx0 = f(x0); % podpunkt c
    % podpunkt d
    if fx0*f(a) < 0
    x2 = x0;
    else
       x1 = x0;
    end
    x0 = (a+b)/2; % podpunkt b
end
x0
double(f(x0))
% X = a:1:b
% F = X^2-3*X-9
% plot(X,F)


```