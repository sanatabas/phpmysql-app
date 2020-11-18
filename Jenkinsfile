node{

    stage('SCM Checkout')
    {
        git credentialsId: 'sanatabas', url: 'https://github.com/sanatabas/phpmysql-app.git'
    }
    
    stage('Run Docker Compose File')
    {
    
        sh 'sudo docker-compose build'
        sh 'sudo docker-compose up -d'
    }
    
    stage('PUSH image to Docker Hub')
    {
        withCredentials([string(credentialsId: 'dockerhub_id1', variable: 'dockerhub_id1')]) 
        {
            sh "sudo docker login -u sanataba -p ${dockerhub_id1}"
        }
        sh 'sudo docker push sanataba/phpmysql-app_web'
    }
}
