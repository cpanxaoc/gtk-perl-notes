# Todos #
By Brian Manning (PAUSE ID: XAOC)

## Misc ##
- Fix compiler warnings under LLVM on Mac OS X
- Fix test issues under Win32
- Automate updating MacPorts Perl modules in public.git repo

## Automate the release process??? ##
  - Updating the version numbers in the correct files
  - Creating the tarball
  - Unpacking and building the tarball
  - Generating the release announcement e-mail
  - Generating the release announcement blurbs for Sourceforge and Freshmeat
    - Posting said blurbs on Sourceforge and Freshmeat
    - Checking that the blurbs posted correctly on Sourceforge and Freshmeat
  - Uploading the release tarball
    - CPAN
    - Sourceforge
  - Generating the e-mail for the next release due date
- Release Helper
  - Checkѕ for correct versions of ExtUtils::MakeMaker and CPAN::Meta
  - Generates release e-mail
    - Populates release info from NEWS file
    - Checks git link
    - Checks sourceforge download link
    - Checks version numbers in module files, NEWS file, and anywhere else it
      needs to be checked

## Continuous Build ##
- Build in Jenkins
- Build NEWS files
- Build release tarballs
- Use Vagrant to test

## Links to e-mail threads about build problems on *BSD ##
- http://comments.gmane.org/gmane.os.openbsd.ports/50008
- http://thread.gmane.org/gmane.os.openbsd.misc/162657/focus=162657
- https://www.google.com/search?oq=lazy+binding+failed!+Segmentation+fault+(core+dumped)+OpenBSD

# vim: filetype=markdown shiftwidth=2 tabstop=2
