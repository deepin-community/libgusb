GUsb Release Notes
==================

git log --format="%s" --cherry-pick --right-only 0.4.7... | grep -i -v trivial | grep -v Merge | sort | uniq
Add any user visible changes into ../contrib/org.freedesktop.GUsb.metainfo.xml
appstream-util appdata-to-news ../contrib/org.freedesktop.GUsb.metainfo.xml > ../NEWS

Update library version if new ABI or API in `meson.build`, commit, and build tarball:

    # MAKE SURE THIS IS CORRECT
    export release_ver="0.4.8"

    git commit -a -m "Release version ${release_ver}"
    git tag -s -f -m "Release ${release_ver}" "${release_ver}"
    ninja dist
    git push --tags
    git push
    gpg -b -a meson-dist/libgusb-${release_ver}.tar.xz

Upload tarball and GPG signatures to https://github.com/hughsie/libgusb

Do post release version bump in `meson.build` and commit changes:

    git commit -a -m "trivial: post release version bump"
    git push

Send an email to devkit-devel@lists.freedesktop.org

    =================================================
    GUsb 0.4.7 released

    GUsb is a GObject wrapper for libusb1 that makes it easy to do
    asynchronous control, bulk and interrupt transfers with proper
    cancellation and integration into a mainloop.

    Tarballs available here: https://github.com/hughsie/libgusb/releases
    =================================================
