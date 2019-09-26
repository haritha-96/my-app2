pipeline{
  agent any
    stages {
        stage('deploy development branch to-tomcat'){
            when {
                branch 'development'
                stage('build using maven') {
                     steps {
                         def mvnHome = tool name: 'Apache Maven', type: 'maven'
                         def mvnCMD = "${mvnHome}/bin/mvn"
                         sh "${mvnCMD} clean package"
                     }
                }
            }
            steps('deploy'){
                 echo "hello"
            }
        }
     }
}
