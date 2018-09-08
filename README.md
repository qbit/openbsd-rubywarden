openbsd-rubywarden
=========

Role to setup a [rubywarden](https://github.com/jcs/rubywarden] instance on OpenBSD.

Requirements
------------

- OpenBSD

Role Variables
--------------

| Variable | Default | Description |
|--------- | ------- | ----------- |
| rw_port  | 4567    | The port rubywarden should listen on. |
| rw_user  | _rubywarden | The user that will be added to the system in order to run rubywarden. |
| rw_home  | /var/rubywarden | Home directory for rw_user. |
| rw_group  | _rubywarden | The group that will be added to the system in order to run rubywarden. |
| rw_signups | false | Tells rubywarden to allow signups. Requires a service restart to change. |
| rw_commit | master | Specific commit to be used during the checkout process. |

Example Playbook
----------------

    - hosts: rw_server
      roles:
         - { role: qbit.rubywarden }

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
