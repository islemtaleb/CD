pipeline {
    agent any
    stages{
       
        stage('Checkout GIT') {
            steps {
                echo 'Pulling branch from Git' ;
                git branch: 'main',
                
                url: 'https://github.com/islemtaleb/CD.git';                     
            }
        }
     stage('build'){
    steps {
          script{
          sh "npm -v "
          sh "npm install --legacy-peer-deps"

          sh "ansible-playbook Ansible/build.yml -i Ansible/inventory/host.yml"
}
}
}
    stage('DockerImage'){
    steps {
          script{
          sh "ansible-playbook Ansible/docker.yml -vvv -i Ansible/inventory/host.yml"
}
}
}
stage('Push to Dockerhub'){
    steps {

          script{
          sh "ansible-playbook Ansible/docker-registry.yml -i Ansible/inventory/host.yml"
}


}
}

}
}
