# Content

- [Summary Report](https://github.com/tanvirseraj/Restful-Booker-Performance-Testing#SummaryReport)
- [Introduction](https://github.com/tanvirseraj/Restful-Booker-Performance-Testing#introduction)  
- [Install](https://github.com/tanvirseraj/Restful-Booker-Performance-Testing)      
- [Prerequisites](https://github.com/imranhasanraaz/jmeter-perfomance-testing#prerequisites)
- [Elements of a Minimal Test Plan](https://github.com/imranhasanraaz/jmeter-perfomance-testing#Elements-of-a-minimal-test-plan)    
- [Test Plan](https://github.com/imranhasanraaz/jmeter-perfomance-testing#test-plan)
- [Collection of API](https://github.com/imranhasanraaz/jmeter-perfomance-testing#collection-of-api)   
    - [List of API](https://github.com/imranhasanraaz/jmeter-perfomance-testing#list-of-api) 
    - [Load the JMeter Script](https://github.com/imranhasanraaz/jmeter-perfomance-testing#load-the-jmeter-script)
- [Make jtl File](https://github.com/imranhasanraaz/jmeter-perfomance-testing#make-jtl-file)  
- [Make html File](https://github.com/imranhasanraaz/jmeter-perfomance-testing#make-html-file)  
- [HTML Report](https://github.com/imranhasanraaz/jmeter-perfomance-testing#html-report) 

# Summary Report



![Screenshot 2024-01-16 170507](https://github.com/tanvirseraj/Restful-Booker-Performance-Testing/assets/85784149/5963d7a1-4faf-4383-a72c-ccfcc4fd784b)



# Introduction

This document explains how to run a performance test with JMeter against an https://restful-booker.herokuapp.com/

# Install

**Java**  
https://www.oracle.com/java/technologies/downloads/

**JMeter**  
https://jmeter.apache.org/download_jmeter.cgi  

Click =>Binaries    
=>**apache-jmeter-5.6.2.zip**

**We use BlazeMeter to generate JMX files**    
https://chrome.google.com/webstore/detail/blazemeter-the-continuous/mbopgmdnpcbohhpnfglgohlbhfongabi?hl=en

# Prerequisites
- As of JMeter 5.6, Java 8 and above are supported.
- we suggest  multicore cpus with 4 or more cores.
- Memory 16GB RAM is a good value.


# Elements of a minimal test plan
- Thread Group

    The root element of every test plan. Simulates the (concurrent) users and then run all requests. Each thread simulates a single user.

- HTTP Request Default (Configuration Element)

- HTTP Request (Sampler)

- Summary Report (Listener)

# Test Plan

Testplan > Add > Threads (Users) > Thread Group (this might vary dependent on the JMeter version you are using)

- Name: Users
- Number of Threads (users): 10
- Ramp-Up Period (in seconds): 1
- Loop Count: 1

  1) The general setting for the tests execution, such as whether Thread Groups will run simultaneously or sequentially, is specified in the item called Test Plan.

  2) All HTTP Requests will use some default settings from the HTTP Request, such as the Server IP, Port Number, and Content-Encoding.

  3) Each Thread Group specifies how the HTTP Requests should be carried out. To determine how many concurrent "users" will be simulated, one must first know the number of threads. The number of actions each "user" will perform is determined by the loop count.

  4) The HTTP Header Manager, which allows you to provide the Request Headers that will be utilized by the upcoming HTTP Requests, is the first item in Thread Groups.

# Collection of API

- Run BlazeMeter  
- Collect Frequently used API  
- Save JMX file then paste => **apache-jmeter-5.6.2\bin**

    ### List of API 

    - https://restful-booker.herokuapp.com/
    
   **OR**
    
  ### Load the JMeter Script 
   - File > Open (CTRL + O)
   - Locate the "Restful-Booker.jmx" file contained on this repo
   - Open those file
   - The Test Plan will be loaded
     
![Screenshot 2024-01-16 164435](https://github.com/tanvirseraj/Restful-Booker-Performance-Testing/assets/85784149/ad32458f-0e07-4459-9727-abc6e4cfeb8c)



# Test execution (from the Terminal)
 
- JMeter should be initialized in non-GUI mode.
- Make a report folder in the **bin** folder.  
- Run Command in __jmeter\bin__ folder.

 ### Make jtl file

```bash
  jmeter -n -t Restful-Booker.jmx -l Restful-Booker.jtl
```      
  Then continue to upgrade Threads(200 to 400) by keeping Ramp-up Same.   

After completing this command  
   ### Make html file   
  
  ```bash
  jmeter -g Report\Restful-Booker.jtl -o Restful-Booker.html
```
  - **g**: jtl results file

  - **o**: path to output folder

    ![Screenshot 2024-01-16 165209](https://github.com/tanvirseraj/Restful-Booker-Performance-Testing/assets/85784149/35307f29-98b6-46bb-a901-87fcb46c0eb4)


# HTML Report

![Screenshot 2024-01-16 165503](https://github.com/tanvirseraj/Restful-Booker-Performance-Testing/assets/85784149/a272d62c-666e-4803-b34b-f0b5e5f3d29d)

![Screenshot 2024-01-16 165531](https://github.com/tanvirseraj/Restful-Booker-Performance-Testing/assets/85784149/52a6001c-247d-4c79-bf44-124175cced1c)

