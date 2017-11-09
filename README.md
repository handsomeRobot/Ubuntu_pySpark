# Ubuntu_pySpark
Documents the setup and running of pySpark(2.2.0) on Ubuntu(16.04)

#Install pySpark (original post: https://blog.sicara.com/get-started-pyspark-jupyter-guide-tutorial-ae2fe84f594f)

Before installing pySpark, make sure you have Java 8 or higher installed on your computer.
1. First of all, visit the Spark downloads page. Select the latest Spark release, a prebuilt package for Hadoop, and download it directly.Unzip it and move it to your /opt folder:    
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

4. 

