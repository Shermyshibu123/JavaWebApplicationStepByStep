pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                git 'https://github.com/Shermyshibu123/JavaWebApplicationStepByStep.git'
                sh "mvn clean package"
            }
        }
        stage('Test') {
            steps {
                echo 'Testing'
                sh "mvn test"
                
            }
    }
          
    stage('Publish') {
            steps {
                echo 'Publishing'
                sh "mvn package"
            }
    }
      stage('SonarQube Analysis') {
                steps{
                   sh "mvn clean verify sonar:sonar \
  -Dsonar.projectKey=maven \
  -Dsonar.host.url=http://localhost:9000 \
  -Dsonar.login=sqp_2e2d85423bcdabef2bc0b0fcda6e80965d3b1f39"
  }
                }
        }
    }
