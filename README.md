# FillingTank_TiaPortal
## Brief description

In this project, I have been testing a control function developed in a control systems course that I'm taking on Udemy. The function is designed for systems that lack a model and aims to estimate the system's dynamics. Its primary requirement is to measure the variable/variables that we want to control.

For this example, I have chosen the filling tank scenario, which is a commonly used test case for evaluating the control function.

### Note: 
Initially, I attempted to work with Factory IO, using the tank available in the simulation software. However, I encountered an issue when reading the analog signal. The signal appeared to blink instead of providing real-time measurements. If you have a solution to avoid this error, please let me know—I would greatly appreciate it! :)

## Segments explained

- First segment : This is the code for the connection with Factory IO. The information about the tank used for the project can be found [here](https://docs.factoryio.com/manual/parts/stations/#tank). And more information about how to do the connection between TIA PORTAL and Factory IO [here](https://docs.factoryio.com/tutorials/siemens/setting-up-s7-plcsim-v13/#setting-up-s7-plcsim-with-tia-portal). Just make sure to write the addresses of the analog and digital inputs and outputs correctly. [Here](https://community.factoryio.com/t/siemens-inputs-not-working/34) is a explanation about some errors may appeared in the project due the connection with Factory IO.

- First segment: This code establishes the connection with Factory IO. Information about the tank used in the project can be found [here](https://docs.factoryio.com/manual/parts/stations/#tank). Additionally, to learn how to set up the connection between TIA PORTAL and Factory IO, refer to this [link](https://docs.factoryio.com/tutorials/siemens/setting-up-s7-plcsim-v13/#setting-up-s7-plcsim-with-tia-portal). Ensure that you correctly write the addresses for the analog and digital inputs and outputs. [Here](https://community.factoryio.com/t/siemens-inputs-not-working/34) is an explanation of some potential errors that may occur in the project due to the connection with Factory IO.

