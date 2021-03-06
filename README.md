# cloud-init

My personal cloud-init templates
> Note: All templates are targeted to `amd64` architecture. Feel free to change it to your desire architecture.

### About

Cloud-init is the industry standard multi-distribution method for cross-platform cloud instance initialization. It is supported across all major public cloud providers, provisioning systems for private cloud infrastructure, and bare-metal installations.

Cloud instances are initialized from a disk image and instance data:

- Cloud metadata
- User data (optional)
- Vendor data (optional)

Cloud-init will identify the cloud it is running on during boot, read any provided metadata from the cloud and initialize the system accordingly. This may involve setting up the network and storage devices to configuring SSH access key and many other aspects of a system. Later on the cloud-init will also parse and process any optional user or vendor data that was passed to the instance.

See [Cloud config examples](https://cloudinit.readthedocs.io/en/latest/topics/examples.html)

### Testing

To test the config, launch a `multipass` with `--cloud-init` flag.

```
multipass launch --name maas --network en0 --cloud-init maas/cloud-config.yml
```

Or pulling config from remote

```sh
wget -qO- https://raw.githubusercontent.com/socheatsok78/cloud-init/main/maas/cloud-config.yml \
 | multipass launch --name maas --cloud-init -

# or

curl -fsSL https://raw.githubusercontent.com/socheatsok78/cloud-init/main/maas/cloud-config.yml \
 | multipass launch --name maas --cloud-init -
```
