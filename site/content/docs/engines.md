+++
Categories = []
Description = ""
Tags = []
title = "Engines"
date = 2014-09-06T03:30:04Z
+++

A Shipyard cluster contains one or more "engines".  An engine is a Docker daemon that is listening via TCP.  There are no agents or remote applications to install to enable management; just the Docker API.

When an engine is added in Shipyard, you define resource limits for the specified engine.  Those limits are used when scheduling containers to make sure the engine can fulfill the request.  You can also specify SSL certificates for secure communication.

## ID
Each engine has an arbitrary identifier.  This can be anything to identify the engine.

## Addr
This is the URL that is used to access the engine.  Use `http://` for non-SSL endpoints and `https://` for SSL protected.

## Resources
Each engine has a defined limited amount of resources.  These are CPU shares and Memory (in MB).

## Labels
An engine can have one or more labels.  These are used for scheduling and placing containers.

## SSL
An engine can be configured to use SSL.  See the [Docker docs](https://docs.docker.com/articles/https/) on running with SSL.

# Examples

## Add an Engine
```bash
shipyard add-engine --id local --addr http://10.1.2.3:2375 --cpus 4.0 --memory 8192 --label dev --label local
```

## View Engines
```bash
shipyard engines
```

## Inspect an Engine
```bash
shipyard inspect-engine local
```

## Remove an Engine
```bash
shipyard remove-engine local
```