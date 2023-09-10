#! /usr/bin/bash 

echo  "Hello Executing the script" 

if command -v aws &>/dev/null; then
   echo "AWS CLI is there installed "
   echo $(aws --version)
   exit 0

fi 

if ! command -v python3 &>/dev/null; then 
   echo "Install python"
   
   exit 1
fi

    apt-get update && apt-get install -y curl unzip sudo
    curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
    unzip awscliv2.zip
    sudo ./aws/install
    rm -rf awscliv2.zip.aws
    

if command -v aws &>/dev/null; then
   echo "AWS CLI is successfullly installed "

   rm -rf aws awscliv2.zip
   echo aws --versionaws: not found

fi



FROM ubuntu:latest

COPY script.sh /script.sh

RUN chmod +x /script.sh

CMD ["sh","script.sh"]
