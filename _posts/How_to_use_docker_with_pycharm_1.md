---
title: >-
  How to use Docker in Phycharm - Container Configuration and Save it as a new
  Image
author: Sunyoung Yoo
tags: 'docker,phcharm,jetbrain,virtual environment,python'
categories: 'virtual environment,IDE'

---

<h3 id="how-to-use-docker-in-pycharm">How to use Docker in Pycharm</h3>
<p>I prefer terminal commands than GUI but when I use Pycharm… I had to know how to configure things with GUI.</p>
<h4 id="this-post-will-show-you-how-to">This post will show you how to</h4>
<ol>
<li>Start a Docker Container with the Docker Image</li>
<li>Configuration of a Docker Container</li>
<li>Save the Container as an Docker Image</li>
</ol>
<blockquote>
<p>OS: Linux, Debian, Ubuntu 16.04</p>
</blockquote>
<h4 id="start-a-docker-container-with-the-docker-image">1.  Start a Docker Container with the Docker Image</h4>
<p>ref: <a href="https://learnopencv.com/install-opencv-docker-image-ubuntu-macos-windows/">learnopencv.com/install-opencv-docker-image-ubuntu-macos-windows/</a><br>
I was trying to use OpenCV at the moment so let’s start with this page and I will assume you already have your Docker server running and you already have your Docker Image you want to use.</p>
<p><img src="https://blog.kakaocdn.net/dn/b583WL/btqT91KGmgV/wseLExxvYk69OM2fMd5ECK/img.png" alt=""></p>
<p>In the <code>8:Services</code> tab, I already added Docker service in Pycharm and named the daemon as <code>VideoAnalysis</code>.<br>
You can see the <code>spmallick/opencv-docker:opencv</code> docker image under the Images.</p>
<p><img src="https://blog.kakaocdn.net/dn/QkkwS/btqT91DU1JO/V6U1xm6ebukQy6CGMXrSck/img.png" alt=""></p>
<h3 id="configuration-of-a-docker-container">2. Configuration of a Docker Container</h3>
<p>If you right click the name of the image, you can see Create Container, and if you click this Pycharm will show you a Docker Configuration editor.<br>
So the Docker running command, can be configured in this editor.<br>
For example, if I want to run the command below,</p>
<pre><code>docker run -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=$DISPLAY -p 5000:5000 -p 8888:8888 -it spmallick/opencv-docker:opencv /bin/bash
</code></pre>
<p>This command can be saved as a configuration in Pycharm like the image below. *I also added mounting point with <code>Bind mounts</code> menu, so that I can use my scripts in it without saving it in the image.</p>
<p><img src="https://blog.kakaocdn.net/dn/pfofA/btqT0sDjMf0/x3Yu3iEfNpp04bcUt9hWs1/img.png" alt=""></p>
<p>Here, I named the docker container as <code>video_analysis</code>.  *<code>--device=/dev/video0:/dev/video0</code> tag will not work if you don’t have the camera.<br>
Now, you can apply this settings and run the container.<br>
The configuration editor can be found if you right click the name of the container.<br>
Multiple configurations for each image can be saved.</p>
<h3 id="save-the-container-as-an-docker-image">3. Save the Container as an Docker Image</h3>
<p>So here I wanted to change the image so that I don’t have to run trivial stuffs. You remember I put <code>/bin/bash</code> command to be executed in the configuration.<br>
This one means sourcing <code>~/.bashrc</code> in the container.<br>
Then I added some commands I would like to execute by default.<br>
In this case, I was going to use OpenCV-3-4-3 and it was configured in an virtual environment of the docker image. (I don’t understand why people use virtual environments in the virtual environments but… anyway…)<br>
So, I added a command line <code>workon OpenCV-3.4.3-py3</code> into <code>~/.bashrc</code> file like below.</p>
<pre><code>echo workon OpenCV-3.4.3-py3 &gt;&gt; ~/.bashrc
</code></pre>
<p>Then I want to save this container as an image and create a new container with the new image. The reference page shows you how to make a new image from the container more in detail but I will show you what I’ve done as well.<br>
ref: <a href="https://www.scalyr.com/blog/create-docker-image/">www.scalyr.com/blog/create-docker-image/</a></p>
<p><img src="https://blog.kakaocdn.net/dn/4nyVJ/btqT3thblza/s7U0Vajk4xz8HT61GQ4hq1/img.png" alt=""></p>
<p>All we need is the Container ID or the name of the Container name. I will just use the Container name.<br>
I was trying to find how I can do this with GUI but I couldn’t so I just used terminal to run this command below.</p>
<pre><code>docker commit video_analysis_test new_opencv_image
</code></pre>
<p><code>new_opencv_image</code> is the tag of the image.<br>
Now you can see the new image is added in the Docker server.</p>
<p><img src="https://blog.kakaocdn.net/dn/db2k2b/btqT90kH8ht/yAIUZBI2kKpVD4UynyCGjk/img.png" alt=""><br>
Finally, you can create a new container with this new image.</p>
<h3 id="to-be-continued...">To be continued…</h3>
<p>Next, I will show you how to use the virtual environment in the docker image as an interpreter of Pycharm.</p>
<blockquote>
<p>Written with <a href="https://stackedit.io/">StackEdit</a>.</p>
</blockquote>

