
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _get-list-the-backups-for-a-project-v2-project-id-backups:

List the backups for a project
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v2/{project_id}/backups

Lists the backups for a project. 

This operation lists the backups for the specified project.

If no backups have been created for the project, the ``backups`` parameter in the response is an empty array.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |                         |
+--------------------------+-------------------------+-------------------------+
|400                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|401                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|403                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|404                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|405                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|409                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|500                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|503                       |                         |                         |
+--------------------------+-------------------------+-------------------------+


Request
""""""""""""""""




This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{project_id}              |String                   |Project ID of the user.  |
|                          |                         |Also referred to as the  |
|                          |                         |tenant ID or account ID. |
+--------------------------+-------------------------+-------------------------+



This table shows the query parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|marker                    |String *(Optional)*      |ID of the last known     |
|                          |                         |backup, for example,     |
|                          |                         |``0d95d699-d16b-11e4-    |
|                          |                         |93bd-c8e0eb190e3d``.     |
+--------------------------+-------------------------+-------------------------+
|limit                     |Integer *(Optional)*     |Number of backups to     |
|                          |                         |list. The default value  |
|                          |                         |is 100.                  |
+--------------------------+-------------------------+-------------------------+
|sort_dir                  |String *(Optional)*      |Direction to sort the    |
|                          |                         |results. Valid values    |
|                          |                         |are ``asc`` and          |
|                          |                         |``desc``. The default    |
|                          |                         |value is ``desc``.       |
+--------------------------+-------------------------+-------------------------+
|restorable                |Boolean *(Optional)*     |Indicates if only        |
|                          |                         |restorable backups are   |
|                          |                         |returned. If             |
|                          |                         |``restorable`` is        |
|                          |                         |``true``, only           |
|                          |                         |restorable backups are   |
|                          |                         |returned.                |
+--------------------------+-------------------------+-------------------------+
|configuration_id          |String *(Optional)*      |Use only in conjunction  |
|                          |                         |with                     |
|                          |                         |``restorable=true``. If  |
|                          |                         |you provide              |
|                          |                         |``configuration_id``,    |
|                          |                         |only restorable backups  |
|                          |                         |for the specified        |
|                          |                         |configuration are        |
|                          |                         |returned; for example,   |
|                          |                         |``-568f-4d5a-932f-       |
|                          |                         |fb2af86b5fd5``.          |
+--------------------------+-------------------------+-------------------------+




This operation does not accept a request body.




**Example List the backups for a project: JSON request**


.. code::

   GET https://dfw.backup.api.rackspacecloud.com/v2/110011//backups?marker=0d95d699-d16b-11e4-93bd-c8e0eb190e3d&limit=100&sort_dir=asc&restorable=true&configuration_id=7c8ee069-568f-4d5a-932f-fb2af86b5fd5 HTTP/1.1
   Host: dfw.backup.api.rackspacecloud.com
   X-Auth-Token: 0f6e9f63600142f0a970911583522217
   Accept: application/json
   Content-type: application/json





Response
""""""""""""""""





This table shows the body parameters for the response:

