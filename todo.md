# To-do

## ROS support

- [ ] add catkin wrapper
- [ ] add related ROS messages and services
  - Ref:
    1. <https://github.com/leggedrobotics/open3d_slam>
    2. <https://github.com/nachovizzo/vdbfusion_ros>
- [ ] add RVIZ visualization

## Installation deps -  'sh script/tools/install_dep_lib.sh'

- [ ] exisiing `‘dependent_libs’`

```shell
mkdir: cannot create directory ‘dependent_libs’: File exists
```

- [x] `script/tools/install_dep_lib.sh: 23: function: not found`

change shell function to more general fornat

```shell
# original
function checkinstall-auto {
  name=$1
  version=$2
  shift 2
  checkinstall -y --install=no --fstrans=yes --nodoc --exclude=/home --pkgname="$name" --pkgversion="$version" "$@"
  sudo apt install -y ./"$name"_*.deb
}

# current
checkInstallAuto() {
  name=$1
  version=$2
  shift 2
  checkinstall -y --install=no --fstrans=yes --nodoc --exclude=/home --pkgname="$name" --pkgversion="$version" "$@"
  sudo apt install -y ./"$name"_*.deb
}
```

- [x] cannot find checkinstall executable

```shell
script/tools/install_dep_lib.sh: line 27: checkinstall: command not found
```

FIXED: `sudo apt install checkinstall`

- [x] possible make error with sophus -> set tag as `v1.0.0`

```shell
In file included from /home/he/projects/mulls/dependent_libs/Sophus/test/ceres/tests.hpp:5,
                 from /home/he/projects/mulls/dependent_libs/Sophus/test/ceres/test_ceres_so3.cpp:5:
/home/he/projects/mulls/dependent_libs/Sophus/sophus/ceres_manifold.hpp:3:10: fatal error: ceres/manifold.h: No such file or directory
    3 | #include <ceres/manifold.h>
      |          ^~~~~~~~~~~~~~~~~~
compilation terminated.
make[2]: *** [test/ceres/CMakeFiles/test_ceres_so3_local_parameterization.dir/build.make:76: test/ceres/CMakeFiles/test_ceres_so3_local_parameterization.dir/test_ceres_so3.cpp.o] Error 1
make[1]: *** [CMakeFiles/Makefile2:568: test/ceres/CMakeFiles/test_ceres_so3_local_parameterization.dir/all] Error 2
make[1]: *** Waiting for unfinished jobs....
In file included from /home/he/projects/mulls/dependent_libs/Sophus/test/ceres/tests.hpp:5,
                 from /home/he/projects/mulls/dependent_libs/Sophus/test/ceres/test_ceres_se3.cpp:5:
/home/he/projects/mulls/dependent_libs/Sophus/sophus/ceres_manifold.hpp:3:10: fatal error: ceres/manifold.h: No such file or directory
    3 | #include <ceres/manifold.h>
      |          ^~~~~~~~~~~~~~~~~~
compilation terminated.
make[2]: *** [test/ceres/CMakeFiles/test_ceres_se3_local_parameterization.dir/build.make:76: test/ceres/CMakeFiles/test_ceres_se3_local_parameterization.dir/test_ceres_se3.cpp.o] Error 1
make[1]: *** [CMakeFiles/Makefile2:620: test/ceres/CMakeFiles/test_ceres_se3_local_parameterization.dir/all] Error 2
In file included from /home/he/projects/mulls/dependent_libs/Sophus/test/ceres/tests.hpp:5,
                 from /home/he/projects/mulls/dependent_libs/Sophus/test/ceres/test_ceres_rxso3.cpp:5:
/home/he/projects/mulls/dependent_libs/Sophus/sophus/ceres_manifold.hpp:3:10: fatal error: ceres/manifold.h: No such file or directory
    3 | #include <ceres/manifold.h>
      |          ^~~~~~~~~~~~~~~~~~
compilation terminated.
make[2]: *** [test/ceres/CMakeFiles/test_ceres_rxso3_local_parameterization.dir/build.make:76: test/ceres/CMakeFiles/test_ceres_rxso3_local_parameterization.dir/test_ceres_rxso3.cpp.o] Error 1
make[1]: *** [CMakeFiles/Makefile2:594: test/ceres/CMakeFiles/test_ceres_rxso3_local_parameterization.dir/all] Error 2
```

## Misc.

- [ ] add release tag in GitHub
