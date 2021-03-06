# puppet-python

This module is a fork of https://github.com/voxpupuli/puppet-python with modification to
manifests/virtualenv.pp to support specific pip versions.

Puppet module for installing and managing python, pip, virtualenvs and Gunicorn virtual hosts.

**Please note:** The module [stankevich/python](https://forge.puppet.com/stankevich/python) has been deprecated and is now available under Vox Pupuli: [puppet/python](https://forge.puppet.com/puppet/python).

## Usage
For class usage refer to the [Reference]("https://github.com/voxpupuli/puppet-python/blob/master/REFERENCE.md). If contributing, this is updated with
```shell
bundle exec rake strings:generate\[',,,,false,true']
```

### hiera configuration

This module supports configuration through hiera. The following example
creates two python3 virtualenvs. The configuration also pip installs a
package into each environment.

```yaml
python::python_pyvenvs:
  "/opt/env1":
    version: "system"
  "/opt/env2":
    version: "system"
python::python_pips:
  "nose":
    virtualenv: "/opt/env1"
  "coverage":
    virtualenv: "/opt/env2"
python::python_dotfiles:
  "/var/lib/jenkins/.pip/pip.conf":
    config:
      global:
        index-url: "https://mypypi.acme.com/simple/"
        extra-index-url: "https://pypi.risedev.at/simple/"
```

### Using SCL packages from RedHat or CentOS

To use this module with Linux distributions in the Red Hat family and python distributions
from softwarecollections.org, set python::provider to 'rhscl' and python::version to the name
of the collection you want to use (e.g., 'python27', 'python33', or 'rh-python34').

## Release Notes

See [Changelog](https://github.com/voxpupuli/puppet-python/blob/master/CHANGELOG.md)

## Contributors

Check out [Github contributors](https://github.com/voxpupuli/puppet-python/graphs/contributors).
