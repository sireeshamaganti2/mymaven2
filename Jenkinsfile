node('built-in') {
    stage('continuousDownload')
    {
       git '  https://github.com/intelliqittrainings/maven.git'
    }
    stage('continuousBuild')
    {
        sh 'mvn package'
    }
    stage('continuousDeployment')
    {
        deploy adapters: [tomcat9(credentialsId: 'd0a088fd-3d1d-47c6-90de-9cb34d77f17b', path: '', url: 'http://172.31.32.43:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('continuousTesting')
    {
       git '  https://github.com/intelliqittrainings/FunctionalTesting.git'
       sh 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline1/testing.jar'
    }
    stage('continuousDelivery')
    {
        deploy adapters: [tomcat9(credentialsId: 'd0a088fd-3d1d-47c6-90de-9cb34d77f17b', path: '', url: 'http://172.31.33.163:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
    
}
