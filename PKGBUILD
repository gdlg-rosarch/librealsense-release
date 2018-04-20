# Script generated with Bloom
pkgdesc="ROS - Library for capturing data from the Intel(R) RealSense(TM) F200, SR300, R200, LR200 and ZR300 cameras. This effort was initiated to better support researchers, creative coders, and app developers in domains such as robotics, virtual reality, and the internet of things. Several often-requested features of RealSense(TM); devices are implemented in this project, including multi-camera capture."
url='http://www.ros.org/wiki/RealSense'

pkgname='ros-kinetic-librealsense'
pkgver='1.12.1_1'
pkgrel=1
arch=('any')
license=('Apache License, Version 2.0'
)

makedepends=('dkms'
'libusbx'
'linux-headers'
'openssl'
'pkg-config'
'ros-kinetic-catkin'
)

depends=('dkms'
'libusbx'
'linux-headers'
'openssl'
)

conflicts=()
replaces=()

_dir=librealsense
source=()
md5sums=()

prepare() {
    cp -R $startdir/librealsense $srcdir/librealsense
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/kinetic/setup.bash ] && source /opt/ros/kinetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/kinetic \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

