# car1: Carbon flux AR-1 model

Carbon flux AR-1 model by Ito and Reinhard

This is a tutorial example of carbon flux AR-1 model based on the classic 2 box model of ocean carbon cycle

The model includes an upper ocean box of 50m thickness and the thermocline box of 500m. The model includes phosphate (P) and dissolved inorganic carbon (C) as prognostic variables. The two boxes are mixed by the vertical exchange rate, w, which is a sum of the mean (w0) and noise (epsilon). The biological export of P and C is parameterized as a linear function of surface P, which is fully remineralized in the thermocline box. Biological carbon export can change depending on the variability of surface P supply. For the purpose of gas exchange, temperature, salinity and carbonate alkalinity are assumed to be a constant in this model, and a piston velocity of 2000m/yr is applied with a constant atmospheric pCO2 of 400 micro-atm. The carbonate chemistry coefficients are calculated by the PyCO2SYS package. 

## The governing equations are: 
- Surface P $\frac{dPs}{dt} = \frac{w}{h}(Pd-Ps) - k_{bio}Ps$
- Deep P $\frac{dPd}{dt} = -\frac{w}{H}(Pd-Ps) + k_{bio}\frac{h}{H}Ps$
- Surface C $\frac{dCs}{dt} = \frac{w}{h}(Cd-Cs) - k_{bio}R_{C:P}Ps - GK_H(pCO2s - pCO2a)$
- Deep C $\frac{dCd}{dt} = -\frac{w}{H}(Cd-Cs) + k_{bio}\frac{h}{H}R_{C:P}Ps$

