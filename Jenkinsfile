pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout your code from your Git repository
                git clone https://github.com/rtpro/golang-helloworld.git
            }
        }
        
        stage('Build') {
            steps {
                // Set up Go environment
                def goHome = tool name: 'Go', type: 'GoInstallation'
                env.PATH = "${goHome}/bin:${env.PATH}"
                
                // Build your Go application
                sh "go build -o myapp ./main.go"
            }
        }
        
        stage('Test') {
            steps {
                // Set up Go environment if not already done
                def goHome = tool name: 'Go', type: 'GoInstallation'
                env.PATH = "${goHome}/bin:${env.PATH}"
                
                // Run tests
                sh "go test ./main_test.go main.go"
            }
        }
        
        stage('Cleanup') {
            steps {
                // Optionally clean up artifacts or perform other cleanup tasks
                sh "rm -f myapp"
            }
        }
    }
    
    post {
        always {
            // Archive any artifacts you want to keep
            archiveArtifacts artifacts: 'myapp', allowEmptyArchive: true
        }
    }
}
