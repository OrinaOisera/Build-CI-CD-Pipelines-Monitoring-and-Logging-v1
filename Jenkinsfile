pipeline {
     agent any
     stages {
         stage('Build') {
             steps {
                 sh 'echo "Hello World"'
                 sh '''
                     echo "Multiline shell steps works too"
                     ls -lah
                 '''
             }
         }
         stage('Lint HTML') {
              steps {
                  sh 'tidy -q -e *.html'
              }
         }      
         stage('Upload to AWS') {
              steps {
                   pwd();
                   
                  withAWS(region:'us-east-1',credentials:'jenk2') {
                   def identity=awsIdentity();
                      s3Upload( file:'index.html', bucket:'s3jenkins23', path:'index.html')
                  }
              }
         }
     }
}
