# Todos #
By Brian Manning (PAUSE ID: XAOC)

- Automate the release process???
- Fix compiler warnings under LLVM on Mac OS X
- Fix test issues under Win32
- Automate updating MacPorts Perl modules in public.git repo
- Continuous Build
  - Build in Jenkins
  - Build NEWS files
  - Build release tarballs
  - Use Vagrant to test
- Release Helper
  - Checkѕ for correct versions of ExtUtils::MakeMaker and CPAN::Meta
  - Generates release e-mail
    - Populates release info from NEWS file
    - Checks git link
    - Checks sourceforge download link
    - Checks version numbers in module files, NEWS file, and anywhere else it
      needs to be checked

## Links to e-mail threads about build problems on *BSD ##
- http://comments.gmane.org/gmane.os.openbsd.ports/50008
- http://thread.gmane.org/gmane.os.openbsd.misc/162657/focus=162657
- https://www.google.com/search?oq=lazy+binding+failed!+Segmentation+fault+(core+dumped)+OpenBSD

# vim: filetype=markdown shiftwidth=2 tabstop=2
