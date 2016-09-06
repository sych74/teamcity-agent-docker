Teamcity build agent
========================

This is a teamcity build agent docker image, it uses docker in docker from https://github.com/jpetazzo/dind to allow you to start docker images inside of it :)
When starting the image as container you must set the TEAMCITY_SERVER environment variable to point to the teamcity server e.g.
```
docker run -e TEAMCITY_SERVER=http://localhost:8111
```

Optionally you can specify your ownaddress using the `TEAMCITY_OWN_ADDRESS` variable.

Linking example
--------
```
docker run -d --name=teamcity-agent-1 --link teamcity:teamcity --privileged -e TEAMCITY_SERVER=http://teamcity:8111 sjoerdmulder/teamcity-agent:latest
```

## What is inside

- node 4.2.6, npm 3.5.0
 
##Deployment to the Cloud

###[Jelastic](https://jelastic.com)

This [JPS](../../raw/master/manifest.jps) manifest  deploys TeamCity that initially contains [TeamCity server](https://hub.docker.com/r/sjoerdmulder/teamcity/), [official Postgres image](https://hub.docker.com/_/postgres/) and scalable [TeamCity build agents](https://hub.docker.com/r/sjoerdmulder/teamcity-agent/).

In order to get this solution instantly deployed, click the "Deploy" button, specify your email address within the widget, choose one of the [Jelastic Public Cloud providers](https://jelastic.cloud) and press Install.

[![Deploy](https://github.com/jelastic-jps/git-push-deploy/raw/master/images/deploy-to-jelastic.png)](https://jelastic.com/install-application/?manifest=https://raw.githubusercontent.com/sych74/teamcity-docker/master/manifest.jps) 

To deploy this package to Jelastic Private Cloud, import [this JPS manifest](../../raw/master/manifest.jps) within your dashboard ([detailed instruction](https://docs.jelastic.com/environment-export-import#import)).

More information about Jelastic JPS package and about installation widget for your website can be found in the [Jelastic JPS Application Package](https://github.com/jelastic-jps/jpswiki/wiki/Jelastic-JPS-Application-Package) reference.
