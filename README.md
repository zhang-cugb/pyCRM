_CRM_ is a physics-inspired model for estimating waterflood performance. It estimates the connectivities and time decays between injectors and producers.

# Overview

A literature review has been written by Holanda, Gildin, Jensen, Lake and Kabir, entitled "A State-of-the-Art Literature Review on Capacitance Resistance Models for Reservoir Characterization and Performance Forecasting." They describe CRM as the following:
> The Capacitance Resistance Model (CRM) is a fast way for modeling and simulating gas and waterflooding recovery processes, making it a useful tool for improving flood management in real-time. CRM is an input-output and material balance-based model, and requires only injection and production history, which are the most readily available data gathered throughout the production life of a reservoir.

# Dependencies
    numpy
    numba
    pandas
    scipy
    joblib
    openpyxl

# Install
The source can be downloaded from <https://github.com/frank1010111/pyCRM>

Python source files are in pyCRM.

# A simple example
    import pandas as pd
    from pyCRM.CRM import CRM

    prod = pd.read_csv('testing/data/production.csv').values
    inj = pd.read_csv('testing/data/injection.csv').values
    time = pd.read_csv('testing/data/time.csv').values
    
    crm = CRM(tau_selection='per-pair', constraints='up-to one')
    crm.fit(prod, inj, time)
    q_hat = crm.predict()
    residuals = crm.residual()

