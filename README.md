# Windows on ARM Device Drivers

Drivers from End of Life (EOL) / End of Sale (EOS) / End of Development (EOD) Hardware, Older Chipsets and other 

## Source

Drivers are pulled from clean OS installs, using either OEM restore media or OEM install media.

`dism /online /export-driver /destination:"x:\Drivers"`

## Usage

Inject into bootable media, usually `install.wim`

See [GUIDE.md](GUIDE.md)

## Devices

| Device | Drivers | OEM Recovery | Windows Recovery |
| -- | -- | -- | -- |
| [Lenovo Yoga C630-13Q50 (81JL)](https://github.com/tordona/woa-device-drivers/tree/main/Lenovo/81JL) | [⬇️](https://github.com/tordona/woa-device-drivers/releases/tag/lenovo-c630-drivers) | x | x |
| [Lenovo Flex 5G 14Q8CX05 (82AK)](https://github.com/tordona/woa-device-drivers/tree/main/Lenovo/82AK) | [⬇️](https://github.com/tordona/woa-device-drivers/releases/tag/lenovo-flex-5g-drivers) | x | x |
| Aspire 1 Laptop - A114-61 (S3US) | x | x | x |
| HP 14-ed0010nr | x | x | x |
| ASUS NovaGo TP370QL | [⬇️](https://github.com/jakibaki/novago-driver-dumpx) | x | x |
| Gateway GWTC11 | x | x | x |
| Gateway GWTN133 | x | x | x |

