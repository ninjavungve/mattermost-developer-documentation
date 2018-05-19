---
title: "Developer Setup"
date: 2017-08-20T11:35:32-04:00
weight: 2
subsection: Server
---

<div class="section" id="installing-developer-components-on-mac-os-x">
<span id="dev-setup"></span><h1>Environment Setup</h1>
<p>Set up your development environment for building, running, and testing Mattermost.</p>

<div class="tab">
  <button class="tablinks active" onclick="openTab(event, 'mac')">Mac OS X</button>
  <button class="tablinks" onclick="openTab(event, 'ubuntu')">Ubuntu 16.04</button>
  <button class="tablinks" onclick="openTab(event, 'windows')">Windows</button>
  <button class="tablinks" onclick="openTab(event, 'archlinux')">Archlinux</button>
  <button class="tablinks" onclick="openTab(event, 'centos')">CentOS 7</button>
</div>

<div id="mac" class="tabcontent" style="display: block;">
<ol class="arabic simple">
<li>If you are developing with the Docker container, install and configure Docker CE:</li>
</ol>
<blockquote>
<div><ol class="loweralpha simple">
<li>Follow the Docker installation instructions at <a class="reference external" href="https://docs.docker.com/docker-for-mac/">https://docs.docker.com/docker-for-mac/</a>.</li>
<li>Edit your <code class="docutils literal"><span class="pre">/etc/hosts</span></code> file to include the following line:</li>
</ol>
<blockquote>
<div><code class="docutils literal"><span class="pre">127.0.0.1</span>&#160;&#160;&#160;&#160; <span class="pre">dockerhost</span></code></div></blockquote>
</div></blockquote>
<ol class="arabic simple" start="2">
<li>Download and install Brew, which you’ll use for installing dependencies. Follow the Brew installation instructions at <a class="reference external" href="https://brew.sh/">https://brew.sh/</a></li>
<li>Install Node.js, Yarn, libpng, and Go:</li>
</ol>
<blockquote>
<div><code class="docutils literal"><span class="pre">brew</span> <span class="pre">install</span> <span class="pre">node</span> <span class="pre">yarn</span> <span class="pre">libpng</span> <span class="pre">go</span></code></div></blockquote>
<ol class="arabic simple" start="4">
<li>Set up your Go workspace:</li>
</ol>
<blockquote>
<div><ol class="loweralpha simple">
<li><code class="docutils literal"><span class="pre">mkdir</span> <span class="pre">~/go</span></code></li>
<li>Add the following lines to your <code class="docutils literal"><span class="pre">~/.bashprofile</span></code> file:</li>
</ol>
<blockquote>
<div><div class="highlight-bash"><div class="highlight"><pre><span></span><span class="nb">export</span> <span class="nv">GOPATH</span><span class="o">=</span><span class="nv">$HOME</span>/go
<span class="nb">export</span> <span class="nv">PATH</span><span class="o">=</span><span class="nv">$PATH</span>:<span class="nv">$GOPATH</span>/bin
<span class="nb">export</span> <span class="nv">PATH</span><span class="o">=</span><span class="nv">$PATH</span>:/usr/local/go/bin
<span class="nb">ulimit</span> -n <span class="m">8096</span>
</pre></div>
</div>
</div></blockquote>
<ol class="loweralpha simple" start="3">
<li>Reload your bash configuration.</li>
</ol>
<blockquote>
<div><code class="docutils literal"><span class="pre">source</span> <span class="pre">~/.bashprofile</span></code></div></blockquote>
</div></blockquote>
<ol class="arabic simple" start="5">
<li>Fork Mattermost on GitHub from <a class="reference external" href="https://github.com/mattermost/platform">https://github.com/mattermost/platform</a>.</li>
<li>Download the Mattermost code from your forked repository:</li>
</ol>
<blockquote>
<div><ol class="loweralpha simple">
<li>Create the directory for the code.</li>
</ol>
<blockquote>
<div><code class="docutils literal"><span class="pre">mkdir</span> <span class="pre">-p</span> <span class="pre">~/go/src/github.com/mattermost</span></code></div></blockquote>
<ol class="loweralpha simple" start="2">
<li>Change to the directory that you created.</li>
</ol>
<blockquote>
<div><code class="docutils literal"><span class="pre">cd</span> <span class="pre">~/go/src/github.com/mattermost</span></code></div></blockquote>
<ol class="loweralpha simple" start="3">
<li>Clone your Mattermost fork. In the following command, replace <em>{username}</em> with your GitHub username.</li>
</ol>
<blockquote>
<div><code class="docutils literal"><span class="pre">git</span> <span class="pre">clone</span> <span class="pre">https://github.com/{username}/platform.git</span></code></div></blockquote>
<ol class="loweralpha simple" start="4">
<li>Change into the platform directory</li>
</ol>
<blockquote>
<div><code class="docutils literal"><span class="pre">cd platform</span></code></div></blockquote>
</div></blockquote>
<ol class="loweralpha simple" start="7">
<li>Run the server and build the webapp with:</li>
</ol>
<blockquote><div><code class="docutils literal"><span class="pre">make run</span></code></div></blockquote>
</div>
</div>

