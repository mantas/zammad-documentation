Mentions
********

   .. warning::

      Mention endpoints depend on on group permissions if the user you're 
      using is an agent. Because of this tickets may or may not be available.

List
====

Required permission: ``ticket.agent`` with ``read`` access to the ticket. The only valid ``type`` so far is ``Ticket``.

``GET``-Request sent: ``/api/v1/mentions?mentionable_type={type} &mentionable_id={id}``

.. code-block:: json
   :force:
   
   # HTTP-Code 200 Ok

   {
     mentions: [
       {
         "id":2,
         "mentionable_type":"Ticket",
         "mentionable_id":1,
         "user_id":3,
         "updated_by_id":3,
         "created_by_id":3,
         "created_at":"2021-03-16T08:51:08.985Z",
         "updated_at":"2021-03-16T08:51:08.985Z"
       },
       {
         "id":3,
         "mentionable_type":"Ticket",
         "mentionable_id":1,
         "user_id":4,
         "updated_by_id":4,
         "created_by_id":4,
         "created_at":"2021-03-16T08:51:08.986Z",
         "updated_at":"2021-03-16T08:51:08.986Z"
       },
     ]
   }

It will list users mentioned in the ticket.

Create
======

Required permission: ``ticket.agent`` with ``read`` access to the ticket. The only valid ``type`` so far is ``Ticket``.

``POST``-Request sent: ``/api/v1/mentions``

.. code-block:: json

   {
     "mentionable_type": "Ticket",
     "mentionable_id": 12,
   }

Response:

.. code-block:: json
   :force:

   # HTTP-Code 201 Created
   
   {
     "id":2,
     "mentionable_type":"Ticket",
     "mentionable_id":1,
     "user_id":3,
     "updated_by_id":3,
     "created_by_id":3,
     "created_at":"2021-03-16T08:51:08.985Z",
     "updated_at":"2021-03-16T08:51:08.985Z"
   }

The mention will be created for the user of the current session.

Delete
======

Required: ``Mention`` user has to match the user of the current session.

``DELETE``-Request sent: ``/api/v1/mentions/{id}``

Response:

.. code-block:: json
   :force:

   # HTTP-Code 200 Ok
   
   {
     "id":2,
     "mentionable_type":"Ticket",
     "mentionable_id":1,
     "user_id":3,
     "updated_by_id":3,
     "created_by_id":3,
     "created_at":"2021-03-16T08:51:08.985Z",
     "updated_at":"2021-03-16T08:51:08.985Z"
   }

The given mention will be deleted
