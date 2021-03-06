# Todos #
By Brian Manning (PAUSE ID: XAOC)

## Misc ##
- Fix compiler warnings under LLVM on Mac OS X
- Fix test issues under Win32
- Make a link to some getting started docs on the website
- Describe what packages are required by which distros

## Website ##
- Link to twitter account
- Add a "How do I..." section on the front page, and link to different things,
  like the git repos, getting started docs, mailing list, list of modules
- `Gtk2`/`Gtk3` advent calendars
- Codex/Guide to `Gtk2`/`Gtk3`
  - See:
    - `gtk-perl-codex.md` in `public.git/presentations/` for notes/content for
      the codex
    - `gtk-perl-codex.md` and `gtk-perl.md` in `project_journals.git` for
      journal entries describing work done on the project
- Add the `Gtk3` module to the list of modules on the homepage
- Add a "how to get started with `Gtk3`" section
- change _gtk2-perl Git Repo_ link to _Git Repo_ on the right hand nav bar
- Change the first paragraph to say `Gtk+ 2.x and 3.x`
- Add links to `Gtk3` tutorials posted on the web
  - https://github.com/dave-theunsub/gtk3-perl-demos
  - https://github.com/cpanxaoc/gtk3-perl-demos
  - https://github.com/kevinphilp/Perl-gtk3-Tutorial
  - https://github.com/cpanxaoc/Perl-gtk3-Tutorial
- Fix link to study guide in links page
  - "Dirk van der Walt has a rather detailed Gtk2-Perl Study Guide." should
    point to the local copy on Sourceforge

## Docs Integration ##
Find some way to pull the method descriptions out of glib/gtk2/gtk3/etc. docs,
and insert those method descriptions into the corresponding Perl modules,
using the correct syntax for using the Glib/Gtk2/Gtk3 modules in Perl.
- Use `jhbuild` to build glib/gtk+2/gtk+
  - This should also get `gtk-doc`
- Run `gtk-doc` in the source directories to build the XML files
- Parse the XML files, and match Perl methods with methods from GTK libs

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
      - https://metacpan.org/pod/CPAN::Uploader
    - Sourceforge
  - Generating the e-mail for the next release due date
  - Getting `bit.ly` URLs for twits
  - Checking regular/`bit.ly`/Sourceforge URLs for valid contents (non-404s)
- Release Helper
  - Checkѕ for correct versions of ExtUtils::MakeMaker and CPAN::Meta
  - Generates release e-mail
    - Populates release info from NEWS file
    - Checks git link
    - Checks sourceforge download link
    - Checks version numbers in module files, NEWS file, and anywhere else it
      needs to be checked
  - Generates shortened text for tweets
  - Generates shortened text for the Sourceforge News/blog post
    - Posts the news item on Sourceforge

## Release Automation TODOs ##
- Generate release e-mail bodies using _Template::Toolkit_
- Check the status of the PAUSE indexer e-mails generated by the upload
- Generate Twitter messages with `bit.ly` URLs
  - https://metacpan.org/pod/Net::Twitter::OAuth
- Upload files to CPAN
  - https://metacpan.org/pod/CPAN::Uploader
- Upload files to Sourceforge
  - Creates folders as needed, not all projects use individual folders for
    each release
    - Net::SFTP
- Generate blog post for Sourceforge
  - Need to generate an OAuth token for Sourceforge
  - https://metacpan.org/pod/OAuth::Lite
  - https://metacpan.org/pod/OAuth::Lite2
  - https://metacpan.org/pod/Net::OAuth

## Continuous Build ##
- Build in Jenkins
- Build NEWS files
- Build release tarballs
- Use Vagrant to test

## Links to e-mail threads about build problems on *BSD ##
- http://comments.gmane.org/gmane.os.openbsd.ports/50008
- http://thread.gmane.org/gmane.os.openbsd.misc/162657/focus=162657
- https://www.google.com/search?oq=lazy+binding+failed!+Segmentation+fault+(core+dumped)+OpenBSD

## Done TODOs ##
- Add screenshots to the Sourceforge homepage
- Generate release e-mail bodies using _Template::Toolkit_
  - Include version of this release
  - Include release date in the "Overview" block
  - Include the full URL to the Git repo
    - Checks the validity of the Git repo URL
  - Include the fill URL to the tarball on Sourceforge
    - Checks the validity of the Sourceforge tarball URL
  - Include `bit.ly` shortened URLs
    - Need `bit.ly` API key

# vim: filetype=markdown shiftwidth=2 tabstop=2
