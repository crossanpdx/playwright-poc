pipeline {
    agent{
        docker {
            image 'mcr.microsoft.com/playwright:v1.17.2-focal'
        }
    }
        stage('test') {
            steps {
                script {
                sh mvn compile exec:java -D exec.mainClass=org.example.App
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
