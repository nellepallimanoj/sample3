pipeline {
  agent any
  parameters {
    gitParameter branchFilter: 'origin/(.*)', defaultValue: 'production', name: 'BRANCH', type: 'PT_BRANCH'
  }
  stages {
    stage('Example') {
      steps {
        git branch: "${params.BRANCH}", url: 'https://github.com/nellepallimanoj/sample3.git'
      }
      
    }
    stage('Tesing') {
            steps {
                sh 'git clone https://github.com/nellepallimanoj/sample3.git'
            }
        }
        stage('dir') {
            steps {
                
                sh 'cat sample3/src/main/webapp/application.properties'
                
               
            }
        }
        stage ('Print'){
            steps {
                script {
                     def inptext = readFile file: "sample3/src/main/webapp/application.properties" 
                     inptext = inptext.replaceAll(~/root/, "#")      
                     writeFile file: "sample3/src/main/webapp/application.properties", text: inptext
                }

            }
        }     
  }
}
