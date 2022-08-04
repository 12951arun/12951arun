
// fitting a straight line with w
clc;
x=input("enter the values of x")
y=input("enter the values of y")
w=input("enter the values of w")
n=length(x)
s1=0
s2=0
s3=0
s4=0
s5=0
a=[2 ;2]
for i=1:n
    s1=s1+w(i)
    s2=s2+w(i)*x(i)
    s3=s3+w(i)*y(i)
    s4=s4+w(i)*x(i)*x(i)
    s5=s5+w(i)*x(i)*y(i)
end
a=[s1 s2; s1 s4]
b=[s3;s5]
disp(a)
disp(b)
c=inv(a)*b
disp(c)
for i=1:n
    y(i)=c(1)+c(2)*x(i)
    plot(x(i),y(i),"b") 
end
plot2d(x,y)
title("weighted least square by linear data")
"results"
 







Wave 

clc;clear;
h=0.25
k=0.2
c=1
g=c^2*k^2/h^2
t0=0
x0=0
xn=1
tn=0.6
x=0
n=round((xn-x0)/h+1)
m=round((tn-t0)/k+1)
u=zeros(m,n)
u0=0
un=0
u(1:m,1)=u0
u(1:m,n)=un
for i=2:n-1
     x=x+h
     u(m,i)=(sin(%pi*x))^3
end
disp("Boundary Conditions:",u)
for i=m:-1:2
    for j=2:n-1       
        u(i-1,j)=g^2/2*(u(i,j+1)+u(i,j-1))+(1-g^2)*u(i,j)

    end
end
disp(" |_________required values_________| ")
disp(u)


