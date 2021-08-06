pipeline {
    agent any
        environment {
        registry = "shahidrisi/hobsons-cms-new"
        registryCredential = 'dockerhub-credentials'
        dockerImage = ''
        GIT_URL="https://github.com/shahabuddin11/Security.git"
        BRANCH_NAME="main"
        Crunch42_Token = credentials('42crunch-token-id-1')

    }
    parameters {
        string(name: 'git_repo_source', defaultValue: 'https://github.com/shahabuddin11/Security.git', description: 'Git repository from where we are going to checkout the code (dev  branch) and build.')
        string(name: 'git_repo_branch', defaultValue: 'main', description: 'The branch to be checked out')
        credentials(name: 'API_TOKEN', defaultValue: 'API Token', description: 'helm repo credentials', credentialType: "Secret text", required: true)
    }
    }
    options {
        disableConcurrentBuilds()
        buildDiscarder(logRotator(daysToKeepStr: '7', artifactDaysToKeepStr: '7'))
        timeout(time: 1, unit: 'HOURS')
    }
   stages {
        stage("Checkout git repo") {
            steps {
                script{
                    // cleanWs()
                // env.code_author_name = sh(returnStdout: true, script: "git --no-pager show -s --format='%an' ${commitId}").trim()
                // env.code_author_email = sh(returnStdout: true, script: "git --no-pager show -s --format='%ae' ${commitId}").trim()
                sh 'echo building image'
                echo "Removing git references"
                
                     }
                }
            
        } 
       stage('Audit OpenAPI files') {
        steps {
            audit repositoryName: "${params.git_repo_source}", branchName: "${params.git_repo_branch}", credentialsId: '42crunch-token-id-1', withCredentials([(credentialsId: params.API_TOKEN, apiToken: 'API Token')]), minScore: 75, platformUrl: 'https://platform.42crunch.com/api/v1/collections', logLevel: 'DEBUG', shareEveryone: 'READ_ONLY'
            }
        }
   }
}
