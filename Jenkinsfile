pipeline {
    agent {
        node {
            label 'maven'
        }
    }
    environment {
        PATH = "/opt/apache-maven-3.9.9/bin:$PATH"
        MAVEN_OPTS = "-Xmx4096m"
    }
    stages {
        stage("build") {
            steps {
                sh 'mvn clean deploy -DskipTests'
            }
        }
        stage('SonarQube analysis') {
            environment {
                scannerHome = tool 'emrah-sonar-scanner'
            }
            steps {
                withSonarQubeEnv('emrah-sonarqube-server') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
    }
}