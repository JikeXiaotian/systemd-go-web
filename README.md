# A Go Server Controlled with Systemd

**A Project for GCI 2019.**

## How I create a systemd service
As an example here, I am going to create a systemd service of a tiny Go server that displays "Hello, world!" on localhost:9090.

### Create a service unit file
Create a file called *goweb.service* in /usr/lib/systemd/system/ (the file in my case can be found [here](https://github.com/JikeXiaotian/systemd-go-web/blob/master/goweb.service)).

Especially, two sections of the unit configuration file is important.

The first one is ```ExecStart``` in ```[Service]``` part. It tells systemd that what script should be run when the service gets enabled.

Format: ```ExecStart=YourShellPath YourScriptPath```