+-------------------------------+-----------+----------------------------------+
|Name                           |Type       |Description                       |
+===============================+===========+==================================+
|\ **backups**                  |String     |Information about the backups for |
|                               |           |the project.                      |
+-------------------------------+-----------+----------------------------------+
|backups.\ **project_id**       |String     |ID of the project.                |
+-------------------------------+-----------+----------------------------------+
|backups.\ **id**               |String     |ID of the backup.                 |
+-------------------------------+-----------+----------------------------------+
|backups.\ **agent**            |String     |Information about the agent for   |
|                               |           |the backup.                       |
+-------------------------------+-----------+----------------------------------+
|backups.agent.\ **id**         |String     |ID of the agent.                  |
+-------------------------------+-----------+----------------------------------+
|backups.agent.\ **links**      |String     |Link for the agent for the backup.|
+-------------------------------+-----------+----------------------------------+
|backups.agent.links.\ **href** |String     |Location (URI) of agent.          |
+-------------------------------+-----------+----------------------------------+
|backups.agent.links.\ **rel**  |String     |How the href link provided is     |
|                               |           |related to this resource URI.     |
+-------------------------------+-----------+----------------------------------+
|backups.\ **configuration**    |String     |Information about the             |
|                               |           |configuration.                    |
+-------------------------------+-----------+----------------------------------+
|backups.configuration.\ **id** |String     |ID of the configuration.          |
+-------------------------------+-----------+----------------------------------+
|backups.configuration.\        |String     |Link for the configuration of the |
|**links**                      |           |backup.                           |
+-------------------------------+-----------+----------------------------------+
|backups.configuration.links.\  |String     |Location (URI) of the             |
|**href**                       |           |configuration.                    |
+-------------------------------+-----------+----------------------------------+
|backups.configuration.links.\  |String     |How the href link provided is     |
|**rel**                        |           |related to this resource URI.     |
+-------------------------------+-----------+----------------------------------+
|backups.\ **state**            |String     |State of the backup, for example, |
|                               |           |``completed_with_errors``.        |
+-------------------------------+-----------+----------------------------------+
|backups.\ **started_time**     |String     |Time the backup started.          |
+-------------------------------+-----------+----------------------------------+
|backups.\ **ended_time**       |String     |Time the backup ended.            |
+-------------------------------+-----------+----------------------------------+
|backups.\ **snapshot_id**      |String     |ID of the snapshot.               |
+-------------------------------+-----------+----------------------------------+
|backups.\ **errors**           |String     |Information about errors.         |
+-------------------------------+-----------+----------------------------------+
|backups.errors.\ **count**     |String     |Number of errors.                 |
+-------------------------------+-----------+----------------------------------+
|backups.errors.\ **reason**    |String     |Cause of the error, for example,  |
|                               |           |``unable_to_process_some_files``. |
+-------------------------------+-----------+----------------------------------+
|backups.errors.\               |String     |Additional information about the  |
|**diagnostics**                |           |cause of the error; for example,  |
|                               |           |``Some files could not be backed  |
|                               |           |up. Partial list follows.``       |
+-------------------------------+-----------+----------------------------------+
|backups.errors.\ **links**     |String     |Links for the errors.             |
+-------------------------------+-----------+----------------------------------+
|backups.errors.links.\ **href**|String     |Location (URI) of the errors.     |
+-------------------------------+-----------+----------------------------------+
|backups.errors.links.\ **rel** |String     |How the href link provided is     |
|                               |           |related to this resource URI.     |
+-------------------------------+-----------+----------------------------------+
|backups.\ **files_searched**   |String     |Number of files searched.         |
+-------------------------------+-----------+----------------------------------+
|backups.\ **files_backed_up**  |String     |Number of files backed up.        |
+-------------------------------+-----------+----------------------------------+
|backups.\ **bytes_searched**   |String     |Number of bytes searched.         |
+-------------------------------+-----------+----------------------------------+
|backups.\ **bytes_backed_up**  |String     |Number of bytes backed up.        |
+-------------------------------+-----------+----------------------------------+
|backups.\ **bytes_in_db**      |String     |Number of bytes in the backup     |
|                               |           |database.                         |
+-------------------------------+-----------+----------------------------------+
|backups.\ **bandwidth_avg_bps**|String     |Average bandwidth in bytes per    |
|                               |           |second.                           |
+-------------------------------+-----------+----------------------------------+
|backups.\ **restorable**       |String     |Specifies whether the backup can  |
|                               |           |be used for restores.             |
+-------------------------------+-----------+----------------------------------+
|backups.\ **links**            |String     |Links for the backup.             |
+-------------------------------+-----------+----------------------------------+
|backups.links.\ **href**       |String     |Location (URI) of the backup.     |
+-------------------------------+-----------+----------------------------------+
|backups.links.\ **rel**        |String     |How the href link provided is     |
|                               |           |related to this resource URI.     |
+-------------------------------+-----------+----------------------------------+
|\ **links**                    |String     |Links for the next and previous   |
|                               |           |backup.                           |
+-------------------------------+-----------+----------------------------------+
|links.\ **href**               |String     |Location (URI).                   |
+-------------------------------+-----------+----------------------------------+
|links.\ **rel**                |String     |How the href link provided is     |
|                               |           |related to this resource URI.     |
+-------------------------------+-----------+----------------------------------+







**Example List the backups for a project: JSON response**


.. code::

   200 (OK)
   Content-Type: application/json


.. code::

   {
       "backups": [
           {
               "project_id": "123456",
               "id": "0d95d699-d16b-11e4-93bd-c8e0eb190e3d",
               "agent": {
                   "id": "8f135b4f-7a69-4b8a-947f-5e80d772fd97",
                   "links": [
                       {
                           "href": "https://cloudbackupapi.apiary-mock.com/v2/agents/8f135b4f-7a69-4b8a-947f-5e80d772fd97", 
                           "rel": "full"
                       }
                   ]
               },
               "configuration": {
                   "id": "7c8ee069-568f-4d5a-932f-fb2af86b5fd5",
                   "links": [
                       {
                           "href": "https://cloudbackupapi.apiary-mock.com/v2/configurations/7c8ee069-568f-4d5a-932f-fb2af86b5fd5", 
                           "rel": "full"
                       }
                   ]
               },
               "state": "completed_with_errors",
               "started_time": "2014-08-05T18:22:22.238641Z",
               "ended_time": "2014-08-05T18:23:50.489715Z",
               "snapshot_id": 1111,
               "errors": {
                   "count": 1,
                   "reason": "unable_to_process_some_files",
                   "diagnostics": "Some files could not be backed up. Partial list follows.",
                   "links": [
                       {
                           "href": "https://cloudbackupapi.apiary-mock.com/v2/backups/0d95d699-d16b-11e4-93bd-c8e0eb190e3d/errors",
                           "rel": "full"
                       }
                   ]
               },
               "files_searched": 1222,
               "files_backed_up": 6,
               "bytes_searched": 3700000000,
               "bytes_backed_up": 127000000,
               "bytes_in_db": 49340871,
               "bandwidth_avg_bps": 16628982,
               "restorable": true,
               "links": [
                   {
                       "href": "https://cloudbackupapi.apiary-mock.com/v2/backups/0d95d699-d16b-11e4-93bd-c8e0eb190e3d",
                       "rel": "self"
                   },
                   {
                       "href": "https://cloudbackupapi.apiary-mock.com/v2/backups/0d95d699-d16b-11e4-93bd-c8e0eb190e3d/events",
                       "rel": "events"
                   }
               ]
           }
       ],
       "links": [
           {
               "href": "https://cloudbackupapi.apiary-mock.com/v2/backups?marker=0d95d699-d16b-11e4-93bd-c8e0eb190e3d",
               "rel": "next"
           },
           {
               "href": "https://cloudbackupapi.apiary-mock.com/v2/backups?marker=0d95d699-d16b-11e4-93bd-c8e0eb190e3d&sort_dir=asc",
               "rel": "previous"
           }
       ]
   }




