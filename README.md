## Nexus Installation Ubuntu 18.04
    apt-get update  
    apt install openjdk-8-jre-headless -y
    cd /opt
    wget https://sonatype-download.global.ssl.fastly.net/nexus/3/nexus-3.0.2-02-unix.tar.gz
    tar xvzf /opt/nexus-3.0.2-02-unix.tar.gz
    mv /opt/nexus-3.0.2-02 /opt/nexus
## Add "nexus" user
    sudo adduser nexus  
## Add sudo permission to nexus user
    vi /etc/sudoers
    ------------------------------------------
    nexus   ALL=(ALL)       NOPASSWD: ALL
    -------------------------------------------
## Change ownership for nexus directory
    sudo chown -R nexus:nexus /opt/nexus
## add "nexus" to run_as_user
    vi /opt/nexus/bin/nexus.rc
    ----------------------------------------------------
    run_as_user="nexus"
    ----------------------------------------------------
## Create softlink for nexus
    sudo ln -s /opt/nexus/bin/nexus /etc/init.d/nexus
## Switch to nexus user
    su - nexus  
## Start nexus
    /etc/init.d/nexus start
## check in UI
    http://18.236.130.34:8081/
## Default Credentials
    Username: admin
    Password: admin123
