Add branch owner tracking to gitolite.  This is a feature that we wanted at
work -- it is meant to allow developers to create topic branches and have
'ownership' of them.  Later, the creator of the branch can delete it (if, e.g.
the feature was merged, or abandoned, or re-done on a different topic branch)

Based on an old discussion in the gitolite mailing list: https://groups.google.com/g/gitolite/c/hi0qrXEX7PU/m/1VBUOA0WCQAJ

The author of gitolite has stated that it (gitolite) has become more like a
programming toolkit that allows people to extend the functionality of git.
Having created this little utility, I have to agree.  Also, the gitolite author
ought to be commended for creating such a finely crafted tool.

Set-Up instructions:

  * make sure local code is enabled in gitolite.rc (I like to keep my customizations in the admin repo, so LOCAL_CODE => "$rc{GL_ADMIN_BASE}/local")

  * add the files in this repo to the gitolite local/ dir (keep dir structure and +x flags)

  * edit (or add) the ACCESS_2, and POST_GIT blocks in gitolite.rc and add the br_own
  and br_own_post triggers there

  * run gitolite setup? (not sure this is needed)

  * add VREF rules to the repos you want to have this feature

NOTE: I make no assurances as to the quality of this implementation.  It could
be full of security holes.  It could destroy all of your git repos. It might
just convert all the world's water to ice-9. Caveat Emptor.
