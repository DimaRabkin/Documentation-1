---
description: This page details the different permission options available in Upsolver.
---

# Permissions list

* [Billing](permissions-list.md#billing)
* [Cluster](permissions-list.md#cluster)
* [Connection](permissions-list.md#connection)
* [IAM](permissions-list.md#iam)
* [Input](permissions-list.md#input)
* [Lookup table](permissions-list.md#lookup-table)
* [Monitoring](permissions-list.md#monitoring)
* [Notifications](permissions-list.md#notifications)
* [Organization](permissions-list.md#organization)
* [Output](permissions-list.md#output)
* [Reference data](permissions-list.md#reference-data)
* [UDF](permissions-list.md#udf)
* [Workspace](permissions-list.md#workspace)

## Billing

<table>
  <thead>
    <tr>
      <th style="text-align:left">Permission</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p></p>
        <p><b>billing:view:describe</b>
        </p>
      </td>
      <td style="text-align:left">
        <p></p>
        <p>Allows viewing of the account&apos;s billing information including credit
          reports, graphs and purchases</p>
      </td>
    </tr>
  </tbody>
</table>

## Cluster

<table>
  <thead>
    <tr>
      <th style="text-align:left">Permission</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p></p>
        <p><b>cluster:edit:attach-workspace</b>
        </p>
      </td>
      <td style="text-align:left">
        <p></p>
        <p>Allows the attachment of a workspace to a cluster</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p></p>
        <p><b>cluster:edit:cancel-roll</b>
        </p>
      </td>
      <td style="text-align:left">
        <p></p>
        <p>Cancels the next scheduled roll on a cluster</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p></p>
        <p><b>cluster:edit:change-name-and-description</b>
        </p>
      </td>
      <td style="text-align:left">
        <p></p>
        <p>Allows changing of the name and description of a cluster</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p></p>
        <p><b>cluster:edit:change-size</b>
        </p>
      </td>
      <td style="text-align:left">
        <p></p>
        <p>Allows changing the size of a cluster</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>cluster:edit:create</b>
      </td>
      <td style="text-align:left">Allows the creation of a new cluster</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>cluster:edit:delete</b>
      </td>
      <td style="text-align:left">Allows the deletion of a cluster</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>cluster:view:describe</b>
      </td>
      <td style="text-align:left">Allow viewing the cluster</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>cluster:edit:detach-workspace</b>
      </td>
      <td style="text-align:left">Allows the detachment of a workspace from a cluster</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>cluster:view:list</b>
      </td>
      <td style="text-align:left">Allow listing all instances of clusters</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>cluster:edit:roll</b>
      </td>
      <td style="text-align:left">Schedules a roll for a cluster</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>cluster:edit:set-replay-cluster-size</b>
      </td>
      <td style="text-align:left">Allows the setting of the replay cluster size of a cluster</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>cluster:edit:set-server-type</b>
      </td>
      <td style="text-align:left">Allows the setting of the server type of a cluster</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>cluster:edit:start</b>
      </td>
      <td style="text-align:left">Allows starting of a cluster</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>cluster:edit:stop</b>
      </td>
      <td style="text-align:left">Allows stoppage of a cluster</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>cluster:edit:toggle-elastic-ips</b>
      </td>
      <td style="text-align:left">Allows the enabling or disabling of the elastic IPs of a cluster</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>cluster:edit:update</b>
      </td>
      <td style="text-align:left">Allows the update of cluster settings</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>cluster:edit:update-target-capacity</b>
      </td>
      <td style="text-align:left">Allows the update of the target capacity of a cluster</td>
    </tr>
  </tbody>
</table>

## Connection

| Permission | Description |
| :--- | :--- |
| **connection:edit:attach-workspace** | Allows the attachment of a connection to workspaces |
| **connection:edit:create** | Allows the creation of a new connection |
| **connection:edit:delete** | Allows the deletion of a connection |
| **connection:edit:detach-workspace** | Allows the detachment of a connection from workspaces |
| **connection:view:list** | Allows listing of all instances of a connection |
| **connection:edit:update** | Allows the update of a connection |
| **connection:view:use** | Allows the use of a connection |
| **connection:view:validate** | Allows the validating of a connection |

## IAM

| Permission | Description |
| :--- | :--- |
| **iam:edit:attach-policy-group** | Allows the attachment of a policy to a group |
| **iam:edit:attach-policy-user** | Allows the attachment of a policy to a user |
| **iam:edit:attach-user-group** | Allows the attachment of a user to a group |
| **iam:edit:change-password-user** | Allows the changing of the password of a user |
| **iam:edit:create-group** | Allows the creation of a new group |
| **iam:edit:create-policy** | Allows the creation of a new policy |
| **iam:edit:create-token** | Allows the creation of a new token |
| **iam:edit:delete-group** | Allows the deletion of a group |
| **iam:edit:delete-policy** | Allows the deletion of a policy |
| **iam:edit:delete-token** | Allows the deletion of a token |
| **iam:edit:delete-user** | Allows the deletion of a user |
| **iam:view:describe-group** | Allows viewing of a group |
| **iam:view:describe-policy** | Allows viewing of a policy |
| **iam:view:describe-user** | Allows viewing of a user |
| **iam:edit:detach-policy-group** | Allows the detachment of a policy from a group |
| **iam:edit:detach-policy-user** | Allows the detachment of a policy from a user |
| **iam:edit:detach-user-group** | Allows the detachment of a user from a group |
| **iam:edit:invite-user** | Allows inviting of a user |
| **iam:view:list-group** | Allows the listing of all instances of a group |
| **iam:view:list-policy** | Allows the listing of all instances of a policy |
| **iam:view:list-token** | Allows the listing of all instances of a token |
| **iam:view:list-user** | Allows the listing of all instances of a user |
| **iam:edit:update-statements-policy** | Allows the update of the statements of a policy |
| **iam:edit:update-user** | Allows the update of a user |

## Input

| Permission | Description |
| :--- | :--- |
| **input:edit:add-custom-field** | Allows the addition of a custom field to an input |
| **input:edit:archive** | Allows the archiving of an input |
| **input:edit:attach-workspace** | Allows the attachment of a workspace to an input |
| **input:edit:create** | Allows the creation of a new input |
| **input:edit:delete** | Allows the deletion of an input |
| **input:edit:delete-custom-field** | Allows the deletion of a custom field from an input |
| **input:view:describe** | Allows the viewing of the input |
| **input:view:detach-from-cluster** | Allows the detachment of the input from its compute cluster, this stops the input |
| **input:edit:detach-workspace** | Allows the detachment of a workspace from an input |
| **input:edit:edit-custom-field** | Allows editing of a custom field in an input |
| **input:view:list** | Allows the listing of all instances of inputs |
| **input:edit:rename** | Allows the renaming of an input |
| **input:edit:restore** | Allows the restoring of an input |
| **input:edit:set-compute-environment** | Allows the setting of the compute environment of an input |
| **input:edit:stop** | Allows the stoppage of an input |
| **input:edit:stop-delete** | Allows the stoppage of a delete of an input |
| **input:edit:toggle-soft-retention** | Allows the enabling or disabling of the soft retention of an input |
| **input:edit:update-connection** | Allows the update of the connection of an input |
| **input:edit:update-content-type** | Allows the update of the content type of an input |
| **input:edit:update-description** | Allows the update of the description of an input |
| **input:edit:update-end-execution-at** | Allows the update of the end execution of an input |
| **input:edit:update-kafka-hosts** | Allows the update of the kafka hosts of an input |
| **input:edit:update-parallelism** | Allows the update of the parallelism of an input |
| **input:edit:update-real-time-statistics** | Enable or disable real-time statistics for an input |
| **input:edit:update-reporting-tags** | Allows the update of the reporting tags of an input |
| **input:edit:update-retention** | Allows the update of the retention of an input |
| **input:edit:update-shard-parallelism** | Allows the update of the shard parallelism of an input |
| **input:edit:upload-file** | Allows the upload of a file to be used as an input |
| **input:view:use** | Allows the use of an input |

## Lookup table

| Permission | Description |
| :--- | :--- |
| **lookup-table:edit:add-aggregation** | Allows the addition of an aggregation to a lookup table |
| **lookup-table:edit:add-custom-field** | Allows the addition of a custom field to a lookup table |
| **lookup-table:edit:add-key-column** | Allows the addition of a key column to a lookup table |
| **lookup-table:edit:add-lookup** | Allows the addition of a lookup to a lookup table |
| **lookup-table:edit:add-new-block** | Allows the addition of a new block to a lookup table |
| **lookup-table:edit:add-raw-field** | Allows the addition of a raw field to a lookup table |
| **lookup-table:edit:add-time-field** | Allows the addition of a time field to a lookup table |
| **lookup-table:edit:archive** | Allows the archiving of a lookup table |
| **lookup-table:edit:attach-alias** | Allows the attachment of an alias to a lookup table alias |
| **lookup-table:edit:attach-workspace** | Allows the attachment of a lookup table to workspaces |
| **lookup-table:edit:create** | Allows the creation of a new lookup table |
| **lookup-table:edit:create-alias** | Allows the creation of a new lookup table alias |
| **lookup-table:edit:delete** | Allows the deletion of a lookup table |
| **lookup-table:edit:delete-alias** | Allows the deletion of a lookup table alias |
| **lookup-table:edit:delete-block** | Allows the deletion of a block from a lookup table |
| **lookup-table:edit:deploy** | Allows the deployment of a lookup table |
| **lookup-table:edit:deploy-options** | Changes the deployment target of an output. This can include target connection and location |
| **lookup-table:view:describe** | Allows the viewing of a lookup table |
| **lookup-table:view:describe-alias** | Allows the viewing of a lookup table alias |
| **lookup-table:edit:detach-alias** | Allows the detachment of an alias from a lookup table alias |
| **lookup-table:view:detach-from-cluster** | Detaches the output from its compute and/or query clusters, this stops the output |
| **lookup-table:edit:detach-workspace** | Allows the detachment of a workspace from a lookup table |
| **lookup-table:edit:discard** | Allows the discarding of a lookup table |
| **lookup-table:edit:dismiss-duplication-warning** | Allows the dismissal of a duplication warning of a lookup table |
| **lookup-table:edit:dismiss-warning** | Allows the dismissal of a warning of a lookup table |
| **lookup-table:edit:duplicate** | Allows the duplication of a lookup table |
| **lookup-table:view:list** | Allows the listing of all instances of lookup tables |
| **lookup-table:view:list-alias** | Allows the listing of all instances of a lookup table alias |
| **lookup-table:edit:map-field** | Allows the mapping of a field of a lookup table |
| **lookup-table:edit:order-blocks** | Allows the ordering of a lookup table |
| **lookup-table:edit:order-fields** | Changes the order of the fields in an output or lookup table |
| **lookup-table:edit:remove-aggregation** | Allows the removal of an aggregation of a lookup table |
| **lookup-table:edit:remove-feature** | Allows the removal of a feature of a lookup table |
| **lookup-table:edit:remove-field** | Allows the removal of a field of a lookup table |
| **lookup-table:edit:remove-field-mapping** | Allows the removal of a field mapping of a lookup table |
| **lookup-table:edit:remove-key-column** | Allows the removal of a key column of a lookup table |
| **lookup-table:edit:rename** | Allows the renaming of a lookup table |
| **lookup-table:edit:rename-alias** | Allows the renaming of a lookup table alias |
| **lookup-table:edit:restore** | Allows the restoration of a lookup table |
| **lookup-table:edit:set-compute-environment** | Allows the setting of the compute environment of a lookup table |
| **lookup-table:edit:set-event-time-field** | Allows the setting of the event time field of a lookup table |
| **lookup-table:edit:set-fail-on-write-error** | Allow setting the fail on write error of a lookup table |
| **lookup-table:edit:set-is-delete** | Delete indicator field \(row is deleted when field's value is true\) |
| **lookup-table:edit:set-output-aggregation** | Allows the setting of the output aggregation of a lookup table |
| **lookup-table:edit:set-output-name** | Allows the setting of the output name of a lookup table |
| **lookup-table:edit:set-output-type** | Allows the setting of the output type of a lookup table |
| **lookup-table:edit:set-partial-key-queries** | Allows the setting of partial key queries of a lookup table |
| **lookup-table:edit:set-partition-columns** | Allows the setting of the partition columns of a lookup table |
| **lookup-table:edit:set-partition-time** | Allows the setting of the partition time of a lookup table |
| **lookup-table:edit:set-query-environment** | Allows the setting of the query environment of a lookup table |
| **lookup-table:edit:set-real-time** | Enables or disables the real-time capabilities of the lookup table |
| **lookup-table:edit:set-start-execution-from** | Allows the setting of the start execution from of a lookup table |
| **lookup-table:edit:set-upsert-key** | Allows the setting of the upsert key of a lookup table |
| **lookup-table:edit:stop** | Allows the stoppage of a lookup table |
| **lookup-table:edit:toggle-omit-key-columns** | Enables or disables whether or not the key columns are saved in the lookup table |
| **lookup-table:edit:toggle-run-compactions** | Allows enabling or disabling of the run compactions of a lookup table |
| **lookup-table:edit:toggle-soft-retention** | Allows enabling or disabling of the soft retention of a lookup table |
| **lookup-table:edit:unmap-field** | Allows the un-mapping of a lookup table |
| **lookup-table:edit:update** | Allows the update of a lookup table |
| **lookup-table:edit:update-aggregation** | Allows the update of an aggregation of an output or lookup table |
| **lookup-table:edit:update-alias** | Allows the update of a lookup table alias |
| **lookup-table:edit:update-block-title** | Allows the update of the block title of a lookup table |
| **lookup-table:edit:update-blocks** | Allows the update of the blocks of a lookup table |
| **lookup-table:edit:update-compaction-shards** | Allows the update of the compaction shards of a lookup table |
| **lookup-table:edit:update-compression** | Allows the update of the compression of a lookup table |
| **lookup-table:edit:update-date-format** | Allows the update of the date format of a lookup table |
| **lookup-table:edit:update-delete-indices** | Allows the update of the delete indices of a lookup table |
| **lookup-table:edit:update-description** | Allows the update of the description of a lookup table |
| **lookup-table:edit:update-elastic-connection** | Allows the update of the elastic connection of a lookup table |
| **lookup-table:edit:update-elastic-index** | Allows the update of the elastic index of the output \(for Elastic search outputs\) |
| **lookup-table:edit:update-end-execution-at** | Allows the update of the end execution at of a lookup table |
| **lookup-table:edit:update-excluded-partitions** | Allows the update of the excluded partitions of a lookup table |
| **lookup-table:edit:update-feature** | Allows the update of an existing calculated feature of the output or lookup table |
| **lookup-table:edit:update-inputs** | Allows the update of the inputs of a lookup table |
| **lookup-table:edit:update-output-interval** | Allows the update of the output interval of a lookup table |
| **lookup-table:edit:update-partition-size** | Allows the update of the partition size of a lookup table |
| **lookup-table:edit:update-path** | Allows the update of the path of a lookup table |
| **lookup-table:edit:update-reporting-tags** | Allows the update of the reporting tags of a lookup table |
| **lookup-table:edit:update-retention** | Allows the update of the retention of a lookup table |
| **lookup-table:edit:update-shards** | Allows the update of the shards of a lookup table |
| **lookup-table:edit:update-sql** | Allow updating the sql of a lookup table |
| **lookup-table:edit:update-window** | Allows the update of the window of a lookup table |
| **lookup-table:edit:update-window-size-override** | Allows the update of the window size override of a lookup table |

## Monitoring

| Permission | Description |
| :--- | :--- |
| **monitoring:edit:create** | Allows the creation of a new monitoring reporter |
| **monitoring:edit:delete** | Allows the deletion of a monitoring reporter |
| **monitoring:view:describe** | Allows the viewing of a monitoring reporter |
| **monitoring:view:list** | Allows the listing of all instances of monitoring reporters |
| **monitoring:edit:update** | Allows the update of a monitoring reporter |

## Notifications

| Permission | Description |
| :--- | :--- |
| **notifications:edit:dismiss** | Allows the dismissal of a notification |
| **notifications:edit:read** | Allows reading of a notification |

## Organization

| Permission | Description |
| :--- | :--- |
| **organization:edit:create-git-integration** | Allows the creation of a new git integration for the organization |
| **organization:edit:delete-git-integration** | Allows the deletion of a git integration for the organization |
| **organization:edit:run-cloud-integration** | Allows the running of cloud integrations for the organization |
| **organization:edit:set-default-connection** | Allows the setting of the default connection of an organization |
| **organization:edit:set-default-soft-retention** | Allows the setting of the default soft retention of an organization |
| **organization:edit:set-preferences** | Allows the setting of the preferences of an organization |
| **organization:edit:update-git-integration** | Allows the update of a git integration for the organization |

## Output

| Permission | Description |
| :--- | :--- |
| **output:edit:add-aggregation** | Allows the addition of an aggregation to an output |
| **output:edit:add-custom-field** | Allows the addition of a custom field to an output |
| **output:edit:add-key-column** | Allows the addition of a key column to an output |
| **output:edit:add-lookup** | Allows the addition of a lookup to an output |
| **output:edit:add-new-block** | Allows the addition of a new block to an output |
| **output:edit:add-raw-field** | Allows the addition of a raw field to an output |
| **output:edit:add-time-field** | Allows the addition of a time field to an output |
| **output:edit:archive** | Allows the archiving of an output |
| **output:edit:attach-workspace** | Allows the attachment of output to workspaces |
| **output:edit:create** | Allows the creation of a new output |
| **output:edit:delete** | Allows the deletion of an output |
| **output:edit:delete-block** | Allows the deletion of a block from an output |
| **output:edit:deploy** | Allows the deployment of an output |
| **output:edit:deploy-options** | Changes the deployment target of an output. This can include target connection and location |
| **output:view:describe** | Allows the viewing of the output |
| **output:view:detach-from-cluster** | Detaches the output from its compute and/or query clusters, this stops the output. |
| **output:edit:detach-workspace** | Allows the detachment of a workspace from an output |
| **output:edit:discard** | Allows the discarding of an output |
| **output:edit:dismiss-duplication-warning** | Allows the dismissal of a duplication warning of an output |
| **output:edit:dismiss-warning** | Allows the dismissal of a warning of an output |
| **output:edit:duplicate** | Allows the duplication of an output |
| **output:view:list** | Allows the listing of all instances of outputs |
| **output:edit:map-field** | Allows the mapping of a field of an output |
| **output:edit:order-blocks** | Allows the ordering of an output |
| **output:edit:order-fields** | Changes the order of the fields in an output or lookup table |
| **output:edit:remove-aggregation** | Allows the removal of an aggregation of an output  |
| **output:edit:remove-feature** | Allows the removal of a feature of an output |
| **output:edit:remove-field** | Allows the removal of a field of an output |
| **output:edit:remove-field-mapping** | Allows the removal of a field mapping of an output |
| **output:edit:remove-key-column** | Allows the removal of a key column of an output |
| **output:edit:rename** | Allows the renaming of an output |
| **output:edit:restore** | Allows the restoration of an output |
| **output:edit:set-compute-environment** | Allows the setting of the compute environment of an output |
| **output:edit:set-event-time-field** | Allows the setting of the event time field of an output |
| **output:edit:set-fail-on-write-error** | Allow setting the fail on write error of an output |
| **output:edit:set-is-delete** | Delete indicator field \(row is deleted when field's value is true\) |
| **output:edit:set-output-aggregation** | Allows the setting of the output aggregation of an output |
| **output:edit:set-output-name** | Allows the setting of the output name of an output |
| **output:edit:set-output-type** | Allows the setting of the output type of an output |
| **output:edit:set-partial-key-queries** | Allows the setting of the partial key queries of an output |
| **output:edit:set-partition-columns** | Allows the setting of the partition columns of an output |
| **output:edit:set-partition-time** | Allows the setting of the partition time of an output |
| **output:edit:set-query-environment** | Allows the setting of the query environment of an output |
| **output:edit:set-real-time** | Enables or disables the real-time capabilities of the lookup table |
| **output:edit:set-start-execution-from** | Allows the setting of the start execution of an output |
| **output:edit:set-upsert-key** | Allows the setting of the upsert key of an output |
| **output:edit:stop** | Allows the stoppage of an output |
| **output:edit:toggle-omit-key-columns** | Enables or disables whether or not the key columns are saved in the lookup table |
| **output:edit:toggle-run-compactions** | Allows the enabling or disabling of the run compactions of an output |
| **output:edit:toggle-soft-retention** | Allows the enabling or disabling of the soft retention of an output |
| **output:edit:unmap-field** | Allows the un-mapping of an output |
| **output:edit:update** | Allows the update of an output |
| **output:edit:update-aggregation** | Allows the update of an aggregation of an output or materialized view |
| **output:edit:update-block-title** | Allows the update of the block title of an output |
| **output:edit:update-blocks** | Allows the update of the blocks of an output |
| **output:edit:update-compaction-shards** | Allows the update of the compaction shards of an output |
| **output:edit:update-compression** | Allows the update of the compression of an output |
| **output:edit:update-date-format** | Allows the update of the date format of an output |
| **output:edit:update-delete-indices** | Allows the update of the delete indices of an output |
| **output:edit:update-description** | Allows the update of the description of an output |
| **output:edit:update-elastic-connection** | Allows the update of the elastic connection of an output |
| **output:edit:update-elastic-index** | Allows the update of the elastic index of the output \(for Elastic search outputs\) |
| **output:edit:update-end-execution-at** | Allows the update of the end execution of an output |
| **output:edit:update-excluded-partitions** | Allows the update of the excluded partitions of an output |
| **output:edit:update-feature** | Update an existing calculated feature of the output or lookup table |
| **output:edit:update-inputs** | Allows the update of the inputs of an output |
| **output:edit:update-output-interval** | Allows the update of the output interval of an output |
| **output:edit:update-partition-size** | Allows the update of the partition size of an output |
| **output:edit:update-path** | Allows the update of the path of an output |
| **output:edit:update-reporting-tags** | Allows the update of the reporting tags of an output |
| **output:edit:update-retention** | Allows the update of the retention of an output |
| **output:edit:update-shards** | Allows the update of the shards of an output |
| **output:edit:update-sql** | Allow updating the SQL of an output |
| **output:edit:update-window** | Allows the update of the window of an output |
| **output:edit:update-window-size-override** | Allows the update of the window size override of an output |

## Reference data

| Permission | Description |
| :--- | :--- |
| **reference-data:edit:create** | Allows the creation of new reference data |
| **reference-data:edit:delete** | Allows the deletion of reference data |
| **reference-data:view:describe** | Allows the viewing of the reference data |
| **reference-data:view:list** | Allows the listing of all instances of reference data |
| **reference-data:edit:update** | Allows the update of reference data |
| **reference-data:edit:upload-file** | Allows the upload of a file to be used as reference data |

## UDF

| Permission | Description |
| :--- | :--- |
| **udf:edit:create** | Allows the creation of a new user defined function |
| **udf:edit:delete** | Allows the deletion of a user defined function |
| **udf:view:describe** | Allows the viewing of a user defined function |
| **udf:edit:disable** | Allows the disabling of a user defined function |
| **udf:edit:enable** | Allows the enabling of a user defined function |
| **udf:view:list** | Allows the listing of all instances of user defined functions |
| **udf:edit:update** | Allows the update of a user defined function |

## Workspace

| Permission | Description |
| :--- | :--- |
| **workspace:edit:create** | Allows the creation of a new workspace |
| **workspace:edit:delete** | Allows the deletion of a workspace |
| **workspace:view:describe** | Allows the viewing of a workspace |
| **workspace:view:list** | Allows the listing of all instances of a workspace |

