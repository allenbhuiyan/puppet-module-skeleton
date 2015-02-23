# Puppet Module Skeleton

A common file system structure for Puppet modules that is slightly more advanced than the skeleton provided in the built in Puppet module tool.

This skeleton has been taken from [Gareth Rushgrove's own module skeleton](https://github.com/garethr/puppet-module-skeleton) with a couple of changes I was consistently making to certain files and therefore makes the same assumptions:

* You are going to practice TDD and write both unit and system tests
* You are going to follow the Puppet styleguide
* You will use Travis to execute your tests on committing to the repo
* You want to follow strong conventions for the structure of your modules

## Installation

The Puppet module tool will use `~/.puppet/var/puppet-module/skeleton` as the template for its `generate` command. That is where we will place the files provided here.

### Easy Install

Simply run:

```
./install.sh
```

### Manual Install

As we don't want our .git files or this README in the skeleton we can export it like so:

```
git clone https://github.com/unfinisheddev/puppet-module-skeleton
cd puppet-module-skeleton
find skeleton -type f | git checkout-index --stdin --force --prefix="$HOME/.puppet/var/puppet-module" --
```

## Usage

Generate a new module is the same way as you always would:

```
puppet module generate your-module
```

Once your module is generated then you can install the development dependencies:

```
cd your-module
bundle install
```

You now have some Rake commands that will help you with the development of your module:

```
bundle exec rake -T
rake acceptance        # Run acceptance tests
rake build             # Build puppet module package
rake clean             # Clean a built module package
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
rake test	       # Run lint, syntax and spec tasks
```

### Automatically running your tests

The skeleton comes with a Guardfile that will allow you to execute relevant tests as you modify your files (manifests, lib files, spec files, etc). To start the watching process, simply run:

```
guard
```

The Guard process will assume that any fixtures have already been downloaded. This can be done using the `rake spec_prep` task. If you add any dependencies to your module you will need to stop the Guard process and download the required fixtures before restarting Guard.

## Appreciation &amp; Thanks

As I said, the majority of this skeleton and the installation process was taken from the excellent skeleton by [Gareth Rushgrove](https://github.com/garethr/puppet-module-skeleton)
