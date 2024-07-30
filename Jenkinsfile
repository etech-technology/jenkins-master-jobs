pipeline{
  agent {
      label 'slave1'
  }
  stages{
    stage('version-control'){
      steps{
        checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'jenkins_github_id', url: 'https://github.com/etech-technology/jenkins-master-jobs.git']])
      }
    }
    stage('parallel-job'){
      parallel{
        stage('sub-job1'){
          steps{
            echo 'action1'
          }
        }
        stage('sub-job2'){
          steps{
            echo 'action2'
          }
        }
        stage('sub-job3'){
            steps{
                echo 'action3'
            }
        }
      }
    }
    stage('codebuild'){
      agent {
          label 'slave2'
      }
      steps{
        sh 'cat /etc/passwd'
      }
    }
  }
}