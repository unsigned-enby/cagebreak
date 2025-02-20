# Security

The main possibility for security bugs in cagebreak is by privilege
escalation through the socket. Any program with access to the socket
immediately gains arbitrary code execution rights. The socket
is restricted to the user of the cagebreak process (700) and has to
be explicitely enabled using the `-e` flag on invocation.

If you disagree with this threat model, you may contact us via email (See
section Email Contact below.) or [open an issue on github](https://github.com/project-repo/cagebreak/issues/new).

Should any problem with the github issue system arise or any other reason
for (potentially confidential) contact with the Cagebreak authors appear,
you may contact us via email (See section Email Contact below.).

## Supported Versions

The most recent release always contains the latest bug fixes and features.
There are no official backports for security vulnerabilities.
Builds are reproducible under conditions outlined in [README.md](README.md).

## Bug Reports

For normal bugs you may [open an issue on github](https://github.com/project-repo/cagebreak/issues/new).

For everything else, an email contact (with gpg encryption and signature)
is available below.

## Email Contact

If you want to get in touch with the developers of cagebreak to report
a security vulnerability or anything else via email, contact
`cagebreak @ project-repo . co`.

We try to respond to everything that is not obvious spam.

### GPG-Encrypted Emails

If you can, please encrypt your email with the appropriate GPG key found
in `keys/` and sign your message with your own key.

* B15B92642760E11FE002DE168708D42451A94AB5
* F8DD9F8DD12B85A28F5827C4678E34D2E753AA3C
* 3ACEA46CCECD59E4C8222F791CBEB493681E8693
* 0A268C188D7949FEB39FD1462F2AD980247E4918

Note that our keys are signed by cagebreak signing keys.

If you want us to respond via GPG-encrypted email, please include your own
public key or provide the fingerprint and directions to obtain the key.

## Threat Model

Cagebreak is a wayland compositor run by the user of the system
and thus has access to whichever resources this user has access to.
Cagebreak can restrict other programs in no way, because this would hamper
usability (consider a web browser unable to write a downloaded file to disk
for instance).

There is no transmission of information by cagebreak other than to the
screens, ipc and potentially other documented local channels.

### STRIDE Threat List

This is not a thorough analysis, just an overview of the ways in which cagebreak
has (no) attack surface. Please reference the man pages for details but especially
the -e and --bs options.

#### Spoofing

Not applicable - Using Cagebreak already requires a login as a user.

#### Tampering

Not applicable - Cagebreak must allow system manipulation for user software.

#### Repudiation

Not applicable - There are no prohibited operations (See Tampering above.).
While cagebreak does send events over documented channels there is no logging
activated by default, though, of course, this can be changed by the user
by logging socket output (if enabled) for example.

#### Information Disclosure

Not applicable - Information disclosure over documented channels is a feature
and any software run by the user may exfiltrate any data the user has access to.

#### Denial of Service

Not applicable - Cagebreak offers functionality to terminate itself, which is
available to all user software over the socket if the socket is enabled.

#### Elevation of Privilege

Software may gain arbitrary code execution rights if it has access to the
Cagebreak socket. Privilege escalation to root is unlikely since privileges
are dropped before any user input is accepted.

## GPG Keys of the Cagebreak Repository

All Cagebreak project keys are found under keys/ in the cagebreak
repository (the public keys anyway).

The most trusted keys of the Cagebreak project are its signing keys,
all signing keys are signed by at least one of its predecessors and at
least one non-expired signing key is used at the time of release to
sign the commit tag and the release code tarball.

Signing keys are also used to lend credence to other keys in the Cagebreak
project, such as the keys for email correspondence and the key used in the
cagebreak-pkgbuild repository.

