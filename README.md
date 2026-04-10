# Digital-Signal-Processing--Design-of-Adaptive-Filter

## AIM:
To Design and Implementation of Adaptive filters using MATLAB.

## SOFTWARE REQUIRED:
MAT LAB R2012

## ALGORITHM:
Step 1: Open mat lab. Write the program.

Step 2: Generating the desired signal. 

Step 3: Generating a signal corrupted with noise

Step 4: Estimating the signal. 

Step 5: Computing the Error signal. 

Step 6: Plot all the signals with x-label and y-label with suitable title

Step 7: Terminate the program.

## PROGRAM: 
```
clc;
clear all;
close all;

% Generating the desired signal
t = 0.001 : 0.001 : 1;
D = 2 * sin(2 * pi * 50 * t);

% Generating a signal corrupted with noise
n = numel(D);
A = D + 0.9 * randn(1, n);

% Error between original and noisy signal
l = D - A;

% Autocorrelation
r = xcorr(A);

M = 25;
rr = zeros(1, M);

for i = 1:M
    rr(i) = r(n - i + 1);
end

% Toeplitz matrix
R = toeplitz(rr);

% Cross-correlation
p = xcorr(D, A);
P = zeros(1, M);

for i = 1:M
    P(i) = p(n - i + 1);
end

% Wiener filter coefficients
w = inv(R) * P';

% Estimating the signal
Est = zeros(1, n);

for i = M:n
    j = A(i:-1:i-M+1);
    Est(i) = w' * j';
end

% Computing the error signal
Err = Est - D;

% Display of signals
subplot(4,1,1);
plot(D);
title('Desired Signal');

subplot(4,1,2);
plot(A);
title('Signal Corrupted with Noise');

subplot(4,1,3);
plot(Est);
title('Estimated Signal');

subplot(4,1,4);
plot(Err);
title('Error Signal');
```
## OUTPUT:
<img width="1919" height="1034" alt="image" src="https://github.com/user-attachments/assets/2ec70cec-4c70-499b-96f1-5a91ff328ec9" />


## RESULT:

![WhatsApp Image 2026-04-10 at 6 48 02 PM (2)](https://github.com/user-attachments/assets/cc5b43f8-0a9b-463d-aa09-bbb4e3642584)

