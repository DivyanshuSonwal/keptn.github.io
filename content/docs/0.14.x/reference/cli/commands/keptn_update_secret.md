---
date: "2022-02-17T14:31:25+01:00"
title: "keptn update secret"
slug: keptn_update_secret
---
## keptn update secret

Updates an existing secret

```
keptn update secret SECRET_NAME --from-literal="key1=value1" --from-literal="key2=value2" --scope=my-scope" [flags]
```

### Examples

```
keptn update secret SECRET_NAME --from-literal="key1=value1" --from-literal="key2=value2" --scope=my-scope"
```

### Options

```
      --from-literal stringArray   Specify a key and literal value to insert in secret (i.e. my-key=some-value)
  -s, --scope string               The scope of the secret (default "keptn-default")
```

### Options inherited from parent commands

```
      --config-file string   Specify custom Keptn Config file path (default: ~/.keptn/config)
  -h, --help                 help
      --mock                 Disables communication to a Keptn endpoint
  -n, --namespace string     Specify the namespace where Keptn should be installed, used and uninstalled in (default "keptn")
  -q, --quiet                Suppresses debug and info messages
  -v, --verbose              Enables verbose logging to print debug messages
  -y, --yes                  Assume yes for all user prompts
```

### SEE ALSO

* [keptn update](../keptn_update/)	 - Updates an existing Keptn project

###### Auto generated by spf13/cobra on 17-Feb-2022