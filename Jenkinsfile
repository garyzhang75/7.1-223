pipeline {
    agent any 
     stages {
        stage("Build") {
            steps {
                // Build the code using a build automation tool (e.g., Maven)
                // Tool: Maven
                sh "mvn clean package"
            }
        }
        stage("Unit and Integration Tests") {
            steps {
                // Run unit tests to ensure code functions as expected
                // Run integration tests to ensure components work together
                // Test automation tools: JUnit, TestNG (for unit tests)
                // Test automation tools: Postman, Selenium (for integration tests)
                sh "mvn test" // Assuming Maven is used for both unit and integration tests
            }
        }
        stage("Code Analysis") {
            steps {
                // Integrate a code analysis tool to ensure code meets industry standards
                // Tool: SonarQube, Checkstyle, PMD
                // Jenkins integration: Install and configure SonarQube plugin
                sh "mvn sonar:sonar" // Assuming SonarQube is integrated via Maven
            }
        }
        stage("Security Scan") {
            steps {
                // Perform a security scan on the code to identify vulnerabilities
                // Tool: OWASP Dependency-Check, SonarQube (security features)
                // Jenkins integration: Install and configure OWASP Dependency-Check plugin
                sh "mvn org.owasp:dependency-check-maven:check" // Assuming OWASP Dependency-Check
            }
        }
        stage("Deploy to Staging") {
            steps {
                // Deploy the application to a staging server (e.g., AWS EC2 instance)
                // Tool: AWS CLI, Jenkins Deploy to AWS plugin
                sh "aws deploy-to-staging-script.sh" // Example command for deploying to AWS staging
            }
        }
        stage("Integration Tests on Staging") {
            steps {
                // Run integration tests on the staging environment
                // Ensure application functions as expected in a production-like environment
                // Test automation tools: Postman, Selenium
                sh "mvn verify -Pintegration-tests" // Assuming Maven profile for integration tests
            }
        }
        stage("Deploy to Production") {
            steps {
                // Deploy the application to a production server (e.g., AWS EC2 instance)
                // Tool: AWS CLI, Jenkins Deploy to AWS plugin
                sh "aws deploy-to-production-script.sh" // Example command for deploying to AWS production
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