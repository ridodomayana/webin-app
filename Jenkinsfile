pipeline {
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'maven') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'maven') {
                    sh 'mvn test'
                }
            }
        }


        stage ('Installation Stage') {
            steps {
                withMaven(maven : 'maven') {
                    sh 'mvn install'
                }
            }
        }

        stage ('SonarQube Scanner') {
            steps {
                withSonarQubeEnv(sonarqube9.9) {
                sh "mvn sonar:sonar"
                }
            }
        }
    }
}
