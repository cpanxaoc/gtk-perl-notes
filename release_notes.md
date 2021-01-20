## Release Setup ##

Export PKG_CONFIG_PATH to the installed version of XQuartz, so the GTK modules
can pick up the `*.pc` file for `xcb-shm`; also need to pick up the libs for
GTK+/Glib/Pango/Cairo from Homebrew, if used.

    export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig:/opt/X11/lib/pkgconfig

## Release Checklist ##
- Check bugs in distributions, see if anything can quickly be fixed
  - RT: https://rt.cpan.org/Public/Dist/ByMaintainer.html?Name=XAOC
  - Bugzilla: http://tinyurl.com/ootsv9n
- Check copyright date in all files that have changed in the current year
- CPAN Meta-Spec v2 - Check to see if the project has an updated `%meta_merge`
  structure in `Makefile.PL`; see `Cairo` commit ID `17f2def7` for an idea of
  what changes need to me made
  - http://blogs.perl.org/users/peter_rabbitson/2014/09/encourage-user-participation-via-a-single-line-patch-to-your-dist-metadata.html
- `README` - Check to see if the project has an updated `README` file; see
  `Cairo` commit ID `081061c` for the changes made
- SUPPORT section in the POD
  - Add sections for Bugs, Feature Requests, and Source code using POD
  - See `ExtUtils::Depends` for an example
