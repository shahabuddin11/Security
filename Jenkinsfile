pipeline {
    agent any
        environment {
        registry = "shahidrisi/hobsons-cms-new"
        registryCredential = 'dockerhub-credentials'
        dockerImage = ''

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
            audit repositoryName: "${env.GIT_URL}", branchName: "${env.BRANCH_NAME}", credentialsId: '42crunch-token-id', minScore: 75, platformUrl: 'https://platform.42crunch.com', logLevel: 'DEBUG', shareEveryone: 'READ_ONLY'
                }
             }
   }
}
