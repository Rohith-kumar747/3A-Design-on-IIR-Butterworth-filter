# IIR-FILTER-DESIGN
# EXP 3 A: DESIGN OF LOW PASS BUTTERWORTH FILTER USING BILINEAR TRANSFORMATION TECHNIQUE

# AIM: 

# To perform design of Butterworth Filter Using Impulse Invariant and Bilinear Transformation Techniques using SCILAB.

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
```
clc ; 
close ; 
wp=input('Enter the pass band frequency (Radians )= ' ); 
ws=input('Enter the stop band frequency (Radians )= ' ); 
alphap=input( ' Enter the pass band attenuation (dB)=' ); 
alphas=input( ' Enter the stop band attenuation(dB)=' ); 
T=input('Enter the Value of sampling Time=');

//Pre warping- Bilinear Transformation 
omegap=(2/T)*tan(wp/2); 
disp(omegap,'omegap='); 
omegas=(2/T)*tan(ws/2); 
disp(omegas,'omegas=');

//Order of the filter 
N=log10(((10^(0.1*alphas))-1)/((10^(0.1*alphap))-1))/(2*log10(omegas/omegap)); 
disp(N,'N='); 
N=ceil(N); 
disp(N,'Round off value of N=');

//Cut off frequency 
omegac=omegap/(((10^(0.1*alphap)) -1)^(1/(2* N))); 
disp(omegac,'omegac='); 
 
disp('Normalised Analog LPF Transfer function H(S)='); 
hs_Normalised = analpf(N,'butt',[0,0],1); 
disp(hs_Normalised); 
 
disp('Analog LPF Transfer function H(S)='); 
hs= analpf(N,'butt',[0,0],omegac); 
disp(hs); 
z=poly(0,'z');//Defining variable z 
Hz=horner(hs,(2/ T)*((z -1)/(z+1)))// Bilinear Transformation 
disp('Digital LPF Transfer function H(Z)='); 
disp(Hz);
HW=frmag(Hz,512); // Frequency response 
w=0:%pi/511:%pi ; 
plot(w/%pi,abs(HW)); 
xlabel(' Normalized Digital Frequency w'); 
ylabel('Magnitude ');
title(' Frequency Response of Butterworth IIR LPF');
```
# CALCULATION:
<img width="963" height="1523" alt="image" src="https://github.com/user-attachments/assets/7ea7e27d-9814-4319-ad3b-c3ac54527a03" />
<img width="950" height="1471" alt="image" src="https://github.com/user-attachments/assets/60be1831-50ad-478e-9640-3db50e171d72" />
<img width="1600" height="1528" alt="image" src="https://github.com/user-attachments/assets/3974d13c-53d8-4e0b-b8b8-89cb3ea5b6cf" />

# OUTPUT: 
CONSOLE WINDOW

<img width="741" height="1025" alt="Butterworth calculation" src="https://github.com/user-attachments/assets/f9b1cc63-f40a-41cc-8106-0262aa056d46" />

# GRAPH:

<img width="756" height="721" alt="Butterworth graph" src="https://github.com/user-attachments/assets/7c3a7c84-6daf-4786-8857-d999d43e0fec" />

# RESULT: 

Thus, design of Butterworth Low pass IIR filter waveforms were plotted and output was verified.
