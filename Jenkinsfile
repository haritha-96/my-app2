pipeline{
  agent any
    stages {
        stage('deploy development branch to-tomcat'){
            when {
                branch 'development'
            }
          steps('deploy'){
            echo "hello"
          }
        }
     }
}
