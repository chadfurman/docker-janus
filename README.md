# Docker-Janus (Lua Edition)

## What is this?

Janus Gateway is an open-source WebRTC gateway by Meetecho.  Janus Gateway supports writing plugins in C, and now there is a PR open to allow you to write plugins in Lua.

This docker-compose setup will help remove a barrier to entry w.r.t. Lua plugin development in Janus by solving some initial compilation and dependency issues.

When the docker container finishes building and starts up (i.e. `docker-compose up`), the echotest.lua plugin will automatically be loaded in.

Websockets are available on port 8188, http on port 8088 -- both are exposed through Docker.

The only modifications I made to echotest.js were:

1) to change the host to point to localhost (and avoid the ports from the node server)
2) change `janus.plugin.echotest` to `janus.plugin.lua` as it's the lua plugin that loads the script

### This is based on the latest janus-lua branch

To use, clone down the repo and then run:

```
docker-compose up
```

There's also a modified echotest.html bundled in the `html` folder.
To try out the echotest plugin's HTML/JS, put the entire /html directory in your local development document root (or `yarn global add light-server && light-server -s html`)
