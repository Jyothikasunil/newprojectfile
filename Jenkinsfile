pipeline {
    agent any

    stages {
        stage("Build") {
            steps {
                echo "Building the code using Maven"
            }
        }

        stage("Unit and Integration Tests") {
            steps {
                echo "Running unit tests with JUnit"
                echo "Running integration tests with Selenium"
            }
        }

        stage("Code Analysis") {
            steps {
                echo "Running code analysis with SonarQube"
            }
        }

        stage("Security Scan") {
            steps {
                echo "Running security scan with OWASP ZAP"
            }
            post {
                success {
                    archiveArtifacts artifacts: 'logs/*', allowEmptyArchive: true
                    emailext to: "jyothikasunil006@gmail.com",
                        subject: "Security Scan Successful",
                        body: "The security scan was successful. Check the attached logs for details.",
                        attachLog: true
                }
                failure {
                    archiveArtifacts artifacts: 'logs/*', allowEmptyArchive: true
                    emailext to: "jyothikasunil006@gmail.com",
                        subject: "Security Scan Failed",
                        body: "The security scan failed. Check the attached logs for details.",
                        attachLog: true
                }
            }
        }

        stage("Deploy to Staging") {
            steps {
                echo "Deploying the application to staging server using AWS CodeDeploy"
            }
        }

        stage("Integration Tests on Staging") {
            steps {
                echo "Running integration tests on the staging environment with Selenium"
            }
            post {
                success {
                    archiveArtifacts artifacts: 'logs/*', allowEmptyArchive: true
                    emailext to: "jyothikasunil006@gmail.com",
                        subject: "Staging Tests Successful",
                        body: "The integration tests on the staging environment were successful. Check the attached logs for details.",
                        attachLog: true
                }
                failure {
                    archiveArtifacts artifacts: 'logs/*', allowEmptyArchive: true
                    emailext to: "jyothikasunil006@gmail.com",
                        subject: "Staging Tests Failed",
                        body: "The integration tests on the staging environment failed. Check the attached logs for details.",
                        attachLog: true
                }
            }
        }

        stage("Deploy to Production") {
            steps {
                echo "Deploying the application to production server using AWS CodeDeploy"
            }
            post {
                success {
                    archiveArtifacts artifacts: 'logs/*', allowEmptyArchive: true
                    emailext to: "jyothikasunil006@gmail.com",
                        subject: "Deployment to Production Successful",
                        body: "The deployment to the production server was successful. Check the attached logs for details.",
                        attachLog: true
                }
                failure {
                    archiveArtifacts artifacts: 'logs/*', allowEmptyArchive: true
                    emailext to: "jyothikasunil006@gmail.com",
                        subject: "Deployment to Production Failed",
                        body: "The deployment to the production server failed. Check the attached logs for details.",
                        attachLog: true
                }
            }
        }
    }
}
