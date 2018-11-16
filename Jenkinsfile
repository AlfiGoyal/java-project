pipeline { 
    agent { label 'linux' }
    stages { 
        stage ("Unit Tests") {
          steps {
            git url: 'https://github.com/AlfiGoyal/java-project.git'
            sh "ant -f test.xml -v"
            junit "reports/result.xml"
          }
        }
        stage ("Build") {
            steps {
                sh 'ant -f build.xml -v'
            }
        }
        stage ("Deploy") {
            steps {
                    sh 'aws s3 cp /workspace/Assignment9Pipeline/dist/rectangle-*.jar s3://jenkins-assignment9-s3bucket-ag/' 
            }
        }
     }
 }
