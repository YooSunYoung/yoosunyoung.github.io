---


---

<h1 id="how-to-use-docker-in-pycharm---2---python-interpreter">How to use Docker in Pycharm - 2 - Python Interpreter</h1>
<p>After making a docker server and docker container with the image you want to use, there is one more thing you should set up in order to use Pycharm debugger, interpreter and auto-completion.</p>
<blockquote>
<p>OS: Linux, Debian, Ubuntu 16.04</p>
</blockquote>
<p>You can specify the project Interpreter under <code>Project/Project Interpreter</code> tab in  <code>file/Settings</code>.<br>
Let’s click the gear icon next to the Project interpreter path like below and click <code>Add</code>.</p>
<p><img src="https://blog.kakaocdn.net/dn/TrKQf/btqT02RSoKb/pneJKo2DbjFVI2q0cyDzyk/img.png" alt=""><br>
If you go click the docker tab, you can see docker servers and images you can use.<br>
There is another post about running a docker server, creating a container, or new docker image from the container in this blog.</p>
<p><img src="https://blog.kakaocdn.net/dn/KGHt7/btqT7VxqmHe/24GbjHpM0IpK73nkJ4cLM1/img.png" alt=""><br>
Then it is pretty much done.<br>
However, there are some docker images which have virtual environments in them.<br>
Therefore you need to be careful for the <code>Python interpreter path</code>.<br>
In this case, I wanted to use the<br>
<code>OpenCV-3-4-3</code> environment in it.</p>
<p><img src="https://blog.kakaocdn.net/dn/v4uTj/btqT02xCM4D/vflu1To7u6tybufkacafJ1/img.png" alt=""><br>
Here is the docker container I created from the image I made last time.<br>
You can see we’re already in the virtual environment named <code>OpenCV-3.4.3-py3</code>.<br>
Still we need to specify the real python path it uses in Pycharm settings.<br>
I found the python path by</p>
<pre><code>which python
</code></pre>
<p><img src="https://blog.kakaocdn.net/dn/lcEz9/btqT8Iq4ccd/mCOydrZJiDWnFZfNiy3PKK/img.png" alt=""><br>
Now we have the path so let’s go back to the settings and insert the path like below.</p>
<p><img src="https://blog.kakaocdn.net/dn/cAmjG5/btqT6Hzs7N3/EjkgXclXo5qxHplDo6TyVk/img.png" alt=""><br>
Finally Pycharm can see all the packages we need.</p>
<p><img src="https://blog.kakaocdn.net/dn/TkOdx/btqT8HTfcOL/rQrqQbvNRKCL7vBLKdLYqk/img.png" alt=""><br>
However, for me, it took a several minutes until I can use the auto-completion in the IDE.</p>
<p>It is such a trivial thing but still hope it can be useful to someone :)</p>
<blockquote>
<p>Written with <a href="https://stackedit.io/">StackEdit</a>.</p>
</blockquote>

