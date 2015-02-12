# Motion Google Drive Uploader and Pushover Notifier

## Introduction
Motion Uploader and Notifier allows you to upload captures, send email and pushover notification from Motion. Motion is a program that monitors the video signal from cameras. It is able to detect if a significant part of the picture has changed; in other words, it can detect motion.

## How to configure
Edit `motionuploader.ini`. Provide your Gmail address and password. If you want pushover notifications you will need to provide the `token` and `user key` as well. You can get a token from [Pushover Apps and Api](https://pushover.net/apps) and user key from your pushover app or [Pushover Home Page](https://pushover.net/) .

## Two-Factor-Authentication
If you have enabled two factor authentication in your Google account, then you need to provide `app password` instead of your regular password. This can be generated at [Google App Passwords page](https://security.google.com/settings/security/apppasswords)

## Configuring with Motion
Make the script executable and install the python (2.7) dependencies:
```sh
$ chmod +x motionuploader.py
$ pip install gdata
```
You can configure it at any of the motion event you find suitable. You will need to add the configuration in your motion config file `~/.motion/motion.conf` or `/etc/motion/motion.conf`
```ini
[motion_event_name] [/path/to/motionuploader.py]  [/path/to/ini/file]
```
For example the following line configures it `on_picture_save` and `on_movie_end`.
```sh
on_picture_save ~/.motion/motionuploader.py ~/.motion/motionuploader.ini %f
on_movie_end ~/.motion/motionuploader.py ~/.motion/motionuploader.ini %f
```
>Currently its a python 2.7 script. I am planning to release a Python 3.x script as well. Based on
>the original work by [Jermy Blythe](http://jeremyblythe.blogspot.in/).
