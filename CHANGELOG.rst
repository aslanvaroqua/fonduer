Version 0.1.8 (coming soon...)
------------------------------

* `@lukehsiao`_: Remove unnecessary encoding in __repr__
  (`#50 <https://github.com/HazyResearch/fonduer/pull/50>`_)
* `@lukehsiao`_: Fix LocationMatch NER tags for spaCy 
  (`#50 <https://github.com/HazyResearch/fonduer/pull/50>`_)

Version 0.1.7
-------------

.. warning::
    This release is NOT backwards compatable with v0.1.6. Specifically, the
    ``snorkel`` submodule in fonduer has been removed. Any previous imports of
    the form:

    .. code:: python

        from fonduer.snorkel._ import _

    Should drop the ``snorkel`` submodule:

    .. code:: python
        
        from fonduer._ import _

.. tip::
    To leverage the logging output of Fonduer, such as in a Jupyter Notebook,
    you can configure a logger in your application:

    .. code:: python

        import logging

        logging.basicConfig(stream=sys.stdout, format='[%(levelname)s] %(name)s - %(message)s')
        log = logging.getLogger('fonduer')
        log.setLevel(logging.INFO)


* `@lukehsiao`_: Remove SQLite code, switch to logging, and absorb snorkel
  codebase directly into the fonduer package for simplicity
  (`#44 <https://github.com/HazyResearch/fonduer/pull/44>`_)
* `@lukehsiao`_: Add lf_helpers to ReadTheDocs 
  (`#42 <https://github.com/HazyResearch/fonduer/pull/42>`_)
* `@lukehsiao`_: Remove unused package dependencies 
  (`#41 <https://github.com/HazyResearch/fonduer/pull/41>`_)

Version 0.1.6
-------------

* `@senwu`_: Fix support for providing a PostgreSQL username and password as
  part of the connection string provided to Meta.init() 
  (`#40 <https://github.com/HazyResearch/fonduer/pull/40>`_)
* `@lukehsiao`_: Switch README from Markdown to reStructuredText 

Version 0.1.5 
-------------
.. warning::
    This release is NOT backwards compatable with v0.1.4. Specifically, in order
    to initialize a session with postgresql, you no longer do

    .. code:: python
        
        os.environ['SNORKELDB'] = 'postgres://localhost:5432/' + DBNAME
        from fonduer import SnorkelSession       
        session = SnorkelSession()

    which had the side-effects of manipulating your database tables on import
    (or creating a ``snorkel.db`` file if you forgot to set the environment
    variable). Now, you use the Meta class to initialize your session:

    .. code:: python

        from fonduer import Meta       
        session = Meta.init("postgres://localhost:5432/" + DBNAME).Session()
      
    No side-effects occur until ``Meta`` is initialized.

* `@lukehsiao`_: Remove reliance on environment vars and remove side-effects of
  importing fonduer (`#36 <https://github.com/HazyResearch/fonduer/pull/36>`_)
* `@lukehsiao`_: Bring codebase in PEP8 compliance and add automatic code-style
  checks (`#37 <https://github.com/HazyResearch/fonduer/pull/37>`_)

Version 0.1.4 
-------------

* `@lukehsiao`_: Separate tutorials into their own repo (`#31
  <https://github.com/HazyResearch/fonduer/pull/31>`_)

Version 0.1.3
-------------

Minor hotfix to the README formatting for PyPi.

Version 0.1.2
-------------

* `@lukehsiao`_: Deploy Fonduer to PyPi using Travis-CI 


.. 
  For convenience, all username links for contributors can be listed here

.. _@lukehsiao: https://github.com/lukehsiao
.. _@senwu: https://github.com/senwu
