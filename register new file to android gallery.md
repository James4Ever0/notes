---
created: 2022-11-04T09:36:07+08:00
modified: 2022-11-04T09:37:03+08:00
---

# register new file to android gallery

code in beanshell:

```java
import android.net.Uri;
Intent mediaScanIntent = new Intent(Intent.ACTION_MEDIA_SCANNER_SCAN_FILE);
Uri contentUri = Uri.parse("file:///storage/emulated/0/Movies/output0_higher.mp4");
mediaScanIntent.setData(contentUri);
ctx.sendBroadcast(mediaScanIntent);
```
