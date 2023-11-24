# Differential LNA of a Receiver 
## The aim of the following is to:-
A) Analyse mathematically, the LO leakage from the output to input of a differential LNA of a receiver when the input is a pure pulse-train corrupted by BPF
B) Model, simulate, and graph the signals at all nodes in a situation 
(a) when the input noisy pulse train has a small secondary sinusoidal signal at a slightly different frequency. Analyze the simulated nodes in the report.
(b) When the input noisy pulse train has a small secondary sinusoidal signal at a slightly different frequency. Analyze the simulated nodes in the report.

## Calculation
We have assumed non-linearity only due to cross-coupling interaction and no other factors have been taken into consideration.
We have begun by drawing the CG differential-LNA circuit and applying a pure-pulse train with noises induced by the Band Pass Filter we have designed. We can calculate LO – -leakage values from design parameters theoretically by calculations from formulae :

```
VLO-leakage = A * VLO   and PLO_leakage = A^2 * PLO

Relationally, PLO = (VLO^2) / (2 * RLO) (rms calculations)

P_LO_leakage = (V_LO_leakage^2) / (4 * R_leakage)

V_LO_leakage = (I_LO_leakage / (2 * pi * f_LO * C_coupling))

Using initial value consideration and values given in [4],

I_LO_leakage= gm * VDS 

VDS=VDD−Ibias⋅RL1,2   = 1.2 -1.96m*500 =1.102V

I_LO_leakage= gm * VDS = 10m * 1.102 = 0.01102A

V_LO_leakage = (0.01102A/ (2 * π* 3kHz * 4pF)) values from [4] and [5]
V_LO_leakage = 0.208V
P_LO_leakage = (0.208V) / (4 * 5Ω) from [4]

P_LO_leakage = 0.00186 =1.86mW
```

## Circuit

![image](https://github.com/Srini-web/DiffrentialLNA-R-/assets/77874288/7e213a57-4d73-4e5c-8d49-cb3cd6650bf0)

Here, R1 and R2 are the differential resistances corresponding to RL1 and RL2, M1 and M3 are NMOSs, M2 and M4 are PMOSs, Vb is the bias current, L1 and L2 are differential inductances. Vin0 is the pure-pulse train. Vin is the final input voltage after adding the bandpass disturbances.
Note: Vins is the secondary sinusoidal voltage which will be connected and used for part B.

## Simulations 

Input voltages
![image](https://github.com/Srini-web/DiffrentialLNA-R-/assets/77874288/ff42ca56-51d3-4c29-9a20-3401f673cfb7)

BPF pulses detail
![image](https://github.com/Srini-web/DiffrentialLNA-R-/assets/77874288/60596844-5cd4-4199-843e-d44eb33102fe)

Vout 1 and Vout 2 refer to Vout+ and Vout- by convention.
![image](https://github.com/Srini-web/DiffrentialLNA-R-/assets/77874288/d752d318-e354-4aba-88f4-996232d3e77f)

Total output wave
![image](https://github.com/Srini-web/DiffrentialLNA-R-/assets/77874288/c898a299-083f-4f5f-80c7-b5ceb013be09)
The above graphs are all results of transient analyses. Now using formulae
Av=20 log10(Vout/Vin), A=10^(Av/20), LO_leakage=(Vout-A*Vin0)/A
We get 

LO_leakage=(V(vout1)-(10^((20*log( V(vout1)/ V(vin)))/20)* V(vin0))/10^((20*log( V(vout1)/ V(vin)))/20)) That plotted is 
![image](https://github.com/Srini-web/DiffrentialLNA-R-/assets/77874288/05920a7e-7b54-4b8c-8b90-bb9a37fde58c)
![image](https://github.com/Srini-web/DiffrentialLNA-R-/assets/77874288/e1d2fae0-4467-48f8-a042-a8f06c3a1177)

`V_LO_leakage = 1V`
with I_LO_leakage =1.6KA
`P_LO_leakage= V_LO_leakage* I_LO_leakage =1 * 1.6K= 1.6KW`

<img width="412" alt="image" src="https://github.com/Srini-web/DiffrentialLNA-R-/assets/77874288/83f524ab-f9f7-4dba-9e3f-c6dcdf2f9513">

## Conclusion
A) The effects of BPF disturbances on pure pulse train input on the lo leakage of the differential LNA are as follows. The BPF attenuates frequencies and only lets signals within a given range pass. The LNA then transforms the impulse train of sinusoidal waves to regular square pulse output. It causes distortion of pulse shape to the extent of changing square waves to sinusoidal ones. The LNA interferes with the functioning of the BPF and we see an unprecedented spike. The output does not seem to match the theoretical output owing to the extremely low frequency assigned) Introducing a secondary sinusoidal wave seems to have an interfering effect. It affects the total input wave due to overlapping. The higher frequency assigned acts in our favour and the overlapping causes the total frequency to regularise leading to a value similar to the theoretical value calculated. It also cuts the stray noises previously present. But when the frequency is reduced, it affects the system negatively and causes erratic output including irregular waveform. 

For a detailed report, please check out DiffferentialLNA-R.pdf








