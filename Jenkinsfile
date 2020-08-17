pipeline {
   agent any

   stages {
      stage('Pack') {
         steps {
        echo 'Packing UiBank RPA Process.'
        UiPathPack (
        outputPath:'${WORKSPACE}\\Output', 
        projectJsonPath: '${WORKSPACE}', 
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
