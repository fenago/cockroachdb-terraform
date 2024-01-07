
# Lab 9: Performing a backup and restore operation

In this lab, we will look intro backup and restore operation.

- Backups tab
- Restore a cluster

**Note:** If your cluster was created few minutes ago, you will not see any automated backups.

To access your managed-service backups, select a cluster from the
**Clusters** page,
then click **Backup and Restore** in the **Data** section of the left
side navigation.


This lab describes the **Backup and Restore** page and how to restore
your data.


Cockroach Labs runs `full cluster backups` hourly for every CockroachDB Serverless cluster. 
The full backups are
retained for 30 days. Once a cluster is deleted, Cockroach Labs retains
the full backups for 30 days.

## Backups tab

The **Backups** tab displays a list of your full cluster backups. Use
the calendar drop-down to view all backups taken on a certain date.

For each backup, the following details display:

-   **Data From**: The date and time the backup was taken.
-   **Status**: Whether the backup is `In Progress` or `Complete`.
-   **Expires In**: The remaining number of days Cockroach Labs will
    retain the backup.


## Restore a cluster

Find the cluster backup you want to restore, and click **Restore**.


Performing a restore will cause your cluster to be unavailable for the
duration of the restore. All current data is deleted, and the cluster
will be restored to the state it was in at the time of the backup. There
are no automatic incremental backups, and no automatic database or table
level backups.
