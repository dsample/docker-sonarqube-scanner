# Dockerised SonarQube Scanner
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fdsample%2Fdocker-sonarqube-scanner.svg?type=shield)](https://app.fossa.io/projects/git%2Bgithub.com%2Fdsample%2Fdocker-sonarqube-scanner?ref=badge_shield)


The aim of these images are to give the ability to scan a codebase simply, with the only prerequisite on the host (eg. a CI agent) being Docker.

Each languages has its own image, in order to keep them as streamlined as possible:

* `sonarqube-scanner:javascript` for JavaScript

## Usage

Using JavaScript (eg. a Node.JS project) as an example. Within the project's directory, run the following line of code, making sure you have a `sonar-project.properties` file in the current directory.

```shell
docker run --rm -i --user=$(shell id -u) -v $(pwd):/src dsample/sonarqube-scanner:javascript
```

The components of the command above are:

* `--rm`, remove the container upon exit.
* `-i`, wait for the container to exit.
* `--user=$(shell id -u)`, run the container with the User ID (UID) of the current host user. _This allows a CI agent to clean up any files the image may create within the working directory._
* `-v $(pwd):/src`, a 'Docker Volume', making the corrent directory appear within the `/src/` directory within the image.


## License
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fdsample%2Fdocker-sonarqube-scanner.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2Fdsample%2Fdocker-sonarqube-scanner?ref=badge_large)