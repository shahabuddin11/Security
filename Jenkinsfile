pipeline {
    agent any
        environment {
        registry = "shahidrisi/hobsons-cms-new"
        registryCredential = 'dockerhub-credentials'
        dockerImage = ''
        GIT_URL="https://github.com/shahabuddin11/Security.git"
        BRANCH_NAME="main"

    }
    parameters {
        string(name: 'git_repo_source', defaultValue: 'https://github.com/shahabuddin11/Security.git', description: 'Git repository from where we are going to checkout the code (dev  branch) and build.')
        string(name: 'git_repo_branch', defaultValue: 'main', description: 'The branch to be checked out')
        
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
                sh "rm -rf .git"
                     }
                }
            
        } 
       stage('Audit OpenAPI files') {
        steps {
<<<<<<< HEAD
            audit repositoryName: "${env.GIT_URL}", branchName: "${env.GIT_BRANCH.replaceFirst(/^.*\//, '')}", credentialsId: '42crunch-token-id', minScore: 75, platformUrl: 'https://platform.42crunch.com', logLevel: 'DEBUG', shareEveryone: 'READ_ONLY'
                
            }
        }
=======
            audit repositoryName: "${params.git_repo_source}", branchName: "${params.git_repo_branch}", credentialsId: '42crunch-token-id', minScore: 75, platformUrl: 'https://platform.42crunch.com/api/v1/collections', logLevel: 'DEBUG', shareEveryone: 'READ_ONLY'
                }
             }
>>>>>>> 46b41a7153bfc1a804ef2acf37f8bc1370c1b8f5
   }
}
