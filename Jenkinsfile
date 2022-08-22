pipeline {
    agent {
    label 'staging'
    }
     triggers {
        githubPush()
      }
    
   
    stages {
        stage('Restore packages'){
           steps{
               sh 'dotnet restore WebApplication.sln'
            }
         }        
        stage('Clean'){
           steps{
               sh 'dotnet clean WebApplication.sln --configuration Release'
            }
         }
        stage('Build'){
           steps{
               sh 'dotnet build WebApplication.sln --configuration Release --no-restore'
            }
         }
      
        stage('Publish'){
             steps{
               sh 'dotnet publish WebApplication/WebApplication.csproj --configuration Release --no-restore'
               sh 'nohup dotnet WebApplication.dll --urls="http://13.214.36.215:9090" --ip="13.214.36.215" --port=9090 --no-restore > /dev/null 2>&1 &'
             }
        }
 
    }
}
