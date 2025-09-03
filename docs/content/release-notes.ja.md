---
title: "Release Notes"
draft: false
---

{{ `<!--` | safeHTML }}
The data is fetched from the GitHub API.
See https://docs.github.com/en/rest/reference/releases#get-the-latest-release
{{ `-->` | safeHTML }}

{{ $rancher_release := getJSON "https://api.github.com/repos/rancher/rancher/releases/latest" }}
{{ $rke2_release := getJSON "https://api.github.com/repos/rancher/rke2/releases/latest" }}

## Rancher

### [{{ $rancher_release.name }}]({{ $rancher_release.html_url }})

**Tag:** {{ $rancher_release.tag_name }}

**Published at:** {{ time.AsTime $rancher_release.published_at | time.Format ":date_long" }}

{{ $rancher_release.body | markdownify }}

---

## RKE2

### [{{ $rke2_release.name }}]({{ $rke2_release.html_url }})

**Tag:** {{ $rke2_release.tag_name }}

**Published at:** {{ time.AsTime $rke2_release.published_at | time.Format ":date_long" }}

{{ $rke2_release.body | markdownify }}
