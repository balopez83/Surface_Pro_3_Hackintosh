## Chapter 7) Other OS Quirks & Fixes

### After installing Other OS's such as ChromeOS, Linux, and even Windows, you may find several things that need to be resolved. Please use the following quirks & fixes to fix known issues.

1. The rotation sensor is not calibrated correctly in Linux. As such you must edit a special file with terminal after installing linux and signing in. Open Terminal and then please use the following commands in terminal to fix rotation issues:

```
sudo nano /etc/udev/hwdb.d/60-sensor.hwdb
```

The file that opens should be empty. Try pasting the following into the terminal window (alternate settings may be needed):

```
sensor:modalias:*
  ACCEL_MOUNT_MATRIX=0, -1, 0; -1, 0, 0; 0, 0, 1
```

After pasting the settings click the following keys (without quotes) on your keyboard to save the file and exit.

```
"CTRL" "O" and then "Enter" and then "CTRL" "X"
```

Your calibration configuration should now be saved. Restart your computer for the changes to go into effect. If you locked screen rotation previously, remember to unlock it for rotation to work again.
