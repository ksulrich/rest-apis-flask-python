# Run code  

```shell
pipenv shell
pip install -r requirements.txt
python app.py
```

Next verify the server

* Install newman: `npm install -g newman`
* Run test: `newman run REST.postman_collection.json --env-var url=http://$(ifconfig | grep "inet 9\." | awk '{ print $2}'):5000
`

You can also run a jenkins server like this:

```shell
docker run -d --name jenkins -p 8080:8080 -p 50000:50000 jenkins/jenkins:lts-jdk11
```

* Login to <http://localhost:8080> as user `admin` and the displayed password
* Install suggested plugins
* Install NodeJS and JDK

**Not needed** Copy jenkins configuration

```shell
docker cp jenkins/config.xml jenkins:/var/jenkins_home/config.xml
```

Copy this job to jenkins

```shell
docker cp jenkins/jobs/baw-evilly jenkins:/var/jenkins_home/jobs/baw-evilly
```

Reload configuration or restart jenkins server

```shell
docker stop jenkins
docker start jenkins
```
