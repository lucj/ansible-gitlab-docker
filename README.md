Deployment of a ci server
-------------------------

This playbook setup a Ubuntu (14.04 / 16.04) host containing
* GitLab
* Docker
* Docker Compose

Inventory
---------

The inventory.ini file defines the host the server needs to be deployed on
Next to the host's ip, the external_url parameter needs to be set, this indicates to GitLab the url it must send the http requests to.

Running option
--------------

Several possible cases depending upon the way the nodes are created:

* Vagrant VM are used for test => **vagrant** user needs to be used

  ```ansible-playbook -i inventory.ini -k -u vagrant -s main.yml```

Note: vagrant ssh password requested (sudo password not requested as vagrant user is authorized to sudo without password)

* root access is provided => **root** user needs to be used

  ```ansible-playbook -i inventory.ini -k -u root main.yml```

Note: root ssh password will be requested

* another user provided with sudo right and a password needed to issue sudo commands

  ```ansible-playbook -i inventory.ini -k -K -u USER -s main.yml```

Note: both user's ssh password + sudo password will be requested

* user provided with a ssh key added to its authorized_keys

   ```ansible-playbook -i inventory.ini -u USER --private-key PATH_TO_KEY -s main.yml```

Note: this option is usefull in the case where a ssh key is used when creating the host (AWS, DO, ...)

License
-------

The MIT License (MIT)

Copyright (c) [2016]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