- Update the FSF address in all license blurbs (RT#72664)
  - *51 Franklin Street, Fifth Floor, Boston, MA 02110-1301  USA*
- Update the NEWS file using the contents of the commit logs 
- Update the module versions in the .pm files and in some of the README files
  - Go over the list of files that need to be changed for each project (below)
- Create tarball 
  - perl Makefile.PL
  - Check MYMETA.yml and MYMETA.json in the tarball (not in the source dir)
  - make dist
  - make clean
  - rm Makefile.old
- Test
  - Check META.yml and META.json
- Make a release commit with the contents of the above changes
  - use git diff -r [previous release tag] to get a list of differences
    between the previous release and this release
- Create a signed tag in git (git tag -s rel-x-xx-x)
- Push the new release with tags to the server (git push --tags)
- Upload
  - Sourceforge
  - PAUSE
    - Check for release version using `perl -MCPAN -e shell` after you get the
      confirmation e-mails from PAUSE
- Announce
  - Verify URLs to Git repo and download tarballs in any posts
  - mailing list
  - Sourceforge - https://sourceforge.net/p/gtk2-perl/news/
  - *cpanxaoc* and *GTKPerl* accounts on Twitter
    - use bit.ly to shorten URLs

## List of files to change, by module ##
- Cairo
  - NEWS
  - lib/Cairo.pm +17
  - Makefile.PL (stable/unstable flag)
- Cairo::GObject
  - NEWS
  - lib/Cairo/GObject.pm +19
  - Makefile.PL (stable/unstable flag)
- ExtUtils::Depends
  - Changes
  - lib/ExtUtils/Depends.pm +15
  - **NOTE:** You need to generate the `MANIFEST` file using the `Makefile`
    target `make manifest` after `perl Makefile.PL`, but prior to running
    `make dist` (`perl Makefile.PL -> make manifest -> make dist`)
  - You can safely delete the `MANIFEST` file and regenerate it prior to
    running `make dist`
- ExtUtils::PkgConfig
  - Changelog
  - lib/ExtUtils/PkgConfig.pm +27
  - Makefile.PL (stable/unstable flag)
- Glib
  - NEWS
  - lib/Glib.pm +30
  - lib/Glib/CodeGen.pm +8
  - lib/Glib/GenPod.pm +12
  - lib/Glib/MakeHelper.pm +7
  - lib/Glib/ParseXSDoc.pm +16
  - lib/Glib/Object/Subclass.pm +23
  - Makefile.PL (stable/unstable flag, unstable block that gets output when an
    unstable release is made)
- Glib::Object::Introspection
  - NEWS
  - lib/Glib/Object/Introspection.pm +22
  - Makefile.PL (stable/unstable flag)
  - See instructions below for building Glib for testing
- Gnome2
  - NEWS
  - Gnome2.pm +17
  - Makefile.PL (stable/unstable flag)
- Gnome2::Canvas
  - NEWS
  - META.yml +4
  - README +1
  - GConf.pm +30
  - Makefile.PL (stable/unstable flag)
- Gnome2::GConf
  - NEWS
  - META.yml +4
  - README +1
  - GConf.pm +30
  - Makefile.PL (stable/unstable flag)
- Gnome2::VFS
  - NEWS
  - VFS.pm +29
  - Makefile.PL (stable/unstable flag)
- Gnome2::Vte
  - NEWS
  - Vte.pm +15
  - Makefile.PL (stable/unstable flag)
- GStreamer
  - NEWS
  - lib/GStreamer.pm +31
  - Makefile.PL (stable/unstable flag)
- Gtk2
  - NEWS
  - lib/Gtk2.pm +76
  - Makefile.PL (stable/unstable flag)
  - See instructions below for building Glib for testing
- Gtk3
  - **DO NOT MAKE A RELEASE COMMIT**
    - Dist::Zilla takes care of all of the files, as well as tagging and
      making the release commit and push to `git.gnome.org` and uploading the
      release tarball to Sourceforge
  - Update the `dist.ini` file with the next release version
  - Update the `NEWS` file with changes since the last commit
    - Put the changes below the line that says `{{$NEXT}}`
  - Call `dzil build` to build a release distribution
    - Check the files in the release distribution, using the list above
  - _DO NOT COMMIT THE UPDATED FILES_
    - Simply call `dzil release`
      - Part of `dzil release` is to make a "release commit" with these files
        automagically, as well as uploading tarballs to CPAN and Sourceforge
- Pango
  - NEWS
  - lib/Pango.pm +32
  - Makefile.PL (stable/unstable flag)

## Building a copy of Glib for testing ##
- Glib
  - tar -zxvf Glib-1.3XX.tar.gz
  - cd Glib-1.3XX
  - perl Makefile.PL INSTALL_BASE=/tmp/Glib-1.2XX
  - time make
  - time make test
  - make install

## Using the testing copy of Glib to build another module ##
- PERL5LIB=/tmp/Glib-1.2XX/lib/perl5/darwin-thread-multi-2level \
  perl Makefile.PL
- time make
- time make test
- FIXME: how do you build the test libraries that GOI uses for testing?
  - Something in g-in-something is not building correctly
  - Disable output redirection in Makefile.PL to see the actual error

## Release Inputs ##
- E-mails to developers for submissions
- Cull patches from CPAN's RT queues
- Cull patches from Gnome's Bugzilla

lynx -dump "http://git.gnome.org/browse/" | grep perl | grep -P "\d{2,4}\." |
awk -F'/' '{ print $5; }' | uniq | sort | egrep -v
"gimp-perl|gnome-perl-introspection"

## Sourceforge News Support Page ##
- https://sourceforge.net/apps/trac/sourceforge/wiki/News

## Gnome.org Links ##
- https://live.gnome.org/MaintainersCorner/Releasing
- https://live.gnome.org/ThreePointSeven (Calendar)
- https://live.gnome.org/Git/Developers

## Sections to check for in the README file ##
- e-mail address of the mailing list
- IRC
- how to report problems
  - test program that demonstrates the problem
- patch submission guidelines
  - send patches to the mailing list
  - git pull requests from github/your own hosted repo to the mailing list
  - those with a gnome ID can push trivial commits
    - If you're not sure if it's a trivial commit, post to the mailing list
- URL of the web page
- source repo
  - how to clone fresh source
  - how to update previously cloned source

## Generating docs from .gir files ##
- https://live.gnome.org/GObjectIntrospection/Doctools

# vim: filetype=markdown tabstop=2 shiftwidth=2
