podTemplate(label: 'pod',
    volumes: [hostPathVolume(hostPath: '/var/run/docker.sock', mountPath: '/var/run/docker.sock')
    containers: [
            containerTemplate(name: 'docker', image: 'ibmcase/bluemix-image-deploy:latest', alwaysPullImage: true, ttyEnabled: true)
    ]) {

    node('pod') {
        stage('Distribute Docker Image') {
            checkout scm
            container('docker') {
                stage('testy') {
                    sh 'echo Hi'
                }
            }
        }
    }
}
