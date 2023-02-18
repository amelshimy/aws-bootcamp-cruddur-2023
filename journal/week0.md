# AWS Cloud Project BootCamp 
### Week 0 billing and architecture 

### Activities in AWS:
- Create AWS account.
- Create admin account.
- Secure both accounts with MFA.
- Create billing alarm.

## Activity in Lucid:
- create napkin diagram for an application
![CrudderNapkinDiagram](images/CrudderNapkinDiagram.svg)

## Install AWS cli 
#### Prepare enviornment 
1. Linux machine
    I use vagrant to prepare linux VM to let my PC clean as posible.
    I use Fedora 37 to install aws cli.
    ```vagrant
      config.vm.define "aws" do |amazon|
    amazon.vm.box = "generic/fedora37"
    amazon.vm.hostname = "aws01"
    amazon.vm.provider :libvert do |aws01|
        aws01.cpus = 2
        aws01.memory = 2048
        end    
    end
    ``` 
    vagrant commands:
        ```
        vagrant up aws
        vagrant ssh-config aws >> ~/.ssh/config 
        ssh aws
        sudo dnf update -y 
        ```

2. Install aws cli for linux

    [aws instruction page](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)
    - download zip file 

    ``` 
    curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
    ```
    ![Curl command](images/curl-awscli-zip.png)
    - Unzip the installer 
    ```
    unzip awscliv2.zip
    ```
    - Run installer
    as i do not like to use root previliges as much, so i will install without root/sudo previliges
    ```
    ./aws/install -i /usr/local/aws-cli -b /usr/local/bin
    ```
    to verify the installation, just run 
    ```
    which aws
    ```
    ![Verify the installation](images/aws-install.png)

3. configure AWS account with awd-cli
    - Create CLI access key 
    ![Access key creation](images/access-key.png)
    - Configure aws-cli with my credentiales 
    ```
    aws configure
    AWS Access Key ID [None]: 
    AWS Secret Access Key [None]: 
    Default region name [None]: eu-west-1
    Default output format [None]: 

  ![aws-conf-list](images/aws-access-key.png)

    For verification that credenciales work as expected, run next 
    ```
    aws sts get-caller-identity
    ```
  ![AWS-cli proof](images/aws-proof-cli.png)
  




