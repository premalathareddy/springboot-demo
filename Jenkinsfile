pipeline {
    agent any

    environment {
        JAVA_HOME = tool name: 'JDK 17', type: 'Tool'
        MAVEN_HOME = tool name: 'Maven 3', type: 'Tool'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    // Ensure Maven is used
                    sh "'${MAVEN_HOME}/bin/mvn' clean install"
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Running tests
                    sh "'${MAVEN_HOME}/bin/mvn' test"
                }
            }
        }

        stage('Package') {
            steps {
                script {
                    // Package the application
                    sh "'${MAVEN_HOME}/bin/mvn' package"
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Deploy to the desired environment (e.g., Dev, Prod)
                    // Example: sh "scp target/*.jar user@server:/path/to/deploy"
                    echo "Deploying to the environment..."
                }
            }
        }
    }

    post {
        success {
            echo 'Build and deployment succeeded.'
        }

        failure {
            echo 'Build failed.'
        }

        always {
            cleanWs()
        }
    }
}
