clear all
%超精细能级中的极化泵浦
%概率随机分配
%设置m=-2,-1,0,1,2的原子布局(归一化)
m1(1)=0.1;m2(1)=0.4;m3(1)=0.1;m4(1)=0.2;m5(1)=0.2;
%设置步数a
%a=100;
%for i=1:a-1;
i=1;
while(1-m3(i)>=0.000001)
    i=i+1;
    %1
    p1=rand(1);
    %2
    p2=rand(1);
    p21=rand(1)*(1-p2);
    p23=1-p2-p21;
    %4
    p4=rand(1);
    p43=rand(1)*(1-p4);
    p45=1-p4-p43;
    %5
    p5=rand(1);
    m1(i)=m1(i-1)*p1+m2(i-1)*p21;
    m2(i)=m1(i-1)*(1-p1)+m2(i-1)*p2;
    m3(i)=m3(i-1)+m2(i-1)*p23+m4(i-1)*p43;
    m4(i)=m4(i-1)*p4+m5(i-1)*(1-p5);
    m5(i)=m4(i-1)*p45+m5(i-1)*p5;
end
x=[1:1:i];
plot(x,m1,x,m2,x,m3,x,m4,x,m5);
 
