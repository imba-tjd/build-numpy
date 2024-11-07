# Build [Numpy](https://github.com/numpy/numpy)

This repo builds Numpy via GitHub Actions with the versions of:

* Windows X64
* Python 3.13
* Numpy 1.26.5
* MSVC
* No Blas (PR welcome)

You can download the build from GitHub Actions Artifacts (require login) or Release (if you trust me) or fork to your repo and use Actions to build.

Unzip, `pip install numpy-1.26.5-cp313-cp313-win_amd64.whl`.

## Remarks

The build command logic is from [azure-steps-windows.yml](https://github.com/numpy/numpy/blob/v1.26.5/azure-steps-windows.yml).

If you try to use [.github/workflows/wheels.yml](https://github.com/numpy/numpy/blob/v1.26.5/.github/workflows/wheels.yml), you will fail due to
  1. *This job was skipped*. **Solved** by prepending *[wheel build]* to the commit messages **and** removing *if: github.repository == 'numpy/numpy'*. This is mentioned on the top of wheels.yml.
  2. *cibuildwheel: No build identifiers selected. Here we go!*. This is due to old version of *pypa/cibuildwheel*. **Solved** by changing version ref tag to *main*.
  3. *End-of-central-directory signature not found...; unzip: cannot find zipfile directory in one of openblas_win-amd64.zip ..., period.* This is due to unaccessible to [openblas64_-v0.3.23-293-gc2f4bdbb-win_amd64-gcc_10_3_0.zip](https://anaconda.org/scientific-python-nightly-wheels/openblas-libs/v0.3.23-293-gc2f4bdbb/download/openblas64_-v0.3.23-293-gc2f4bdbb-win_amd64-gcc_10_3_0.zip) because the Anaconda website requires login and no one mentioned this.

```py
> import numpy; numpy.show_config()
{
  "Compilers": {
    "c": {
      "name": "msvc",
      "linker": "link",
      "version": "19.41.34123",
      "commands": "cl"
    },
    "cython": {
      "name": "cython",
      "linker": "cython",
      "version": "3.0.11",
      "commands": "cython"
    },
    "c++": {
      "name": "msvc",
      "linker": "link",
      "version": "19.41.34123",
      "commands": "cl"
    }
  },
  "Machine Information": {
    "host": {
      "cpu": "x86_64",
      "family": "x86_64",
      "endian": "little",
      "system": "windows"
    },
    "build": {
      "cpu": "x86_64",
      "family": "x86_64",
      "endian": "little",
      "system": "windows"
    }
  },
  "Build Dependencies": {
    "blas": {
      "name": "none"
    },
    "lapack": {
      "name": "dep2198563803488",
      "found": true,
      "version": "1.26.5",
      "detection method": "internal",
      "include directory": "unknown",
      "lib directory": "unknown",
      "openblas configuration": "unknown",
      "pc file directory": "unknown"
    }
  },
  "Python Information": {
    "path": "C:\\hostedtoolcache\\windows\\Python\\3.13.0\\x64\\python.exe",
    "version": "3.13"
  },
  "SIMD Extensions": {
    "baseline": [
      "SSE",
      "SSE2",
      "SSE3"
    ],
    "not found": [
      "SSSE3",
      "SSE41",
      "POPCNT",
      "SSE42",
      "AVX",
      "F16C",
      "FMA3",
      "AVX2",
      "AVX512F",
      "AVX512CD",
      "AVX512_SKX",
      "AVX512_CLX",
      "AVX512_CNL",
      "AVX512_ICL"
    ]
  }
}
```
