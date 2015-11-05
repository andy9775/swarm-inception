## Swarm Inception
Swarm Inception can be used to implement continuous deployments for any Giant Swarm service. Builds are conducted via Docker Hub using Github webhooks. When the build is complete, Docker Hub will call this service's webhooks, which in turn triggers a deployment or update of the service.

Swarm Inception does not provide continuous integration tests. If you would like to do continuous integration builds with tests, you may want to check out [Wercker's CI/CD service](http://wercker.com/).

### Prerequisites
At a minimum you will need the following to launch this guide's services:

* A Github [account](https://github.com).
* A Giant Swarm [account](https://giantswarm.io/request-invite/).
* A Docker Hub [account](https://hub.docker.com).

### Video Walkthrough
Here's another fine video guide by your's truly. Look for the kick.

[![](https://raw.githubusercontent.com/giantswarm/swarm-wercker/master/static/video.png)](https://vimeo.com/134043502)

### Getting Started
This project should take you about 10 minutes to run through. We'll start by forking the sample repo, setting up a Docker Hub account and then configuring it to build the repo.

#### Fork the Repo
Start by heading over to [the swarm-flask-hello repo](https://github.com/giantswarm/swarm-flask-hello) and **fork it** into your Github account. Make sure you leave the repository public!

There are detailed [instructions](https://github.com/giantswarm/swarm-flask-helloworld/blob/master/README.md#flask-helloworld) on the repository's `README.md` file you may follow.

Verify you have built and checked in the `swarm-api.json` file for the `swarm-flask-hello` repo:

```
$ cd swarm-flask-hello # ensure this is your forked copy

$ make config
rm -f swarm-api.json swarm.json
##########################################################
Definition files written...
Check swarm-api.json into your repo before deployment...
##########################################################

$ git add swarm-api.json

$ git commit -m 'config file'
[master 743c7aa] config file
 1 file changed, 18 insertions(+)
 create mode 100644 swarm-api.json

$ git push
Counting objects: 4, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 424 bytes | 0 bytes/s, done.
Total 3 (delta 1), reused 0 (delta 0)
To https://github.com/kordless/swarm-flask-hello.git
   077eddf..743c7aa  master -> master
```

You are now ready to connect this repository to your Docker Hub account.

#### Create Automated Build on Docker Hub
Start by creating an account on [Docker Hub](https://hub.docker.com/) if you don't have one, and then logging into your account.

Click on the `Create` pulldown on the top left of Docker Hub and then click on `Create Automated Build`. If you haven't linked a Github account yet, you will need to do so before continuing with this guide.

Select or search for the `swarm-flask-hello` repository in the list Docker Hub displays. Once you've selected the repository, you'll be presented with the `Automated Build` page:

![](https://raw.githubusercontent.com/giantswarm/swarm-inception/master/assets/setupbuild.png)


{"github": {"org": "kordless", "repo": "python-flask-helloworld", "branch": "master"} }
