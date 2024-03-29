# sample-go

A collection of Go based sample code.

## Overview

This repository host minimal assets develop for the Golang runtime. These samples are used in [Shipwright/Build](https://github.com/shipwright-io/build) for testing purposes.

## Structure

This repository consists of multiple directories, each directory is intended to work with a particular set of tools that are currently supported in [Shipwright/Build](https://github.com/shipwright-io/build).

### `/docker-build`

Assets with a Dockerfile, which indicates how to compile the specified go file.
This asset is intended to work with tools like [Kaniko](https://github.com/GoogleContainerTools/kaniko) and [Buildah](https://github.com/containers/buildah).

### `/source-build`

Assets with pure source code, without any knowledge about Docker.
This asset is intended to work with [Buildpacks](https://buildpacks.io/), like the [Paketo](https://paketo.io/) and [Heroku](https://www.heroku.com/) implementation.

### `/source-build-with-package`

Assets with `main.go` in another target (`/main-package`) rather than in source root. This asset is intended to work with [Buildpacks](https://buildpacks.io/), like the [Paketo](https://paketo.io/) and [Heroku](https://www.heroku.com/) implementation when we have [`BP_GO_TARGETS`](https://github.com/paketo-buildpacks/go-build#bp_go_targets) environment variable.
