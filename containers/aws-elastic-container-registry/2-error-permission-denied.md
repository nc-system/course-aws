
# Error Permission Denied

    - Este error se produce por no reiniciar el PC despues de instalar docker o por no instalar de la 
    documentacion oficial.

    1. instalar docker con la documentacion oficial para evitar este error
    URL: https://docs.docker.com/engine/install/ubuntu/

    2. Reboot PC
    - Con esto se deberia solucionar el problema




    - Esta opcion no es necesario si el proceso anterior es exitoso
    - URL: https://www.digitalocean.com/community/questions/how-to-fix-docker-got-permission-denied-while-trying-to-connect-to-the-docker-daemon-socket

    1. Create the docker group.
    $ sudo groupadd docker

    2. Add your user to the docker group.
    $ sudo usermod -aG docker ${USER}

    3. You would need to loog out and log back in so that your group membership is re-evaluated or type the following command:
    $ su -s ${USER}

    4. Verify that you can run docker commands without sudo.
    $ docker run hello-world