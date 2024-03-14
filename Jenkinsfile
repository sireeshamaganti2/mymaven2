pipeline
{
  agent any
  stages
  {
    stage('ContinuousDownload')
    {
      steps
      {
         git ' https://github.com/sireeshamaganti2/mymaven2.git'
      }
    }
    stage('ContinuousBuild')
    {
      steps
      {
          sh 'mvn package'
      }
    }
    stage('ContinuousDeployment')
    {
      steps
      {
          deploy adapters: [tomcat9(credentialsId: 'd0a088fd-3d1d-47c6-90de-9cb34d77f17b', path: '', url: 'http://172.31.32.43:8080')], contextPath: 'testapp', war: '**/*.war'
      }
    }
    stage('ContinuousTesting')
    {
      steps
      {
          git '  https://github.com/intelliqittrainings/FunctionalTesting.git'
       sh 'java -jar /home/ubuntu/.jenkins/workspace/DeclarativePipeline1/testing.jar'
      }
    }
    stage('ContinuousDelivery')
    {
      steps
      {
           deploy adapters: [tomcat9(credentialsId: 'd0a088fd-3d1d-47c6-90de-9cb34d77f17b', path: '', url: 'http://172.31.33.163:8080')], contextPath: 'prodapp', war: '**/*.war'
      }
    }
  }
}

