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
            echo 'Executing RPA tests.'
            UiPathTest (
            credentials: UserPass('Orchestrator'), 
            orchestratorAddress: 'https://orch-testingsol-web0-we-webapp.azurewebsites.net/', 
            orchestratorTenant: 'Default', 
            testResultsOutputPath: 'result.xml',
            folderName: 'Ashraya',
            timeout: 10000,
            testTarget: TestProject(environments: 'ASHENV', testProjectPath: 'project.json')
            )
         }
      }
      stage('Deploy') {
         steps {
            echo 'Deploying to production Orchestrator.'
            UiPathDeploy (
            credentials: Token(accountName: 'Ashraya', credentialsId: 'UserKey'), 
            environments: 'ASHENV',
            folderName: 'Default', 
            orchestratorAddress: 'https://cloud.uipath.com/', 
            orchestratorTenant: 'Ashraya', 
            packagePath: 'Output'
             )
         }
      }
   }
}
