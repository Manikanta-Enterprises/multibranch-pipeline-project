pipeline{
    agent any
    stages{
        stage('Build'){
            steps{
                sh 'npm install'
            }
        }
        stage('Test'){
            steps{
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('Deliever for Development'){
            when{
                branch('development')
            }
            steps{
                sh './jenkins/scripts/deliver-for-development.sh'
                input(message: 'Click OK to proceed for Prod deployement!')
                sh './jenkins/scripts/kill.sh'
                
            }
        }
        stage('Deploy for Production'){
            when{
                branch('production')
            }
            steps{
                sh './jenkins/scripts/deploy-for-production.sh'
                input(message: 'Click OK to proceed for Prod deployement!')
                sh './jenkins/scripts/kill.sh'
                
            }
        }
    }
}
