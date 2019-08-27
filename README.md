## F0cal Device Farm Orb
This orb simplifies interactions with the F0cal device farm allowing you to 
run your builds on a variety of edge compute  devices including the Raspberry Pi, Jetson Nano, and the Jetson TX1 and TX2 and many more.


#### Example usage 
```
description: >
  This sample shows how to use the F0cal orb to run your tests on a Raspberry PI
usage:
  version: 2.1
  orbs:
    farm: f0cal/farm@1.0.0
  workflows:
    build-test-deploy:
      jobs:
        - farm/with_f0cal_device:
            name: test_device
            api_key: "<YOUR F0CAL API KEY >"
            device_type: raspi
            ssh_key_name: my_key_pair
            ssh_key_fingerprint: "<YOUR SSH_KEY FINGER PRINT>"
            steps:
              - farm/f0cal_run:
                  command: cmake .
              - farm/f0cal_run:
                  command: make
              - farm/f0cal_run:
                  command: ./bin/test
```              