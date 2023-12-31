# Big Data Architecture - Concepts and Technologies

![Big Data Arch](/Images/Big%20Data%20Architecture.jpeg)

* Big Data Architecture is the foundation for big data analytics.

* It serves as a reference blueprint for big data infrastructures and solutions, logically defining how big data solutions will work, the components that will be used, how information will flow and security details.

## Layers of Big Data Architecture

### Data Ingestion
* Responsible for collecting and storing data from various sources into data repository.
* Determining how data will be ingested, transformed and stored.

### Data Processing
* Collecting, cleaning and preparing the data for analysis
* Ensuring that the data is high quality and ready to be used the future.

### Data Storage
* Storing the data in a format that can be easily accessed and analyzed.
* Ensuring the data is accessible and available to the other layers.

### Data Visualization
* Creating visualizations of data

## Types of Big Data Architecture

### 1. Lambda Architecture
![Lambda Architecture](/Images/Lambda-Architecture.png)
_(batch only serving layer)_
* **Batch Layer**:
    * Responsible for managing the master dataset (all input data).
    * Perform batch processing on the data (as schedule).
    * Outcome are pre-computed views.

_(the process frequency should not be too high to minimize the tasks of merging the results to make up the view)_

* **Speed Layer**:
    * Process any type of data received in realtime
    * Calculation of incremental views that will complement (bổ sung) batch views to provide more recent data.
    * Deleteing obsolete (lỗi thời) realtime views (post-process) batch.

* **Serving Layer**:
    * Responding to queries by returning pre-computed views from the batch layer and real-time views from the speed layer.
    * Index and Expose the data to the queries

### 2. Kappa Architecture
![Kappa Architecture](/Images/Kappa-Architecture.png)
* is a simplified alternative to Lambda Architecture.

* Design mainly for handling streaming data

* Batch Layer is removed and Speed Layer now can provide reprocessing capabilities

||Lambda|Kappa|
|-----|-----|-----|
|Adoption|Easy, reuse existing ETL|More complex, New system need new tech stack|
|Implementation|Simpler|Complex|
|Maintenance|Need to maintain 2 systems (Batch/Stream)|Easier|
|Performance|Depends on the complexity of batch and speed layers|Generally faster due to simplified architecture|
|Resource|Requires more resources for two systems|More resource-efficient|
|Code Duplication|Possible, since batch and speed layers may have similar processing logic|No, as there is only one proccessing layer|
|Use Case|Best for storing historical data|Best for real-time processing|

### 3. Zeta Architecture
![Zeta Architecture](/Images/Zeta-Architecture.png)
* New approach, define a scable way to increase the speed of data integration into the business -> Make business powerful and data-centric.

* Provide containers which isolate software enviroments that can be run and use.

Zeta Architecture consists of 7 elements:
* **Dynamic and Global Resource Management**: 
    * dynamically allocates resources based on the current needs of the system.
        * Computing resources, Storage resources, network resources.
    * Apply to entire system -> Help with overall performance and efficiency

* **Pluggable Compute Model/Execution Engine**:
    * provide different engines and processing models to meet the needs of diverse applications and users within an organization.

* **Realtime Data Storage**:
    * supports the need for high-speed enterprise applications through the use of realtime databases.
    Ex: Cassandra

* **Distributed File System**:
    * All applications read and write on a common scalable solution

* **Deployment / Container Management System**:
    * provide a standardized approach to software deployment.

* **Solution Architecture**: 
* focuse on solving specific business problems and combines one or more applications designed to provide the complete solution.

* **Enterprise Applications**: 
    * provide simplicity and reusability by providing the components needed to achieve all business objectives defined for an application.

### 4. Microservice Architecture
![Microservice](/Images/Microservice-Architecture.png)
* Composed of loose coupling services, which can operate independently.
* They communicate with other via REST Web services.
* Each service focuses on specific task and represents a stand-alone application.


### 5. IoT Architecture
![IoTA](/Images/IoT-Architecture.png)

### Comparison
| | Type of Treatment | Treatment Methodology | Data Frequency | Data Type | Data Format | Data Source | Data Consumers |
| -------- | -------- | -------- | -------- | -------- | -------- | -------- | -------- |
| _**Lambda**_ | Batch/Realtime | Query and Reporting | Real-time feed | Basic Data | Structured, Semi-Structured & Unstructured | Generated by Human/Machine, Web, Social Media | Human |
| _**Kappa**_ | Realtime | Query and Reporting | Continuous Flows | Transactional Data | Structured, Semi-Structured & Unstructured | Generated by Human/Machine, Web, Social Media | Human |
| _**Zeta**_ | Batch/Realtime | Query and Reporting | Ondemand stream | Transactional Data | Structured, Semi-Structured & Unstructured | Web and Social Media, Internal Data Sources | Business Applications |
| _**Microservice**_ | Batch/Realtime | Query and Reporting/Analytic | Ondemand stream | Transactional Data | Structured, Semi-Structured & Unstructured | Internal Data Sources, Machine Generated | Business Process |
| _**IoT-a**_ | Batch/Realtime | Query and Reporting/Analytic/Predictive Analysis | Ondemand stream | Basic Data | Structured, Semi-Structured, Unstructured | Generated by Machine | Human/other data repositories |