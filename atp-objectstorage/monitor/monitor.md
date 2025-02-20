# Monitor Extracts and Replicats

## Introduction

This lab walks you through the steps to monitor the Extract and Replicat processes created and run in the previous lab.

Estimated Lab Time: 2 minutes

Watch the video below for a quick walk-through of the lab.
[Monitor Extracts and Replicats](videohub:1_x48jlq8y)

### About Performance Monitoring

Monitoring the performance of your GoldenGate instance ensures that your data replication processes are running smoothly and efficiently. You can monitor performance in both the Oracle Cloud Infrastructure (OCI) GoldenGate Deployment Console as well as in the Oracle Cloud Console on the Deployment Details page.

### Objectives

In this lab, you will:
* View charts and statistics using the Performance Metrics Server in the GoldenGate deployment console
* Use Metrics on the Deployment Details page in the Oracle Cloud Console to determine overall instance health and utilization.

### Prerequisites

In order to complete this lab, you should have completed the preceding lab and have both an Extract and Replicat running.

## Task 1: Perform inserts to the source database

1.  Return to the Oracle Cloud console and use the navigation menu (hamburger icon) to navigate back to **Oracle Database**, **Autonomous Transaction Processing**, and then **SourceATP**.

2.  On the SourceATP Details page, click **Tools**, and then **Database Actions**.

3.  Use the SourceATP database credentials in the Workshop details to log in to Database Actions, and then click **SQL**.

4.  Enter the following inserts, and then click **Run Script**:

    ```
    <copy>Insert into SRC_OCIGGLL.SRC_CITY (CITY_ID,CITY,REGION_ID,POPULATION) values (1000,'Houston',20,743113);
Insert into SRC_OCIGGLL.SRC_CITY (CITY_ID,CITY,REGION_ID,POPULATION) values (1001,'Dallas',20,822416);
Insert into SRC_OCIGGLL.SRC_CITY (CITY_ID,CITY,REGION_ID,POPULATION) values (1002,'San Francisco',21,157574);
Insert into SRC_OCIGGLL.SRC_CITY (CITY_ID,CITY,REGION_ID,POPULATION) values (1003,'Los Angeles',21,743878);
Insert into SRC_OCIGGLL.SRC_CITY (CITY_ID,CITY,REGION_ID,POPULATION) values (1004,'San Diego',21,840689);
Insert into SRC_OCIGGLL.SRC_CITY (CITY_ID,CITY,REGION_ID,POPULATION) values (1005,'Chicago',23,616472);
Insert into SRC_OCIGGLL.SRC_CITY (CITY_ID,CITY,REGION_ID,POPULATION) values (1006,'Memphis',23,580075);
Insert into SRC_OCIGGLL.SRC_CITY (CITY_ID,CITY,REGION_ID,POPULATION) values (1007,'New York City',22,124434);
Insert into SRC_OCIGGLL.SRC_CITY (CITY_ID,CITY,REGION_ID,POPULATION) values (1008,'Boston',22,275581);
Insert into SRC_OCIGGLL.SRC_CITY (CITY_ID,CITY,REGION_ID,POPULATION) values (1009,'Washington D.C.',22,688002);</copy>
    ```

5.  In the ATPDeployment deployment console, click the **Extract name (UAEXT)**, and then click **Statistics**. Verify that **SRC\_OCIGGLL.SRC\_CITY** is listed with 10 inserts.

    ![UAEXT](images/01-04a.png " ")

    ![Extract Process Information - Statistics](https://oracle-livelabs.github.io/goldengate/ggs-common/monitor/images/04-17-ext-stats.png " ")

6.  Go back to the Overview screen, click the **Replicat name (REP)**, and then click **Statistics**. Verify that **SRC\_OCIGGLL.SRC\_CITY** is listed with 10 inserts.

    ![Replicat Process Information - Statistics](https://oracle-livelabs.github.io/goldengate/ggs-common/monitor/images/01-06-rep-statistics.png " ")

7.  In the Oracle Cloud console, navigate to the OCI Object Storage bucket and then download the JSON file OCI GoldenGate created.

    ![Buckets in Oracle Cloud navigation menu](images/01-07a.png " ")

    ![Buckets](images/01-07b.png " ")

## Task 2: Using the Performance Metrics Server

1.  In the GoldenGate deployment console, click **Performance Metrics Server**, and then click **EXT**.

    ![Performance Metrics Service page - EXT highlighted](https://oracle-livelabs.github.io/goldengate/ggs-common/monitor/images/05-01-perf-serv.png " ")

    > **Note:** *You can also view performance details for the Administration, Distribution, and Receiver Servers, as well as any processes created.*

2.  Click **Database Statistics**.

    ![Database Statistics page](https://oracle-livelabs.github.io/goldengate/ggs-common/monitor/images/05-03-db-stats.png " ")

    Here, you can view the real time database statistics, such as Inserts, Updates, Deletes, and so on.

4.  Repeat steps 1-3 in OBJDeployment to view a snapshot of the Replicat's (named **Rep** in our lab) Database Statistics.

## Task 3: Viewing GoldenGate metrics in the Oracle Cloud console

1.  On the OCI GoldenGate Deployments page, select **ATPDeployment**.

2.  On the ATPDeployment details page, scroll down to the **Metrics** section.

    ![Metrics on Deployment Details page](https://oracle-livelabs.github.io/goldengate/ggs-common/monitor/images/05b-02-metrics.png " ")

3.  Review the **DeploymentInboundLag** and **DeploymentOutboundLag** charts.

4.  Refresh your view after 5 minutes to see updated metrics.

5.  You can repeat these steps for the OBJDeployment.

In this lab, you learned to monitor performance in the OCI GoldenGate deployment console and in the Oracle Cloud console.

**Proceed to the next lab.**

## Learn more

* [Monitor performance in the Oracle Cloud console](https://docs.oracle.com/en/cloud/paas/goldengate-service/vddvk/index.html)
* [Monitor performance in the deployment console](https://docs.oracle.com/en/cloud/paas/goldengate-service/alllr/index.html)

## Acknowledgements
* **Author** - Jenny Chan, Consulting User Assistance Developer, Database User Assistance
* **Contributors** -  Denis Gray, Database Product Management
* **Last Updated By/Date** - Jenny Chan, July 2022
