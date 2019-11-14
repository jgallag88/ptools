# ptools

FOOBAR

This repository contains a collection of Linux utilities for inspecting the
state of processes, modeled after the tools by the same name which exist on
Solaris/Illumos.

## Getting Started:

To build `ptools`, run the following on an Ubuntu 18.04 VM:

    $ git clone https://github.com/delphix/ptools.git
    $ cd ptools/
    $ curl https://sh.rustup.rs -sSf | bash -s -- -y
    $ cargo build

The utilities can be run out of the `target/debug` directory, e.g.

    $ ./target/debug/ptree 1

To install `ptools`, additionally run:

    $ cargo install cargo-deb
    $ cargo deb
    $ sudo apt install ./target/debian/ptools_0.1.0_amd64.deb

## Why ptools?

Linux already has a number of mechanisms which can be used to inspect the state
of processes (the proc filesystem, `ps`, `lsof`, etc.). Why add a new set of
tools?

The main advantage of ptools is consistency. The utilities provided by ptools
are consistently named and have a consistent interface. Also, significantly,
they can be run against core dumps where applicable, providing a uniform way to
examine live processes and core dumps. This is very useful for those who rely
heavily on core dumps to do postmortem debugging. The goal of this project is
to make this same consistent debugging experience available on Linux.

## Current State

Currently, this repository provides the following commands

* `pfiles` - shows the open files and sockets of the process, as well as their
   corresponding file descriptors
* `pargs` - shows the command line arguments passed to the process
* `penv` - shows the environment of the process
* `ptree` - shows the process tree containing the process

There are a number of other commands available on Solaris/Illumos which have not
been implemented here yet, perhaps most notably `pstack`. Also support for
examining core dumps has not yet been implemented.

## Contribute

1.  Fork the project.
2.  Make your bug fix or new feature.
3.  Add tests for your code.
4.  Send a pull request.

#### <a id="code-of-conduct"></a>Code of Conduct

This project operates under the [Delphix Code of Conduct](https://delphix.github.io/code-of-conduct.html). By participating in this project you agree to abide by its terms.

#### <a id="contributor-agreement"></a>Contributor Agreement

All contributors are required to sign the Delphix Contributor agreement prior to contributing code to an open source repository. This process is handled automatically by [cla-assistant](https://cla-assistant.io/). Simply open a pull request and a bot will automatically check to see if you have signed the latest agreement. If not, you will be prompted to do so as part of the pull request process.


## Reporting Issues

Issues should be reported in the GitHub repo's [issue tab](https://github.com/delphix/ptools/issues).

## Statement of Support

This software is provided as-is, without warranty of any kind or commercial
support through Delphix. See the associated license for additional details.
Questions, issues, feature requests, and contributions should be directed to the
community as outlined in the
[Delphix Community Guidelines](https://delphix.github.io/community-guidelines.html).

## License

This is code is licensed under the Apache License 2.0. Full license is
available [here](./LICENSE).
