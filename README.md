# Batch Connect - Cheaha OnDemand Sandbox Template

[![GitHub License](https://img.shields.io/badge/license-MIT-green.svg)](https://opensource.org/licenses/MIT)

A SandBox template Batch Connect app designed for Cheaha OnDemand that launches a GUI module on Cheaha

This app has been adapted from OSC's matlab [repo](https://github.com/OSC/bc_osc_matlab)

## Prerequisites

This Batch Connect app requires the following software be installed on the
**compute nodes** that the batch job is intended to run on (**NOT** the
OnDemand node):

- Software/App that needs to be run
- [Xfce Desktop] 4+

For VNC server support:

- [TurboVNC] 2.1+
- [websockify] 0.8.0+

For hardware rendering support:

- [X server]
- [VirtualGL] 2.3+

## Setup on cheaha

Setup sandbox on your profile by following the instructions [here](https://docs.uabgrid.uab.edu/wiki/Open_OnDemand_Sandbox#Setting_up_sandbox_for_your_profile)

Go to your DATA_USER/ondemand/dev directory, and clone this repo there

Use git to clone this app:

```sh
git clone
```

Open #manifest.yml file and change SOFTWARE_NAME and SOFTWARE_LINK variables appropriately.

Open #form.yml, and uncomment version section:

```
 version:
    widget: select
    label: "SOFTWARE_NAME version"
    help: "This defines the version of SOFTWARE_NAME you want to load."
    options:
      - [ "display_version", "corresponding_cheaha_module" ]
```

NOTE: Change SOFTWARE_NAME appropriately. Under ""options"" change """display_version""" to the the version that you want to display on teh form, and change """corresponding_cheaha_module""" to matching module name on cheaha.
For example, to load FSL version 6.0.3, you can change the above to :

```
 version:
    widget: select
    label: "FSL version"
    help: "This defines the version of FSL you want to load."
    options:
      - [ "6.0.3", "FSL/6.0.3" ]
```

Open #template/script.sh.erb , and at end add the execute command to launch GUI app.
For example, to launch FSL, at the end I'll add

```
# Launch your GUI app
fsl
```

Change """icon.png""" to appropriate Software logo

Your Dev app should be available now, for you to launch.

Again, you do not need to restart the app as it isn't a Passenger app.

## Contributing

1. Fork it ( https://github.com/OSC/bc_osc_matlab/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request
