---
Keywords: code  
Copyright: (C) 2021 Laboratory Design  
---

# コードのサンプル  
```html
<!-- コメント -->
<a nref="https://embresearch.com/?post=20210920_ramen">最近のラーメン</a>
```

```bash
#!/bin/bash -euxv
source "$(dirname $0)/conf"
exec 2> "$logdir/$(basename $0).$(date +%Y%m%d_%H%M%S).$$"
```

