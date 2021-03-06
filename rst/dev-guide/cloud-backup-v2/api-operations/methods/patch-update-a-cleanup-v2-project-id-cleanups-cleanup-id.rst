
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _patch-update-a-cleanup-v2-project-id-cleanups-cleanup-id:

Update a cleanup
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    PATCH /v2/{project_id}/cleanups/{cleanup_id}

Updates the specified cleanup.

This operation updates the specified cleanup. Cleanups are updated with the JSON Patch. For more information about the JSON Patch, see `RFC6902 <http://tools.ietf.org/html/rfc6902>`__.

You can issue updates only for the following scenarios:



*  The agent is reporting the state of the cleanup. For example, ``[{ "op": "replace", "path": "/state", "value": "queued" }]``. The following values are valid for ``value`` :
   
   
   
   *  ``queued``
   *  ``in_progress``
*  The agent is reporting the results of the finished cleanup (see the example request in this section). The following values are valid for ``/state`` :
   
   
   
   *  ``completed``
   *  ``completed_with_errors``
   *  ``failed``
   *  ``stopped``
*  You are issuing a request to stop the cleanup. For example, `` [{ "op": "replace", "path": "/state", "value": "stop_requested" }`` ].


You can use the ``add`` and ``replace`` operations interchangeably because they are interpreted identically for these scenarios.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|204                       |No Content               |                         |
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
|{cleanup_id}              |String *(Required)*      |Cleanup ID. For example, |
|                          |                         |``2f8708b3-d16b-11e4-    |
|                          |                         |bc22-c8e0eb190e3d``.     |
+--------------------------+-------------------------+-------------------------+





This table shows the body parameters for the request:

+-------------------------+------------------------+---------------------------+
|Name                     |Type                    |Description                |
+=========================+========================+===========================+
|\ **op**                 |String *(Required)*     |The ``replace`` or ``add`` |
|                         |                        |operation to update the    |
|                         |                        |cleanup.                   |
+-------------------------+------------------------+---------------------------+
|\ **path**               |String *(Required)*     |Path.                      |
+-------------------------+------------------------+---------------------------+
|\ **value**              |String *(Required)*     |Value related to the       |
|                         |                        |``path``. See the          |
|                         |                        |beginning of this section  |
|                         |                        |for additional information.|
+-------------------------+------------------------+---------------------------+
|value.\ **count**        |String *(Optional)*     |Number of errors, when     |
|                         |                        |``path`` is ``/errors``.   |
+-------------------------+------------------------+---------------------------+
|value.\ **reason**       |String *(Optional)*     |Cause of the error, when   |
|                         |                        |``path`` is ``/errors``;   |
|                         |                        |for example,               |
|                         |                        |``error_deleting_object``. |
+-------------------------+------------------------+---------------------------+
|value.\ **diagnostics**  |String *(Optional)*     |Additional information     |
|                         |                        |about the cause of the     |
|                         |                        |error, when ``path`` is    |
|                         |                        |``/errors``.               |
+-------------------------+------------------------+---------------------------+
|value.\ **list**         |String *(Optional)*     |Additional information     |
|                         |                        |about the error, when      |
|                         |                        |``path`` is ``/errors``.   |
+-------------------------+------------------------+---------------------------+
|value.list.\ **index**   |String *(Optional)*     |Index.                     |
+-------------------------+------------------------+---------------------------+
|value.list.\ **path**    |String *(Optional)*     |Path to the log.           |
+-------------------------+------------------------+---------------------------+
|value.list.\ **type**    |String *(Optional)*     |Type of error.             |
+-------------------------+------------------------+---------------------------+
|value.list.\             |String *(Optional)*     |Information about the      |
|**exception**            |                        |exception.                 |
+-------------------------+------------------------+---------------------------+





**Example Update a cleanup: JSON request**


.. code::

   PATCH https://dfw.backup.api.rackspacecloud.com/v2/110011/cleanups/2f8708b3-d16b-11e4-bc22-c8e0eb190e3d HTTP/1.1
   Host: dfw.backup.api.rackspacecloud.com
   X-Auth-Token: 0f6e9f63600142f0a970911583522217
   Content-Type: application/json-patch+json


.. code::

   [
       {
           "op": "replace",
           "path": "/state",
           "value": "completed_with_errors"
       },
       {
           "op": "add",
           "path": "/started_time",
           "value": "2014-10-10T19:05:44.632393Z"
       },
       {
           "op": "add",
           "path": "/ended_time",
           "value": "2014-10-10T19:35:44.632393Z"
       },
       {
           "op": "add",
           "path": "/snapshot_ids",
           "value": [23, 51]
       },
       {
           "op": "add",
           "path": "/errors",
           "value": {
               "count": 1,
               "reason": "error_deleting_object",
               "diagnostics": null,
               "list": [
                   {
                       "index": 34,
                       "path": "/var/www/html/log/st_808_playlist.txt",
                       "type": "file_missing_blocks",
                       "description": "A vault validation determined that the specified file is missing blocks.",
                       "exception": null
                   }
               ]
           }
       },
       {
           "op": "add",
           "path": "/bytes_before",
           "value": 1073741824
       },
       {
           "op": "add",
           "path": "/bytes_after",
           "value": 1067030938
       }
   ]





Response
""""""""""""""""










**Example Update a cleanup: JSON response**


.. code::

   204 (No Content)




