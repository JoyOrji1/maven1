node('built-in') 
{
    stage('ContinuousDownload')
    {
        git 'https://github.com/JoyOrji1/maven1.git'
    }
    stage('ContinuousBuild')
    {
        sh 'mvn package'
    }
    stage('ContinuousDeployment')
    {
        deploy adapters: [tomcat9(credentialsId: 'cd595cf8-6c78-42e2-8384-ef161cccf279', path: '', url: 'http://172.31.41.233:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('ContinuousTesting')
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh 'java -jar /var/lib/jenkins/workspace/Scriptedpipeline/testing.jar'
    } 
    stage('ContinuousDelivery')
    {
         deploy adapters: [tomcat9(credentialsId: 'cd595cf8-6c78-42e2-8384-ef161cccf279', path: '', url: 'http://172.31.42.23:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
}
