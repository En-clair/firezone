---
layout: default
title: Install Server
nav_order: 4
parent: Deploy
---
---

**Important**: Ensure you've satisfied the
[prerequisites]({% link docs/deploy/prerequisites.md %}) before following this
guide.

## Installation Instructions

**NOTE**: Firezone modifies the kernel netfilter and routing tables. Other
programs that modify the Linux routing table or netfilter firewall
will likely interfere with Firezone's operation.

Assuming you're running a supported Linux kernel on one of the [distros
listed above](#supported-linux-distributions), follow these steps to install and
configure Firezone for first use:

1. [Install WireGuard](https://www.wireguard.com/install/) for your distro.
   If using Linux kernel 5.6 or higher, skip this step.
2. Download the relevant package for your distribution from the
   [releases page](https://github.com/firezone/firezone/releases).
3. Install with `sudo rpm -i firezone*.rpm` or `sudo dpkg -i firezone*.deb`
   depending on your distro.
4. Bootstrap the application with `sudo firezone-ctl reconfigure`. This will
   initialize config files, set up needed services and generate the default
   configuration.
5. Edit the default configuration located at `/etc/firezone/firezone.rb`.
   At a minimum, you'll need to review the following configuration variables:

   ```ruby
   # Auto-generated based on the server's hostname.
   # Set this to the FQDN used to access the Web UI.
   default['firezone']['fqdn'] = 'firezone.example.com'

   # Specify the path to your SSL cert and private key.
   # If set to nil, a self-signed cert will be generated for you.
   default['firezone']['ssl']['certificate'] = '/path/to/cert.pem'
   default['firezone']['ssl']['certificate_key'] = '/path/to/key.pem'
   ```

6. Reconfigure the application to pick up the new changes:
   `sudo firezone-ctl reconfigure`.
7. Finally, create an admin user with `sudo firezone-ctl create-or-reset-admin`.
   The login credentials will be printed to the console output.
8. Now you should be able to log into the web UI at the FQDN you specified in
   step 5 above, e.g. `https://firezone.example.com`

Next, proceed to [install WireGuard clients
]({% link docs/deploy/clients.md %}).
