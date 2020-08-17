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
            echo 'Execute smoke tests.'
         }
      }
      stage('Deploy') {
         steps {
            echo 'Deploying to UAT environment.'
         }
      }
   }
}
