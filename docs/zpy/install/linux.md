# Install Developer Environment on Linux

First clone the zpy repository:

```
mkdir -p $HOME/zumolabs && cd $HOME/zumolabs
git clone https://github.com/ZumoLabs/zpy.git zpy
```

Set the following environment variables:

```
export ZPY_SRC_PATH="$HOME/zumolabs/zpy"
export BLENDER_VERSION="2.93"
export BLENDER_VERSION_FULL="2.93.0"
export BLENDER_PATH="$HOME/blender-${BLENDER_VERSION_FULL}-linux-x64/${BLENDER_VERSION}"
export BLENDER_LIB_PY="${BLENDER_PATH}/python/lib/python3.9"
export BLENDER_BIN_PY="${BLENDER_PATH}/python/bin/python3.9"
export BLENDER_BIN_PIP="${BLENDER_PATH}/python/bin/pip3"
```

**NOTE** The `BLENDER_PATH` variable might change depending on where you downloaded your Blender. Change the path accordingly.

Install additional Python dependencies using Blender Python's pip:

```
${BLENDER_BIN_PY} -m ensurepip
${BLENDER_BIN_PIP} install --upgrade pip
${BLENDER_BIN_PIP} install -r ${ZPY_SRC_PATH}/requirements.txt
```

If you are setting up a development environment it will be easier to symlink the zpy pip module directly into the Blender python library. This can be achieved with something like:

```
ln -s ${ZPY_SRC_PATH}/zpy ${BLENDER_LIB_PY}/site-packages/
mkdir -p ~/.config/blender/${BLENDER_VERSION}/scripts/addons
ln -s ${ZPY_SRC_PATH}/zpy_addon ~/.config/blender/${BLENDER_VERSION}/scripts/addons/zpy_addon
```

