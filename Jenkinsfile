pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout your code from your Git repository
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                // Set up Go environment
                def goHome = tool name: 'Go', type: 'GoInstallation'
                env.PATH = "${goHome}/bin:${env.PATH}"
                
                // Build your Go application
                sh "go build -o myapp ./path/to/your/app"
            }
        }
        
        stage('Test') {
            steps {
                // Set up Go environment if not already done
                def goHome = tool name: 'Go', type: 'GoInstallation'
                env.PATH = "${goHome}/bin:${env.PATH}"
                
                // Run tests
                sh "go test ./path/to/your/app/..."
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
