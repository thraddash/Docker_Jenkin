Notes:
Oracle VM (centos 7)
sudo rpm --import "https://sks-keyservers.net/pks/lookup?op=get&search=0xee6d536cf7dc86e2d7d56f59a178ac6c6238f52e"
sudo yum install -y yum-utils
sudo yum-config-manager --add-repo https://packages.docker.com/1.13/yum/repo/main/centos/7
sudo yum install docker-engine

systemctl enable docker
systemctl start docker

docker pull jenkins

docker images
[root@localhost docker]# docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
jenkins             latest              681ef98a247f        7 days ago          704MB

mkdir /opt/jenkins_home
chown 1000 /opt/jenkins_home

[root@localhost opt]# docker run -p 8080:8080 -p 50000:50000 -v /opt/jenkins_home:/var/jenkins_home -d jenkins
205c968e57c55f74ea2ae82d9647fb57d8f517d803bf5e18d788ad16d1796373

[root@localhost opt]# docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                                              NAMES
205c968e57c5        jenkins             "/bin/tini -- /usr..."   11 seconds ago      Up 10 seconds       0.0.0.0:8080->8080/tcp, 0.0.0.0:50000->50000/tcp   inspiring_mayer

docker exec -it 205c968e57c5 /bin/bash


http://127.0.0.1:8080/
