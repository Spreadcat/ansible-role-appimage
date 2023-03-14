# Role spreadcat.appimage

Role which deploys appimage applications on the local host.

## Requirements

* Internet access for downloading the appimage images.
* root rights on the target host.

## Role Variables

```yaml
appimage_download_urls: list
```

* List of download URLs for appimage files.

## Other Variables

```yaml
appimage_binary_dir: str
```

* Path to the directory where to store the links for the appimage files.

```yaml
appimage_group: str
```

* Group of the appimage installation directory.

```yaml
appimage_installation_dir: str
```

* Path for storing the installed appimage files.

```yaml
appimage_owner: str
```

* Owner of the appimage installation directory.

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