<div id="ubuntu" class="tabcontent">
<ol class="arabic simple">
<li>If you are developing with the Docker container, install and configure Docker CE:</li>
</ol>
<blockquote>
<div><ol class="loweralpha simple">
<li>Follow the Docker installation instructions at <a class="reference external" href="https://docs.docker.com/engine/installation/linux/ubuntu/#install-using-the-repository">https://docs.docker.com/engine/installation/linux/ubuntu/#install-using-the-repository</a>.</li>
<li>Edit your <code class="docutils literal"><span class="pre">/etc/hosts</span></code> file to include the following line:</li>
</ol>
<blockquote>
<div><code class="docutils literal"><span class="pre">127.0.0.1</span>&#160;&#160;&#160;&#160; <span class="pre">dockerhost</span></code></div></blockquote>
<ol class="loweralpha simple" start="3">
<li>Add your username to the <em>docker</em> group so that you can run Docker without using sudo. Replace <em>{username}</em> with your username.</li>
</ol>
<blockquote>
<div><code class="docutils literal"><span class="pre">sudo</span> <span class="pre">gpasswd</span> <span class="pre">-a</span> <span class="pre">{username}</span> <span class="pre">docker</span></code></div></blockquote>
<ol class="loweralpha simple" start="4">
<li>Restart the Docker daemon.</li>
</ol>
<blockquote>
<div><code class="docutils literal"><span class="pre">sudo</span> <span class="pre">service</span> <span class="pre">docker</span> <span class="pre">restart</span></code></div></blockquote>
<ol class="loweralpha simple" start="5">
<li>Change your current group ID to the <em>docker</em> group.</li>
</ol>
<blockquote>
<div><code class="docutils literal"><span class="pre">newgrp</span> <span class="pre">docker</span></code></div></blockquote>
</div></blockquote>
<ol class="arabic simple" start="2">
<li>Install the build-essential package.</li>
</ol>
<blockquote>
<div><code class="docutils literal"><span class="pre">sudo</span> <span class="pre">apt-get</span> <span class="pre">install</span> <span class="pre">build-essential</span></code></div></blockquote>
<ol class="arabic" start="3">
<li><p class="first">Download and install Go {{< goversion >}} for Linux:</p>
<blockquote>
<div><ol class="loweralpha">
<li><p class="first">Download the Go binary.</p>
<p><code class="docutils literal"><span class="pre">wget</span> <span class="pre">https://redirector.gvt1.com/edgedl/go/go{{< goversion >}}.linux-amd64.tar.gz</span></code></p>
</li>
<li><p class="first">Install the Go binary.</p>
<p><code class="docutils literal"><span class="pre">sudo</span> <span class="pre">tar</span> <span class="pre">-C</span> <span class="pre">/usr/local</span> <span class="pre">-xzf</span> <span class="pre">go{{< goversion >}}.linux-amd64.tar.gz</span></code></p>
</li>
</ol>
</div></blockquote>
</li>
<li><p class="first">Set up your Go workspace:</p>
</li>
</ol>
<blockquote>
<div><ol class="loweralpha simple">
<li><code class="docutils literal"><span class="pre">mkdir</span> <span class="pre">~/go</span></code></li>
<li>Add the following lines to your <code class="docutils literal"><span class="pre">~/.bashrc</span></code> file:</li>
</ol>
<blockquote>
<div><div class="highlight-bash"><div class="highlight"><pre><span></span><span class="nb">export</span> <span class="nv">GOPATH</span><span class="o">=</span><span class="nv">$HOME</span>/go
<span class="nb">export</span> <span class="nv">PATH</span><span class="o">=</span><span class="nv">$PATH</span>:<span class="nv">$GOPATH</span>/bin
<span class="nb">export</span> <span class="nv">PATH</span><span class="o">=</span><span class="nv">$PATH</span>:/usr/local/go/bin
<span class="nb">ulimit</span> -n <span class="m">8096</span>
</pre></div>
</div>
</div></blockquote>
<ol class="loweralpha simple" start="3">
<li>Reload your bash configuration.</li>
</ol>
<blockquote>
<div><code class="docutils literal"><span class="pre">source</span> <span class="pre">~/.bashrc</span></code></div></blockquote>
</div></blockquote>
<ol class="arabic" start="5">
<li><p class="first">Install Node.js:</p>
<blockquote>
<div><ol class="loweralpha simple">
<li>Add the Node.js repository to your repository list.</li>
</ol>
<blockquote>
<div><p><code class="docutils literal"><span class="pre">curl</span> <span class="pre">-sL</span> <span class="pre">https://deb.nodesource.com/setup_8.x</span> <span class="pre">|</span> <span class="pre">sudo</span> <span class="pre">-E</span> <span class="pre">bash</span> <span class="pre">-</span></code></p>
</div></blockquote>
<ol class="loweralpha simple" start="2">
<li>Install Node.js</li>
</ol>
<blockquote>
<div><p><code class="docutils literal"><span class="pre">sudo</span> <span class="pre">apt-get</span> <span class="pre">install</span> <span class="pre">-y</span> <span class="pre">nodejs</span></code></p>
</div></blockquote>
</div></blockquote>
</li>
<li><p class="first">Install Yarn. Go to <a class="reference external" href="https://yarnpkg.com/en/docs/install">https://yarnpkg.com/en/docs/install</a> and follow the installation instructions.</p>
</li>
<li><p class="first">Fork Mattermost on GitHub from <a class="reference external" href="https://github.com/mattermost/platform">https://github.com/mattermost/platform</a>.</p>
</li>
<li><p class="first">Download the Mattermost code from your forked repository:</p>
</li>
</ol>
<blockquote>
<div><ol class="loweralpha simple">
<li>Create the directory for the code.</li>
</ol>
<blockquote>
<div><code class="docutils literal"><span class="pre">mkdir</span> <span class="pre">-p</span> <span class="pre">~/go/src/github.com/mattermost</span></code></div></blockquote>
<ol class="loweralpha simple" start="2">
<li>Change to the directory that you created.</li>
</ol>
<blockquote>
<div><code class="docutils literal"><span class="pre">cd</span> <span class="pre">~/go/src/github.com/mattermost</span></code></div></blockquote>
<ol class="loweralpha simple" start="3">
<li>Clone your Mattermost fork. In the following command, replace <em>{username}</em> with your GitHub username.</li>
</ol>
<blockquote>
<div><code class="docutils literal"><span class="pre">git</span> <span class="pre">clone</span> <span class="pre">https://github.com/{username}/platform.git</span></code></div></blockquote>
<ol class="loweralpha simple" start="4">
<li>Change into the platform directory</li>
</ol>
<blockquote>
<div><code class="docutils literal"><span class="pre">cd platform</span></code></div></blockquote>
</div></blockquote>
<ol class="loweralpha simple" start="7">
<li>Run the server and build the webapp with:</li>
</ol>
<blockquote><div><code class="docutils literal"><span class="pre">make run</span></code></div></blockquote>
</div>

