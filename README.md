[![License](http://img.shields.io/:license-apache-blue.svg)](http://www.apache.org/licenses/LICENSE-2.0.html) [![Build Status](https://travis-ci.org/simp/pupmod-simp-chkrootkit.svg)](https://travis-ci.org/simp/pupmod-simp-chkrootkit) [![SIMP compatibility](https://img.shields.io/badge/SIMP%20compatibility-6.0.*-orange.svg)](https://img.shields.io/badge/SIMP%20compatibility-6.0.*-orange.svg)

#### Table of Contents

1. [Description](#description)
2. [Setup - The basics of getting started with chkrootkit](#setup)
    * [What chkrootkit affects](#what-chkrootkit-affects)
    * [Beginning with chkrootkit](#beginning-with-chkrootkit)
3. [Usage - Configuration options and additional functionality](#usage)
4. [Reference - An under-the-hood peek at what the module is doing and how](#reference)
5. [Limitations - OS compatibility, etc.](#limitations)
6. [Development - Guide for contributing to the module](#development)
    * [Acceptance Tests - Beaker env variables](#acceptance-tests)


## Description

chkrootkit is a Puppet module that manages chkrootkit, a daemon that checks for
rootkits on Linux system.


### This is a SIMP module

This module is a component of the [System Integrity Management Platform](https://github.com/NationalSecurityAgency/SIMP), a compliance-management framework built on Puppet.

If you find any issues, they may be submitted to our [bug tracker](https://simp-project.atlassian.net/).

This module is optimally designed for use within a larger SIMP ecosystem, but it can be used independently:

 * When included within the SIMP ecosystem, security compliance settings will be managed from the Puppet server.


## Setup


### What chkrootkit affects

This module configures:
  * chkrootkit package
  * chkrootkit cron job

### Beginning with chkrootkit

To use this module with it's default settings, just instantiate it. The following example is in hiera:

  ```yaml
  ---
  classes:
    - chkrootkit

  ```


## Usage

The class will install the package and crob job automatically.

The output of the cron job will be sent to the default cron mechanism unless
`simp_options::syslog` or `chkrootkit::syslog` is set to true.


## Reference

Please refer to the inline documentation within each source file, or to the module's generated YARD documentation for reference material.


## Limitations

SIMP Puppet modules are generally intended for use on Red Hat Enterprise Linux and compatible distributions, such as CentOS. Please see the [`metadata.json` file](./metadata.json) for the most up-to-date list of supported operating systems, Puppet versions, and module dependencies.


## Development

Please read our [Contribution Guide] (http://simp-doc.readthedocs.io/en/stable/contributors_guide/index.html)


### Acceptance tests

This module includes [Beaker](https://github.com/puppetlabs/beaker) acceptance tests using the SIMP [Beaker Helpers](https://github.com/simp/rubygem-simp-beaker-helpers).  By default the tests use [Vagrant](https://www.vagrantup.com/) with [VirtualBox](https://www.virtualbox.org) as a back-end; Vagrant and VirtualBox must both be installed to run these tests without modification. To execute the tests run the following:

```shell
bundle install
bundle exec rake beaker:suites
```

Please refer to the [SIMP Beaker Helpers documentation](https://github.com/simp/rubygem-simp-beaker-helpers/blob/master/README.md) for more information.
