======
pairid
======

Library of cryptographic key generation and data preparation procedures associated with the PAIR protocol.

|pypi|

.. |pypi| image:: https://badge.fury.io/py/pairid.svg#
   :target: https://badge.fury.io/py/pairid
   :alt: PyPI version and link.

Installation and Usage
----------------------
This library is available as a `package on PyPI <https://pypi.org/project/pairid>`__:

.. code-block:: bash

    python -m pip install pairid

The library can be imported in the usual ways:

.. code-block:: python

    import pairid
    from pairid import *

Examples
^^^^^^^^
This library makes it possible to perform the key generation, data salting, encryption, and decryption steps that are required for the PAIR protocol.

.. code-block:: python

    >>> ks = key_salt()
    >>> ka = key_commutative()
    >>> kb = key_commutative()
    >>> ciphertext_s = salt(ks, 'alice@example.com')
    >>> ciphertext_sa = encrypt(ka, ciphertext_s)
    >>> ciphertext_sab = encrypt(kb, ciphertext_sa)
    >>> decrypt(ka, ciphertext_sab) == encrypt(kb, ciphertext_s)
    True

Development
-----------
All installation and development dependencies are fully specified in ``pyproject.toml``. The ``project.optional-dependencies`` object is used to `specify optional requirements <https://peps.python.org/pep-0621>`__ for various development tasks. This makes it possible to specify additional options (such as ``lint``) when performing installation using `pip <https://pypi.org/project/pip>`__:

.. code-block:: bash

    python -m pip install .[lint]

Testing and Conventions
^^^^^^^^^^^^^^^^^^^^^^^
All unit tests are executed and their coverage is measured when using `pytest <https://docs.pytest.org>`__ (see the ``pyproject.toml`` file for configuration details):

.. code-block:: bash

    python -m pip install ".[test]"
    python -m pytest

Alternatively, all unit tests are included in the module itself and can be executed using `doctest <https://docs.python.org/3/library/doctest.html>`__:

.. code-block:: bash

    python src/pairid/pairid.py -v

Style conventions are enforced using `Pylint <https://pylint.readthedocs.io>`__:

.. code-block:: bash

    python -m pip install ".[lint]"
    python -m pylint src/pairid

Versioning
^^^^^^^^^^
The version number format for this library and the changes to the library associated with version number increments conform with `Semantic Versioning 2.0.0 <https://semver.org/#semantic-versioning-200>`__.
