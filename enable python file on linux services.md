https://tinkerboarding.co.uk/forum/thread-1056.html


Besides adding a line to the autostart file you can also make a systemd Service file. Using systemd makes it easier to manage your processes..

example of an service file.
Code:
```
[Unit]
Description=Description of the processes
After=multi-user.target (defines when to start the sevice file)

[Service]
Type=idle
ExecStart=/user/bin/python example.py (what to execute)

[Install]
WantedBy=multi-user.target (to which target this applies to)
```

The service files has to be added to the following directory:
Code:
```
/etc/systemd/system/<file_location>
```

When the Service files are added to the above metioned location, then the user has to execute the following commando's

Code:
```
sudo systemctl daemon-reload (Notifies that there are changes to the Service files of new Service files are added)
sudo systemctl enable <file_name>.service (tells systemd that the service file has to be executed on start up)
```

When you reboot your TinkerBoard the script should start up at boot.

Some useful commando's that can be used to manually start, stop or see the status of the service file:
Code:
```
sudo systemctl start<file_name>.service  (starts the service)
sudo systemctl stop<file_name>.service  (stops the service)
sudo systemctl status<file_name>.service  (displays the status of the service)
```

For more information:
https://www.freedesktop.org/software/systemd/man/systemd.service.html

Hope this helps for futher readers.
