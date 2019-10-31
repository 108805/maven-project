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
}
}