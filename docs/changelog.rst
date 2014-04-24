.. _changelog:

ChangeLog
=========

Changes to the library are recorded here.

v0.2.9
------

Serializable models via pickle.

.. code-block:: python

    import pickle

    vertex = MyTestVertex.create(name='test')
    serialized_vertex = pickle.dumps(vertex)
    deserialized_vertex = pickle.loads(serialized_vertex)
    assert vertex == deserialized_vertex


v0.2.8
------

Re-Release of Mogwai to the public. Name change to Mogwai, which loosely means "gremlin". This is a major refactor of the original `thunderdome` library by Blake.

 * Using RexPro, updated library to utilize RexPro and compatible with Titan 0.4.2
 * Refactored library, changed the way properties are handled, validated and their associated save strategies.
 * Removed vid and eid as primary keys, titan generates unique primary keys that we can utilize. Now accessible via Element._id or Element.id (the latter is a property shortcut to Element._id)
 * Added groovy tests, updated gremlin base method for new _type_name
 * Added interactive shell with some slight magic::

        Usage:
            python -m mogwai.shell --host localhost
        For more help see:
            python -m mogwai.shell --help
        Also HELP is available in the shell

 * Preview of index specification system, initial commit
 * Relationship system, includes generic query method, create relationship method and strict relationship checker
 * Fixed groovy files to only use local variables in core structure, will prevent Concurrent Global variable scope locks
 * Special Enum Vertex metaclass now available. ie. `MyVertex.MY_ENUM` will be able to resolve to an actual database entry
 * Performance monitoring tools now available - Customizable for different metric reporting mechanisms, ie, console, logs, graphite, newrelic.
 * Apache 2.0 License