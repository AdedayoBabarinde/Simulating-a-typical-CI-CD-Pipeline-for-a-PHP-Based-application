# Simulating-a-typical-CI-CD-Pipeline-for-a-PHP-Based-application

![image](https://user-images.githubusercontent.com/50416701/133063815-23a7c079-a732-47a9-88ce-f433914b960c.png)



###### Install ansible galaxy dependencies and others

ansible-galaxy collection install community.postgresql
•	python3 -m pip install --upgrade setuptools
•	python3 -m pip install --upgrade pip
•	python3 -m pip install PyMySQL
•	python3 -m pip install mysql-connector-python
•	python3 -m pip install psycopg2==2.7.5 --ignore-installed



##### Jenkinsfile for simple task
```
pipeline {
    agent any
  
  stages {
    stage("Initial Cleanup") {
           steps {
             dir("${WORKSPACE}") {
               deleteDir()
             }
           }
        }

    stage('Build') {
      steps {
        script {
          sh 'echo "Building Stage"'
        }
      }
    }
    
    stage('Test') {
      steps {
        script {
          sh 'echo "Testing Stage"'
        }
      }
    }
    
    stage('Package') {
      steps {
        script {
          sh 'echo "Package App"'
        }
      }
    }
    

    stage('Deploy') {
      steps {
        script {
          sh 'echo "Deploy to Dev"'
        }
      }
    }


    stage('Clean up') {
      steps {
        cleanWs()
      }
    }
    }
}  
```