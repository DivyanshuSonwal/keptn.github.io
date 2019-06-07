---
title: Troubleshooting
description: The sections describes tips and tricks to deal with troubles that may occur when using keptn. 
weight: 30
keywords: [troubleshooting]
---

In this section, instructions are summarized that help to trouble shoot known issues that may occur when using keptn.

<!-- ## Knative Eventing -->

### Service does not receive event, even though it has been sent
<details><summary>Expand instructions</summary>
<p>

**Investigation:**

1. Check the logs of the *event-broker* using the [keptn's log](../keptnslog/) and looking for the current *keptnContext*, e.g., `keptnContext: 6177178624927956405`
1. The event-broker was not able to send an event to a channel, if the log shows:
    ```
    {"keptnContext":"6177178624927956405","message":"Error while sending request: Error: Request failed with status code 500","keptnService":"eventbroker","logLevel":"ERROR"}
    ```

**Reason:** 

Internal knative problem, seen with knative 0.4

**Solution:** 

1. Re-apply the channel, which should have received the event, e.g., the *problem* channel. The manifest is provided by the event-broker: 
    ```
    kubectl apply -f ./keptn/core/eventbroker/config/problem-channel.yaml
    ```

1. Re-apply the services that have a subscription to this channel, e.g., for the *problem* channel it is the *servicenow-service*: 
    ```
    kubectl apply -f keptn/install/scripts/keptn-services/servicenow-service/config/servicenow-service.yaml
    ```

1. (optional) Delete all pods in the *knative-eventing* namespace:
    ```
    kubectl delete pods --all -n knative-eventing
    ```
</p></details>

<!-- ## Control service is not available -->

### CLI command was not executed correctly
<details><summary>Expand instructions</summary>
<p>

**Investigation:**

The control service is not available at the time when a command was sent by the keptn CLI. 
The resulting response message will look similar to this:

```console
keptn onboard service --project=sockshop --values=values_carts.yaml
```

```console
Starting to onboard service
Onboard service was unsuccessful
Error: Post https://control.keptn.1xx.xxx.xx.xx.xip.io/service: dial tcp: lookup control.keptn.1xx.xxx.xx.xx.xip.io: no such host
``` 

**Reason:** 

We are investiagting this problem in issue [#392](https://github.com/keptn/keptn/issues/392).

**Solution:** 

Please wait a couple of minutes for the cluster to recover and try again. 

Alternatively, you can try to delete the `control` pod in the `keptn` namespace. Therefore, first get
the name of the `control` pod:

```console
kubectl get pods -n keptn | grep control
```

```console
control-k8stj-deployment-5f8d986946-r4l69            3/3     Running   0          20h
```
Second, use the name of your `control` pod and delete it:

```console
kubectl delete pod control-k8stj-deployment-5f8d986946-r4l69 -n keptn
```

```console
pod "control-k8stj-deployment-5f8d986946-r4l69" deleted
```

The `control` pod will automatically restart.

</p></details>

### Jenkins Builds are not starting ###
<details><summary>Expand instructions</summary>
<p>

**Investigation:**

In Jenkins, investigate the logs of the build that was triggered by keptn, e.g. the `deploy` pipeline.
The last line in the logs says something like **"Jenkins doesn't have label kubegit"**, and it does not proceed for an extended amount of time (i.e., ~2 minutes). 

**Solution:**

can work around this problem by following these instructions:

1. In Jenkins, navigate to **Manage Jenkins > Configure System**.
1. In the **Cloud** section of the settings page, you should see the parameters **Jenkins URL** and **Jenkins tunnel** (see screenshot below)
1. In the field for **Jenkins URL**, enter 'http://jenkins', and hit save.
1. Afterwards, delete this value again and hit save once again.

{{< popup_image link="./assets/jenkins-tunnel.png" caption="Jenkins configuration">}}
</p></details>
</details>