<div align="center"><h1>
Robotics2_IKMidtermProject_Group2_Spherical Manipulator_2025
</h1></div>

## Forward Kinematics

<img src="https://github.com/Kenji-san25/Inverse-Kinematics/blob/ce084fcdb172e9e195a2c39762e2b5c0b7d485c1/IMG_20250423_110212.jpg" width="600"/>

## Parametric Table

<img src="https://github.com/Kenji-san25/Inverse-Kinematics/blob/45ba9ea7cd90ff3678ee3f450ab94e2c80a544ee/IMG_20250423_110234.jpg" width="600"/>

## Inverse Kinematics Top View

<img src="https://github.com/Kenji-san25/Inverse-Kinematics/blob/52c0c8d0c94aa99b2330248a4a47876a7ae37ebd/TOP%20VIEW.jpg" width="600"/>

## Inverse Kinematics Front View

<img src="https://github.com/Kenji-san25/Inverse-Kinematics/blob/d4241b7177e22471bdd9a3ea7f6d7ea5fbd964bf/FRONT%20VIEW.jpg" width="600"/>

***Python Script***

```Python
import numpy as np


# Input from the user
x = np.array(float(input("X: ")))
y = np.array(float(input("Y: ")))
z = np.array(float(input("Z: ")))
a1 = np.array(float(input("a1: ")))
a2 = np.array(float(input("a2: ")))
a3 = np.array(float(input("a3: ")))

# Calculations
t1 = np.arctan2(y, x)
r1 = np.sqrt(x**2 + y**2)
r2 = z - a1
t2 = np.arctan2(r2, r1)
d3 = np.sqrt(r1**2 + r2**2) - a2 - a3

dg1 = np.degrees(t1)
dg2 = np.degrees(t2)


# Display results

print(f"Q1: {dg1}")
print(f"Q2: {dg2}")
print(f"D3: {d3}")
```

***Mathlab Script***

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


## Table with Trial Values

<img src="https://github.com/user-attachments/assets/c1f7f2bf-9a6c-4409-97d2-ecccb59985f8" width="600"/>

### Trial #1 

<img src="https://github.com/user-attachments/assets/e55cc59e-c50a-4dd7-9680-c97881bf8afe" width="1050"/>

![1M](https://github.com/user-attachments/assets/4a29a303-c1c5-4fb2-92ff-9b603b8dc56c)

### Trial #2 

<img src="https://github.com/user-attachments/assets/c53663aa-56ed-45f1-87d0-fdd2b06934f8" width="1050"/>

![2M](https://github.com/user-attachments/assets/596af7d8-37e1-4129-aa1f-a0801292c40b)

### Trial #3 

<img src="https://github.com/user-attachments/assets/3adc6ec1-0382-4dc9-a5a6-4b9ced75da0b" width="1050"/>

![3m](https://github.com/user-attachments/assets/dcc34393-35c5-4dbe-ac30-7f63d4bf4e82)


### Trial #4 

<img src="https://github.com/user-attachments/assets/fe24eb45-eb7f-443d-a92c-2c8624696fdf" width="1050"/>

![4M](https://github.com/user-attachments/assets/f4983516-e689-47b9-8b3a-ba1f638cae9d)

### Trial #5 

<img src="https://github.com/user-attachments/assets/a20af2e6-a2a4-4bda-b3c7-6d1fccdbec5e" width="1050"/>

![5M](https://github.com/user-attachments/assets/43bf9ad6-b622-47f9-8539-7ef99c161d00)


