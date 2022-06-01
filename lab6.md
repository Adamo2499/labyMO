### Laboratorium 6 - 31 V 2022
# Zadanie  - Metoda regresji liniowej (metoda najmniejszych kwadratow)
## a) Uzupełnij brakujący kod
## b) Po wyznaczeniu linii regresj, zmodyfikuj program tak, aby wyznaczył linię regresji dla funkcji y(x) = af(x) + bg(x) + ch(x):
    
#### f(x) = cos(x)
#### g(x) = sin(x)
#### h(x) = e^x

## Cały kod (dla funkcji liniowej):
```matlab
%% regresja liniowa MNK y(x) = ax+b

clear;
clc;

% -- generacja danych wejsciowych
xk = linspace(0,10,1e2)
xx = linspace(0,10,1e3)

% -- tworzenie wspolczynnikow modelu (losowe)
terms = zeros(1,2);
range = 10;
Coefs = (range+range).*rand(1,max(size(terms)))

% -- definicja modelu
yk = Coefs(1).*xk+Coefs(2)

% -- definicja szumu
a = 20;
r = -a+(a+a).*rand(1,max(size(yk)))

% -- dodanie szumu
yk = yk+r

% -- wykreslenie rysunku
plot(xk,yk,'o');
% -- definicja skladowych modelu
f=@(u)u.^1;
g=@(u)u.^0;


% -- definicja tablicy typu 'cell' dla skladowych modelu
funTab = {f,g}

% -- alokacja pamieci
A = zeros(max(size(terms)));
B = zeros(max(size(terms)),1);

% -- uklad rownan
for i = 1:1:max(size(terms))
    for j=1:1:max(size(terms))
            firstFun = funTab{i};
            secondFun = funTab{j};
            % -- obliczenie wartosci elementu macierzy A
            A(i,j) = sum(firstFun(xk).*secondFun(xk))
    end
end

% -- obliczenie wartosci wektora wyrazow wolnych
for j=1:1:max(size(B))
    thisFun = funTab{j}
    B(j) = sum(thisFun(xk).*yk)
end

% -- rozwiazanie ukladu rownan
Coefs2 = A\B

% -- tworzenie modelu przy pomocy obliczonych wspolczynnikach
yk2 = Coefs2(1).*xk+Coefs2(2)

% -- rysunek
plot(xk,yk,'o',xk,yk2);

% -- definicja oraz obliczenie wartosci funkcji bledu
psi = sum((Coefs2(1).*xk+Coefs2(2)).^2)
```