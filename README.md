# Heroku Proxy Buildpack

This is a [Heroku Buildpack](https://devcenter.heroku.com/articles/buildpacks)
for running a reverse proxy to an auxiliary port in a dyno.

```
$ heroku buildpacks:add [this-buildpack]
$ heroku buildpacks:add [your-buildpack]
```

Then choose the port:

```
$ heroku config:set PROXY_PORT=[your-port]
```

Then prefix your web process with `with_proxy` in your `Procfile`:

```
web: with_proxy sh start.sh
```

And deploy. You'll see this in your logs:

```
2015-06-02T22:18:11.921683+00:00 app[web.1]: Starting TCP tunnel on port 5001...
2015-06-02T22:18:11.922536+00:00 app[web.1]: Tunnel running at ec2-52-26-62-97.us-west-2.compute.amazonaws.com:5001
```

Then you can access that port.
