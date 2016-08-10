# IDOT-SmartWorkzone
Yanning Li, Juan Carlos Martinez Mori, August, 2016

## 1) Overview
This repository contains the source code developed during the project *"Improving the effectiveness of smart work zones"* (IDOT R27-155). This repository also supports a journal paper *"Estimating traffic conditions from smart work zone systems"* was submitted to *Journal of Intelligent Transportation Systems* during this project. The preprint of the journal can be downloaded in this [link](https://www.dropbox.com/s/0p4s5amhcjjou5h/LiMoriWork2016.pdf?dl=0). The final project report will be available upon the completion of the project by Oct 15, 2016.

In this project, two work zones in Illinois were modeled and calibrated in a micro calibration software AIMSUN. The source code for calibrating AIMSUN using its API and the calibration data can be found in the AutoCalibration folder. In the calibrated work zones, a variety of sensor network configurations and traffic estimation algorithms were evaluated in terms of traffic estimation accuracy. The source code and data supporting the cross evaluation can be found in the [Cross_Evaluation folder](https://github.com/Lab-Work/IDOT-SmartWorkzone/tree/master/Cross_Evaluation). 

## 2) License

This software is licensed under the *University of Illinois/NCSA Open Source License*:

**Copyright (c) 2016 The Board of Trustees of the University of Illinois. All rights reserved**

**Developed by: Department of Civil and Environmental Engineering University of Illinois at Urbana-Champaign**

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal with the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions: Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimers. Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimers in the documentation and/or other materials provided with the distribution. Neither the names of the Department of Civil and Environmental Engineering, the University of Illinois at Urbana-Champaign, nor the names of its contributors may be used to endorse or promote products derived from this Software without specific prior written permission.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE CONTRIBUTORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS WITH THE SOFTWARE.

## 3) Folders

1. Autocalibration of the microscopic parameters in AIMSUN, which uses Python scripting to automate the calibration of AIMSUN based on NOMAD optimization software. **Please refer to  for the [calibrated parameter values](https://github.com/Lab-Work/IDOT-SmartWorkzone/blob/master/I80_calibrated_AIMSUN_parameters.pdf).**
2. Virtual sensor data generator, which generates realistic sensors measurements using trajectory data from AIMSUN based on dedicated virtual sensor models develope in this project.
3. Implementation of interpolation, kernel filtering, and ensemble Kalman filter algorithms for estimation of the traffic speed, the queue length, and the travel time.
4. Analysis and visualization of estimation resutls. 

