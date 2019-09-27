pipeline{
  agent any
  environment{
      PATH = "/usr/share/maven/bin/:$PATH"
  }
    stages {
        stage("build using maven") {
            steps {
                sh "mvn clean package"
            }
        }
      stage("development branch"){
          when {
                branch 'development'
            }
          steps {
                echo 'hello'
            }
      }
        stage("deploy to-tomcat"){
            steps{
                sshagent(['tomcat-dev']){
                    sh  """
                        scp -o StrictHostKeyChecking=no target/*.war ec2-user@172.31.45.91:/home/ec2-user/tomcat8/webapps/
                        ssh ec2-user@172.31.45.91 /home/ec2-user/tomcat8/tomcatup
                        ssh ec2-user@172.31.45.91 /home/ec2-user/tomcat8/tomcatdown
                    """
                }
            }
        }
    }
}
