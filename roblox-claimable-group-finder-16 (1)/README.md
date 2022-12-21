# roblox-claimable-group-finder
<p align="center"><img src="https://i.imgur.com/131wdCq.png" height="300" width="637"></p>

# Features
- High-performance scanning (up to 50M+ checks-per-minute)
- Zero dependencies
- Automatic ID calibration on start
- Webhook and HTTP proxy support

# Instructions
0. Download the [latest release](https://www.python.org/downloads/) of Python and install it with the [Add to PATH](https://datatofish.com/wp-content/uploads/2018/10/0001_add_Python_to_Path.png) option checked.
1. [Download](https://github.com/h0nde/roblox-claimable-group-finder/archive/refs/heads/main.zip) this repository and extract it to a folder.
2. Create a `proxies.txt` file within the folder and fill it with your HTTP proxies.
3. Click the `File` tab on your file explorer window, and then click `Open PowerShell`.
4. Execute the command in the `Usage` section below.

# Usage
```bash
python finder.py --workers 16 --proxy-file proxies.txt -u https://discord.com/api/webhooks/906766650454450228/IZvVG3jlXPwVt2hDAly6LVuwoDUZXWZVeW99hxmUPmu8eNeNXcHlr8WCRTOEwdW_nPt6
```

```
-w <num>, --workers <num>
                      Number of workers
-t <num>, --threads <num>
                      Number of threads (per worker)
-r <range> [<range> ...], --range <range> [<range> ...]
                      Range(s) of group IDs
-p <file>, --proxy-file <file>
                      File containing HTTP proxies
-u <url>, --webhook-url <url>
                      Send group results to <url>
-c <id>, --cut-off <id>
                      ID limit for skipping missing groups
-C <size>, --chunk-size <size>
                      Number of groups to be sent per batch request
-T <seconds>, --timeout <seconds>
                      Timeout for connections and responses
```

# Things to note
- Ownerless groups will be ignored on the first cycle of scanning (regardless of approval-only or locked status).
- Proxies are required as of 2021-09.

# --webhook-url
If the `--webhook-url` arg. is specified, an embed will be sent whenever a claimable group is found. E.g.:

<img src="https://i.imgur.com/VeMBoCA.png" alt="Embed sample" width="400"/>

# --cut-off
By default, when encountering a missing/deleted group, it's ID will be removed from the queue so that it won't be checked again.

The `--cut-off` argument specifies at which ID (and above) missing groups shouldn't be removed from the queue. This is ideal in scenarios where you also wanna scan groups that haven't been created yet.
