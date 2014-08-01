# tuxpaint-box
This is a small fun project I made for my five year old daughter. She loves Tux Paint, a very simple paint program. After using my other Linux boxes for that, I created a Vagrantfile to give her an own Ubuntu box with just that application in it.

![tux paint](pics/tuxpaint.png)

## Create the box
The box is tested with both VirtualBox and VMware Fusion, but should work with VMware Workstation as well. The base box is retrieved from the Vagrant Cloud, so you only need Vagrant and one of the hypervisors.

```bash
git clone https://github.com/StefanScherer/tuxpaint-box
cd tuxpaint-box
vagrant up
```

## Start Tux Paint
Log into the newly created Ubuntu 14.04 desktop box, the password is `vagrant` (same as the username). Click on the Ubuntu search icon in the launcher (top left) and enter `tux`. An icon with Tux Paint should appear. Click on that icon. You may lock the icon to the launcher.

Have fun!

## Saved images
After I have done a `vagrant destroy -f` one evening and received complains that the paintings from yesterday have been lost, I improved the provisioning. The tux paint folder will be created in the shared folder, so the saved pictures are stored on the host machine in the folder `saved`.

So it is save to do a `vagrant destory -f` to save disk space and do a `vagrant up` if the tux painter will be needed again.

## Known Issues
* I have to set the auto login, so the desktop will appear automatically on a `vagrant up`.
* I have to pin the Tux Paint icon to the dock, so it will be easier for kids to start the paint program.

## Next steps
Perhaps I try this in a Dockerfile as well in the future.

# MIT License
