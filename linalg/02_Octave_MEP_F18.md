# Sammlung Octave Code für MEP F18

## Aufgabe: Kreiszahl $\pi$

```matlab
clear;

% a)
k = 1:19;
s = 3+sum(4*(-1).^(k+1)./((2*k+1).^3-(2*k+1)));
% b)
dif = s - pi;
% c)
(dif / pi) * 100;
```

## Aufgabe: Sieb des Eratosthenes

```matlab
clear;

n = 100;
v = 1:n;

% fix(x) gibt den ganzzahligen Anteil von x zurück
for k = 2: fix(sqrt(n))
  vielf = k.*(2:fix(n/k));
  v(vielf) = zeros(1,length(vielf));
end
primzahlen = find(v>1);
```

## Aufgabe: Tauchgang U-Boot

```matlab
clear;

%a)
% Parameter
g = 9.81;
eta = 0.01; % Viskositaet von Wasser kg/(m*s)
rho_W = 1000; % Dichte von Wasser in kg/m^3 
r = 1.4; % Radius U-Boot in m

% Masse des U-Boots als Funktion der Zeit
%m=@(t) max(1-1e-3*t*(t-20),1)*11500;
m = @(t) (1-1e-3*t*(t-20))*11500;

%Anfangswerte
y0 = [10;0];

%Zeitintervall
I = [0 35];

%DGL
ypunkt = @(t,y) [y(2); g-4/3*pi*r^3*rho_W*g/m(t)-6*pi*eta*r*y(2)/m(t)];
[t,y] = ode45(ypunkt,I, y0);
plot(t,y);

%b)
t
y(16,1)

%c)
[M,j] = max(y(:,2))
t(j)
```