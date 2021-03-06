
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _patch-update-a-restore-v2-project-id-restores-restore-id:

Update a restore
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    PATCH /v2/{project_id}/restores/{restore_id}

Updates the specified restore.

This operation updates the specified restore. Restores are updated with the JSON Patch. For more information about the JSON Patch, see `RFC6902 <http://tools.ietf.org/html/rfc6902>`__.

You can issue updates only for the following scenarios:



*  The agent is reporting the state of the restore. For example, ``[{ "op": "replace", "path": "/state", "value": "queued" }]``. The following values are valid for ``value`` :
   
   
   
   *  ``queued``
   *  ``preparing``
   *  ``in_progress``
*  The agent is reporting the results of the finished restore (see the example request in this section). The following values are valid values for ``/state`` :
   
   
   
   *  ``completed``
   *  ``completed_with_errors``
   *  ``failed``
   *  ``stopped``
*  The agent is issuing a request to stop the restore. For example, ``[{ "op": "replace", "path": "/state", "value": "stop_requested" }]``.


You can use the ``add`` and ``replace`` operations interchangeably because they are interpreted identically for these scenarios. The only paths that you cannot modify are those listed in this endpoint's description.



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
|{restore_id}              |String *(Required)*      |Restore ID. For example, |
|                          |                         |``e87e6f7d-d166-11e4-    |
|                          |                         |8689-c8e0eb190e3d``.     |
+--------------------------+-------------------------+-------------------------+





This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|\ **op**                  |String *(Required)*      |The ``replace`` or       |
|                          |                         |``add`` operation to     |
|                          |                         |update the restore.      |
+--------------------------+-------------------------+-------------------------+
|\ **path**                |String *(Required)*      |Path. Valid values are   |
|                          |                         |``/state``, ``/started-  |
|                          |                         |time``, ``/ended-time``, |
|                          |                         |``/errors``,             |
|                          |                         |``/files_restores``, and |
|                          |                         |``/bytes-restored``.     |
+--------------------------+-------------------------+-------------------------+
|\ **value**               |String *(Required)*      |Value related to the     |
|                          |                         |``path``.                |
+--------------------------+-------------------------+-------------------------+
|value.\ **count**         |String                   |When ``path`` is         |
|                          |                         |``/errors``, specifies   |
|                          |                         |the number of errors     |
|                          |                         |that the restore can     |
|                          |                         |encounter.               |
+--------------------------+-------------------------+-------------------------+
|value.\ **reason**        |String                   |When ``path`` is         |
|                          |                         |``/errors`` and an error |
|                          |                         |is encountered,          |
|                          |                         |specifies the reason for |
|                          |                         |the error.               |
+--------------------------+-------------------------+-------------------------+
|value.\ **diagnostics**   |String                   |When ``path`` is         |
|                          |                         |``/errors`` and an error |
|                          |                         |is encountered, provides |
|                          |                         |information about        |
|                          |                         |possible reasons for the |
|                          |                         |error.                   |
+--------------------------+-------------------------+-------------------------+
|value.\ **list**          |String                   |Additional information   |
|                          |                         |for the errors.          |
+--------------------------+-------------------------+-------------------------+
|value.list.\ **index**    |String                   |Index for the error.     |
+--------------------------+-------------------------+-------------------------+
|value.list.\ **path**     |String                   |Path for the error.      |
+--------------------------+-------------------------+-------------------------+
|value.list.\ **type**     |String                   |Type of error.           |
+--------------------------+-------------------------+-------------------------+
|value.list.\ **exception**|String                   |Information about the    |
|                          |                         |exception.               |
+--------------------------+-------------------------+-------------------------+
|value.list.exception.\    |String                   |Code for the exception.  |
|**code**                  |                         |                         |
+--------------------------+-------------------------+-------------------------+
|value.list.exception.\    |String                   |Description for the      |
|**description**           |                         |exception.               |
+--------------------------+-------------------------+-------------------------+
|value.list.exception.\    |String                   |Details about the        |
|**details**               |                         |exception.               |
+--------------------------+-------------------------+-------------------------+





**Example Update a restore: JSON request**


.. code::

   PATCH https://dfw.backup.api.rackspacecloud.com/v2/110011/restores/e87e6f7d-d166-11e4-8689-c8e0eb190e3d HTTP/1.1
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
           "value": "2014-10-20T13:11:58.985151Z"
       },
       {
           "op": "add",
           "path": "/ended_time",
           "value": "2014-10-20T13:12:58.985151Z"
       },
       {
           "op": "add",
           "path": "/errors",
           "value": {
               "count": 1,
               "reason": "unable_to_process_some_files",
               "diagnostics": "Some files may not have been restored.",
               "list": [
                   {
                       "index": 3,
                       "path": "/usr/bin/h2xs",
                       "type": "phx_exception",
                       "exception": {
                           "code": 9016,
                           "description": "WRITE failed (3042): No space left on device",
                           "details": "1: [virtual void phx::LinuxFs::Write(boost::shared_ptr<phx::AbstractFileRef>, phx::BinaryStream&, phx::file_size_t): 290-virtual void phx::LinuxFs::Write(boost::shared_ptr<phx::AbstractFileRef>, phx::BinaryStream&, phx::file_size_t)] Ex Code(9016): WRITE failed (3042): No space left on device"
                       }
                   }
               ]
           }
       },
       {
           "op": "add",
           "path": "/files_restored",
           "value": 2
       },
       {
           "op": "add",
           "path": "/bytes_restored",
           "value": 1512
       }
   ]





Response
""""""""""""""""










**Example Update a restore: JSON response**


.. code::

   204 (No Content)
   




