# WordCount using MapPreduce in Hadoop HDFS

## Overview

* This project uses:
    * Version 
    <table>
    <tr>
        <td>Hadoop</td>
        <td>2.10.1</td>
    </tr>
    <tr>
        <td>Java</td>
        <td>1.8</td>
    </tr>
   </table>
   
## Build project

* Step 1: Export Hadoop classpath
  * *export HADOOP_CLASSPATH=$(hadoop classpath)*
  * *echo $HADOOP_CLASSPATH*
* Step 2: Create compiled directory
  * *mkdir container*
* Step 3: Compile project with Hadoop JARs
  * *javac -cp ${HADOOP_CLASSPATH} -d container/ WordCount.java*
* Step 4: Create project JAR file
  * *jar -cvf wc.jar -C container/ .*
  
## Step & Run project

* Step 1: Create Hadoop input directory for storing our data
  * *hadoop fs -mkdir inputdir*
* Step 2: Copy our local data to Hadoop HDFS directory
  * *hadoop fs -put inputdir/\* inputdir*
* Step 3: Run MapPreduce job in Hadoop
  * *hadoop jar wc.jar WordCount inputdir outputdir*
* Step 4: View MapPreduce result
  * *hadoop fs -cat outputdir/part-r-00000*
