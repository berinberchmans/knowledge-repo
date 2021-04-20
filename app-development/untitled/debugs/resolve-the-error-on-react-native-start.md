---
description: '"error Invalid regular expression:" issue on RN'
---

# Resolve the error on 'react-native start'

Under `\node_modules\metro-config\src\defaults\blacklist.js,`

 change `sharedBlacklist` as below.

```text
var sharedBlacklist = [
  /node_modules[/\\]react[/\\]dist[/\\].*/,
  /website\/node_modules\/.*/,
  /heapCapture\/bundle\.js/,
  /.*\/__tests__\/.*/
];
```

to:

```text
var sharedBlacklist = [
  /node_modules[\/\\]react[\/\\]dist[\/\\].*/,
  /website\/node_modules\/.*/,
  /heapCapture\/bundle\.js/,
  /.*\/__tests__\/.*/
];
```

