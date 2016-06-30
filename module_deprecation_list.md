# List of Gtk2::* modules to deprecate #

    perl-Clutter                    Glib::Object::Introspection
    perl-GStreamer                  G:O:I
    perl-GStreamer-GConf            no upstream replacement AFAIK
    perl-GStreamer-Interfaces       no upstream replacement AFAIK
    perl-Gnome2                     no upstream replacement
    perl-Gnome2-Dia                 no upstream replacement
    perl-Gnome2-PanelApplet         Gtk3::StatusIcon
    perl-Gnome2-Rsvg                G:O:I
    perl-Gnome2-VFS                 Glib::IO (not on CPAN yet)
    perl-Gnome2-Vte                 G:O:I
    perl-Gtk2-MozEmbed              no clue, maybe Gtk3::WebKit?
    perl-Gtk2-SourceView2           G:O:I
    perl-Gtk2-Spell                 G:O:I
    perl-Gtk2-Unique                Gtk3::Application

    archive/perl-Champlain          G:O:I
    archive/perl-Gnome2-Canvas      Cairo
    archive/perl-Gnome2-GConf       Glib::IO::Settings
    archive/perl-Gnome2-Notify      G:O:I
    archive/perl-Gnome2-Print       Gtk3::Print*
    archive/perl-Gnome2-Wnck        G:O:I
    archive/perl-Goo-Canvas         G:O:I
    archive/perl-Gtk2-Champlain     G:O:I
    archive/perl-Gtk2-GLExt         Gtk3::GLArea
    archive/perl-Gtk2-GladeXML      Gtk3::Builder
    archive/perl-Gtk2-Html2         no clue, maybe Gtk3::WebKit
    archive/perl-Gtk2-Recent        Gtk3::Recent*
    archive/perl-Gtk2-SourceView    G:O:I
    archive/perl-Gtk2-TrayIcon      Gtk3::StatusIcon
    archive/perl-Gtk2-TrayManager   no clue

## Deprecation Checklist ##
Check bugs in distributions, see if anything can quickly be fixed, otherwise
close bugs that require changes to upstream
- RT: https://rt.cpan.org/Public/Dist/ByMaintainer.html?Name=XAOC
- Bugzilla: http://tinyurl.com/ootsv9n

Check copyright date in all files that have changed in the current year

CPAN Meta-Spec v2
- Check to see if the project has an updated `%meta_merge` structure in
  `Makefile.PL`; see `Cairo` commit ID `17f2def7` for an idea of what changes
  need to me made
- http://blogs.perl.org/users/peter_rabbitson/2014/09/encourage-user-participation-via-a-single-line-patch-to-your-dist-metadata.html

`README`
- Check to see if the project has an updated `README` file; see `Cairo` commit
  ID `081061c` for the changes made

SUPPORT section in the POD
- Add sections for Bugs, Feature Requests, and Source code using POD
- See `ExtUtils::Depends` for an example

Update the FSF address in all license blurbs (RT#72664)
- *51 Franklin Street, Fifth Floor, Boston, MA 02110-1301  USA*

Update the NEWS file using the contents of the commit logs 

Update the module versions in the .pm files and in some of the README files
- Go over the list of files that need to be changed for each project (below)

Create tarball 
- perl Makefile.PL
- Check MYMETA.yml and MYMETA.json in the tarball (not in the source dir)
- make dist
- make clean
- rm Makefile.old

Test
- Check META.yml and META.json
- Try and do a test install, and run all of the module's test cases

Make a release commit with the contents of the above changes
- Use `git diff -r [previous release tag]` to get a list of differences
  between the previous release and this release

Create a signed tag in git (git tag -s rel-x-xx-x)

Push the new release with tags to the server (git push --tags)

Upload
- Sourceforge
- PAUSE
  - Check for release version using `perl -MCPAN -e shell` after you get the
    confirmation e-mails from PAUSE

Announce
- Verify URLs to Git repo and download tarballs in any posts
- mailing list
- Sourceforge - https://sourceforge.net/p/gtk2-perl/news/
- *cpanxaoc* and *GTKPerl* accounts on Twitter
  - use bit.ly to shorten URLs

# vim: filetype=markdown tabstop=2 shiftwidth=2
