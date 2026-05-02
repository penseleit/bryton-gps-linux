# Bryton GPS on linux

This is an attempt to make Bryton GPS devices usable on Linux.


Code for the **Rider40** is now available in the **code** directory.

There is also branches for **Rider20**, **Rider20+**, **Rider35**, **Rider310** and **Rider50**:

- `Rider35
  <https://github.com/Pitmairen/bryton-gps-linux/tree/rider35>`_
- `Rider20 (works with cardio35)
  <https://github.com/Pitmairen/bryton-gps-linux/tree/rider20>`_
- `Rider20+ (works with rider21)
  <https://github.com/Pitmairen/bryton-gps-linux/tree/rider20plus>`_
- `Rider310
  <https://github.com/Pitmairen/bryton-gps-linux/tree/rider310>`_
- `Rider50
  <https://github.com/Pitmairen/bryton-gps-linux/tree/rider50>`_

It currently has the following functionality:

- Readonly not write support
- List track history
- List track summary
- Generate GPX (plain and Garmin extension) and TCX files.
- Upload to strava.com
- Elevation correction using the SRTM Elevation Database.

Use the --help argument to see all the options.

The code is released under the GPL v3 license.

I have only access to a Rider40, but im interested in data from other
devices. See dump.py for an example how to read the data from you device.
It probably works with other devices.


**Rider 40:**

Data Description for Rider40

<https://github.com/pitmairen/bryton-gps-linux/raw/master/Rider40>.


**Rider 10**

Tyr to connect via bluetooth

```
sudo btmon 
```

to view live bluetooth status.

```
sudo bluetoothctl 
```

to try to connect/pair


## Usage:

This code has been updated to use Python 3.14.4.

And if you are using one of Rider20, Rider40, Rider35, you also need the
`py3_sg module <https://pypi.org/project/py3-sg//>`.

Rider50 and Rider20+ don't need this.

### Setup virtual environment

```
  $ cd bryton-gps-linux

  $ python3 -m venv venv
```

### Install dependencies

```
  (.venv)$ pip install -r requirements.txt
```

To access the device without root access you can use the following udev rule:
(Not needed by Rider50 and Rider20+)

```
  SUBSYSTEMS=="usb", ATTRS{idVendor}=="0483", ATTRS{idProduct}=="5720", GROUP="users"
```

Place this into the file "/etc/udev/rule.d/99-brytongps.rules" you may have to reboot for it to take effect.

Now you can run:

```
  (.venv)$ cd code
  (.venv)$ python brytongps.py -h
```
