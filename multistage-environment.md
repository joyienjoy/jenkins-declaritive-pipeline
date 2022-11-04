// This script is for a multiple stages and environment command execution
// Here two variables are defined. $name is Globally defined and $surname is defined locally in stage "Code test"


pipeline {
    agent any
    environment {
        name = 'Joydeep'
    }
    stages {
        stage('Code Test') {
            environment {
                surname = 'Sarkar'
            }
            steps {
                sh '''
                echo "Hello This is 1st script by $name $surname"
                pwd
                sleep 5
                '''
            }
        }
        stage('Code Retest'){
            steps {
                sh '''
                echo $name
                echo $surname
                echo $BUILD_ID
                pwd
                sleep 5
                '''
            }
        }
    }
}


![image](https://user-images.githubusercontent.com/92083624/199916403-12262baa-3101-44fe-9b42-730f23e2b75a.png)

![image](https://user-images.githubusercontent.com/92083624/199916518-967800e9-fc1a-4697-a1d8-e35200e42a50.png)


