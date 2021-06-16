# uwsgi_app

This role configures a new uwsgi service.

## Dependencies

This role uses [uwsgi](https://github.com/itbane/ansible-uwsgi) to install uwsgi itself.

## Variables

| variables | default | description |
| --------- | ------- | ----------- |
| uwsgi_app__name | - | A name for the app - will be used as file- and servicename |
| uwsgi_app__config | `{}` | A dict containing key/value pairs that will be written to the `ini`-File | 
| uwsgi_app__systemd_config | `{}` | A dict containing key/value pairs that will be written to an systemd-override-file to extend uwsgi service configuration |

## Usage:

~~~yaml
- name: deploy uwsgi
  roles:
    - name: uwsgi_app
      vars:
        uwsgi_app__name: my-app
        uwsgi_app__config:
          socket: 127.0.0.1:5000
          master: true
          plugin: python
          chdir: "/my/app/dir"
          module: app:app
          processes: 2
~~~

# Authors

Jascha Sticher (itbane) <dev@b4ne.de>
