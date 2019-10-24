# Setting up Nexus on AWS Linux

## SSH into Linux server

Using putty or MobaXterm or any ssh client

## Install java 

sudo yum install java-1.8.0-openjdk -y


## Install Nexus 3

```
  cd /opt/
  
  sudo wget https://download.sonatype.com/nexus/3/latest-unix.tar.gz
```

Untar the file

```
  sudo tar xvf latest-unix.tar.gz
```

Change the ownership

```
  sudo chown -R ec2-user:ec2-user nexus-3.19.1-01 sonatype-work
  
```

## Run nexus as a service

### 1 Change user for nexus
open bin/nexus.rc and make sure the following line is present
```
  run_as_user="ec2-user"
```

### 2 Execute following command

```
  sudo ln -s /opt/nexus-3.19.1-01/bin/nexus /etc/init.d/nexus
 
  cd /etc/init.d
  sudo chkconfig --add nexus
  sudo chkconfig --levels 345 nexus on
  sudo service nexus start
```

