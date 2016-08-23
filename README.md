# ansible-kafka 

Create Kafka cluster with Zookeeper quorum via Ansible over CentOS*.

## Usage

### Requeriments
-  Ansible 2.0 or higher.

### Steps
#### 1. Install Ansible on your machine

  * **Via YUM:** http://docs.ansible.com/ansible/intro_installation.html#latest-release-via-yum
  * **Via APT:** http://docs.ansible.com/ansible/intro_installation.html#latest-releases-via-apt-ubuntu
  * **Via PIP:** http://docs.ansible.com/ansible/intro_installation.html#latest-releases-via-pip

For other systems, checkout the installation page of Ansible.
http://docs.ansible.com/ansible/intro_installation.html

#### 2. Clone this repo

```
git clone git@github.com:aleonsan/ansible-kafka.git
cd ansible-kafka
```

#### 3. Edit and customize your hosts file.

#### 4. Run Ansible playbook. Check _Tags section_ and _Variables section_ to see other playbook run options.

```
ansible-playbook kafka.yml -i hosts _[options]
```

#### 5. Use Kafka !

* **Creating a topic:** http://kafka.apache.org/documentation.html#quickstart_createtopic
* **Sending messages:** http://kafka.apache.org/documentation.html#quickstart_send
* **Consuming messages:** http://kafka.apache.org/documentation.html#quickstart_consume

## Playbook variables

Use command line variables as playbook input:

* **force_cleanup:** _[True/False]_ Force downloaded packages cleanup. Default or unknown value assumes False. 
```
ansible-playbook kafka.yml -i hosts -e force_cleanup=True 
ansible-playbook kafka.yml -i hosts -e force_cleanup=False 
```

## Playbook tags

Use tags to run a part of the playbook:

```
ansible-playbook kafka.yml -i hosts tags kafka 
ansible-playbook kafka.yml -i hosts tags "zookeeper,kafka" 
ansible-playbook kafka.yml -i hosts tags "java,zookeeper,kafka" 
```

* **java / java_installation:** Install and configure jdk.
* **zk_setup:** Setup user/group _zookeeper_ into zookeeper nodes.
* **zk_installation:** Get _zookeeper_ package if needed and install it.
* **zk_configuration:** Set _zookeeper_ configuration needed, create service script and (re)start it.
* **zookeeper:** zk_setup + zk_installation + zk_configuration.
* **kafka_setup:** Setup user/group _kafka_ into zookeeper nodes.
* **kafka_installation:** Get _kafka_ package if needed and install it.
* **kafka_configuration:** Set _kafka_ configuration needed, create service script and (re)start it.
* **kafka:** kafka_setup + kafka_installation + kafka_configuration.

## Group variables
#### GENERAL variables
* **package_download_path:** Path to download service packages (may be temp).

#### JAVA variables
#### ZOOKEEPER variables
#### KAFKA variables
_coming soon_


