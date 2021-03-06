Quick Start
---------------------------

OSX and Linux
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The recommended was to use pygauss is to download the
`Anaconda <http://continuum.io/downloads>`__ Scientific Python
Distribution (64-bit). Once downloaded a new environment can be created
in terminal and pygauss installed in one simple line:

::

    conda create -n pg_env -c https://conda.binstar.org/cjs14 pygauss


Windows
~~~~~~~~~~~~~~~~~~~~~~

There is currently no pygauss Conda distributable for Windows or for
chemlab, which has C-extensions that need to be built using a compiler.
Therefore chemlab will need to be cloned from GitHub, its extensions built,
dependancies installed and finally install pygauss.

::

    conda create -n pg_env python=2.7
    conda install -n pg_env -c https://conda.binstar.org/cjs14 cclib
    conda install -n pg_env -c https://conda.binstar.org/cjs14 chemview
    conda install -n pg_env -c https://conda.binstar.org/cjs14 pyopengl     
    git clone --recursive https://github.com/chemlab/chemlab.git
    cd chemlab
    python setup.py build_ext --inplace
    conda install -n pg_env <pil, pandas, matplotlib, scikit-learn, ...> 
    activate pg_env
    pip install . # or add to PYTHONPATH
    pip install pygauss

Troubleshooting
~~~~~~~~~~~~~~~~~~~~~~

If you encounter difficulties it may be useful to look in
`working\_conda\_environments <https://github.com/chrisjsewell/PyGauss/tree/master/working_conda_environments>`__
at conda environments known to work.

Testing
~~~~~~~~~~~~~~~~~~~~~~

Pygauss utilises a unit test suite (`nose <https://nose.readthedocs.org>`__/`nose-parameterized <https://github.com/wolever/nose-parameterized>`__) to ensure that computations run, 
and are correct. Continuous integration testing of the source code is provided by `Travis CI <https://travis-ci.org/>`__ 
and pass completion is an automated condition of the Conda build. 
These unit tests can also be run manually in the command line;

::

	nosetests -v --with-doctest

or directly in python;

::

	pygauss.run_nose(verbose=True)
