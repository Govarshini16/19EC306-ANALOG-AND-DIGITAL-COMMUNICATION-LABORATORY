# AIM:
To implement error control coding schemes with linear block codes using MATLAB.

# SOFTWARE REQUIRED: 
  MATLAB

# PROGRAM:
# ERROR CODING
# ENCODING:
clc;
close all;
n = 7;
k = 4;
msg = [1 0 0 1;
       1 0 1 0;
       1 0 1 1];
code = encode(msg, n, k, 'cyclic');
msg
code
# ENCODING OUTPUT:

<img width="490" height="247" alt="image" src="https://github.com/user-attachments/assets/8391ec53-692c-4ff1-b25f-85361e853a26" />


# DECODING PROGRAM:
clc;

clear all;

close all;

q = 3;

n = 2^q - 1;
k = n - q;

parmat = hammgen(q);
trt = syndtable(parmat);

recd = [1 0 1 1 1 1 0];

syndrome = rem(recd * parmat', 2);
syndrome_de = bi2de(syndrome, 'left-msb');

disp(['syndrome = ', num2str(syndrome_de), ' (decimal) ', ...
      num2str(syndrome), ' (binary)']);

corrvect = trt(1 + syndrome_de, :);

correctedcode = rem(corrvect + recd, 2);

parmat
corrvect
correctedcode

# DECODING OUTPUT:

<img width="411" height="242" alt="image" src="https://github.com/user-attachments/assets/825dec39-0e87-4371-9411-8744814c975c" />


# RESULT:
Thus encoding and decoding of block codes are performed using MATLAB.

