pipeline {
    
    agent any

    tools {
        nodejs "13.0.0"
    }

    environment {
        GITHUB_TOKEN = credentials('github-pta')
        REPOSITORY_URL = 'https://github.com/i-dipanshu/electron-react-boilerplate-jenkins-ci.git'
    }

    stages {
        // Stage 1: configure the Github repository 
        stage('Checkout') {
            steps {
                sh 'echo Github and repository and credential is already configured during pipeline configuration'
                // uncomment below line if we're using direct script 
                // git branch: 'main', url: env.REPOSITPRY_URL
            }
        }
        // // Stage 2: Install Node.js with npm
        // stage('Install Node.js and NPM') {
        //     steps {
        //         // script {
        //         //     tools {
        //         //         nodejs '13.0.0' 
        //         //     }
        //         // }

        //         nodejs(nodeJSInstallationName: 'Node 14.0.0') {
        //             sh 'npm config ls'
        //         }
        //     }
        // }
        
        // Stage 3: Install all dependencies
        stage('npm install') {
            steps {
                sh 'npm version'
                sh 'npm install'
            }
        }
        
        // Stage 4: Run npm tes
        stage('npm test') {
            steps {
                sh 'npm run package-ci'
                sh 'npm run lint'
                sh 'npm run ts'
            }
        }
    }
}
