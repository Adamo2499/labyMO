### Laboratorium 1 - 26 IV 2022
## Zadanie 1 - parzystość
Wypisz liczby parzyste z zakresu 0-100
```matlab
clc
clear
for i=0:100
    if mod(i,2) == 0 
        i
    end
end
```
## Zadanie 2 - funkcja kwadratowa
Wyznacz pierwiastki funkcji kwadratowej dla 3 wybranych współczynników. Uwzględnij przypadki, kiedy delta będzie > 0 lub = 0;
```matlab
clc
clear
wyniki_funkcji_kwadratowej(2,8,-10); % wywołanie funkcji dla delty > 0
%wyniki_funkcji_kwadratowej(1,4,4); %wywołanie funkcji dla delty = 0
%wyniki_funkcji_kwadratowej(-2,-8,-10); %wywołanie funkcji dla delty < 0

function [x1,x2] = wyniki_funkcji_kwadratowej(a,b,c)
        delta = b^2 - (4*a*c)
        if delta > 0
           x1 = (-1*b - sqrt(delta))/2*a
           x2 = (-1*b + sqrt(delta))/2*a
        elseif delta == 0 
           x1 = (-1*b)/2*a 
           x2 = (-1*b)/2*a
           sprintf("Delta jest rowna 0!")
        else 
            sprintf("Delta jest mniejsza od 0!")
        end
end

```
## Zadanie 3 - Układ równań
Rozwiąż układ równań. Ilość równań oraz współczynniki i rozwiązania powinny być podane przez użytkownika
```matlab
clc
clear
wielkosc_macierzy = input('Podaj wielkosc macierzy');
for x = 1:wielkosc_macierzy
      for y = 1:wielkosc_macierzy
         A(x,y) = input('Podaj wspolczynnik')
   end
end
for i = 1:wielkosc_macierzy
        B(i) = input('Podaj wynik')
end
rozwiazanie_ukladu(A,B);

function [wynik] = rozwiazanie_ukladu(A,B)
    b = B';
    X = A \ b;
    disp(X);
end
```
## Zadanie 4 - wykresy
Wyznacz wartości funkcji i przedstaw je na jednym wykresie:<br>
a) y(t) = 2e<sup>3sint</sup><br>
b) y(t) = e<sup>-3sint</sup>
```matlab
t=0:0.1:20 %zakres wybrany losowo
Y1 = wyniki(2,3,t)
Y2 = wyniki(1,-3,t)
plot(t,Y1,t,Y2);

function [y] = wyniki(a,b,T)
    y = a*exp(b.*sin(T));
end
```