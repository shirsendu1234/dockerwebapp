node {

    checkout scm

    docker.withRegistry('https://registry.hub.docker.com', 'shir1234') {

        def customImage = docker.build("miltonc/dockerwebapp")

        /* Push the container to the custom Registry */
        customImage.push()
    }
}
