pipeline
{
agent any
stages
{
    stage('Continue Download')
    { 
     steps
     {
         git 'https://github.com/intelliqittrainings/maven.git'
     }
    }
    stage('Continue Build') 
    {
     steps
{
    sh 'mvn package'
}    
    }
    stage('Continue Deployment')
    {
steps
{
        deploy adapters: [tomcat9(credentialsId: 'cdb57107-2ffe-4c9d-b5c5-9795648bdee7', path: '', url: 'http://172.31.95.249:8080')], contextPath: 'testd', war: '**/*.war'
    }
}
    stage('Continue Testing')
    {
steps
{
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh 'java -jar /var/lib/jenkins/workspace/declarativepipeline/testing.jar'
    }
}
stage('Continue delivery')
    {
steps
{
input message: 'need approval for delivery manager', submitter: 'srinivas'
deploy adapters: [tomcat9(credentialsId: 'cdb57107-2ffe-4c9d-b5c5-9795648bdee7', path: '', url: 'http://172.31.94.133:8080')], contextPath: 'prodd', war: '**/*.war'
}
}
}
}
