## ws_moveit2
### ROS2 MOVEIT2  설치와 관련하여 방법을 설명하는 Repository 입니다.

#### 우선 ros2 에 moveit2를 설치시 네트워크 문제와 인증 문제가 발생하여 이문서를 만듭니다.

#### 사용방법은 아래와 같습니다.
#### ws_moveit2.zip 파일을  다운로드 합니다.
#### virtual box 의 ubuntu 22.04 /home/<user id 폴더> 에 파일을 옮깁니다.

#### 압축을 풉니다.
#### 아래와 같이 폴더가 정리됩니다.

/home/<user_id_folder>/ws_moveit2/src
src 폴더에는 moveit2를 실행하기 위한 폴더와 파일들이 들어 있습니다.
별도로  github에서 받으실 필요가 없습니다.

### 아래 명령어를 터미널 창에 입력하여 설치를 진행합니다.
---
#### 폴더를 이동한다.
  cd ~

###  기존에 설치된 패키지가 있는 경우 삭제한다.

  sudo apt remove ros-humble-moveit*       

  source /opt/ros/humble/setup.bash 

  sudo apt install python3-rosdep 

  sudo rosdep init 

  rosdep update 

  sudo apt update 

  sudo apt dist-upgrade 


  sudo apt install python3-colcon-common-extensions 

  sudo apt install python3-colcon-mixin 

  colcon mixin add default https://raw.githubusercontent.com/colcon/colcon-mixin-repository/master/index.yaml 

  colcon mixin update default

  sudo apt update 

  rosdep install -r --from-paths . --ignore-src --rosdistro $ROS_DISTRO –y

  cd ~/ws_moveit2 

  colcon build --mixin release

#### colcon build 시에 빌드가 제대로 안되는 경우가 발생합니다. 그럴경우 위의 명령어를 다시 입력하여 
#### 빌드가 완료될때까지 colcon build 를 실행합니다. 

  source install/setup.bash

  ros2 launch moveit2_tutorials demo.launch.py rviz_config:=panda_moveit_config_demo_empty.rviz

---
#### 이제 rviz2가 실행이 되고  moveit2를 사용하여 panda 로봇이 보여집니다.
교재를 따라 로봇의 움직임을 제어할수 있습니다.

