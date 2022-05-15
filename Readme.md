# Build Numpy

This repo builds Numpy via GitHub Actions with the versions of:

* Windows 10 x64
* Python 3.11
* Numpy master && Cython master
* No Blas

## Remarks

* setuptools>61时无法用pip wheel .构建，也许可用python setup.py bdist_wheel，但按计划未来会用别的build system probably meson
