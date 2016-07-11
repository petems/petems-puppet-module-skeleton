# petems-module-skeleton

This is a fork of Gareth R's Puppet Skeleton, tweaked to my requirements.

# Original documentation with a few edits:

Puppet modules often take on the same file system structure. The
built-in puppet-module tool makes starting modules easy, but the build
in skeleton module is very simple. This skeleton is very opinionated.
It's going to assume you're going to start out with tests (both unit and
system), that you care about the puppet style guide, test using Travis,
keep track of releases and structure your modules according to strong
conventions.

[![Build
Status](https://travis-ci.org/petems/petems-puppet-module-skeleton.svg?branch=master)](https://travis-ci.org/petems/petems-puppet-module-skeleton)

## Installation

As a feature, puppet module tool will use `~/.puppet/var/puppet-module/skeleton`
(or `~/.puppetlabs/opt/puppet/cache/puppet-module/` for Puppet 4) as template for
its `generate` command. The files provided here are meant to be better templates
for use with the puppet module tool.

## Manual install

As we don't want to have our .git files and this README in our skeleton, we export it like this :

### for puppet 3.x:

    git clone https://github.com/petems/petems-puppet-module-skeleton
    cd petems-puppet-module-skeleton
    find skeleton -type f | git checkout-index --stdin --force --prefix="$HOME/.puppet/var/puppet-module/" --

### for puppet 4.x

    git clone https://github.com/petems/petems-puppet-module-skeleton
    cd petems-puppet-module-skeleton
    find skeleton -type f | git checkout-index --stdin --force --prefix="$HOME/.puppetlabs/opt/puppet/cache/puppet-module/" --

## the install.sh

I provided a script installing the skeleton in the right place depending on the detected puppet version

## Usage

Then just generate your new module structure like so:

    puppet module generate user-module

Once you have your module then install the development dependencies:

    cd user-module
    bundle install

Now you should have a bunch of rake commands to help with your module
development:

    bundle exec rake -T
    rake acceptance        # Run acceptance tests
    rake build             # Build puppet module package
    rake clean             # Clean a built module package
    rake contributors      # Populate CONTRIBUTORS file
    rake coverage          # Generate code coverage information
    rake help              # Display the list of available rake tasks
    rake lint              # Check puppet manifests with puppet-lint / Run puppet-lint
    rake spec              # Run spec tests in a clean fixtures directory
    rake spec_clean        # Clean up the fixtures directory
    rake spec_prep         # Create the fixtures directory
    rake spec_standalone   # Run spec tests on an existing fixtures directory
    rake syntax            # Syntax check Puppet manifests and templates
    rake syntax:manifests  # Syntax check Puppet manifests
    rake syntax:templates  # Syntax check Puppet templates

Of particular interst should be:

* `rake spec` - run unit tests
* `rake lint` - checks against the puppet style guide
* `rake syntax` - to check your have valid puppet and erb syntax
* `rake metadata_lint` - to check your have a valid metadata.json file

## Thanks

The trick used in the installation above, and a few other bits came from
another excellent module skeleton from [spiette](https://github.com/spiette/puppet-module-skeleton).
