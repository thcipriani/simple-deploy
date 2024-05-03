Use this with scap3-dev to recreate the problem in T342162.

    ./scap3-dev.sh con deploy
    cd /srv/deployment
    mkdir simple
    cd simple
    git clone https://github.com/thcipriani/simple-deploy.git deploy
    cd deploy
    scap deploy
    exit
    ./scap3-dev.sh con phorge
    rm /srv/deployment/simple/deploy-cache/revs/*/.git/config-files/tmp/test
    exit
    ./scap3-dev.sh con deploy
    cd /srv/deployment/simple/deploy
    scap deploy
    exit
    ./scap3-dev.sh con phorge
    cat /tmp/test
    cat: /tmp/test: No such file or directory
    ls -lh /tmp
    total 8.0K
    drwx------ 3 root        root        4.0K May  3 21:00 systemd-private-7c18108124f14de3ab4f7f6a93e4c395-apache2.service-ikk6gf
    lrwxrwxrwx 1 scap-deploy scap-deploy  110 May  3 21:08 test -> ../srv/deployment/simple/deploy-cache/revs/4708ba0f3ded7bc0c977822d130cb3d9e3dca958/.git/config-files/tmp/test
