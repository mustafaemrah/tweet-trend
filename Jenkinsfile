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
        stage("build"){
            steps {
                sh 'mvn clean deploy -DskipTests'
            }
        }
    }
}