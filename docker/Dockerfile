# FROM nvidia/cuda
FROM nvidia/cuda:11.1-cudnn8-runtime-ubuntu20.04


RUN apt-key adv --fetch-keys http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/7fa2af80.pub
RUN apt-get update 
RUN apt-get clean

RUN apt-get install -y rsync 
RUN apt-get install -y htop 
RUN apt-get install -y git 
RUN bash -c "export DEBIAN_FRONTEND=noninteractive && apt-get install -y openssh-server"

RUN apt-get install -y python3-venv
RUN python3 -m venv env
CMD source env/bin/activate

RUN apt-get install python3-pip -y
RUN pip3 install --upgrade pip
RUN ln -s /usr/bin/python3 /usr/bin/python

#Torch and dependencies:
# JT RUN pip3 install http://download.pytorch.org/whl/cu80/torch-0.4.0-cp35-cp35m-linux_x86_64.whl 
# JT RUN pip3 install torch==1.7.1+cu110 torchvision==0.8.2+cu110 torchaudio===0.7.2 -f https://download.pytorch.org/whl/torch_stable.html
RUN pip3 install cffi 

# JT RUN pip install torchvision 
RUN pip3 install tensorboardX
RUN pip3 install tqdm scipy scikit-image colorama==0.3.7 
RUN pip3 install setproctitle pytz ipython

#vid2vid dependencies
RUN apt-get install libglib2.0-0 libsm6 libxrender1 -y
RUN pip3 install dominate requests opencv-python 

#vid2vid install
RUN git clone https://github.com/bazarum/MacDirty-GANcing.git /pose2vid
WORKDIR /pose2vid


RUN pip3 install -r requirements_1st.txt
RUN pip3 install -r requirements_2nd.txt
