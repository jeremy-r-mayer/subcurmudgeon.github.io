---
title: PiTemps
---

Report Raspberry Pi CPU and GPU temperatures.

```shell
#!/bin/bash

CPU="$(cat /sys/class/thermal/thermal_zone0/temp | cut -c1-2).$(cat /sys/class/thermal/thermal_zone0/temp | cut -c3-5)"
GPU="$(/opt/vc/bin/vcgencmd measure_temp | cut -c6-9)"

printf "\e[96m%-5s %10s %10s\e[0m\n" "Zone" "Celcius" "Fahrenheit"
echo -e "\e[96m---------------------------\e[0m"
printf "%-5s %10.2f %10.2f\n" "CPU" "${CPU}" "$(echo "${CPU} * 1.8 + 32.0" | bc)"
printf "%-5s %10.2f %10.2f\n" "GPU" "${GPU}" "$(echo "${GPU} * 1.8 + 32.0" | bc)"
```