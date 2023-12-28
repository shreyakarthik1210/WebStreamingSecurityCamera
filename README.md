# WebStreamingSecurityCamera
A live security camera built with Raspberry Pi.


Set up Raspberry Pi:

1. Install the Raspbian OS (Debian: Bookworm version) using the Raspberry Pi Imager application (https://www.raspberrypi.com/software/). Use cat /etc/os-release to check the current OS version. 
2. Set up the camera module and enable it. Use Vcgencmd get_camera to see if the camera is detected. Use Libcamera-still -o new.jpg to test whether the camera module works by taking a picture.
3. SSH into the pi using the user@IPAddress command. Get the IP address using ifconfig.
4. Utilize RealVNC viewer to create a remote desktop for the Raspberry Pi by entering the Raspberry Pi’s IP address. You might have to configure Pi to allow VNC viewer, do this using the sudo raspi-config command.

Website Setup:

1. Test camera.py is working (python3 camera.py)
2. Port forwarding with DuckDNS and Deco to get a domain name for the website and ensure the user gets to the website when using the public IP:
    a. Use command: echo url="https://www.duckdns.org/update?domains=birdieut.duckdns.org&token=36c498d4-bbb3-4c99-ae59-4d12456e0d21&ip=" | curl -k -o ~/duckdns/duck.log -K -
3. Gunicorn is a WSGI server specifically designed for Python Flask applications. Set up gunicorn: 
    a. Install gunicorn: pip3 install gunicorn
    b. Create wsgi.app file
    c. Then: gunicorn --bind 0.0.0.0:5000 wsgi:app 
4. Set up nginx (reverse proxy):
    a. apt install nginx
    b. cd /etc/nginx
    c. nano nginx.conf 
    d. service nginx restart



Architecture Diagram:
![WebStreaming_Security_Architecture](https://github.com/shreyakarthik1210/WebStreamingSecurityCamera/assets/52420053/c9f7fe22-335d-43ed-9b3b-74e5efbeb291)



References:
1. DuckDNS: https://www.youtube.com/watch?v=s-66gmIHoyE
2. Nginx: https://www.youtube.com/watch?v=KWIIPKbdxD0
3. Reference Git Hub Repo: https://github.com/avseng/LiveStramingCamera 
