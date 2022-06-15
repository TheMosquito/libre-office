# libre-office

An Open Horizon service making Libre Office usable from any remote browser.

In the browser, it looks like this:

![screen shot of libre-office in the browser](https://raw.githubusercontent.com/TheMosquito/libre-office/master/libreoffice.png)

To use this service outside of Open Horizon:

```
make build
make run
```

Then connect yoour browser to the IP address of the machine where you ran it, at port 3000. For example, if your machine is at 192.168.1.100, you could use this URL:

[http://192.168.1.100:3000/?login=true](http://192.168.1.100:3000/?login=true)

To stop the container you can run:

```
make stop
```

When you are ready to try it inside Open Horizon, setup your Open Horizon credentials in your shell environment, and install the Open Horizon Agent, then:

```
docker login
hzn key create **yourcompany** **youremail**
make build
make push
make publish-service
make publish-patterrn
```

Once the service and the pattern have been published, then you can get the agent on this (or any other) Open Horizon node to deploy it:

```
make agent-run
```

Then you can watch the agreement form, see the container run, then test it:

```
watch hzn agreement list
... (runs forever, so press Ctrl-C when you want to stop)
docker ps
```

Then when you are done you can get the Agent to stop running it with this command that will unregister your node:

```
make agent-stop
```

