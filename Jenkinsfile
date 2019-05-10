#!/测试

pipeline {
    agent any
    stages {
        stage('build-test') {
            steps {
                sh 'dotnet restore ./WebApiTest/WebApiTest.csproj'
                sh 'dotnet build ./WebApiTest/WebApiTest.csproj'
            }
        }
    stage('Publish') {
            steps{
                sh 'dotnet build ./WebApiTest/WebApiTest.csproj'
                sh 'dotnet publish ./WebApiTest/WebApiTest.csproj -o "$(pwd)/publish" --framework netcoreapp2.2'
                echo 'publish done'
            }
        }
    stage('Deploy To Server') {
            steps{
            sshPublisher(publishers: [sshPublisherDesc(configName: 'Tencent2', 
            transfers: [sshTransfer(cleanRemote: false, excludes: '', 
            execCommand: '''pwd''', 
            execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: 'EDC.XDP.Core.Delivery.API/', remoteDirectorySDF: false, removePrefix: 'EDC.XDP.Core.Delivery.API/publish/', sourceFiles: 'EDC.XDP.Core.Delivery.API/publish/**')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
            echo 'Deploy To Server Done'    
            }
        }
        
    }
}