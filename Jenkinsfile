pipeline {
  agent any
  stages {
    stage('get data') {
      steps {
        git(url: 'https://github.com/Chethangowdar/project1.git', branch: 'main', poll: true)
      }
    }

    stage('install kubernetes') {
      steps {
        sh '''swapoff -a
sudo apt install curl
sudo apt-get update && sudo apt-get install -y apt-transport-https curl
sudo curl -fsSLo /usr/share/keyrings/kubernetes-archive-keyring.gpg https://packages.cloud.google.com/apt/doc/apt-key.gpg
echo "deb [signed-by=/usr/share/keyrings/kubernetes-archive-keyring.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list
sudo apt-get update

'''
      }
    }

    stage('shhs') {
      steps {
        sh '''sudo apt-get install -y kubelet=1.21.1-00 kubeadm=1.21.1-00 kubectl=1.21.1-00 #--allow-change-held-packages
sudo apt-mark hold kubelet kubeadm kubectl
'''
      }
    }

  }
}