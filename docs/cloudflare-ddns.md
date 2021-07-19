---
title: Cloudflare DDNS
---

This is the script I use on my Raspberry Pi to update its Cloudflare A-record from behind the VPN.

> Note: `01001010.ddns.net` is set by my modem which is *not* behind the VPN.

```shell
#!/bin/bash

# Make certain this script is chmod 700.

# Zone
ZONE="01001010.net"

# DNS Record - Be sure the record type in step 3 matches the type for this record.
RECORD="01001010.net"

# API Token - Requires DNS:Edit permission for the above zone, nothing else.
TOKEN="<API TOKEN HERE>"

# Local IP Address
IP=$(dig +short 01001010.ddns.net)

# Step 1: Get ID for $ZONE. This is shown in the dashboard, but it's simple to retrieve.
ZONEID=$(curl -s -X GET "https://api.cloudflare.com/client/v4/zones?name=$ZONE&status=active" \
	-H "Authorization: Bearer $TOKEN" \
	-H "Content-Type: application/json" | jq -r '{"result"}[] | .[0] | .id')

# Step 2: Get ID for $RECORD. This is not shown in the dashboard and must be retrieved via API.
RECORDID=$(curl -s -X GET "https://api.cloudflare.com/client/v4/zones/$ZONEID/dns_records?type=A&name=$RECORD" \
	-H "Authorization: Bearer $TOKEN" \
	-H "Content-Type: application/json" | jq -r '{"result"}[] | .[0] | .id')

# Step 3: API request to update record.
curl -s -X PUT "https://api.cloudflare.com/client/v4/zones/$ZONEID/dns_records/$RECORDID" \
	-H "Authorization: Bearer $TOKEN" \
	-H "Content-Type: application/json" \
	--data "{\"type\":\"A\",\"name\":\"$RECORD\",\"content\":\"$IP\",\"ttl\":1,\"proxied\":true}" | jq
```