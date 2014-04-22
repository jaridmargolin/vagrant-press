vagrant-press
=============

Wordpress theme development env - Vagrant, chef, berkshelf.

[Vagrant](http://www.vagrantup.com/) virtual machine running ubuntu 12.04 (64 bit). Uses [Berkshef](http://berkshelf.com/) + [Chef Solo](http://docs.opscode.com/chef_solo.html) to install wordpress and accompanying tools.



Dependencies
------------

1. **[Download Virtual Box (4.3.6)](http://https://www.virtualbox.org/wiki/downloads)**

2. **[Install Ruby (2.0.0p247)](http://octopress.org/docs/setup/rvm/)**

3. **[Install Vagrant (1.5.4)](http://downloads.vagrantup.com/)**

4. **Install Berkshelf:** `gem install berkshelf`

5. **Instal Vagrant Berkshelf Plugin:** `vagrant plugin install vagrant-berkshelf`


Setup
-----

Create project directory

    mkdir proj-name

Move into dir

    cd proj-name

Clone vagrant-press into directory

    git clone git@github.com:jaridmargolin/vagrant-press.git

Clone theme repository into theme dir

    git clone git@github.com:username/your/theme/repo.git ./theme

Usage
-----

### Start VM
    
`vagrant up`

### SSH In

`vagrant ssh`


Configuration
-------------------------

### Networking

By default port 80 on your virtual machine is forwarded to port 8080 on your host machine. View [Vagrant Networking Documentation](http://docs.vagrantup.com/v2/networking/index.html) for more information on changing defaults

**Default**
    
    config.vm.network :forwarded_port, guest: 80, host: 8080



License
-------
The MIT License (MIT)
Copyright (c) 2013 Jarid Margolin

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.