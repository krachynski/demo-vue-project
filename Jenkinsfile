pipeline {
    agent any
    stages {
        stage('npm-build') {
            agent {
                docker {
                    label 'linux'
                    image 'docker.io/node:23'
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
