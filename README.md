# car1: Carbon flux AR-1 model

Carbon flux AR-1 model by Ito and Reinhard

This is a tutorial example of carbon flux AR-1 model based on the classic 2 box model of ocean carbon cycle

The model includes an upper ocean box of 50m thickness and the thermocline box of 500m. The model includes phosphate (P) and dissolved inorganic carbon (C) as prognostic variables. The two boxes are mixed by the vertical exchange rate, w, which is a sum of the mean (w0) and noise (epsilon). The biological export of P and C is parameterized as a linear function of surface P, which is fully remineralized in the thermocline box. Biological carbon export can change depending on the variability of surface P supply. For the purpose of gas exchange, temperature, salinity and carbonate alkalinity are assumed to be a constant in this model, and a piston velocity of 2000m/yr is applied with a constant atmospheric pCO2 of 400 micro-atm. The carbonate chemistry coefficients are calculated by the PyCO2SYS package. 

## The governing equations are: 
- Surface P $\frac{dPs}{dt} = \frac{w}{h}(Pd-Ps) - k_{bio}Ps$
- Deep P $\frac{dPd}{dt} = -\frac{w}{H}(Pd-Ps) + k_{bio}\frac{h}{H}Ps$
- Surface C $\frac{dCs}{dt} = \frac{w}{h}(Cd-Cs) - k_{bio}R_{C:P}Ps - GK_H(pCO2 - pCO2atm)$
- Deep C $\frac{dCd}{dt} = -\frac{w}{H}(Cd-Cs) + k_{bio}\frac{h}{H}R_{C:P}Ps$

## Numerical integration
The four equations above are numerically integrated using Euler Forward scheme with a 5-day timestep for 100 years. The last 10 years is used for analysis. 

## Transformation to the AR-1 framework
The above governing equation for surface C can be transformed to the AR-1 model as follows. 
- Air-sea CO2 flux, $F(t) = GK_H(pCO2a - pCO2(t))$. F(t) is positive into the surface ocean. 
- Net Community Production, $NCP(t) = k_{bio}R_{C:P}Ps$
- Surface transport convergence, $STC(t) = \frac{w}{h}(Cd-Cs)$
- AR-1 equation: $\frac{dF}{dt} = -\lambda F + G [ \alpha NCP(t) - \alpha STC(t) ]$ where $\alpha$ is set by the carbonate chemistry as $\frac{\partial CO2}{\partial C}$ and $\lambda$ is the air-sea gas transfer inverse timescale and is equal to $\frac{G \alpha}{h}$

