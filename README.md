# elementary-dev-os

Build an elementary linux OS for development and devops.
Based for some parts on the [fbertola box](https://github.com/fbertola/dev-box).

## Build vagrant box

```
$ packer build elementary.json
$ vagrant box add elementary-dev build/elementaryos-0.4.1-amd64.box
```

## Build vm

```
$ vagrant up
```
