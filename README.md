# Configure mac keyboard for linux

This is what needs to be run to make the mac external keyboard work properly in linux.

## Fix <> in the wrong place
### Immediately:
```echo 0 | sudo tee /sys/module/hid_apple/parameters/iso_layout```
### Permanently:
```
echo options hid_apple iso_layout=0 | sudo tee -a /etc/modprobe.d/hid_apple.conf
sudo update-initramfs -u -k all
```

## Fix the FN button so that the F keys are F-keys by default
### Immediately:
```echo 2 | sudo tee /sys/module/hid_apple/parameters/fnmode```
### Permanently:
```
echo options hid_apple fnmode=2 | sudo tee -a /etc/modprobe.d/hid_apple.conf
sudo update-initramfs -u -k all
```

## Just fix it...

```
echo 0 | sudo tee /sys/module/hid_apple/parameters/iso_layout
echo 2 | sudo tee /sys/module/hid_apple/parameters/fnmode
echo options hid_apple iso_layout=0 | sudo tee -a /etc/modprobe.d/hid_apple.conf
echo options hid_apple fnmode=2 | sudo tee -a /etc/modprobe.d/hid_apple.conf
sudo update-initramfs -u -k all
```


