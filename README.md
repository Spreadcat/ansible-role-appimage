# spreadcat.appimage

Role which deploys appimage applications on the local host.

## Requirements

* Internet access for downloading the appimage images.
* root rights on the target host.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
appimage_download_urls: []
```

* List of download URLs for appimages. Takes either a list of strings or dicts. See `defaults/main.yml` for details. Using the dict allows it to uninstall an appimage and to set the application name that shall be used to start the application.

```yaml
appimage_installation_dir: '/opt/appimage'
```

* Default installation dir for appimage applications.

## Other variables

Second class variables, not immediately needed.

```yaml
appimage_owner: root
```

* Default user name which owns the appimage files.

```yaml
appimage_group: root
```

* Default group name which owns the appimage files.

```yaml
appimage_binary_dir: /usr/local/bin
```

* Destination directory where the file to start the application will be linked to.

## Dependencies

* None

## Example Playbook

The following example would install two appimage applications:

1. appimage01
1. appimage02

The first application _appimage01_ will be installed and can be started by running `appimage01`.
The second application _appimage02_ will be installed and can be started by running `my_app`.

The parameter `state` is optional when installing, mandatory when removing and needs to be set to `state: absent` then.

```yaml
---
- hosts: all
  vars:
    appimage_download_urls:
      - 'https://example.com/appimage01.image'
      - name: 'my_app'
        url: 'https://example.com/appimage02.image'
        state: present
  roles:
     - role: spreadcat.appimage
```

## License

BSD

## Author Information

This role is written an maintained by DBV.
