---
layout: home
---

## Table of Contents
- [Threat Model](Content/Threat%20Model/guide.html)


## Tools to help create

**yt-dlp**

```bash
yt-dlp --skip-download --write-subs --write-auto-subs --sub-lang en --sub-format ttml --convert-subs srt --output "transcript.%(ext)s" <URL_HERE_NO_QUOTES> && \
sed -i -e '/^[0-9][0-9]:[0-9][0-9]:[0-9][0-9].[0-9][0-9][0-9] --> [0-9][0-9]:[0-9][0-9]:[0-9][0-9].[0-9][0-9][0-9]$/d' -e '/^[[:digit:]]\{1,3\}$/d' -e 's/<[^>]*>//g' transcript.en.srt && \
awk 'BEGIN {buffer=""} /^[0-9]+$/ {next} /^$/ {print buffer; buffer=""; next} {if (buffer != "") buffer = buffer " "; buffer = buffer $0} END {if (buffer != "") print buffer}' transcript.en.srt > output.txt && \
rm transcript.en.srt
```