---
name: Speaker Standby Bypass (in progress)
tools: [Bash, AppleScript]
image: https://image.shutterstock.com/image-vector/black-waves-equalizer-isolated-on-260nw-1446388454.jpg
description: I have good speakers that enter standby mode in 10 minutes (600 seconds) if no audio is output. This sometimes causes me to miss discord, iMessage, or whatever notifications in the background. Therefore, the goal of this script is to play a 15Hz inaudible 3 second waveform every 580 seconds to prevent standby mode - if and only if there is no audio playing. The script must be a shell script daemon managed by launchd process.
external_url:
---
