# NX-FanControl

Fan curve control for Nintendo Switch. Overlay plus sysmodule, built from source with current devkitPro so it runs on Atmosphère 1.10 and newer.

### Prebuilt

Grab `NXFanControl-1.0.4.zip` from Releases and unpack it at the root of your SD card. That gives you:

```
atmosphere/contents/00FF0000B378D640/exefs.nsp
atmosphere/contents/00FF0000B378D640/toolbox.json
atmosphere/contents/00FF0000B378D640/flags/boot2.flag
switch/.overlays/Nx-FanControl.ovl
```

The existing `config/NX-FanControl/` folder is left alone, so a rebuild keeps your saved curve.

### Requirements

[devkitPro](https://devkitpro.org/wiki/Getting_Started). No other pinned versions; the build uses whatever libnx you have installed.

### Building from source

```
git clone --recurse-submodules https://github.com/Insektaure/NX-FanControl.git
cd NX-FanControl
make all
```

The tree lands in `out/` with the same layout as the release zip.

### Why this fork exists

The 1.0.3 release was built in November 2025. Atmosphère 1.10 notes that Nintendo changed the userland to kernel TLS ABI in firmware 21.0.0, which needs modules compiled against the newer ABI. A 1.0.3 binary left over from before that change loads and then fails, and `ovlSysmodules` reports the module as incompatible.

Recompiling the same source against current libnx produces a working module. No source changes were needed. This fork exists so people can download that binary instead of setting up devkitPro.
