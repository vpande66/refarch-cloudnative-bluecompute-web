podTemplate(label: 'pod',
    volumes: [hostPathVolume(hostPath: '/var/run/docker.sock', mountPath: '/var/run/docker.sock'),
              secretVolume(secretName: 'bluemix-api-key', mountPath: '/var/run/secrets/bluemix-api-key'),
              configMapVolume(configMapName: 'bluemix-target', mountPath: '/var/run/configs/bluemix-target')],
    containers: [
            containerTemplate(name: 'docker', image: 'ibmcase/bluemix-image-deploy:latest', alwaysPullImage: true, ttyEnabled: true),
            containerTemplate(name: 'helm', image: 'ibmcase/helm:latest', alwaysPullImage: true, ttyEnabled: true, command: 'cat'),
            containerTemplate(name: 'kubectl', image: 'ibmcase/kubectl:latest', alwaysPullImage: true, ttyEnabled: true, command: 'cat')
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
