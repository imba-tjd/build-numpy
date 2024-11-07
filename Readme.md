# Build [Numpy](https://github.com/numpy/numpy)

This repo builds Numpy via GitHub Actions with the versions of:

* Windows X64
* Python 3.13
* Numpy 1.26.5
* No Blas

You can download the build from GitHub Actions Artifacts (require login). Unzip, `pip install numpy-1.26.5-cp313-cp313-win_amd64.whl`.

The build command logic is from [azure-steps-windows.yml](https://github.com/numpy/numpy/blob/v1.26.5/azure-steps-windows.yml).

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
