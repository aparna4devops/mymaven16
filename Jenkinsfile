
pipeline
{
    agent any
    stages
  {
    stage('continous download')
        {
         steps
            {
              git 'https://github.com/intelliqittrainings/maven.git'
            }
         }
         stage('continous build')
        {
         steps
        {
          sh 'mvn package'          
         }
        }
        stage('continous deployment')
        {
       steps
        {
           deploy adapters: [tomcat9(credentialsId: '6395dc2e-5378-4e00-9d04-1c0a798b3745', path: '', url: 'http://172.31.30.227:8080')], contextPath: 'test1app', war: '**/*.war'       
         }
        }
        stage('continous testing')
        {
       steps
        {
            git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
            sh 'java -jar /var/lib/jenkins/workspace/declarativepipeline/testing.jar'
         }
        }
        stage('continous Delivery')
        {
       steps
        {
          deploy adapters: [tomcat9(credentialsId: '6395dc2e-5378-4e00-9d04-1c0a798b3745', path: '', url: 'http://172.31.31.86:8080')], contextPath: 'prod1app', war: '**/*.war'   
         }
        }
   }
}
