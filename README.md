# FillingTank_TiaPortal
## Brief description

In this project i was testing a control function developed in a control system course that i'm following in UDEMY. It consist in a control function that works for systems that doesn't have a model. The control function consists in stimated the dynamic of the model. This function only has to measure the variable/variables that we want to control. 

In this example i want to make work the filling tank example (most commonly used) to test the control function. 

### Note: 
I wanted to work with Factory IO with the tank that is included in the simulation software, but it did not work very well. This was beacause at the moment of read the analog signal this was blinking, instead of reading the measure in real time. So if you know how to do the connection to avoid this error let me know please :)

## Segments explained

- First segment : This is the code for the connection with Factory IO. The project to work in Factory IO can be founded [here](https://docs.factoryio.com/manual/parts/stations/#tank). And more information about how to do the connection between TIA PORTAL and Factory IO [here](https://docs.factoryio.com/tutorials/siemens/setting-up-s7-plcsim-v13/#setting-up-s7-plcsim-with-tia-portal). Just make sure to write the addresses of the analog and digital inputs and outputs correctly.


