pipeline {
  agent any
  stages {

stage('Project information!') {
    steps {
            echo "Nome do projeto no git ${APP_NAME_GIT}"
            echo "Tag usada para deploy ${BRANCH_TAG}"
            sh 'echo ${USER}'
            sh 'node -v'
            sh 'npm -v'
        }
   }
  

stage('Git Clone') {
            steps  {
                 sh 'rm -rf ${APP_NAME_GIT} && git clone -b ${BRANCH_TAG} https://github.com/brunobaltazar/${APP_NAME_GIT}.git'
                 echo 'Projetos clonados'
                 }  
            } 
            
stage('Buid e Test') {
            steps  {
                 sh 'ls -l && pwd'
                 sh 'cd ${APP_NAME_GIT} && npm install'
                 sh 'cd ${APP_NAME_GIT} && npm test'
                 
                 }  
            } 
   
stage('Docker build e push registry') {
            steps  {
                 sh 'docker system prune -f'
                 sh 'docker image prune -a -f'
                 sh 'cd ${APP_NAME_GIT} && docker build --tag ${APP_NAME_GIT}:${BRANCH_TAG} .;'
                 sh 'docker tag ${APP_NAME_GIT}:${BRANCH_TAG} tecnobooks.azurecr.io/${APP_NAME_GIT}:${BRANCH_TAG};'
                 sh 'docker images'
                 sh 'docker login -u $ACR_USER -p $ACR_PASSWORD https://$ACR_SERVER'
                 sh 'docker push  tecnobooks.azurecr.io/${APP_NAME_GIT}:${BRANCH_TAG}'
            }
         }

       
stage('Deploy Aks Azure') {
            steps  {
		    sh 'cd ${APP_NAME_GIT}'
		    sh 'ls -l && pwd'
		    sh 'sed -i -e "s/TOKEN/${APP_NAME_GIT}/g" ${APP_NAME_GIT}/k8s-deployment.yaml'
		    sh 'sed -i -e "s/APP_NAME_GIT/${APP_NAME_GIT}:${BRANCH_TAG}/g" ${APP_NAME_GIT}/k8s-deployment.yaml'
		    sh 'cat ${APP_NAME_GIT}/k8s-deployment.yaml'
		    sh 'kubectl delete pods ${APP_NAME_GIT} || echo "não a pods da aplicação ${APP_NAME_GIT} para remover" '
		    sh 'kubectl create -f  ${APP_NAME_GIT}/k8s-deployment.yaml'
            }
         }   
   }
}