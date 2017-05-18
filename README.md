== README

The goal of this app is to make it trivial to demodulate common RF signals, and provide a digital worksheet for your reverse engineering efforts.


== INSTALLATION (Instructions tested on Kali Rolling 2.0 - may be slightly different for other Operating Systems)

```bash
# Installing RVM & Ruby 2.2.2
gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
\curl -sSL https://get.rvm.io | bash

source /etc/profile.d/rvm.sh
echo "source /etc/profile.d/rvm.sh" >> ~/.bashrc

rvm install 2.2.2

# Installing Inspectrum (instructions from: https://github.com/miek/inspectrum/wiki/Build)

git clone https://github.com/miek/inspectrum.git
cd inspectrum
sudo apt-get install qt5-default libfftw3-dev cmake pkg-config
mkdir build
cd build
cmake ..
make
sudo make install

# Installing DSpectrumGUI (this app)

git clone https://github.com/tresacton/dspectrumgui.git
cd dspectrumgui
bundle
rake db:setup && rake db:migrate && rake db:seed

# Launcing DSpectrumGUI

rails s -p 3001

echo "You can now open a browser and navigate to http://localhost:3001/"

```

## Default Credentials (and how to change them)

Username: user@example.com
Password: password

To change them:

```bash
cd dspectrumgui
rails c
u = User.last
u.email = "you@somewhere.com"
u.password = u.password_confirmation = "YourSecurePassword"
u.save!
```


## Security Considerations

Despite being a security researcher, I have given zero thought to the security of this app. I will go over it from a security perspective later (then update this text), so keep that in mind.
Don't expose the app to the internet.
Don't keep the server running while you're not using it (i.e. do a [ctrl][c] in the window where you ran the "rails s -p xxxx" command).

