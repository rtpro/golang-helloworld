pipeline {
    agent { label 'slave1' }
    tools { go '1.20' }

    stages {
        
        stage('Build') {
            steps {

                // Build your Go application
                sh "go build -o myapp main.go"
            }
        }
        
        stage('Test') {
            steps {
                // Run tests
                sh "go test main_test.go main.go"
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
