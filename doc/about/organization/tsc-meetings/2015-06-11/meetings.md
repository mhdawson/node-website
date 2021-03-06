# Node 0.10.X/0.12.X LTS team meeting 06/11/2015

## Participants

*  Julien Gilli
*  Alexis Campailla
*  Michael Dawson
*  Colin Ihrig

## Agenda

*  Logjam/openssl upgrade
*  Upgrade of libuv to 1.6.1
*  First draft of breaking changes between io.js/Node 0.12
*  Windows Installer Changes


## Minutes

###  Logjam/openssl upgrade

Michael: Expect OpenSSL upgrade imminently. Just drop support for smaller size. Do we expect that to break users?

Michael: should also consider including:

*  https://github.com/nodejs/io.js/pull/1739
*  https://github.com/nodejs/io.js/pull/1831
*  https://github.com/joyent/node/issues/25366  (checked and docs for io.js indicate modp1 is still there)

Michael: Stewart on my team has volunteered to create a PR against Node.js to upgrade OpenSSL.

### Libuv upgrade to 1.6.1

Julien: Libuv PR, fixes annoying issue on OSX 10. Worth reviewing soon.

Colin: PR already landed in io.js

Julien: top priority to review that ABI/API hasn.t changed in a breaking way.

Julien: Julien to try and review today, likely to be included in release for openssl upgrade

### Breaking changes between io.js and Node 0.12.X

First draft of doc of breaking changes between 0.12 and next LTS.

Julien: https://github.com/nodejs/node/wiki/Breaking-changes-between-v0.12-and-next-LTS-release

Based on io.js issue tracker, joyent\node backport commit log. v8 breaking changes from release notes (?)

Please review and comment on issue.

### Debug port issues

Collin working to fix https://github.com/nodejs/io.js/pull/1949 - new debug port for each worker.

### Windows installer changes

Alexis: https://github.com/joyent/node/issues/5849 - currently a hybrid/broken, will submit PR to do full install for all users, to be added to next milestone

https://github.com/joyent/node/issues/25087, same upgrade code used for 32/64 bit which is not good practice.  Can result in binaries from one (32/64) being put into the other.  Will move to use 2 upgrade codes, but this will break upgrade. Going to add manual action to check for old code and give message saying you cannot upgrade and that you should un-install and install again

