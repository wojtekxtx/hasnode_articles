# Monitoring H/W with NetData

Ive been long user of various monitoring solutions but none of them suits my need. ND doesnt also. But, amongst other tools, its the coomest.

# NetData

## Installation

Its super easy. Just `apt install netdata` After 3-5 minutes, you have fully working ND instance accessible via webbrowser.

## Dashboard

By entering your hosts's ip ( usually ) in webbrowser you launch dashboard. Clean, easy to use/understand, Nicely designed, etc. So far so good.

## Alerting

UI lack option for creating/managing alerts, go to console; itd be a breeze.........

Suppose you need to adjust percentage that triggers alert on `CPU usage`:

```bash
sudo ./edit-config health.d/cpu.conf
```

and edit:

```bash
    warn: $this > (($status >= $WARNING)  ? (60) : (75))
    crit: $this > (($status == $CRITICAL) ? (75) : (85))
```

Than:

*   save edits,
    
*   `netdatacli reload-health` **without it you wont see your changes !!!**
    
*   wait for alert to be triggered
    
*   enjoy :)
    

Exactly the same way you can use to edit/add other alerts.

**Happy monitoring everyone :)**