<div id="windows" class="tabcontent">
<ol class="arabic simple">
<li>Install and setup Docker. If you are using Windows 10 Pro or Enterprise, you can use Docker for Windows.</li>
</ol>
<blockquote>
<div><ol class="loweralpha simple">
<li>Install <a class="reference external" href="https://docs.docker.com/docker-for-windows/">Docker for Windows</a>.</li>
<li>Add the line <code class="docutils literal"><span class="pre">127.0.0.1</span> <span class="pre">dockerhost</span></code> to <code class="docutils literal"><span class="pre">C:\Windows\System32\drivers\etc\hosts</span></code> using a text editor with administrator privileges.</li>
</ol>
</div></blockquote>
<ol class="arabic simple" start="2">
<li>For other Windows versions, or if you prefer to use VirtualBox, use Docker Toolbox:</li>
</ol>
<blockquote>
<div><ol class="loweralpha simple">
<li>Install <a class="reference external" href="https://www.docker.com/products/docker-toolbox">Docker Toolbox</a>.</li>
<li>Run the <em>Docker Quickstart Terminal</em> and let it configure the <code class="docutils literal"><span class="pre">default</span></code> machine.</li>
<li>Run <code class="docutils literal"><span class="pre">docker-machine</span> <span class="pre">ip</span> <span class="pre">default</span></code> in the terminal to get the IP address for the next step.</li>
<li>Add the line <code class="docutils literal"><span class="pre">{Docker-IP}</span> <span class="pre">dockerhost</span></code> to <code class="docutils literal"><span class="pre">C:\Windows\System32\drivers\etc\hosts</span></code> using a text editor with administrator privileges.</li>
</ol>
</div></blockquote>
<ol class="arabic simple" start="3">
<li>Download and install Node.js from <a class="reference external" href="https://nodejs.org/">https://nodejs.org/</a>.</li>
<li>Download and install Go {{< goversion >}} from <a class="reference external" href="https://golang.org/dl/">https://golang.org/dl/</a>.</li>
<li>Install Yarn. Go to <a class="reference external" href="https://yarnpkg.com/en/docs/install#windows-tab">https://yarnpkg.com/en/docs/install#windows-tab</a> and follow the installation instructions.</li>
<li>Fork Mattermost on GitHub.com from <a class="reference external" href="https://github.com/mattermost/platform">https://github.com/mattermost/platform</a>, then:</li>
</ol>
<blockquote>
<div><ol class="loweralpha simple">
<li><code class="docutils literal"><span class="pre">cd</span> <span class="pre">~/go</span></code></li>
<li><code class="docutils literal"><span class="pre">mkdir</span> <span class="pre">-p</span> <span class="pre">src/github.com/mattermost</span></code></li>
<li><code class="docutils literal"><span class="pre">cd</span> <span class="pre">src/github.com/mattermost</span></code></li>
<li><code class="docutils literal"><span class="pre">git</span> <span class="pre">clone</span> <span class="pre">https://github.com/{username}/platform.git</span></code></li>
<li><code class="docutils literal"><span class="pre">cd</span> <span class="pre">platform</span></code></li>
<li><code class="docutils literal"><span class="pre">git</span> <span class="pre">config</span> <span class="pre">core.eol</span> <span class="pre">lf</span></code></li>
<li><code class="docutils literal"><span class="pre">git</span> <span class="pre">config</span> <span class="pre">core.autocrlf</span> <span class="pre">input</span></code></li>
<li><code class="docutils literal"><span class="pre">git</span> <span class="pre">reset</span> <span class="pre">--hard</span> <span class="pre">HEAD</span></code></li>
</ol>
</div></blockquote>
<ol class="arabic simple" start="7">
<li>Install and setup babun from <a class="reference external" href="http://babun.github.io/">http://babun.github.io/</a>.</li>
<li>Setup the following environment variables (change the path accordingly):</li>
</ol>
<blockquote>
<div><div class="highlight-batch"><div class="highlight"><pre><span></span>export PATH=<span class="s2">&quot;/c/Program Files/go/bin&quot;</span>:$PATH
export PATH=<span class="s2">&quot;/c/Program Files/nodejs&quot;</span>:$PATH
export PATH=<span class="s2">&quot;/c/Program Files/Git/bin&quot;</span>:$PATH
export GOROOT=<span class="s2">&quot;c:\\Program Files\\go&quot;</span>
export GOPATH=<span class="s2">&quot;c:\\User\\{user-name}\\go&quot;</span>
export PATH=<span class="s2">&quot;/c/Program Files/Docker Toolbox&quot;</span>:$PATH #change the path accordingly if you are using Docker for Windows
eval $(docker-machine env default) #skip this line if you are using Docker for Windows
</pre></div>
</div>
</div></blockquote>
</div>

