
# Manage a CockroachDB Serverless Cluster

In this lab, we will look into the cluster management for CockroachDB Serverless.

- View cluster overview
- Estimate usage cost
- Edit your resource limits
- Edit regions
- Add regions
- Edit the primary region

**Important!** Some of the below options will not allowed for free CockroachDB Serverless Cluster.


## View Clusters page

On `logging in to the CockroachDB Cloud Console`, the **Clusters** page is displayed. The **Clusters**
page provides a high-level view of your clusters.

For each cluster, the following details display:

- The cluster\'s **Name**
- The cluster\'s **Plan type**, either Serverless or Dedicated
- The date and time the cluster was **Created**
- The cluster\'s current **State**
- The cluster\'s cloud provider, either GCP or AWS
- The **Version** of CockroachDB the cluster is running
- The **Action** button, which is used to:
    - **Edit resource limits**
    - **Delete cluster**

To view and manage a specific cluster, click the name of the cluster.

The **Overview** page will display.

## View cluster overview

The **Overview** page displays details about the selected CockroachDB
Serverless cluster:

- The **Cluster settings** section, including **Cloud provider**,
    **Plan type**, and **Regions**
- The **Usage this month** section, including the **Resource limits**,
    **Storage**, and **Request Units**
- The cluster\'s **Current activity**
-   Time-series graphs of the cluster\'s **Storage usage**, **Request
    Units**, and **SQL statements**


## Estimate usage cost

Note: This feature is not available if your organization is billed through Credits.


The monthly cost estimate is calculated using simple extrapolation that
assumes your workload during the selected time frame is an accurate
representation of your workload over the month. If you haven\'t been
running a workload for at least the length of the selected time frame,
your results will be inaccurate.

1.  In the **Usage this month** section of your cluster\'s **Overview** page,
    click **Estimate usage cost**.

2.  Select a time period in which your workload was active.

    Your used `RUs`, used storage, and accrued costs during the time period will be shown
    along with a monthly cost estimate. The accrused costs and monthly
    cost estimate do not account for the [free
    resources]
    granted to each non-contract organization, which you would have to
    use up before being charged.

## Edit your resource limits

On the **Overview** page, you can edit your resource limits.

Changes apply to the current and future billing cycles..

1.  Navigate to the **Overview** page for the cluster you want to edit.

2.  Click the pencil icon (or **Add resource limits** if you haven\'t
    set one before) next to your **Resource limits** in the **Usage this month** section.

    You will be taken to the **Edit cluster** page, which shows a graph
    of your cluster\'s **Recommended budget** compared to your current
    budget.

3.  Enter new **Resource limits**.

4.  Click **Update**.



### Add regions

To add regions to your cluster:

1.  Navigate to the cluster\'s **Overview** page.

2.  In the **Cluster settings** section, click the pencil icon next to
    the cluster\'s **Regions**.

    The **Edit cluster** page displays.

3.  Click **Add region**.

4.  Choose the region you want to add or use the suggested one.

5.  In the **Summary** sidebar, verify the hourly estimated cost for the
    cluster.

6.  Click **Update**.

### Edit the primary region

To set the primary region:

1.  Navigate to the cluster\'s **Overview** page.

2.  In the **Cluster settings** section, click the pencil icon next to
    the cluster\'s **Regions**.

    The **Edit cluster** page displays.

3.  Select **Set primary region** next to your preferred region.

4.  Click **Update**.

