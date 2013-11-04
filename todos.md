# Todos #
By Brian Manning (PAUSE ID: XAOC)

## Misc ##
- Fix compiler warnings under LLVM on Mac OS X
- Fix test issues under Win32
- Automate updating MacPorts Perl modules in public.git repo
- Make a link to some getting started docs on the website
- Describe what packages are required by which distros

## Website ##
- Link to twitter account
- Add a "How do I..." section on the front page, and link to different things,
  like the git repos, getting started docs, mailing list, list of modules
- Add the `Gtk3` module to the list of modules on the homepage
- Add a "how to get started with `Gtk3`" section
- change _gtk2-perl Git Repo_ link to _Git Repo_ on the right hand nav bar
- Change the first paragraph to say `Gtk+ 2.x and 3.x`
- Add links to `Gtk3` tutorials posted on the web
  - https://github.com/dave-theunsub/gtk3-perl-demos
  - https://github.com/cpanxaoc/gtk3-perl-demos
  - https://github.com/kevinphilp/Perl-gtk3-Tutorial
  - https://github.com/cpanxaoc/Perl-gtk3-Tutorial

## Release Automation Ideas ##
  - Runs `git pull` on all source repos and mails a list of changed repos
  - Updating the version numbers in the correct files
  - Copying out POD docs to a common POD docs directory for uploading to the
    Gtk-Perl website
    - Use `Dist::Zilla::Plugin::Run` to copy out/run a POD->HTML converter on
      the POD files at the correct time?
  - Creating the tarball
  - Unpacking and building the tarball
  - Generating the release announcement e-mail
    - Add MD5/SHA1 checksums for downloaded files
  - Generating the release announcement blurbs for Sourceforge and Freshmeat
    - Posting said blurbs on Sourceforge and Freshmeat
    - Checking that the blurbs posted correctly on Sourceforge and Freshmeat
  - Uploading the release tarball
    - CPAN
    - Sourceforge
  - Generating the e-mail for the next release due date
  - Getting `bit.ly` URLs for twits
- Release Helper
  - Checkѕ for correct versions of ExtUtils::MakeMaker and CPAN::Meta
  - Generates release e-mail
    - Populates release info from NEWS file
    - Checks git link
    - Checks sourceforge download link
    - Checks version numbers in module files, NEWS file, and anywhere else it
      needs to be checked

## Release Automation TODOs ##
- Generate release e-mail bodies
  - Include `bit.ly` shortened URLs
- Generate Twitter messages with `bit.ly` URLs

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
