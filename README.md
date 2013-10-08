# Puppet Module for Linux Kernel crashdumps

This puppet modules helps enable crashdumps for the Linux kernel on various Linux distributions. As of now it is tested on Ubuntu and CentOS.

## Documentation

Enabling Linux Kernel Crashdumps:

```puppet
     include crashdump
```

## Patches and Testing

Contributions are highly welcomed, more so are those which contribute patches with tests. Or just more tests! We have [rspec-puppet](http://rspec-puppet.com/) and [rspec-system](https://github.com/puppetlabs/rspec-system-serverspec) tests. When [https://help.github.com/articles/using-pull-requests](Github WorkFlow), please make sure that your patches pass tests:

```
  igalic@levix ~/src/bw/puppet-crashdump (git)-[master] % rake spec
  ....................................

  Finished in 2.29 seconds
  36 examples, 0 failures
  igalic@levix ~/src/bw/puppet-crashdump (git)-[master] % rake spec:system

  ...loads of output...
  2 examples, 0 failures
  igalic@levix ~/src/bw/puppet-crashdump (git)-[master] %
```

## Release process

The version in Modulefile should be bumped according to [semver](http://semver.org/) *during development*, i.e.: The first commit after the release should already bump the version, as master at this point differs from the latest release.

When cutting a new release, please

* make sure that all tests pass
* make sure that the documentation is up-to-date
* verify that all dependencies are correct, and up-to-date
* create a new, *signed* tag and a package, using rake

```
    igalic@levix ~/src/bw/puppet-crashdump (git)-[master] % rake release
    git tag -s 1.3.2 -m 't&r 1.3.2'
    ...
    git checkout 1.3.2
    Note: checking out '1.3.2'.
    ...
    HEAD is now at ff9aaae... Most awesome feature added. SHIPIT!
    puppet module build .
    Notice: Building /home/igalic/src/bw/puppet-crashdump for release
    Module built: /home/igalic/src/bw/puppet-crashdump/pkg/brainsware-crashdump-1.3.2.tar.gz
    igalic@levix ~/src/bw/puppet-crashdump (git)-[1.3.2] %
```

* push the tag,

```
    igalic@levix ~/src/bw/puppet-crashdump (git)-[1.3.2] % git push --tags origin
```

* and finally [upload the new package](http://forge.puppetlabs.com/brainsware/linux-crashdump/upload)

License
-------

Apache Software License 2.0


Contact
-------

You can send us questions via mail [puppet@brainsware.org](puppet@brainsware.org), or reach us IRC: [igalic](https://github.com/igalic) hangs out in [#puppet](irc://freenode.org/#puppet)

Support
-------

Please log tickets and issues at our [Project's issue tracker](https://github.com/Brainsware/puppet-crashdump/issues)