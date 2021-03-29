---
title: Console Twitter Trends
---

Top 50 Twitter trends on the console.

```shell
#!/bin/bash

echo "Twitter Trends:"
curl -s -X GET -H "Authorization: Bearer <API TOKEN HERE>" https://api.twitter.com/1.1/trends/place.json?id=23424977 | \jq -r .[0].trends[].name | \
nl | \
column
```