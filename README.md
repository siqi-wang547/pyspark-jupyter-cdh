# pyspark-jupyter-cdh
Pyspark Jupyter Notebook Daemon on Cloudera CDH

This repository contains files to support the execution of Jupyter notebooks for Pyspark as a daemon on a Cloudera CDH Cluster using the anaconda parcels.

Assuming you have installed anaconda to your CDH cluster using the following guide(s)
http://blog.cloudera.com/blog/2016/02/making-python-on-apache-hadoop-easier-with-anaconda-and-cdh/
http://www.cloudera.com/documentation/enterprise/latest/topics/spark_ipython.html

To enable the Jupyter notebook as a service on a host, as root:

copy the ``pyspark-jupyter-cdh`` file to ``/etc/init.d`` and copy the ``pyspark-jupyter-cdh.sh`` file to ``/usr/local/sbin``

then ``chmod +x /etc/init.d/pyspark-jupyter-cdh`` and ``chmod +x /usr/local/sbin/pyspark-jupyter-cdh.sh``

(ensure the user you wish to use for the daemon has sufficient permissions to execute ``/usr/local/sbin/pyspark-jupyter-cdh.sh``)

If you have installed the anaconda using parcel at defaults the service should operate without changes as the hdfs user.
Otherwise edit the ``/etc/init.d/pyspark-jupyter-cdh`` file and change the values below as you desire

``export DAEMON_USER=hdfs``

``export DAEMON_NAME=pyspark-jupyter-cdh``

``export DAEMON_PATH=/var/jupyter``

``export DAEMON_PORT=8880``


Start the service
``service pyspark-jupyter-cdh start``

Auto start the service
``chkconfig pyspark-jupyter-cdh on``

Point your web browser to your notebook server at http://hostname.domainname:8880

##Using Matplot 
When importing matplotlib, add the following to the beginning of your python code

``%matplotlib notebook``

