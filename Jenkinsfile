pipeline {
    agent any

    
    stages {
        stage('git commit') {
            steps {
              sh '''
              
              git clone https://github.com/BhandeAshi/Maven-Build-Student.git
        
        '''  
            }
        }
        stage('build') {
            steps {
                sh '''
               ROOT_PASSWORD="1234"
               echo "$ROOT_PASSWORD" | su -c "apt update -y && apt install maven -y &&  apt install unzip -y"
               
               cd /var/lib/jenkins/workspace/my-first-job/Maven-Build-Student.git/
               mvn clean
               mvn package
                '''
            }
        }
        stage('test') {
            steps {
                echo "successfully test"
            }
        }
        stage('deploy') {
            steps {
              sh '''
            wget  https://dlcdn.apache.org/tomcat/tomcat-8/v8.5.94/bin/apache-tomcat-8.5.94.zip
              
              
              
               unzip apache-tomcat-8.5.94.zip
               cp  /var/lib/jenkins/workspace/my-first-job/Maven-Build-Student.git/target/studentapp-2.2-SNAPSHOT.war /var/lib/jenkins/workspace/project/apache-tomcat-8.5.94/webapps/
               mv /var/lib/jenkins/workspace/my-first-job/apache-tomcat-8.5.94/webapps/studentapp-2.2-SNAPSHOT.war /var/lib/jenkins/workspace/project/apache-tomcat-8.5.94/webapps/studentapp.war
               chmod -R +x /var/lib/jenkins/workspace/my-first-job/apache-tomcat-8.5.94/bin/
              cd /var/lib/jenkins/workspace/my-first-job/apache-tomcat-8.5.94/bin/
               ./startup.sh  
            '''
            }
        }       
}
}
