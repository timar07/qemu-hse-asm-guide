# Ошибка `qemu-system-x86_64: -cdrom debian-13.3.0-amd64-netinst.iso: Failed to lock byte 100`

Возникает из-за того, что `qemu` не может прочитать образ дебиана, ему тупо не хватает прав.
Если вы качали образ из бразуера, отличного от `firefox` или `chrome`, то это может быть его вина.

Для решения этой проблемы, предлагаю следующее:

```sh
rm -f ./debian-13.3.0-amd64-netinst.iso

brew install wget

wget https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/debian-13.3.0-amd64-netinst.iso
```

После этого команда `bootvm` должна работать.
