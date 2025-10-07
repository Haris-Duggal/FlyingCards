pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                echo 'Cloning the repository...'
                // Jenkins will automatically clone the repository
            }
        }

        stage('Build') {
            steps {
                echo 'Building the static website...'
                // List files to confirm repo contents
                bat 'dir'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying static website...'
                
                // Create a folder for deployment (if it doesn't exist)
                bat 'if not exist C:\\inetpub\\wwwroot\\mysite mkdir C:\\inetpub\\wwwroot\\mysite'

                // Copy files to your deployment folder
                bat 'xcopy * C:\\inetpub\\wwwroot\\mysite /E /Y'

                // Optional: create a zip archive of the deployed files
                bat 'powershell Compress-Archive -Path * -DestinationPath static_site.zip -Force'

                // Save the zip as a Jenkins artifact
                archiveArtifacts artifacts: 'static_site.zip', fingerprint: true
            }
        }
    }
}
