---
created: 2025-10-12T22:04:15+08:00
modified: 2025-10-12T22:08:00+08:00
---

# how to secure compute nodes

use port level isolation
use dedicated, white list based web proxy as the only internet gateway, with physical switch.
input password in a multi step way, send the real password plus inputted salt as md5 hash with ssl encryption, to prevent keylogging.
only privileged process approved manually with multi factor authentication such as email verification code can run with full internet access. others may only use limited approved websites in a short time.
