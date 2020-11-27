openbsd-rubywarden
=========

Role to setup a [rubywarden](https://github.com/jcs/rubywarden) instance on OpenBSD.

Requirements
------------

- OpenBSD

TODO
----

- Stop cloning as `root`.

Role Variables
--------------

| Variable | Default | Description |
|--------- | ------- | ----------- |
| rw_ruby | `2.7` | Ruby version. |
| rw_port  | `4567`  | The port rubywarden should listen on. |
| rw_user  | `_rubywarden` | The user that will be added to the system in order to run rubywarden. |
| rw_home  | `/var/rubywarden` | Home directory for rw_user. |
| rw_group  | `_rubywarden` | The group that will be added to the system in order to run rubywarden. |
| rw_signups | `false` | Tells rubywarden to allow signups. Requires a service restart to change. |
| rw_commit | `master` | Specific commit to be used during the checkout process. |
| rw_env | `production` | Specify if we are running in production or development mode. |
| rw_src | `"{{ rw_home }}/src"` | Dir to clone the rubywarden source to. |
| rw_keepass | `false` | Install gems needed for importing keepass version 1 databases (version 2 is not supported)|

Running rubywarden tool scripts
-------------------------------

The rubywarden scripts are installed in `/var/rubywarden/src/tools/`.

To run the scripts you need to set the proper environment so that the ruby gems installed into the local directory work correctly.

For example, to import a version 1 keepass database:

```
RUBYWARDEN_ENV=production \
	PATH=/bin:/usr/bin:/usr/X11R6/bin:/usr/local/bin:/var/rubywarden/rb/bin \
	HOME=/var/rubywarden \
	GEM_HOME=/var/rubywarden/rb/ruby/2.7 \
	ruby27 tools/keepass_import.rb -f /path/to/keepass.kbdx -u <bw-user>@domain.tld
```

Example Playbook
----------------

    - hosts: rw_server
      roles:
         - { role: qbit.rubywarden }

Upgrading from ruby-2.6 to ruby-2.7
-----------------------------------

Just run the updated role. It automatically upgrades and installs needed packages.

License
-------

```
/*
 * Copyright (c) 2018 Aaron Bieber <aaron@bolddaemon.com>
 *
 * Permission to use, copy, modify, and distribute this software for any
 * purpose with or without fee is hereby granted, provided that the above
 * copyright notice and this permission notice appear in all copies.
 *
 * THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES
 * WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF
 * MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR
 * ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES
 * WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN
 * ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF
 * OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
 */
 ```
