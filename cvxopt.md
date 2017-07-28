# CVXOPT

Last updated: March 27, 2017

# Installing

Pretty good install instructions here: <http://cvxopt.org/install/index.html#ubuntu-debian>.

On Ubuntu 12.04 (the version CARTO runs on), SuiteSparse wasn't linking properly when installed through `apt-get`, so I followed the instructions on the CVXOPT installer page:

```bash
wget http://faculty.cse.tamu.edu/davis/SuiteSparse/SuiteSparse-4.5.4.tar.gz
tar -xf SuiteSparse-4.5.4.tar.gz
export CVXOPT_SUITESPARSE_SRC_DIR=$(pwd)/SuiteSparse
```

Once this was set, the following worked for compiling CVXOPT:

```bash
export CVXOPT_BUILD_FFTW=1
export CVXOPT_BUILD_GLPK=1
export CVXOPT_BUILD_GSL=1
python setup.py install --user
```

To make cvxopt show up in the database, I had to set the path for pip to install in a new file in `$HOME/.config/pip/pip.conf` (<http://stackoverflow.com/questions/28874685/pip-how-to-install-into-usr-local?answertab=active#tab-top>) to specifically install to `dist-packages`:

```
[global]
target = /usr/local/lib/python2.7/dist-packages
```

## Sample function

```python
CREATE OR REPLACE FUNCTION test_cvxopt() returns setof numeric As $$
from cvxopt import matrix, solvers
Q = 2*matrix([ [2, .5], [.5, 1] ])
plpy.notice(Q)
p = matrix([1.0, 1.0])
G = matrix([[-1.0,0.0],[0.0,-1.0]])
h = matrix([0.0,0.0])
A = matrix([1.0, 1.0], (1,2))
b = matrix(1.0)
sol=solvers.qp(Q, p, G, h, A, b)
plpy.notice(sol['x'])
return [x for x in sol['x']]
$$ LANGUAGE plpythonu;
```
