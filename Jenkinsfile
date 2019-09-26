pipeline{
  agent any
    stages {
        def mvnHome = tool name: 'Apache Maven', type: 'maven'
        def mvnCMD = "${mvnHome}/bin/mvn"
        stage('build using maven') {
            steps {
                sh "${mvnCMD} clean package"
            }
        }
        stage('deploy development branch to-tomcat'){
            when {
                branch 'development'
            }
            steps{
                sshagent(['tomcat-dev']){
                    sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@172.31.45.91:/home/ec2-user/tomcat8/webapps/'
                }
            }
        }
    }
}
