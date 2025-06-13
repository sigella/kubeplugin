# kubeplugin

## Description

This is the bash script which gets resourse usage statistic, format and print is out.

## usage

```bash
/bin/bash scripts/kubeplugin.sh  <resource_type (pods|nodes)> <namespace>
"Examples:"
    "/bin/bash scripts/kubeplugin.sh pods kube-system"
    "/bin/bash scripts/kubeplugin.sh pods"
    "/bin/bash scripts/kubeplugin.sh nodes"
```

## Demo

![](images/kubeplugin.gif)