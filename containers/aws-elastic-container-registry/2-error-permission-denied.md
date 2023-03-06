
# Error Permission Denied

    - URL: https://www.digitalocean.com/community/questions/how-to-fix-docker-got-permission-denied-while-trying-to-connect-to-the-docker-daemon-socket

    1. Create the docker group.
    $ sudo groupadd docker

    2. Add your user to the docker group.
    $ sudo usermod -aG docker ${USER}

    3. You would need to loog out and log back in so that your group membership is re-evaluated or type the following command:
    $ su -s ${USER}

    4. Verify that you can run docker commands without sudo.
    $ docker run hello-world