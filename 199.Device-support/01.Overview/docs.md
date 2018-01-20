---
title: Overview
taxonomy:
category: docs
---

In order to enable a robust update process, Mender needs to be able to select which root file system is booted (among other things).
This means that devices need to be [integrated with Mender](../../devices) before you can benefit from a robust OTA update process.

Instead of having a fixed list of supported devices, Mender is designed to enable *easy integration with any device*.
This documentation section contains a description of public Mender device integrations, contributed by
Mender developers or the community. This lets you re-use an existing integration or find starting points for your own Mender device integration.

For commercial support, please see the [Device support offering](https://mender.io/product/board-support?target=_blank).


## Level of support

To ease prototyping and evaluation, some devices are officially supported by the Mender developers.
These devices are in the CI system and it is ensured that they work well with every release of Mender.
They have the highest level of support: **reference**.
Currently, Mender has three reference devices: [Raspberry Pi 3](https://www.raspberrypi.org/products/raspberry-pi-3-model-b?target=_blank), [BeagleBone Black](https://beagleboard.org/black?target=_blank) and a virtual device (`vexpress-qemu`).

Other Mender device integrations are contributed by members of the Mender community;
they have the **community** support level. Maintenance of these integrations may
vary and the best place to look for help is the
[Mender community mailing list](https://groups.google.com/a/lists.mender.io/forum?target=_blank/#!forum/mender).


## Contribute device support

Did you [integrate your device with Mender](../../devices) and would like to contribute your
integration so the community can use it and help maintain it? Great!


### Prerequisites


#### Quality check

Before contributing your device integration, please make sure it passes the [integration checklist](../../devices/integration-checklist).


#### Any required code

Any required meta layers or scripts that you created when [integrating your device with Mender](../../devices)
need to be hosted in a public git repository like [GitHub](https://www.github.com?target=_blank) so 
your integration can easily be used by other users of the Yocto Project toolset.
You can use your own repository or make a pull request towards the [meta-mender repository](https://www.github.com/mendersoftware/meta-mender?target=_blank).


#### A short documentation page

To help others find it, a short documentation on your integration should be published in this documentation section (Device support).
You can look at the other integrations for examples, and there is a template for you to use below:

```
TODO
```

Once you are ready, please submit your documentation as a pull request to [mender-docs](https://github.com/mendersoftware/mender-docs/tree/master/199.Device-support?target=_blank).
