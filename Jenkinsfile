pipeline {
    agent any
    parameters {
        string(name: 'maven_version', defaultValue: '3.9.3', description: 'Pass the version of Maven')
        string(name: 'terraform_version', defaultValue: '1.8.5', description: 'Pass the version of Terraform')	
        string(name: 'JAVA_VERSION', defaultValue: '11', description: 'Version of Java to download (e.g., 16, 17)')
        boolean(name: 'INSTALL_GIT', defaultValue: true, description: 'Install Git')		
    }
    stages {
        stage('Download Maven') {
            steps {
                sh '''
                cd /var/lib/jenkins/
                sudo wget https://dlcdn.apache.org/maven/maven-3/${maven_version}/binaries/apache-maven-${maven_version}-bin.tar.gz
                '''
            }
        }
        stage('Download Terraform') {
            steps {
                sh '''
                cd /opt
                sudo wget https://releases.hashicorp.com/terraform/${terraform_version}/terraform_${terraform_version}_linux_amd64.zip
                '''
            }
        }
        stage('Download Java') {
            steps {
                    def javaUrl = "https://download.java.net/java/GA/jdk${params.JAVA_VERSION}/binaries/openjdk-${params.JAVA_VERSION}_windows-x64_bin.zip"
                    
                    echo "Downloading Java from: ${javaUrl}"
                    sh "curl -O ${javaUrl}"
            }
        }	
        stage('Download Git') {
            steps {
                sh '''
                    sudo apt-get update
                    sudo apt-get install -y git
                '''
            }
        }			
    }
