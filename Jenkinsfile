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
                    script{
    def mvn = tool 'Default_Maven';
    withSonarQubeEnv('Sonar_Test1') {
      sh "${mvn}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=maven"
    }
  }
                }
        }
    }
            post{
                success{
                  echo "Published successfully"
                }
            }
}
