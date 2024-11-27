pipeline {
    agent { label 'linux' }
    stages {
        stage('npm-build') {
            agent {
                docker {
                    image 'node:7.4'
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
