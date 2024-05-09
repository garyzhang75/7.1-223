pipeline {
    agent any 
     stages {
        stage("Build") {
            steps {
                sh "mvn clean package"
            }
        }
        stage("Unit and Integration Tests") {
            steps {
                sh "mvn test" 
            }
        }
        stage("Code Analysis") {
            steps {
                sh "mvn sonar:sonar" 
            }
        }
        stage("Security Scan") {
            steps {
                sh "mvn org.owasp:dependency-check-maven:check" 
            }
        }
        stage("Deploy to Staging") {
            steps {
                sh "aws deploy-to-staging-script.sh" 
            }
        }
        stage("Integration Tests on Staging") {
            steps {
                sh "mvn verify -Pintegration-tests" 
            }
        }
        stage("Deploy to Production") {
            steps { 
                sh "aws deploy-to-production-script.sh" 
            }
        }
    }
    post {
            success {
                mail to: "gerryzhangshuai@gmail.com",
                subject: "Build status Email",
                body: "Build was successful"
            }
        }
}