# Blue Green Rollback

This is a Cloud Foundry CLI plugin. I learn/forked code from the great plugin, [autopilot](https://github.com/contraband/autopilot). You can use this command with 
[blue-green-deploy](https://github.com/sakkuru/rollback-push) which enable you to
deploy with versioning. I and Saki is author of this repo. We develop this feature by pair programming on a hackfest. 

You can rollback gracefully from an old version. Use [blue-green-deploy](https://github.com/sakkuru/rollback-push) to deploy apps.

# install 

```
cf insall-plugin PATH_TO_BLUE_GREEN_BINARY
``` 

# usage 

You can specify g1 ro g2 to rollback the apps. 
```
cf blue-green-rollback application-name g1
```

# behavior

```
cf start application-name-g1
cf map-route application-name-g1 xxxx.io (domain name) -n application-name
cf unmap-route application-name xxxx.io (domain name) -n application-name
cf rename application-name application-name-now-on-swapping
cf rename application-name-g1 application-name
cf rename application-name-now-on-swapping application-name-g1
```
