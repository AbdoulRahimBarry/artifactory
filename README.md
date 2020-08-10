## Implementation of a private registry: Jfrog artifactory

![Jfrog artifactory](https://cdn.opsmatters.com/sites/default/files/logos/jfrog-logo.png)
  ### Create a server on AWS **t2.xlarge** and load the stack [lien](https://github.com/AbdoulRahimBarry/artifactory)

* Or installed from command line
  
  ### prerequisites

* Install docker

`curl -fsSL https://get.docker.com -o get-docker.sh`

`sh get-docker.sh`

`sudo usermod -aG docker centos`

`sudo systemctl enable docker`

`sudo systemctl start docker`
  
  ### Install artifactory-pro version
  
   `mkdir -p $JFROG_HOME/artifactory/var/etc/`

   `cd $JFROG_HOME/artifactory/var/etc/`

   `touch ./system.yaml`

   `chown -R 1030:1030 $JFROG_HOME/artifactory/var`

   `docker run --name artifactory -v $JFROG_HOME/artifactory/var/:/var/opt/jfrog/artifactory -d -p 8081:8081 -p 8082:8082 docker.bintray.io/jfrog/artifactory-pro:latest`
  
  ### To connect: `@IP Jfrog server: 8082`

* Username: admin

* password: password
  
  ### Test an insecure registry

* Edit the `daemon.json` file, whose default location is `/etc/docker/daemon.json`

* If the `daemon.json` file does not exist, create it
  the file should have the following content:
  `{
  "insecure-registries" : ["myregistrydomain.com:5000"]
  }`

* #### the image tags:
  
   `name: "ip_resistry:port_resistry/repository_key/name_image"`

   `tags: "tags_image"`
  
  ### the push/pull image in jfrog artifactory
  
  `push/pull: "ip_resistry:port_resistry/repository_key/name_image:tags_image"`