<div id="archlinux" class="tabcontent">
    <ol class="arabic simple">
<li>If you are developing with the Docker container, install and configure Docker CE:</li>
</ol>
<blockquote>
<div><ol class="loweralpha simple">
<li><code class="docutils literal"><span class="pre">pacman</span> <span class="pre">-S</span> <span class="pre">docker</span></code></li>
<li><code class="docutils literal"><span class="pre">gpasswd</span> <span class="pre">-a</span> <span class="pre">user</span> <span class="pre">docker</span></code></li>
<li><code class="docutils literal"><span class="pre">systemctl</span> <span class="pre">enable</span> <span class="pre">docker.service</span></code></li>
<li><code class="docutils literal"><span class="pre">systemctl</span> <span class="pre">start</span> <span class="pre">docker.service</span></code></li>
<li><code class="docutils literal"><span class="pre">newgrp</span> <span class="pre">docker</span></code></li>
<li>Edit your <code class="docutils literal"><span class="pre">/etc/hosts</span></code> file to include the following line:</li>
</ol>
<blockquote>
<div><code class="docutils literal"><span class="pre">127.0.0.1</span> <span class="pre">dockerhost</span></code></div></blockquote>
</div></blockquote>
<ol class="arabic simple" start="2">
<li>Install Go {{< goversion >}}</li>
</ol>
<blockquote>
<div><code class="docutils literal"><span class="pre">pacman</span> <span class="pre">-S</span> <span class="pre">go</span></code></div></blockquote>
<ol class="arabic simple" start="3">
<li>Set up your Go workspace:</li>
</ol>
<blockquote>
<div><ol class="loweralpha simple">
<li><code class="docutils literal"><span class="pre">mkdir</span> <span class="pre">~/go</span></code></li>
<li>Add the following lines to your <code class="docutils literal"><span class="pre">~/.bashrc</span></code> file:</li>
</ol>
<blockquote>
<div><div class="highlight-bash"><div class="highlight"><pre><span></span><span class="nb">export</span> <span class="nv">GOPATH</span><span class="o">=</span><span class="nv">$HOME</span>/go
<span class="nb">export</span> <span class="nv">PATH</span><span class="o">=</span><span class="nv">$PATH</span>:<span class="nv">$GOPATH</span>/bin
<span class="nb">export</span> <span class="nv">PATH</span><span class="o">=</span><span class="nv">$PATH</span>:/usr/local/go/bin
</pre></div>
</div>
</div></blockquote>
<ol class="loweralpha simple" start="3">
<li>Reload your bash configuration.</li>
</ol>
<blockquote>
<div><code class="docutils literal"><span class="pre">source</span> <span class="pre">~/.bashrc</span></code></div></blockquote>
</div></blockquote>
<ol class="arabic simple" start="4">
<li>Increase the file handle limit. Edit <code class="docutils literal"><span class="pre">/etc/security/limits.conf</span></code> and add the following lines (replace <em>{username}</em> with your user):</li>
</ol>
<blockquote>
<div><div class="highlight-text"><div class="highlight"><pre><span></span>{username}  soft  nofile  8096
{username}  hard  nofile  8096
</pre></div>
</div>
<p>You must reboot for these changes to take effect.</p>
</div></blockquote>
<ol class="arabic simple" start="5">
<li>Install Node.js.</li>
</ol>
<blockquote>
<div><code class="docutils literal"><span class="pre">pacman</span> <span class="pre">-S</span> <span class="pre">nodejs</span> <span class="pre">npm</span></code></div></blockquote>
<ol class="arabic simple" start="6">
<li>Install Yarn.</li>
</ol>
<blockquote>
<div><code class="docutils literal"><span class="pre">pacman</span> <span class="pre">-S</span> <span class="pre">yarn</span></code></div></blockquote>
<ol class="arabic simple" start="7">
<li>Fork Mattermost on GitHub.com from <a class="reference external" href="https://github.com/mattermost/platform">https://github.com/mattermost/platform</a>.</li>
<li>Download the Mattermost code from your forked repository:</li>
</ol>
<blockquote>
<div><ol class="loweralpha simple">
<li>Create the directory for the code.</li>
</ol>
<blockquote>
<div><code class="docutils literal"><span class="pre">mkdir</span> <span class="pre">-p</span> <span class="pre">~/go/src/github.com/mattermost</span></code></div></blockquote>
<ol class="loweralpha simple" start="2">
<li>Change to the directory that you created.</li>
</ol>
<blockquote>
<div><code class="docutils literal"><span class="pre">cd</span> <span class="pre">~/go/src/github.com/mattermost</span></code></div></blockquote>
<ol class="loweralpha simple" start="3">
<li>Clone your Mattermost fork. In the following command, replace <em>{username}</em> with your GitHub username.</li>
</ol>
<blockquote>
<div><code class="docutils literal"><span class="pre">git</span> <span class="pre">clone</span> <span class="pre">https://github.com/{username}/platform.git</span></code></div></blockquote>
</div></blockquote>
</div>

