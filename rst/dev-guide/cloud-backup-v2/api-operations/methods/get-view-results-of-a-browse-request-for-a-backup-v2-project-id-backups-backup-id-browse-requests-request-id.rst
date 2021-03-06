
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _get-view-results-of-a-browse-request-for-a-backup-v2-project-id-backups-backup-id-browse-requests-request-id:

View results of a browse request for a backup
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v2/{project_id}/backups/{backup_id}/browse-requests/{request_id}

Shows the results for the specified browse request ID for the specified backup's files.

This operation shows the results for a browse request ID for the specified backup's files. The request returns a 404 response code until there is a response to the browse request (see "View results of a browse request for a backup").



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
|{backup_id}               |String *(Required)*      |Backup ID. For example,  |
|                          |                         |``0d95d699-d16b-11e4-    |
|                          |                         |93bd-c8e0eb190e3d``.     |
+--------------------------+-------------------------+-------------------------+
|{request_id}              |String *(Required)*      |Browse request ID. For   |
|                          |                         |example, ``ae7528c8-bcc3-|
|                          |                         |4356-a237-f20fbdd79ee4``.|
+--------------------------+-------------------------+-------------------------+





This operation does not accept a request body.




**Example View results of a browse request for a backup: JSON request**


.. code::

   GET https://dfw.backup.api.rackspacecloud.com/v2/110011/backups/0d95d699-d16b-11e4-93bd-c8e0eb190e3d/browse-requests/ae7528c8-bcc3-4356-a237-f20fbdd79ee4 HTTP/1.1
   Host: dfw.backup.api.rackspacecloud.com
   X-Auth-Token: 0f6e9f63600142f0a970911583522217
   Content-type: application/json





Response
""""""""""""""""





This table shows the body parameters for the response:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|\ **id**                  |String                   |ID of the browse event.  |
+--------------------------+-------------------------+-------------------------+
|\ **time**                |String                   |Time of the browse event.|
+--------------------------+-------------------------+-------------------------+
|\ **event**               |String                   |Type of the event.       |
+--------------------------+-------------------------+-------------------------+
|\ **agent**               |String                   |Information about the    |
|                          |                         |agent.                   |
+--------------------------+-------------------------+-------------------------+
|agent.\ **id**            |String                   |ID of the agent.         |
+--------------------------+-------------------------+-------------------------+
|\ **request_id**          |String                   |ID of the request.       |
+--------------------------+-------------------------+-------------------------+
|\ **succeeded**           |String                   |Specifies whether the    |
|                          |                         |request succeeded.       |
+--------------------------+-------------------------+-------------------------+
|\ **path**                |String                   |Path that was browsed.   |
+--------------------------+-------------------------+-------------------------+
|\ **path_encoded**        |String                   |Encoded path for the     |
|                          |                         |browsed path.            |
+--------------------------+-------------------------+-------------------------+
|\ **items**               |String                   |Information about        |
|                          |                         |browsed item.            |
+--------------------------+-------------------------+-------------------------+
|items.\ **name**          |String                   |Name of the browsed item.|
+--------------------------+-------------------------+-------------------------+
|items.\ **name_encoded**  |String                   |Encoded name for the     |
|                          |                         |browsed item.            |
+--------------------------+-------------------------+-------------------------+
|items.\ **bytes**         |String                   |Number of browsed bytes. |
+--------------------------+-------------------------+-------------------------+
|items.\ **mime_type**     |String                   |Mime type for the        |
|                          |                         |browsed item.            |
+--------------------------+-------------------------+-------------------------+







**Example View results of a browse request for a backup: JSON response**


.. code::

   200 (OK)
   Content-Type: application/json


.. code::

   {
       "id": "5152884001",
       "time": "2014-10-07T14:34:05.376357Z",
       "event": "backup_browsed",
       "agent": {
           "id": "8f135b4f-7a69-4b8a-947f-5e80d772fd97"
       },
       "request_id": "ae7528c8-bcc3-4356-a237-f20fbdd79ee4",
       "succeeded": true,
       "path": "/path/to/browse/",
       "path_encoded": "/optional/base64encoded/path/if/non-utf-8/characters/present/",
       "items": [
           {
               "name": "initrd.img",
               "name_encoded": "optional_base64encoded_name_if_non-utf-8_characters_present",
               "bytes": 0,
               "mime_type": "application/x-symlink-file"
           }
       ]
   }




