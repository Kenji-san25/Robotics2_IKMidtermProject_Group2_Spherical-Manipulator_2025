# Inverse-Kinematics

```Matlab
clear all
clc
close all

disp('Spherical')
%% Link lengths
syms a1 a2 a3 d3
a1 = 20;  
a2 = 10;
a3 = 10;
d3 = 20;

%% D-H Parameters [theta, d, r, alpha, offset]
% if prismatic joint: theta = theta, d = 0, offset = 1, after offset put the value of d
% if revolute joint: theta = 0, offset = 0, after offset put the value of theta

H0_1 = Link([0,a1,0,pi/2,0,0]);
H0_1.qlim = [-pi/2 pi/2];

H1_2 = Link([0,0,0,pi/2,0,pi/2]);
H1_2.qlim = [-pi/2 pi/2];

H2_3 = Link([0,0,0,0,1,a2+a3]);
H2_3.qlim = [0 d3];



Spart = SerialLink([H0_1 H1_2 H2_3], 'name', 'Spherical');
Spart.plot([0 0 0], 'workspace', [-30 60 -40 60 0 80], 'scale', 1);

figure(1)
Spart.teach
```
