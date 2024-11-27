pipeline {
    agent any
    stages {
        stage('npm-build') {
            agent {
                docker {
                    label 'linux'
                    image 'node:23'
                    registryUrl 'https://docker.io'
                    registryCredentialsId 'jenkins-docker-hub'
                }
            }

            steps {
                echo "Branch is ${env.BRANCH_NAME}..."

                withNPM(npmrcConfig: 'npmrc') {
                    echo "Performing npm build..."
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }
    }
}
