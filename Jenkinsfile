pipeline {
   agent any

   stages {
      stage('Pack') {
         steps {
        echo 'Packing UiBank RPA Process.'
        UiPathPack (
        outputPath:'Output', 
        projectJsonPath: 'project.json', 
        version: AutoVersion()
        )
         }
      }
      stage('Test') {
         steps {
            echo 'Execute RPA tests.'
            UiPathTest (
            credentials:[ UserPass:'Orchestrator'], 
            orchestratorAddress: 'https://orch-testingsol-web0-we-webapp.azurewebsites.net/', 
            orchestratorTenant: 'Default', 
            testResultsOutputPath: 'result.xml',
            testTarget: [TestProject(environments: 'ASHENV', testProjectPath: 'project.json')]
            )
         }
      }
      stage('Deploy') {
         steps {
            echo 'Deploying to UAT environment.'
         }
      }
   }
}
