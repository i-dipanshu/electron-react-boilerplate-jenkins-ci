pipeline {
    
    agent any

    tools {
        nodejs "13.14.0"
    }

    environment {
        GITHUB_TOKEN = credentials('github-pta')
        REPOSITORY_URL = 'https://github.com/i-dipanshu/electron-react-boilerplate-jenkins-ci.git'
        NODE_HOME = tool name: 'Node 13.14.0', type: 'jenkins.plugins.nodejs.tools.NodeJSInstallation'
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
        // Stage 2: Install Node.js with npm
        // stage('Install Node.js and NPM') {
        //     steps {
        //         // script {
        //         //     tools {
        //         //         nodejs '13.14.0' 
        //         //     }
        //         // }
        //     }
        // }
        
        //  Stage 2: Install Node.js with npm
        // stage('Install Node.js and NPM') {
        //     steps {
        //         script {
        //             env.PATH="${env.NODE_HOME}/bin:${env.PATH}"
        //             sh 'node -v'
        //             sh 'echo $NODE_HOME'
        //          }
        //     }
        // }

        // Stage 3: Install all dependencies
        stage('npm install') {
            steps {
                sh 'npm version'
                sh 'npm install'
                sh 'npm cache verify'
                sh 'npm cache clean'
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
