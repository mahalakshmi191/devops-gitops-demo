pipeline {

agent any

stages {

stage('Checkout') {
steps {
git 'https://github.com/mahalakshmi191/devops-gitops-demo.git'
}
}

stage('Build Image') {
steps {
sh 'docker build -t lakshu18/demo-app:$BUILD_NUMBER .'
}
}

stage('Push Image') {
steps {
sh '''
docker login -u lakshu18 -p PASSWORD
docker push lakshu18/demo-app:$BUILD_NUMBER
'''
}
}

stage('Update Manifest') {
steps {
sh '''
sed -i "s|lakshu18/demo-app:.*|lakshu18/demo-app:$BUILD_NUMBER|g" k8s/deployment.yaml

git add .
git commit -m "update image tag"
git push
'''
}
}

}
}
