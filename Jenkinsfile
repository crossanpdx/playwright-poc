pipeline {
    agent{
        docker {
            image 'docker pull mcr.microsoft.com/playwright/java:v1.46.0-noble'
        }
    }
    stages {
        stage('test') {
            steps {
                script {
                sh 'mvn compile exec:java -D exec.mainClass=org.example.App'
                }
         }
            
            post {
                success {
                    archiveArtifacts(artifacts: 'homepage-*.png', followSymlinks: false)
                    sh 'rm -rf *.png'
                }
            }
        }
    }
}
