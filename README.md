# elementary-dev-os

Build an elementary linux OS for development and devops.
Based for some parts on the [fbertola box](https://github.com/fbertola/dev-box.

For clone submodules
$ git submodule update --init --recursive

## Build vagrant box

The elementary iso url is not static.
If packer has "ISO download failed" issue, please update the iso url in elementary.json file with the good one (view https://elementary.io/).

```
$ packer build elementary.json
$ vagrant box add elementary-dev build/elementaryos-5.0-stable-amd64.box
```

## Build vm

```
$ vagrant up
```

## Local execution

```
cd ansible
echo '[all]' > inventory
echo 'localhost' >> inventory
ansible-playbook -i inventory -u $USER -c local --extra-vars "ansible_distribution=Ubuntu" --extra-vars "ansible_os_family=Debian" --extra-vars "ansible_distribution_release=xenial" --extra-vars "ansible_sudo_pass=SUDOPASSWD" elementary-dev.yml
```
