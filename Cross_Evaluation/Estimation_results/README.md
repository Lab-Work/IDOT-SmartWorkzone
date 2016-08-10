# IDOT_Code
This repository contains all the code implemented for IDOT project, including the auto-calibration, virtual sensor modeling, sensor data quality analysis, algorithms for estimating speed, travel time, and the end of the queue, as well as the code that generates all configurations of the network and evaluates their performances.

## Instruction
### How to generate virtual sensor data?
The generated virtual sensor data are logged in [Ixx_repxx_generated.txt](https://github.com/Lab-Work/IDOT_Code/blob/master/Virtual_sensor_data/I57_rep51595_generated.txt). The real data is saved in the separate folder. All the data should have already been generated. 

In case you would like to generate more data, specify the sensor to be generated in [script](https://github.com/Lab-Work/IDOT_Code/blob/master/src/generate_sensors.py). Run the script, it will generate virtual sensor data in the corresponding folder. 
NOTE: it will overwrite previously generated data. Proceed with caution.

### How to auto generate the configuration file?
Modify the [script](https://github.com/Lab-Work/IDOT_Code/blob/master/src/generate_configurations.py) to include additional configurations or algorithms. It will generate a file [Ixx_configurations_input.txt](https://github.com/Lab-Work/IDOT_Code/blob/master/I57_configurations_input.txt) which will be used as the configuration input to the estimators.
NOTE:
  - The current configuration script will generate a configuration file including all different sensor network deployments using all possible spacings, types of sensors, accuracy of sensors, and availabel algortihms.
  - It also include a manually coded I57 configuration in the field.
  - Though all network configurations and algorithms are included in the configuration input file, the estimators will first check the [result log](https://github.com/Lab-Work/IDOT_Code/blob/master/Result/I57_rep51595_generated.txt) to see if any of the estimation result for configuration&algorithm tuple has been previously generated. If so, the estimators will skip this tuple. 

### How to run estimators?
  - Make sure all the virtual sensor data has been generated.
  - Properly configure the configuration_input file to include the new scenarios to estimate.
  - Run script [test_cross_evaluation.py](https://github.com/Lab-Work/IDOT_Code/blob/master/src/test_cross_evaluation.py) to run estimators. 
  - The estimated result will be logged in the [result log file](https://github.com/Lab-Work/IDOT_Code/blob/master/Result/I57_rep51595_generated.txt) and the actual result data will be saved in corresponding result folder. 
  - Uncomment the various plot functions in [test_cross_evaluation.py](https://github.com/Lab-Work/IDOT_Code/blob/master/src/test_cross_evaluation.py) to visualize the result.

## Folders

### [\Three algorithms](https://github.com/Lab-Work/IDOT_Code/tree/master/Three_algorithms)
This folder contains the three algorithms developed for estimating the speed, travel time, and the end of the queue for two work zones: I80 and I57/I64.
Three algorithms are Interpolation, Filtering, EnKF, each hosted in a subfolder.

### [\virtual sensors](https://github.com/Lab-Work/IDOT_Code/tree/master/virtual_sensors)
This folder contains all the code for:
  - modeling sensor noise.
  - generating the noisy sensor (including a perfect sensor) data using the trajectory data from AIMSUN for all different configurations of the network.
  - extracting and visualizing the true states of the road by using the trajectory data.

### \Virtual\_sensor\_data\
This folder does not contain the actual generated data since the data size may be too large. It keeps the following log files trakcing the virtual sensor data generated and to be generated for each replication
  - I80\_rep1\_generated.txt, this file contains the virtual sensors that has been generated. Each row contains one sensor. This file need to be updated if new virtual sensor data is generated. Note no matter how many different sensor networks are used, each sensor must have a unique id.
  - I80\_rep1\_to_generate.txt, this file contains the virtual sensors that need to be generated. This file should be removed if there is no new virtual sensor data that need to be generated. 
  - I57\_rep1\_generated.txt, same as above.
  - I57\_rep1\_to\_generate.txt, same as above.

### E:\\Workzone\\Virtual\_sensor\_data
This folder contains the generated virtual sensor data for two work zones and 10 replications each.
  - \I80\_rep1\sensor\_id.csv, this is the virtual sensor data for sensor_id generated for I80 work zone using trajecotry data in Replication 1.
  - Similar folder structure for all two work zones and 10 replciations each.


### \Result
This folder does not contain the actual traffic estimation result since the actual data may be too large. It keeps logs tracking the generated results which can be later read and analyzed.
  - I80\_rep1\_generated.txt, this file contains the record of the result that has been generated for a configuration including the sensor network and the algorithm used. Note each configuration must have a unique config_id. 
  - I80\_rep1\_to_generate.txt, this file contains the record of the result to be generated.
  - Similarly files exist for I57 and other replications.

### E:\\Workzone\\Result
This folder contains the actual estimation result. For each configuration (including both the sensor network configuration and the algorithm) in each work zone using the data from each replication, four estimates are saved:
  - \I80\_rep1\config\_id\_density.csv, this file contains the density estimation in each cell. A matrix with dimension num\_steps x num\_cells
  - \I80\_rep1\config\_id\_speed.csv, this file contains the speed estimation in each cell. A matrix with dimension num\_steps x num\_cells
  - \I80\_rep1\config\_id\_queueu.csv, this file contains the queue estimation in all time steps. A single column num_steps x 1 with each entry as the length of the queue.
  - \I80\_rep1\config\_id\_traveltime.csv, this file contains the travel time estimation. A single column num_steps x 1 with each entry as the estimated travel time in seconds.

### [\Auto-calibration](https://github.com/Lab-Work/AutoCalibration)
To be merged from a separate [repo](https://github.com/Lab-Work/AutoCalibration).

### [\Sensor data quality analysis](https://github.com/Lab-Work/sensor_quality)
To be merged from a separate [repo](https://github.com/Lab-Work/sensor_quality).
