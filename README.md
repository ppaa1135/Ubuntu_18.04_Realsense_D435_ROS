# Ubuntu-18.04 Realsense

* ### https://github.com/IntelRealSense/librealsense/blob/master/doc/distribution_linux.md

* ### Installing the packages 항목을 보고 설치

  ``` 
  sudo apt-key adv --keyserver keys.gnupg.net --recv-key F6E65AC044F831AC80A06380C8B3A55A6F3EFCDE || sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-key
  sudo add-apt-repository "deb http://realsense-hw-public.s3.amazonaws.com/Debian/apt-repo bionic main" -u
  sudo apt-get install librealsense2-dkms
  sudo apt-get install librealsense2-utils
  sudo apt-get install librealsense2-dev
  sudo apt-get install librealsense2-dbg
  realsense-viewer (리얼센스 패키지 설치 확인하기)
  ```

* ### Install Realsense ROS - 리얼센스 ROS 패키지 설치하기

  catkin workspace 만들기 (ROS 설치되어 있으면 스킵) 
  ```
  mkdir -p ~/catkin_ws/src
  cd ~/catkin_ws/src/
  ```  
  패키지 다운로드
  ```
  git clone https://github.com/IntelRealSense/realsense-ros.git
  cd realsense-ros/
  git checkout `git tag | sort -V | grep -P "^\d+\.\d+\.\d+" | tail -1`
  cd ..
  ```
  
  패키지 설치
  ```
  catkin_init_workspace
  cd ..
  catkin_make clean
  catkin_make -DCATKIN_ENABLE_TESTING=False -DCMAKE_BUILD_TYPE=Release
  catkin_make install
  echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc
  source ~/.bashrc
  ```
  
  ddynamic_reconfigure 에러나면 
  ```
  cd src
  git clone https://github.com/pal-robotics/ddynamic_reconfigure/tree/kinetic-devel
  cd ..
  ```
  
  D435 
  
  ```
  roslaunch realsense2_camera rs_camera.launch
  ```
  
