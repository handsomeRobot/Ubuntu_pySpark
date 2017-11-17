# Ubuntu_pySpark
Documents the setup and running of pySpark(2.2.0) on Ubuntu(16.04)

#Install pySpark (original post: https://blog.sicara.com/get-started-pyspark-jupyter-guide-tutorial-ae2fe84f594f)

Before installing pySpark, make sure you have Java 8 or higher installed on your computer.
1. First of all, visit the Spark downloads page (http://spark.apache.org/downloads.html). Select the latest Spark release, a prebuilt package for Hadoop, and download it directly.Unzip it and move it to your /opt folder:    
$ tar -xzf spark-2.2.0-bin-hadoop2.7.tgz
$ mv spark-2.2.0-bin-hadoop2.7 /opt/spark-2.2.0  

2. Create a symbolic link:  
$ ln -s /opt/spark-1.2.0 /opt/spark  

3. Finally, tell your bash (or zsh, etc.) where to find spark. To do so, configure your $PATH variables by adding the following lines in your ~/.bashrc (or ~/.zshrc) file:  
export SPARK_HOME=/opt/spark  
export PATH=$SPARK_HOME/bin:$PATH  

4. Your terminal need to be restarted to run pySpark.  

#Setup the basic configurations
Before this, you need to ensure that pcs in the cluster all have ssh installed and configured.

1. Change directory to /etc, and add the followings lines to the hosts file, the nickname and ip should be replaced according to your case:    
master 192.168.0.101  
slave02 192.168.0.102  
slave03 192.168.0.101

2. Change directory to /opt/spark/conf, make a copy of slaves.template file and rename into slaves. And add the following lines into the slaves file, the nicknames should be replaced accordingly:  
slave02  
slave03  

3. Make a copy of the spark-env.sh.template file and rename into spark-env.sh. Add the following line, the ip should be replaced accordingly:  
SPARK_MASTER_HOST=192.168.0.101  

4. Copy the above edited files to the same directory of all the nodes.

5. On your master machine, change directory to /opt/spark/sbin and start the master host by the following command:  
$ sudo start ./start-master.sh

6. Launch your browser and visit localhost://8080, you should see your master running at the assigned ip address.  

7. For each slave machine, change directory to /opt/spark/sbin and start the slave by the following command, the master ip and port should be replaced accordingly:   
$ sudo ./start-slave.sh spark://192.168.0.101:7077  

8. Now refresh your webpage, you should see all the nodes running properly :)  

9. More detailed discussions are available in the attached PPT file. 

10. In order to make use of hdfs on Spark, we need to install hadoop first. Please follow the detailed steps here (https://www.digitalocean.com/community/tutorials/how-to-install-hadoop-in-stand-alone-mode-on-ubuntu-16-04)

11. And detailed introduction on setting up and navigating hdfd:  
(https://www.tutorialspoint.com/hadoop/index.htm)

