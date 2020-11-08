# ESP32S2
### ESP32 S2 ARDUINO GUIDE
Hello, I have run into problems running esp32 s2. This guide will be for ubunutu.
```NAME="Ubuntu"
VERSION="20.04.1 LTS (Focal Fossa)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 20.04.1 LTS"
VERSION_ID="20.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=focal
UBUNTU_CODENAME=focal

```

Skip this step if you have arduino installed. 
follow this guide https://www.arduino.cc/en/Guide/Linux

now install Python 2.7 (this is where it gets tricky)
from this guide https://linuxize.com/post/how-to-install-pip-on-ubuntu-20.04/
enable universe repo
```
sudo add-apt-repository universe
```
update
```
sudo apt update 
sudo apt install python2
```
download pip2 for python 2.7. pip2 will not install from apt-get install pip, as it is removed...
```
curl https://bootstrap.pypa.io/get-pip.py --output get-pip.py
```
install
```
sudo python2 get-pip.py
```

now install pyserial with python 2.7
```
sudo python2.7 -m pip install pyserial
```

download the esp32s2 branch from
https://github.com/espressif/arduino-esp32/tree/esp32s2
download with clone or zip. (I used zip to ensure it was the esp32 s2 branch not the standard esp32, and manually moved the version into ~/Arduino/hardware/espressif ) you can try to git clone and includes set up. yes it will install python 3, I am not sure if it will run on python 2. which is a requirement for arduino not the esptools setup.
```
sudo usermod -a -G dialout $USER && \
sudo apt-get install git && \
wget https://bootstrap.pypa.io/get-pip.py && \
sudo python get-pip.py && \
sudo pip install pyserial && \
mkdir -p ~/Arduino/hardware/espressif && \
cd ~/Arduino/hardware/espressif && \
git clone -b esp32s2 https://github.com/espressif/arduino-esp32.git esp32s2 && \
cd esp32 && \
git submodule update --init --recursive && \
cd tools && \
python3 get.py
```

now run arduino ide using the shortcut created from the install.sh from the arduino tar download. Do not use arduino from the app store.

for an example to get the neopixel running on your esp32 s2
add the library

https://github.com/adafruit/Adafruit_NeoPixel

change the led pin to 18
```
#define LED_PIN    18
```
Then run the code.
