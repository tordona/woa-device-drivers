# Windows on ARM Device Drivers

Drivers from End of Life (EOL) / End of Sale (EOS) / End of Development (EOD) Hardware, Older Chipsets and other 

## Source

Drivers are pulled from clean OS installs, using either OEM restore media or OEM install media.

`dism /online /export-driver /destination:"x:\Drivers"`

## Usage

Inject into bootable media, usually `install.wim`

See [GUIDE.md](GUIDE.md)

## Devices

* Lenovo Yoga C630-13Q50 (81JL)
