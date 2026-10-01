FROM pytorch/pytorch:latest

RUN apt-get update && apt-get install -y --no-install-recommends \
        software-properties-common \
        build-essential \
        curl \
        git \# Source - https://stackoverflow.com/q/79791649
# Posted by PChemGuy, modified by community. See post 'Timeline' for change history
# Retrieved 2026-10-01, License - CC BY-SA 4.0

DEPRECATION: Building 'ffcv' using the legacy setup.py bdist_wheel mechanism, which will be removed in a future version. pip 25.3 will enforce this behaviour change. A possible replacement is to use the standardized build interface by setting the `--use-pep517` option, (possibly combined with `--no-build-isolation`), or adding a `pyproject.toml` file to the source tree of 'ffcv'. Discussion can be found at https://github.com/pypa/pip/issues/6334
  error: subprocess-exited-with-error
  
  python setup.py bdist_wheel did not run successfully.
  exit code: 1
  
  [32 lines of output]
  G:\dev\AIPY\Anaconda\Lib\site-packages\setuptools\dist.py:483: SetuptoolsDeprecationWarning: Cannot find any files for the given pattern.
  !!
  
          ********************************************************************************
          Pattern 'LICENSE.txt' did not match any files.
  
          By 2026-Mar-20, you need to update your project and remove deprecated calls
          or your builds will no longer be supported.
          ********************************************************************************
  
  !!
    for path in sorted(cls._find_pattern(pattern, enforce_match))
  libffcv.cpp
  ./libffcv/libffcv.cpp(38): warning C4244: 'argument': conversion from 'int64_t' to 'int', possible loss of data
  ./libffcv/libffcv.cpp(38): warning C4244: 'argument': conversion from 'int64_t' to 'int', possible loss of data
  ./libffcv/libffcv.cpp(39): warning C4244: 'argument': conversion from 'int64_t' to 'int', possible loss of data
  ./libffcv/libffcv.cpp(39): warning C4244: 'argument': conversion from 'int64_t' to 'int', possible loss of data
  ./libffcv/libffcv.cpp(40): warning C4244: 'argument': conversion from 'int64_t' to 'int', possible loss of data
  ./libffcv/libffcv.cpp(40): warning C4244: 'argument': conversion from 'int64_t' to 'int', possible loss of data
  ./libffcv/libffcv.cpp(40): warning C4244: 'argument': conversion from 'int64_t' to 'int', possible loss of data
  ./libffcv/libffcv.cpp(40): warning C4244: 'argument': conversion from 'int64_t' to 'int', possible loss of data
  ./libffcv/libffcv.cpp(49): warning C4244: 'argument': conversion from 'int64_t' to 'long', possible loss of data
  ./libffcv/libffcv.cpp(98): warning C4244: 'argument': conversion from '__uint64_t' to 'unsigned long', possible loss of data
  ./libffcv/libffcv.cpp(102): warning C4244: '=': conversion from '__uint64_t' to 'unsigned long', possible loss of data
     Creating library build\temp.win-amd64-cpython-311\Release\libffcv\_libffcv.cp311-win_amd64.lib and object build\temp.win-amd64-cpython-311\Release\libffcv\_libffcv.cp311-win_amd64.exp
  libffcv.obj : error LNK2001: unresolved external symbol tjTransform
  libffcv.obj : error LNK2001: unresolved external symbol tjInitDecompress
  libffcv.obj : error LNK2001: unresolved external symbol tjDecompress2
  libffcv.obj : error LNK2001: unresolved external symbol tjFree
  libffcv.obj : error LNK2001: unresolved external symbol tjInitTransform
  build\lib.win-amd64-cpython-311\ffcv\_libffcv.cp311-win_amd64.pyd : fatal error LNK1120: 5 unresolved externals
  error: command 'G:\\dev\\MSBuildTools\\VC\\Tools\\MSVC\\14.44.35207\\bin\\HostX64\\x64\\link.exe' failed with exit code 1120
  [end of output]
  
  note: This error originates from a subprocess, and is likely not a problem with pip.
  ERROR: Failed building wheel for ffcv
error: failed-wheel-build-for-install

Failed to build installable wheels for some pyproject.toml based projects

ffcv

        ffmpeg

RUN conda update conda && \
        conda create -n ffcv python=3.9 \
        cupy \
        pkg-config \
        compilers \
        libjpeg-turbo \
        opencv \
        pytorch \
        torchvision \
        cudatoolkit=11.3 \
        numba -c pytorch -c conda-forge 

RUN echo "source activate" >> ~/.bashrc
RUN echo "conda activate ffcv" >> ~/.bashrc

RUN git clone https://github.com/libffcv/ffcv.git  

RUN conda run -n ffcv pip install ffcv

# To test:
# 1- build the Dockerfile (e.g. docker build -t ffcv .)
# 2- login to the docker container (e.g. docker run -it --gpus all ffcv bash)
# 3- cd ffcv/examples/cifar
# 4- bash train_cifar.sh
