ARG from

FROM ${from}

ENV DEBIAN_FRONTEND = noninteractive

# Timezone Configuration

ENV TZ=Europe/Berlin
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN apt-get update && apt-get install -y tzdata

# Local install

RUN apt update && apt install locales
RUN locale-gen en_US en_US.UTF-8
RUN update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
RUN export LANG=en_US.UTF-8

#RUN add-apt-repository -y universe, ppa:deadsnakes/ppa


RUN apt-get update && apt-get install -y apt-utils \
                                         software-properties-common \
                                         lsb-release \
                                         mesa-utils \
                                         gnupg2 \
                                         net-tools \
                                         build-essential \
                                         wget \
                                         unzip \
                                         curl \
                                         git \
                                         mc \
                                         vim \
                                         gedit \
                                         python2 \
                                         python-dev \
                                         python3-pip \
                                         gcc \
                                         gfortran \
                                         libopenblas-dev \ 
					                          cmake


RUN curl https://bootstrap.pypa.io/pip/2.7/get-pip.py --output get-pip.py

RUN python2 get-pip.py                                        





RUN apt update && apt upgrade -y

RUN pip3 install -U rosinstall msgpack empy defusedxml netifaces keras==2.1.5 catkin_tools tensorboard scipy shapely tabulate mpldatacursor svgpath2mpl numpy==1.21.0 pyqtgraph scikit-build 


RUN pip3 install rcognita[SIPPY]

RUN pip install --ignore-installed --upgrade https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-1.8.0-cp27-none-linux_x86_64.whl

# Install ROS desktop and Gazebo

RUN echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list
RUN curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | apt-key add -

RUN apt-get update && apt-get install -y ros-noetic-desktop-full \
   ros-noetic-joy ros-noetic-teleop-twist-joy \
   ros-noetic-teleop-twist-keyboard ros-noetic-laser-proc \
   ros-noetic-rgbd-launch ros-noetic-rosserial-arduino \
   ros-noetic-rosserial-python ros-noetic-rosserial-client \
   ros-noetic-rosserial-msgs ros-noetic-amcl ros-noetic-map-server \
   ros-noetic-move-base ros-noetic-urdf ros-noetic-xacro \
   ros-noetic-compressed-image-transport ros-noetic-rqt* ros-noetic-rviz \
   ros-noetic-gmapping ros-noetic-navigation ros-noetic-interactive-markers \
   ros-noetic-dynamixel-sdk \
   ros-noetic-turtlebot3-msgs \
   ros-noetic-turtlebot3




RUN echo 'export ROS_DOMAIN_ID=30 #TURTLEBOT3' >> ~/.bashrc                    
RUN echo "source /opt/ros/noetic/setup.bash"  >> ~/.bashrc 

ENV source /opt/ros/noetic/setup.bash


RUN echo 'source ~/../turtlebot3_ws/devel/setup.bash' >> ~/.bashrc \
   && echo 'source ~/../turtlebot3_ws/devel/setup.bash' >> ~/.bashrc \
   && echo 'export GAZEBO_MODEL_PATH=$GAZEBO_MODEL_PATH:~/../turtlebot3_ws/src/turtlebot3/turtlebot3_simulations/turtlebot3_gazebo/models' >> ~/.bashrc \
   && echo 'export TURTLEBOT3_MODEL=burger' >> ~/.bashrc \
   && echo 'export ROS_MASTER_URI=http://192.168.50.62:11311' >> ~/.bashrc \
   && echo 'export ROS_HOSTNAME=192.168.50.62' >> ~/.bashrc

# Need to change your IP in the variables $ROS_MASTER_URI and $ROS_HOSTNAME
