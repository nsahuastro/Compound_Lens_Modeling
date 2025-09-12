# Compound_Lens_Modeling

How to perform compound lens modeling

1- Position modeling: Using only positions
    Notebook: Position_modelingF140W_mp.ipynb

2- Extended Modeling (with fixed Distance Ratio)
   Substep1- Notebook: composite_F140W_5_2_original.ipynb
   Initiallt use optimizer PSO only untill you get the desired result/model

   Substep2- Notebook: composite_F140W_5_2.ipynb
   After getting a good enough model, run mcmc using best parameter from last chain.
   Stop when the parallel mcmc chains converge and provide a physical/sensible model.

3- Free Distance Ratio 
   Notebook: composite_F140W_5_2_DistRatio_3_Original.ipynb
   Add Beta (distance ratio parameter and it's bounds).
   When first chain provides physical result, run next chain with previous best fit.

   Notebook: composite_F140W_5_2_DistRatio_3.ipynb
   Run chain until convergence !

Save mcmc file and go infer cosmological parameters.

This code uses Lenstronomy Package version=1.12.0. Install Lenstronomy and other required packages from requirements.txt   



