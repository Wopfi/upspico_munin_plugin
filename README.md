# upspico_munin_plugin
## What it does

A Munin plugin for monitoring the [UPS PIco](http://http://pimodules.com/)

This plugin displays the UPS PIco's different voltages and the PCB temperature.

## How to install

First you should clone the repository with
`git clone https://github.com/Wopfi/upspico_munin_plugin.git`
You'll end up with directory called upspico_munin_plugin containing this file and the plugin Python script named `upspico_`

The Plugin needs to be copied into the munin plugin directory which should be
`/usr/share/munin/plugins/`
on the Raspberry Pi.

This plugin is enabled for automatic installation by munin-node-configure so after you followed the above steps you just need to run
`sudo munin-node-configure --shell` to get the shell code for creating the needed symlinks. Or you can just pipe that output directly to the shell by running
`sudo /usr/sbin/munin-node-configure --shell | sudo sh` in the `/etc/munin/plugins` directory.

Either way you should end up with this additional symlinks:
```
lrwxrwxrwx 1 root root 33 May 14 22:02 upspico_temperature -> /usr/share/munin/plugins/upspico_
lrwxrwxrwx 1 root root 33 May 14 22:02 upspico_voltages -> /usr/share/munin/plugins/upspico_
```
Now you just need to restart the munin-node by typing
`sudo service munin-node restart`
and the graphs should start showing up in the next cycle.
