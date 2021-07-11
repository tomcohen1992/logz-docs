---
title: Ship Auth0 events
logo:
  logofile: auth0.png
  orientation: vertical
data-source: Auth0
templates: ["no-template"]
contributors:
  - nshishkin
shipping-tags:
  - identity
order: 810
---

### Ship events data from your Auth0 account to Logz.io

Deploy this integration to ship Auth0 events from your Auth0 account to Logz.io using Logstash.

**Before you begin, you'll need**: an active account with Auth0

<div class="tasklist">

#### Install and configure the "Auth0 Logs to Logstash" extension

##### Select the "Auth0 Logs to Logstash" extension

Login to your Auth0 account, navigate to **Auth0 Dashboard > Extensions**, and select **Auth0 Logs to Logstash**.

The following screen will appear:
![Dashboard](https://dytvr9ot2sszz.cloudfront.net/logz-docs/auth0/Dashboard_Logstash.png)

##### Configure the required parameters

Configure the required parameters as follows:

   * Enter your Listener host URL and port into the **LOGSTASH_URL** filed. {% include log-shipping/listener-var.md %}
   * Enter your log shipping token (`<<LOG-SHIPPING-TOKEN>>`) into the **LOGSTASH_TOKEN** field. {% include log-shipping/log-shipping-token.md %}
   * Enter `auth0` into the **LOGSTASH_INDEX** field.

##### Configure the optional parameters

If required, configure the required parameters as follows:

   * Enter the required schedule value into the **Schedule** field. This is the frequency with which logs should be exported. This can be customized after creation.
   * Enter the required batch size value into the **Batch size** field. This is the number of logs to be sent per batch. Maximum is `100`. Logs are batched before sending, and multiple batches are sent each time the extension runs.
   * Enter the **Start from** value. This is the checkpoint ID of the log from which you want to start sending.
   * Enter the adrress for the Slack incoming webhook into the **Slack incoming webhook url** field. This is the specific Slack webhook to which you want to send reports from the extension.
   * Using the selector menu in the **Slack send success** field, choose whether to send verbose notifications to Slack.
   * In the **Log level** field, specify minimal log level of events that you would like sent to Logstash.
   * In the **Log types** field, select the events for which logs should be exported.

 For detailed information on these parameters, refer to the [Auth0 documentation](https://auth0.com/docs/extensions/export-logs-to-logstash).

##### Install the extension

Select **Install** and wait until you are redirected to the **Installed extensions** page.

![Installed extensions](https://dytvr9ot2sszz.cloudfront.net/logz-docs/auth0/Auth0_installed_extensions.png)

##### Authorize the extension

Select the **Auth0 Logs to Logstash** extension and confirm that you authorize this extension.

#####  View the exported logs

Upon authorizing the extension, you will be taken to the **Logs Export** page. Here you can see the events that are exported to Logz.io

![Logs export](https://dytvr9ot2sszz.cloudfront.net/logz-docs/auth0/Auth0_logs_export.png)

#### Check Logz.io for your data

Give your data some time to get from your system to ours, and then open [Kibana](https://app.logz.io/#/dashboard/kibana). You can filter for data of type `auth0` to see the incoming Auth0 events.

If you still don't see your logs, see [log shipping troubleshooting]({{site.baseurl}}/user-guide/log-shipping/log-shipping-troubleshooting.html).

</div>