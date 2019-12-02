pipeline { 
    agent any 
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('Dev') { 
            steps { 
                sh 'rm -rf *'
                sh 'git clone https://github.com/DilanUA/on-prem-ei-ansible-repo.git'
 		sh 'git clone https://github.com/DilanUA/on-prem-ei-artifact-repo.git' 
 		sh 'sleep 10s'
   		sh 'cp -R on-prem-ei-artifact-repo/ on-prem-ei-ansible-repo/'
  		sh 'mv on-prem-ei-ansible-repo/on-prem-ei-artifact-repo/ on-prem-ei-ansible-repo/files/'
 		sh 'mkdir -p on-prem-ei-ansible-repo/files/packs'
		sh 'wget https://d3pxv6yz143wms.cloudfront.net/8.232.09.1/amazon-corretto-8.232.09.1-linux-x64.tar.gz'
            	sh 'cp amazon-corretto-8.232.09.1-linux-x64.tar.gz on-prem-ei-ansible-repo/files/lib/'
            	sh 'cp /home/ubuntu/.wum3/products/wso2ei/6.5.0/wso2ei-6.5.0.zip .'
            	sh 'cp wso2ei-6.5.0.zip on-prem-ei-ansible-repo/files/packs/'
            	sh 'ansible-playbook -i on-prem-ei-ansible-repo/dev on-prem-ei-ansible-repo/site.yml'
            }
        }
        stage('Staging'){
            steps {
                sh 'echo Staging'
            }
        }
        stage('Prod') {
            steps {
                sh 'echo Prod'
            }
        }
    }
}
