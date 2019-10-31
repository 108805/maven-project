pipeline{

agent any

stages{
stage('Build'){
steps{
bat label: '', script: 'mvn clean package'
}
post{
success{
echo 'archiving war file'
archiveArtifacts '**/*.war'
}
failure{
echo 'faied to archive'
}
}
}
stage('Deploy to staging'){

steps{
   build 'deploy-to-server'
}
}
stage('Deploy to production'){

steps{

timeout(time: 3, unit: 'DAYS') {
    input 'Waiting for approval'
}
   build 'deploy-to-productin'
}
post{
success{
echo 'deployment successfull'

}
failure{
echo 'faied to deploy'
}

}
}

}
}