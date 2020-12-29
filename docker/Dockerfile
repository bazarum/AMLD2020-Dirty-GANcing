# FROM nvidia/cuda
FROM nvidia/cuda:8.0-cudnn6-devel-ubuntu16.04

RUN apt-key adv --fetch-keys http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/7fa2af80.pub
RUN apt-get update 
RUN apt-get clean

RUN apt-get install -y rsync htop git openssh-server

RUN apt-get install python3-pip -y
RUN ln -s /usr/bin/python3 /usr/bin/python
RUN pip3 install --upgrade pip

#Torch and dependencies:
RUN pip install http://download.pytorch.org/whl/cu80/torch-0.4.0-cp35-cp35m-linux_x86_64.whl 
RUN pip install cffi 
# RUN pip install torchvision 
RUN pip install tensorboardX
RUN pip install tqdm scipy scikit-image colorama==0.3.7 
RUN pip install setproctitle pytz ipython

#vid2vid dependencies
RUN apt-get install libglib2.0-0 libsm6 libxrender1 -y
RUN pip install dominate requests opencv-python 

#vid2vid install
RUN git clone https://github.com/bazarum/MacDirty-GANcing.git /pose2vid
WORKDIR /pose2vid

RUN apt-get install -y python3-venv

RUN python -m venv env
CMD source env/bin/activate

RUN pip install -r requirements_1st.txt
RUN pip install -r requirements_2nd.txt
