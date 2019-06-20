# Sammlung Octave Code für MEP HS17

## Aufgabe: Taylor-Reihe

```matlab
clear;

%a)
x = (pi/2) - 1;
k = 0:20;
s = sum((-1).^k./factorial(2*k+1).*x.^(2*k+1));
```

## Aufgabe: Diskrete Faltung

```matlab
clear;

v = [1 2 3 4];
w = [1 1 1 1];

if ~isrow(v) || ~isrow(w)
    error('Einer der Vektoren ist kein Zeilenvektor.');
else
    n = length(v);
    m = length(w);
    v = [v zeros(1,m-1)];
    w = [w zeros(1,n-1)];
    for k = 1: (n+m-1)
        f(k) = v(1:k) * w(k:-1:1)';
    end
end
```

## Aufgabe: LGS (4x4) Wassertanks

```matlab
clear;

%b)
A = [1 1 1 0 0; 1 0 0 -1 0; 0 1 0 1 -1; 0 0 1 0 1];
b = [20;10;0;10];
rank(A)
rank([A b])

%c)
f_p = A\b
ker = null(A)
```

## Aufgabe: Fadenpendel

```matlab
clear;

%a)
%Parameter:
g=9.81;
m=0.3;
l=0.2;
mu=0.2;
F0=19;
sigma=0.1; % (1 Pkt.)

%Intervall:
I=[0 5]; % (1 Pkt.)

%Anfangswerte:
y0=[0 0]'; % (1 Pkt.)

%Anregung:
Fext=@(t) F0/(sqrt(2*pi))*exp(-t^2/(2*sigma^2)); % (2 Pkt.)

%DGL: % Umschreiben: 2 Pkt.
ypunkt=@(t,y) [y(2); %=y1'  % (1 Pkt.)
       -g/l*sin(y(1))-mu/m*y(2)+Fext(t)/(m*l)]; %=y2'  % (2 Pkt.)

[t,y]=ode45(ypunkt,I,y0); % (3 Pkt.)
plot(t,y(:,1));

%b)
n=find(y(:,1)<0)(1);
t_n=(t(n)+t(n-1))/2;
%oder
t0=(t(n-1)*y(n,1)-t(n)*y(n-1,1))/(y(n,1)-y(n-1,1));

%Nicht genommen:
%c)
%DGL:
%ypunkt_lin=@(t,y) [y(2); %=y1'
%       -g/l*y(1)-mu/m*y(2)+Fext(t)/(m*l)]; %=y2'

%[t_lin,y_lin]=ode45(ypunkt_lin,I,y0);
%plot(t_lin,y_lin(:,1));

%d)
%n=find(y_lin(:,1)<0)(1);
%t_n_lin=(t_lin(n)+t_lin(n-1))/2;

%Prozentuale Abweichung
%p=abs(t_n_lin-t_n)/t_n;
```