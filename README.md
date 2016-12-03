Assignment Solutions for the Udacity Deep Learning class with TensorFlow
===========================================================

Course information can be found at https://www.udacity.com/course/deep-learning--ud730


I also setup a Public AMI on Amazon AWS that I used for the tutorial.
AMI Name: DeepMind DeepQ Atari 11_25
Instance Type: g2.2xlarge

The AMI has GPU Configured TensorFlow, PyCharm, Website accessible Jupyter Notebook, CUDA Toolkit 8, OpenCV, and Python installed. 

Enter the following in Advanced Details -> User Data during Step 3 Configure Instance when launching an EC2 server.

'''
#!/bin/bash
echo "ubuntu:password" | chpasswd
cd /home/ubuntu/jupyter
git clone https://github.com/chrisbll971/udacity_deep_learning_course.git
chown -R ubuntu:ubuntu /home/ubuntu/jupyter/udacity_deep_learning_course
jupyter notebook --certfile=/home/ubuntu/certs/mycert.pem --no-browser --ip="*" > /tmp/ipynb.out 2>&1 &
'''

This will make the Jupyter notebook accessible via web at https://ec2instanceip:8888/tree automatically on launch. It will also make the instance open to Windows Remote Desktop. The first time you login via Windows Remote Desktop it will fail, but the second time it will work.

Windows Remote Desktop
Username: ubuntu
Password: password
