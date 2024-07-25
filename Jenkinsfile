pipeline {
    agent any

    stages {
        stage('Check Python Version') {
            steps {
                script {
                    def pythonVersion = sh(script: 'python --version', returnStdout: true).trim()
                    echo "Python version: ${pythonVersion}"
                }
            }
        }

        stage('Install pip') {
            steps {
                script {
                    // Download get-pip.py
                    sh '''
                    curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
                    python get-pip.py
                    '''

                    // Verify pip installation
                    def pipVersion = sh(script: 'pip --version', returnStdout: true).trim()
                    echo "pip version: ${pipVersion}"
                }
            }
        }

        stage('Install Required Packages') {
            steps {
                script {
                    // Example of installing a package
                    sh 'pip install requests'
                }
            }
        }

        stage('Bomanai') {
            steps {
                script {
                    // Install boman-cli
                    sh 'pip install --no-cache-dir --upgrade boman-cli'
                    
                    // Run boman-cli with the specified command
                    sh '~/.local/bin/boman-cli -a run -cicd jenkins'
                }
            }
        }
    }
}
