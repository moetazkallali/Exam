pipeline {
    agent any
    
    stages {
        stage('Git') {
            steps {
                echo "Getting Project from Git";
                sh "rm -rf Exam"
                sh "git clone https://github.com/moetazkallali/Exam.git"
                  }
            }
            
        stage('MVN Clean'){  
            steps {
                sh "mvn clean"
                  }
        }        
        
        stage('MVN Install'){
            steps {
                sh "mvn install"
                  }
        }       
        
        stage('MVN Test'){
            steps {
                sh "mvn test"
                  }
        }          
        
        stage('MVN Package'){
            steps {
                sh "mvn package"
                  }
        }          
        
        stage('MVN SONARQUBE'){
            steps{
                sh 'mvn sonar:sonar \
  -Dsonar.projectKey=JenkinsExamProject \
  -Dsonar.host.url=http://192.168.1.120:9000 \
  -Dsonar.login=47e5a816defea731387d72ad9707363b75676b29'
                 }
        }    
        stage('MVN NEXUS'){
            steps {
                sh 'mvn deploy -x -Dmaven.test.skip=true'
                  }
        }          
   }
}
