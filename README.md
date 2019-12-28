# A Go Server Controlled with Systemd

**A Project for GCI 2019.**

## How I create a systemd service
As an example here, I am going to create a systemd service of a tiny Go server that displays "Hello, world!" on localhost:9090.

### Create a service unit file
Create a file called *goweb.service* in /usr/lib/systemd/system/ (the file in my case can be found [here](https://github.com/JikeXiaotian/systemd-go-web/blob/master/goweb.service)).

I think three sections of the unit config are worth specially introducing here.

* ```ExecStart``` in ```[Service]```

	It tells systemd what script should be run when the service gets enabled.

	Format: ```ExecStart=YourShellPath YourScriptPath```

* ```WantedBy``` in ```[Install]```

	It limits the conditions that the service is allowed to start.

	Format: ```WantedBy=TargetName```

* ```Restart``` in ```[Service]```
	
	It appoints when should the service restart(Ususally when errors happen).

	Example: ```Restart=on-failure```


After creating ```goweb.service```, it's time to activate it!

Run ```$ sudo systemctl enable goweb``` in the shell, and there should be output: 

```Created symlink /etc/systemd/system/multi-user.target.wants/goweb.service → /usr/lib/systemd/system/goweb.service.```

### Start the Service
Run ```$ sudo systemctl start goweb```.

In this case, systemctl will run ```/home/jerry/apps/systemd-go-web/goweb.sh``` as I set. And that script will start the go server.


If everything goes well, it should stay in a blocking, and you should be able to see a webpage showing "Hello, world!" on localhost:9090.

### Check the status of the service
```systemctl status goweb```

The Result of this Project:

![Result](https://raw.githubusercontent.com/JikeXiaotian/Image-Storage/master/systemd-go-web/browser-screenshot.png)
