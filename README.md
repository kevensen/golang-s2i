# golang-s2i
## Introduction
This is a Source-to-Image builder for Golang applications.  It supports the Source strategy in OpenShift.

## Included Templates
There are two templates included in this repository.  The [golang.yml](templates/golang-s2i.yml) template builds the builder image.  The [golang.yml](templates/golang.yml) defines the build and deployment for Golang apps using the Golang S2I builder image.

## Building the Builder Image
Before building and deploying Golang based apps, the Golang S2I builder image must first be bult.  There are a couple ways to build the builder image.  One is to use the template.  The other is to use **oc new-build...** from the command line.

### Building from the Template
The template can be imported into OpenShift through the web console.  Alternatively it can be porcessed from the CLI.  For example:
```terminal
oc new-project golang-test
oc process -f templates/golang-s2i.yml | oc create -f -
``` 

### Using oc new-build
Another method to build the builder is the **oc new-build** command/sub-command.
```terminal
oc new-project golang-test
oc new-build https://github.com/kevensen/golang-s2i --to=golang-s2i
```
