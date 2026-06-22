pipeline {

agent any

stages {

stage('Checkout') {
steps {
git 'https://github.com/user/devops-gitops-demo.git'
}
}


stage('Build Image') {
steps {
sh 'docker build -t demo-app:v1 .'
}
}


stage('Docker Login') {
steps {
sh 'docker push demo-app:v1'
}
}


stage('Deploy') {
steps {
sh '''
kubectl apply -f k8s/
'''
}
}

}

}
