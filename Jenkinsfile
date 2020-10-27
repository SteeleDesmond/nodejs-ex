def appName = 'nodejs-ex' 

pipeline {
  agent {
    node {
      label 'nodejs' 
    }
  }
  options {
      timeout(time: 20, unit: 'MINUTES') 
  }
  stages {
      stage('Cloning git') {
          steps {
              git 'https://github.com/SteeleDesmond/nodejs-ex'
          }
      }
      stage('build') {
        // script {
        //   openshift.withCluster() {
        //       openshift.withProject() {
        //         def builds = openshift.selector("bc", appName).related('builds')
        //         timeout(5) { 
        //           builds.untilEach(1) {
        //             return (it.object().status.phase == "Complete")
        //           }
        //         }
        //       }
        //   }
          steps {
              sh 'npm install'
          }
      }
      stage('test') {
          steps {
              sh 'npm test' 
          }
      }
  }
}