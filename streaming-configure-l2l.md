---

copyright:
  years: 2019, 2023
lastupdated: "2022-08-18"

keywords: IBM Cloud, Log Analysis, streaming

subcollection: log-analysis


---

{{site.data.keyword.attribute-definition-list}}

# Configuring streaming to a {{site.data.keyword.la_short}} instance through the UI
{: #streaming-configure-l2l}

Complete the following steps to configure streaming from a {{site.data.keyword.la_short}} instance to another {{site.data.keyword.la_short}} instance:
{: shortdesc}

See [Configure streaming](/docs/log-analysis?topic=log-analysis-streaming#streaming-1) for more information on roles required for streaming.
{: note}

## Prereqs
{: #streaming-configure-l2l-prereqs}

- You must have the ingestion URL and the ingestion key for the {{site.data.keyword.la_short}} instance where you want to stream data.

## Step 1. Configure streaming in the source {{site.data.keyword.la_short}} instance
{: #streaming-configure-l2l-step1}

Complete the following steps to configure the connection between {{site.data.keyword.la_short}} instances:

1. [Launch the {{site.data.keyword.la_short}} web UI](/docs/services/log-analysis?topic=log-analysis-launch).

2. Click the **Settings** icon ![Configuration icon](images/admin.png "Admin icon"). Then select **Streaming** &gt; **Configuration**.

3. Select **Log Analysis / Activity Tracker** as the streaming type. Then, enter the following information:

    1. In the **Ingestion key** field, enter a valid ingestion key for the {{site.data.keyword.la_short}} instance where you want to stream data.

    2. In the **Region URL** field, enter the ingestion URL for the region where the {{site.data.keyword.la_short}} instance where you want to stream data is available, such as `https://logs.us-east.logging.cloud.ibm.com/logs/selfstream`. For more information, see [Ingestion URLs](/docs/log-analysis?topic=log-analysis-endpoints#endpoints_ingestion).

       - If you configure your log sources to send data through private endpoints, make sure you configure a private ingestion endpoint for streaming.

       - If you configure your log sources to send data through private and public endpoints, make sure you configure a private ingestion endpoint for streaming.

    3. Click **Save**.


## Step 2. Verify sample data in the destination {{site.data.keyword.la_short}} instance
{: #streaming-step1-l2l-step2}


To continue, you must verify that sample data reaches the destination {{site.data.keyword.la_short}} instance.

To verify that sample data is streaming, complete the following steps:

1. [Launch the {{site.data.keyword.la_short}} web UI](/docs/services/log-analysis?topic=log-analysis-launch).
2. In the search bar, run the following query:

    ```text
    _line:"LogDNA test message" _app:"logdna-selfstream-config-validation"
    ```
    {: codeblock}

3. Check the field **_meta._source._account** is set to the logging instance ID.  The following additional data is also displayed:

   `_account`
   :   Is the account ID of the account streaming the data.

   `_instanceId`
   :   Is the logging instance ID for the account.

   `_region`
   :   Is the region where the logging data originated. This is the specific region name for the environment where the data originated.

If you do not see data, do 1 of the following:
- **Resend sample logs** to verify that sample data is streaming.
- **Check my setup** to go back to the configuration panel. After you make your changes, retry the verification steps.


If you see data, click **YES**.



## Step 3. Start streaming
{: #streaming-configure-l2l-step3}


After you verify that sample data is reaching the {{site.data.keyword.la_short}} instance, click **Start stream**.

Streaming may take up to 15 minutes to begin.
{: note}
