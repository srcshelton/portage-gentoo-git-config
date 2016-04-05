This is not a full portage configuration. It contains only those parts that are
necessary to set up a Gentoo github-mirror based sync system:

* Configures Portage to sync via `https://github.com/gentoo/gentoo.git`;
* Updates the metadata caches;
* Updates the Gentoo repo's `metadata/dtd` directory;
* Updates the Gentoo repo's `metadata/glsa` directory;
* Updates the Gentoo repo's `metadata/projects.xml` file;
* Updates the Gentoo repo's `metadata/news` directory.

## Installation ##

Compare the files from `repos.conf` to those in `/etc/portage/repos.conf/` and
edit or update as appropriate.

```sh
sudo cp repo.postsync.d/sync_* /etc/portage/repo.postsync.d/
chmod +x /etc/portage/repo.postsync.d/sync_gentoo*
```

If using https://github.com/srcshelton/gentoo-ebuilds/ as an overlay, then the
'`set -u`' at the top of `/etc/portage/repo.postsync.d/sync_*` can be
uncommented to add a little runtime safety since the
`sys-apps/gentoo-functions` ebuild in this repo has been fixed.

## Notes ##

If you want your overlay metadata caches to be automatically regenerated
as well, do:

```sh
chmod +x /etc/portage/repo.postsync.d/sync_overlay_cache
```

