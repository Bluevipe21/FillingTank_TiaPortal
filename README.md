# FillingTank_TiaPortal
## Brief description

In this project, I have been testing a control function developed in a control systems course that I'm taking on [Udemy](https://www.udemy.com/course/control-de-sistemas-dinamicos/). If someone wants to know more how it works you can buy the course in Udemy.  

The project consists in test control function with a filling tank system using Tia Portal and Factory IO. The PLC used for the project is a 1212C AC/DC/RLY. Inside the project there are folders that contains the functions to make work the control function and also to do the connection with Factory IO. I don´t upload the file with the scene in Factory IO because is very easy to make, is just add the tank included inside the software and configure the drivers to connect with the PLC SIM. Also i recommend to run Factory IO and Tia Portal as administrator to avoid an error connection.

### Note
Initially, I attempted to work with Factory IO, using the tank available in the simulation software. However, I encountered an issue when reading the analog signal. The signal appeared to blink instead of providing real-time measurements. If you have a solution to avoid this error, please let me know—I would greatly appreciate it! :)


## Segments explained

- First segment: This code establishes the connection with Factory IO. Information about the tank used in the project can be found [here](https://docs.factoryio.com/manual/parts/stations/#tank). Additionally, to learn how to set up the connection between TIA PORTAL and Factory IO, refer to this [link](https://docs.factoryio.com/tutorials/siemens/setting-up-s7-plcsim-v13/#setting-up-s7-plcsim-with-tia-portal). Ensure that you correctly write the addresses for the analog and digital inputs and outputs. [Here](https://community.factoryio.com/t/siemens-inputs-not-working/34) is an explanation of one common error due to bad addressing in the PLC driver inside Factory IO.

- Second segment : In this part i read the analog signal, in my case i use a variable because of the analog read error that i described early. This takes a variable between 0 - 27648 that is how the PLC interprets the 0 - 10 volts signal that is receiving. I used the NORM_X block to convert the analog signal to a percentage value between 0.0 - 1.0 and later convert to a real scaled value with the SCALE_X block. The SCALE_X block most have the minimun and maximun value that **the sensor can read for the project**. The output of the block is the height measured and it'll be sending this value to the control function.

- Third segment :  Here i call the control function. Because this is a test i called in the main block. But the control functions is recommended to call it inside the *Cyclic interrupt* block that is an organization block. This is because this organization block is executed more times in the *Scan Cycle* of the PLC. Inside the Control_Function folder are the functions with the integration of error (not integral part of a PID) and the error function. The input of the ControlFunction block has three inputs: the desired value, the gain and the measured value. This can change in case of having more than one variable, because in that case you need two gain values, two measured values and two desired values. Because is a filling tank system this only need one gain that is a proportional gain (not a PID!).

- Fourth and fifth segment : This segments are conditional blocks that manage the behavior of the output *U* of the ControlFunction Block. The variable *U* represents the input for the system, in this case is the input flow to the tank. In case the value *U* is positive this sends an analog signal output to the valve in charge of filling the tank. In case the *U* value is negative this enable the discharge valve analog output and disable the analog signal output to the valve in charge of filling the tank.

The results were good because is an alternative for control functions projects when there is no dynamic model to build the control (that is very common in industrial applications). In addition i don´t take in count a dead band as the Tia Portal' PID has, but is very easy to implement because is just select a range were the control function will not take action. Is like a little tolerance error that can be permissible for the process.   
