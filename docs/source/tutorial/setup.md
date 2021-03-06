# Setup guide (for Mac / Linux)

For Windows users, jump to [setup_windows](../setup_windows.html)

## Downloading code
```
git clone https://github.com/mil-tokyo/webdnn
```

Once you learn how to use WebDNN and want to use it in your project, [npm](../../tips/npm.html) and [pip](../../tips/pip.html) packages may be useful (please note that they does not contain examples).

## Installing WebGPU environment
WebDNN runs fastest on browsers which support WebGPU. Currently, only Safari 11 on macOS supports it ([config needed](../../tips/enable_webgpu_macos.html)).

If you don't have such environment, WebGL and WebAssembly backend can be used.
It is supported by most modern browsers.
(Note: IE does not support WebAssembly, but asm.js code is automatically generated along with WebAssembly code, and gives similar performance.)

## Installing python package
This framework requires python3.6+. Some packages need to be installed as precondition.
1.For Mac: need to install `numpy`;
2.For Linux: need to install `setuptools`;

```
pip3 install numpy setuptools
```

```
cd webdnn
python3 setup.py install
```

This will install `webdnn`.

If you want to convert models of Caffe or Chainer, install chainer package.

```
pip install chainer
```

(Currently, tested with `chainer==2.0` and  `chainer==1.23`)

## Installing Emscripten and Eigen
If you want to enable WebAssembly backend, em++ command from [Emscripten](https://github.com/kripken/emscripten) is required. You can skip this section if you try WebGPU backend only.

Before setting up Emscripten which supports WebAssembly, `brew/apt-get install cmake` need to be performed at first.

```
git clone https://github.com/juj/emsdk.git
cd emsdk
./emsdk install sdk-incoming-64bit binaryen-master-64bit
./emsdk activate sdk-incoming-64bit binaryen-master-64bit
```
(see also http://webassembly.org/getting-started/developers-guide/ )

To enable em++ command, you need to type command on the shell.

```
source ./emsdk_env.sh
```

[Eigen](http://eigen.tuxfamily.org) is needed as the library.

```
wget http://bitbucket.org/eigen/eigen/get/3.3.3.tar.bz2
tar jxf 3.3.3.tar.bz2
```

To enable Eigen to be included on compile, you need to type command on the shell.

```
export CPLUS_INCLUDE_PATH=$PWD/eigen-eigen-67e894c6cd8f
```

## Notes on python environment
Emscripten requires `python2` command, you need to setup python environment which `python` (or `python3`) is python 3.6+ and `python2` is python 2.7. [pyenv](https://github.com/pyenv/pyenv) may help to setup such environment ([see also](https://github.com/pyenv/pyenv/blob/master/COMMANDS.md#pyenv-global-advanced)).