<div id="centos" class="tabcontent">
<ol class="arabic simple">
<li>If you are developing with the Docker container, install and configure Docker CE:</li>
</ol>
<blockquote>
<div><ol class="loweralpha simple">
<li>Follow the Docker installation instructions at <a class="reference external" href="https://docs.docker.com/engine/installation/linux/docker-ce/centos/">https://docs.docker.com/engine/installation/linux/docker-ce/centos/</a>.</li>
<li>Edit your <code class="docutils literal"><span class="pre">/etc/hosts</span></code> file to include the following line:</li>
</ol>
<blockquote>
<div><code class="docutils literal"><span class="pre">127.0.0.1</span>&#160;&#160;&#160;&#160; <span class="pre">dockerhost</span></code></div></blockquote>
<ol class="loweralpha simple" start="3">
<li>Add your username to the <em>docker</em> group so that you can run Docker without using sudo. Replace <em>{username}</em> with your username.</li>
</ol>
<blockquote>
<div><code class="docutils literal"><span class="pre">sudo</span> <span class="pre">gpasswd</span> <span class="pre">-a</span> <span class="pre">{username}</span> <span class="pre">docker</span></code></div></blockquote>
<ol class="loweralpha simple" start="4">
<li>Restart the Docker daemon.</li>
</ol>
<blockquote>
<div><code class="docutils literal"><span class="pre">sudo</span> <span class="pre">systemctl</span> <span class="pre">restart</span> <span class="pre">docker</span></code></div></blockquote>
<ol class="loweralpha simple" start="5">
<li>Change your current group ID to the <em>docker</em> group.</li>
</ol>
<blockquote>
<div><code class="docutils literal"><span class="pre">newgrp</span> <span class="pre">docker</span></code></div></blockquote>
</div></blockquote>
<ol class="arabic" start="2">
<li><p class="first">Install the development tools package, wget and libpng12 required by pngquant(a library used by Mattermost).</p>
<blockquote>
<div><ol class="loweralpha simple">
<li><code class="docutils literal"><span class="pre">sudo</span> <span class="pre">yum</span> <span class="pre">group</span> <span class="pre">install</span> <span class="pre">&quot;Development</span> <span class="pre">Tools&quot;</span></code></li>
<li><code class="docutils literal"><span class="pre">sudo</span> <span class="pre">yum</span> <span class="pre">install</span> <span class="pre">-y</span> <span class="pre">wget</span> <span class="pre">libpng12</span></code></li>
</ol>
</div></blockquote>
</li>
<li><p class="first">Download and install Go {{< goversion >}} for Linux:</p>
<blockquote>
<div><ol class="loweralpha">
<li><p class="first">Download the Go binary.</p>
<p><code class="docutils literal"><span class="pre">wget</span> <span class="pre">https://redirector.gvt1.com/edgedl/go/go{{< goversion >}}.linux-amd64.tar.gz</span></code></p>
</li>
<li><p class="first">Install the Go binary.</p>
<p><code class="docutils literal"><span class="pre">sudo</span> <span class="pre">tar</span> <span class="pre">-C</span> <span class="pre">/usr/local</span> <span class="pre">-xzf</span> <span class="pre">go{{< goversion >}}.linux-amd64.tar.gz</span></code></p>
</li>
</ol>
</div></blockquote>
</li>
<li><p class="first">Set up your Go workspace:</p>
</li>
</ol>
<blockquote>
<div><ol class="loweralpha simple">
<li><code class="docutils literal"><span class="pre">mkdir</span> <span class="pre">~/go</span></code></li>
<li>Add the following lines to your <code class="docutils literal"><span class="pre">~/.bashrc</span></code> file:</li>
</ol>
<blockquote>
<div><div class="highlight-bash"><div class="highlight"><pre><span></span><span class="nb">export</span> <span class="nv">GOPATH</span><span class="o">=</span><span class="nv">$HOME</span>/go
<span class="nb">export</span> <span class="nv">PATH</span><span class="o">=</span><span class="nv">$PATH</span>:<span class="nv">$GOPATH</span>/bin
<span class="nb">export</span> <span class="nv">PATH</span><span class="o">=</span><span class="nv">$PATH</span>:/usr/local/go/bin
</pre></div>
</div>
</div></blockquote>
<ol class="loweralpha" start="3">
<li><p class="first">Reload your bash configuration.</p>
<blockquote>
<div><p>source ~/.bashrc</p>
</div></blockquote>
</li>
<li><p class="first">Since you cannot run <code class="docutils literal"><span class="pre">ulimit</span> <span class="pre">-n</span> <span class="pre">8096</span></code> with a regular user, we have to edit the file <code class="docutils literal"><span class="pre">sudo</span> <span class="pre">nano</span> <span class="pre">/etc/security/limits.conf</span></code> to include the following 2 lines at the end of it:</p>
</li>
</ol>
<blockquote>
<div><div class="highlight-bash"><div class="highlight"><pre><span></span><span class="o">{</span>username<span class="o">}</span> soft nofile <span class="m">8096</span>
<span class="o">{</span>username<span class="o">}</span> hard nofile <span class="m">10000</span>
</pre></div>
</div>
</div></blockquote>
<ol class="loweralpha simple" start="5">
<li>After doing the above simple logout then log back in and it should accept the changes.</li>
</ol>
</div></blockquote>
<ol class="arabic" start="5">
<li><p class="first">Install Node.js:</p>
<blockquote>
<div><ol class="loweralpha simple">
<li>Add the Node.js repository to your repository list.</li>
</ol>
<blockquote>
<div><p><code class="docutils literal"><span class="pre">curl</span> <span class="pre">--silent</span> <span class="pre">--location</span> <span class="pre">https://rpm.nodesource.com/setup_8.x</span> <span class="pre">|</span> <span class="pre">sudo</span> <span class="pre">bash</span> <span class="pre">-</span></code></p>
</div></blockquote>
<ol class="loweralpha simple" start="2">
<li>Install Node.js</li>
</ol>
<blockquote>
<div><p><code class="docutils literal"><span class="pre">sudo</span> <span class="pre">yum</span> <span class="pre">install</span> <span class="pre">-y</span> <span class="pre">nodejs</span></code></p>
</div></blockquote>
</div></blockquote>
</li>
<li><p class="first">Install Yarn. Go to <a class="reference external" href="https://yarnpkg.com/en/docs/install">https://yarnpkg.com/en/docs/install</a> and follow the installation instructions.</p>
</li>
<li><p class="first">Fork Mattermost on GitHub from <a class="reference external" href="https://github.com/mattermost/platform">https://github.com/mattermost/platform</a>.</p>
</li>
<li><p class="first">Download the Mattermost code from your forked repository:</p>
</li>
</ol>
<blockquote>
<div><ol class="loweralpha simple">
<li>Create the directory for the code.</li>
</ol>
<blockquote>
<div><code class="docutils literal"><span class="pre">mkdir</span> <span class="pre">-p</span> <span class="pre">~/go/src/github.com/mattermost</span></code></div></blockquote>
<ol class="loweralpha simple" start="2">
<li>Change to the directory that you created.</li>
</ol>
<blockquote>
<div><code class="docutils literal"><span class="pre">cd</span> <span class="pre">~/go/src/github.com/mattermost</span></code></div></blockquote>
<ol class="loweralpha simple" start="3">
<li>Clone your Mattermost fork. In the following command, replace <em>{username}</em> with your GitHub username.</li>
</ol>
<blockquote>
<div><code class="docutils literal"><span class="pre">git</span> <span class="pre">clone</span> <span class="pre">https://github.com/{username}/platform.git</span></code></div></blockquote>
</div></blockquote>
</div>

<div style="margin-top: 15px;">
<span class="pull-left"><a href="/contribute/server/">< Back to Server</a></span>
<span class="pull-right"><a href="/contribute/server/developer-workflow/">Go to Development Workflow ></a></span>
</div>
<br/>
