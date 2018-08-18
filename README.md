huaweicloud-cloud-init
================
# Linux cloud-init support #
----------------------------
Package provides configuration and customization of cloud instance.
- See documentation at http://cloudinit.readthedocs.org/

For information on how to contribute, read:
- http://cloudinit.readthedocs.io/en/latest/topics/hacking.html

#### Download package for cloud-init ####
- https://github.com/huaweicloud/huaweicloud-cloud-init/archive/cloud-init-0.7.6.zip
- https://github.com/huaweicloud/huaweicloud-cloud-init/archive/cloud-init-0.7.9.zip
 
#### Instruction for install package for cloud-init ####
1.  Download the cloud-init ZIP file and transfer the ZIP file to an ECS instance.
    The instruction below will use /tmp/CLOUD-INIT as the workspace for installing the cloud-init package.
    - wget https://github.com/huaweicloud/huaweicloud-cloud-init/archive/cloud-init-0.7.6.zip
    - mkdir /tmp/CLOUD-INIT
    - cp cloud-init-0.7.6.zip /tmp/CLOUD-INIT
    - cd /tmp/CLOUD-INIT
 
2.  Extract the cloud-init ZIP file
    - unzip cloud-init-0.7.6.zip

3.  Install the cloud-init package.

    CentOS|RHEL|Oracle6.x/SLES11.x：
    - python setup.py build
    - python setup.py install --init-system sysvinit

    CentOS|RHEL|Oracle7.x/SLES12.x：
    - python setup.py build
    - python setup.py install --init-system systemd

    RHEL does not have a syslog user by default, you have to add it manually.
    - useradd syslog
    
    System_info section, replace distro: ubuntu with distro: rhel or distro: sles according to the distribution you will use.
   
    Ensure all cloud-init services are in active status by issuing the following commands.
    CentOS|RHEL|Oracle6.x/SLES11.x：
    - chkconfig cloud-init-local on
    - chkconfig enable cloud-init on
    - chkconfig enable cloud-config on
    - chkconfig enable cloud-final on

    CentOS|RHEL|Oracle7.x/SLES12.x：
    - systemctl enable cloud-init-local.service
    - systemctl enable cloud-init.service
    - systemctl enable cloud-config.service
    - systemctl enable cloud-final.service

4.  How to check cloud-init package if install success.
    - cloud-init -v
      /usr/lib64/python2.6/site-packages/cryptography/__init__.py:26: DeprecationWarning: Python 2.6 is no longer supported by the Python core team, please upgrade your Python. A future version of cryptography will drop support for Python 2.6 DeprecationWarning
      cloud-init 0.7.6
      
    - cloud-init init --local
      /usr/lib64/python2.6/site-packages/cryptography/__init__.py:26: DeprecationWarning: Python 2.6 is no longer supported by the Python core team, please upgrade your Python. A future version of cryptography will drop support for Python 2.6 DeprecationWarning
      Cloud-init v. 0.7.6 running 'init-local' at Wed, 29 Mar 2017 04:43:52 +0000. Up 7486345.46 seconds.
      
