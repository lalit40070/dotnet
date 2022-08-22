pipeline {
    agent any
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
               sh 'nohup dotnet WebApplication.dll --urls="http://localhost:9090" --ip="localhost" --port=9090 --no-restore > /dev/null 2>&1 &'
             }
        }
 
    }
}
