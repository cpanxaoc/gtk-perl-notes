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

# vim: filetype=markdown shiftwidth=2 tabstop=2
