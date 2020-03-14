pipeline {
    agent any
    tools { // Tools must be declared in Jenkins
        maven 'Apache-Maven 3.6.3'
    }
    stages {
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''
            }
        }
        stage ('Build') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                    mvn --version
                    mvn -e -X install
                '''
            }
        }
        stage('Results') {
            steps {
                junit 'target/surefire-reports/**/*.xml'
                archive 'target/*.jar'
            }
        }
    }
}
