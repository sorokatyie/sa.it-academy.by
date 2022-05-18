
#### 07.Ansible.Cruise_Alex_Muzhichenko


### Output Nginx Webserver role

```bash

alex@ubuntusa:~/ansible$ ansible-playbook -i inventory.yaml web.yaml

PLAY [test_hosts] ***************************************************************************************************************************************************************************************************************************

TASK [Gathering Facts] **********************************************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:15 +0000 (0:00:00.032)       0:00:00.032 ************
ok: [host32]
ok: [host31]

TASK [webserver : Include deploy for Debian systems] ****************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:37 +0000 (0:00:21.642)       0:00:21.675 ************
skipping: [host31]
included: /home/alex/ansible/roles/webserver/tasks/ubuntu.yaml for host32

TASK [webserver : NGINX. Install packages] **************************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:37 +0000 (0:00:00.110)       0:00:21.785 ************
ok: [host32]

TASK [webserver : Nginx. Enable and start servce] *******************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:39 +0000 (0:00:02.083)       0:00:23.868 ************
ok: [host32]

TASK [webserver : Nginx. Deploy Ubuntu] *****************************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:40 +0000 (0:00:00.985)       0:00:24.854 ************
included: /home/alex/ansible/roles/webserver/tasks/deploy.yaml for host32 => (item=ubuntu1.site)
included: /home/alex/ansible/roles/webserver/tasks/deploy.yaml for host32 => (item=ubuntu2.site)

TASK [webserver : Check if directory exists] ************************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:40 +0000 (0:00:00.075)       0:00:24.930 ************
ok: [host32]

TASK [webserver : Copy index.html] **********************************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:41 +0000 (0:00:00.714)       0:00:25.645 ************
ok: [host32]

TASK [webserver : Templates virtual_hosts] **************************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:42 +0000 (0:00:01.088)       0:00:26.733 ************
ok: [host32]

TASK [webserver : Check if directory exists] ************************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:43 +0000 (0:00:00.978)       0:00:27.712 ************
ok: [host32]

TASK [webserver : Copy index.html] **********************************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:44 +0000 (0:00:00.624)       0:00:28.336 ************
ok: [host32]

TASK [webserver : Templates virtual_hosts] **************************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:45 +0000 (0:00:01.025)       0:00:29.362 ************
ok: [host32]

TASK [webserver : Restart nginx Ubuntu] *****************************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:46 +0000 (0:00:00.984)       0:00:30.346 ************
changed: [host32]

TASK [webserver : Nginx. Check Ubuntu virtualhosts] *****************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:46 +0000 (0:00:00.874)       0:00:31.220 ************
included: /home/alex/ansible/roles/webserver/tasks/check.yaml for host32 => (item=ubuntu1.site)
included: /home/alex/ansible/roles/webserver/tasks/check.yaml for host32 => (item=ubuntu2.site)

TASK [webserver : Check content to the sites] ***********************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:47 +0000 (0:00:00.064)       0:00:31.285 ************
ok: [host32]

TASK [webserver : Print output] *************************************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:47 +0000 (0:00:00.780)       0:00:32.066 ************
ok: [host32] => {
    "msg": "Host: ubuntu1.site"
}

TASK [webserver : Check content to the sites] ***********************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:47 +0000 (0:00:00.044)       0:00:32.110 ************
ok: [host32]

TASK [webserver : Print output] *************************************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:48 +0000 (0:00:00.646)       0:00:32.757 ************
ok: [host32] => {
    "msg": "Host: ubuntu2.site"
}

TASK [webserver : Include deploy for RedHat systems] ****************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:48 +0000 (0:00:00.029)       0:00:32.786 ************
skipping: [host32]
included: /home/alex/ansible/roles/webserver/tasks/centos.yaml for host31

TASK [webserver : Install epel repo] ********************************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:48 +0000 (0:00:00.076)       0:00:32.863 ************
ok: [host31]

TASK [webserver : NGINX. Install packages] **************************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:49 +0000 (0:00:00.899)       0:00:33.763 ************
ok: [host31]

TASK [webserver : NGINX. Enable and start servce] *******************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:50 +0000 (0:00:00.747)       0:00:34.510 ************
ok: [host31]

TASK [webserver : NGINX. Enable firewall port] **********************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:50 +0000 (0:00:00.739)       0:00:35.249 ************
ok: [host31]

TASK [webserver : NGINX. reload service firewalld] ******************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:51 +0000 (0:00:00.971)       0:00:36.221 ************
changed: [host31]

TASK [webserver : Nginx. Deploy CentOS] *****************************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:52 +0000 (0:00:00.880)       0:00:37.102 ************
included: /home/alex/ansible/roles/webserver/tasks/deploy.yaml for host31 => (item=centos1.site)
included: /home/alex/ansible/roles/webserver/tasks/deploy.yaml for host31 => (item=centos2.site)

TASK [webserver : Check if directory exists] ************************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:52 +0000 (0:00:00.070)       0:00:37.172 ************
ok: [host31]

TASK [webserver : Copy index.html] **********************************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:53 +0000 (0:00:00.609)       0:00:37.782 ************
ok: [host31]

TASK [webserver : Templates virtual_hosts] **************************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:54 +0000 (0:00:01.012)       0:00:38.794 ************
ok: [host31]

TASK [webserver : Check if directory exists] ************************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:55 +0000 (0:00:00.983)       0:00:39.778 ************
ok: [host31]

TASK [webserver : Copy index.html] **********************************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:56 +0000 (0:00:00.616)       0:00:40.394 ************
ok: [host31]

TASK [webserver : Templates virtual_hosts] **************************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:57 +0000 (0:00:00.965)       0:00:41.359 ************
ok: [host31]

TASK [webserver : Restart nginx CentOS] *****************************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:58 +0000 (0:00:00.993)       0:00:42.353 ************
changed: [host31]

TASK [webserver : Nginx. Check CentOS virtualhosts] *****************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:58 +0000 (0:00:00.795)       0:00:43.149 ************
included: /home/alex/ansible/roles/webserver/tasks/check.yaml for host31 => (item=centos1.site)
included: /home/alex/ansible/roles/webserver/tasks/check.yaml for host31 => (item=centos2.site)

TASK [webserver : Check content to the sites] ***********************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:58 +0000 (0:00:00.091)       0:00:43.241 ************
ok: [host31]

TASK [webserver : Print output] *************************************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:59 +0000 (0:00:00.670)       0:00:43.912 ************
ok: [host31] => {
    "msg": "Host: centos1.site"
}

TASK [webserver : Check content to the sites] ***********************************************************************************************************************************************************************************************
Monday 16 May 2022  13:33:59 +0000 (0:00:00.050)       0:00:43.962 ************
ok: [host31]

TASK [webserver : Print output] *************************************************************************************************************************************************************************************************************
Monday 16 May 2022  13:34:00 +0000 (0:00:00.631)       0:00:44.593 ************
ok: [host31] => {
    "msg": "Host: centos2.site"
}

PLAY RECAP **********************************************************************************************************************************************************************************************************************************
host31                     : ok=22   changed=2    unreachable=0    failed=0    skipped=1    rescued=0    ignored=0
host32                     : ok=19   changed=1    unreachable=0    failed=0    skipped=1    rescued=0    ignored=0

Monday 16 May 2022  13:34:00 +0000 (0:00:00.081)       0:00:44.675 ************
===============================================================================
Gathering Facts --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 21.64s
webserver : NGINX. Install packages -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 2.08s
webserver : Copy index.html ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 1.09s
webserver : Copy index.html ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 1.02s
webserver : Copy index.html ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 1.01s
webserver : Templates virtual_hosts -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 0.99s
webserver : Nginx. Enable and start servce ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 0.99s
webserver : Templates virtual_hosts -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 0.98s
webserver : Templates virtual_hosts -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 0.98s
webserver : Templates virtual_hosts -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 0.98s
webserver : NGINX. Enable firewall port ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 0.97s
webserver : Copy index.html ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 0.97s
webserver : Install epel repo -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 0.90s
webserver : NGINX. reload service firewalld ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ 0.88s
webserver : Restart nginx Ubuntu ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 0.87s
webserver : Restart nginx CentOS ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 0.80s
webserver : Check content to the sites ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 0.78s
webserver : NGINX. Install packages -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 0.75s
webserver : NGINX. Enable and start servce ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 0.74s
webserver : Check if directory exists ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ 0.71s
Playbook run took 0 days, 0 hours, 0 minutes, 44 seconds


```

### Output Nginx Test role

```bash

alex@ubuntusa:~/ansible$ ansible-playbook -i inventory.yaml testing.yaml

PLAY [test_hosts] ***************************************************************************************************************************************************************************************************************************

TASK [Gathering Facts] **********************************************************************************************************************************************************************************************************************
Monday 16 May 2022  13:41:41 +0000 (0:00:00.011)       0:00:00.011 ************
ok: [host32]
ok: [host31]

TASK [test : Check SUDO with NOPASSWD] ******************************************************************************************************************************************************************************************************
Monday 16 May 2022  13:42:03 +0000 (0:00:21.651)       0:00:21.663 ************
ok: [host31]
ok: [host32]

TASK [test : Check connections to public] ***************************************************************************************************************************************************************************************************
Monday 16 May 2022  13:42:04 +0000 (0:00:00.727)       0:00:22.390 ************
ok: [host31] => (item=https://deb.debian.org/debian)
ok: [host32] => (item=https://deb.debian.org/debian)
ok: [host31] => (item=http://mirror.centos.org/centos/)
ok: [host32] => (item=http://mirror.centos.org/centos/)
ok: [host32] => (item=https://pypi.org/simple)
ok: [host31] => (item=https://pypi.org/simple)

TASK [test : Print status connection] *******************************************************************************************************************************************************************************************************
Monday 16 May 2022  13:42:11 +0000 (0:00:07.514)       0:00:29.905 ************
ok: [host31] => {
    "msg": "All items completed"
}
ok: [host32] => {
    "msg": "All items completed"
}

TASK [test : Check connection Docker hub] ***************************************************************************************************************************************************************************************************
Monday 16 May 2022  13:42:11 +0000 (0:00:00.064)       0:00:29.969 ************
ok: [host31]
ok: [host32]

TASK [test : Print status connection] *******************************************************************************************************************************************************************************************************
Monday 16 May 2022  13:42:13 +0000 (0:00:01.296)       0:00:31.265 ************
ok: [host31] => {
    "msg": "<!doctype html>\n<html lang=\"en\">\n\n<head>\n  <title>Docker Hub</title>\n  <!-- Google Font -->\n  <meta name=\"viewport\" content=\"width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0\">\n  <link href=\"https://fonts.googleapis.com/css?family=Comfortaa|Open+Sans:300,400,400i,600,600i,700\" rel=\"stylesheet\">\n  <link href=\"https://fonts.googleapis.com/css?family=Poppins:400,500,600,700\" rel=\"stylesheet\">\n  <!-- Google Webmaster -->\n  <meta name=\"google-site-verification\" content=\"uXQNygijkvw9KqUBVhYTJW7Gl1yBUOwdAiuhFCUGsz4\" />\n  <meta name=\"fragment\" content=\"!\">\n  \n  <!-- TrustArc updated snippet, load first to ensure Zero Tracker Load policies -->\n  <script async=\"async\" src=\"https://consent.trustarc.com/notice?domain=docker.com&c=teconsent&js=nj&noticeType=bb&gtm=1\"></script>\n  \n  <script type=\"text/javascript\">window.ASSET_PATH = 'https://d36jcksde1wxzq.cloudfront.net/';</script>\n  \n  <script type=\"text/javascript\">var analyticsQueue = window.analyticsQueue || [];</script>\n  <!-- Optimizely -->\n  <script src=\"https://cdn-pci.optimizely.com/js/17888640141.js\"></script>\n  <!-- Mouseflow: heatmap and recording tool -->\n  <script type=\"text/javascript\" src=\"https://cdn.mouseflow.com/projects/31c8bb38-cfeb-4bd8-a60c-d5650a6d6f23.js\" async=\"\"></script>\n  \n  <!-- Google Tag Manager -->\n  <script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':\n  new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],\n  j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=\n  'https://www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);\n  })(window,document,'script','dataLayer','GTM-WL2QLG5');</script>\n  \n  <link rel=\"stylesheet\" href=\"https://d36jcksde1wxzq.cloudfront.net/main.53b2cedffc23b1111652.css\">\n</head>\n\n<body>\n  <div id=\"app\"></div>\n  <script>\n    window.dockerVars = {\n      bugsnagApiKey: 'aebb7f3442de072b3209127919cf37c0',\n      environment: 'production',\n      appVersion: '1454.0.0'\n    };\n    window.recaptchaOptions = {\n      useRecaptchaNet: true\n    };\n  </script>\n  <script src=\"https://d36jcksde1wxzq.cloudfront.net/bugsnag.9472738800348d01a133.js\"></script>\n  <script src=\"https://d36jcksde1wxzq.cloudfront.net/main.b2afacc7b5f99e1a6112.js\"></script>\n</body>\n\n</html>\n"
}
ok: [host32] => {
    "msg": "<!doctype html>\n<html lang=\"en\">\n\n<head>\n  <title>Docker Hub</title>\n  <!-- Google Font -->\n  <meta name=\"viewport\" content=\"width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0\">\n  <link href=\"https://fonts.googleapis.com/css?family=Comfortaa|Open+Sans:300,400,400i,600,600i,700\" rel=\"stylesheet\">\n  <link href=\"https://fonts.googleapis.com/css?family=Poppins:400,500,600,700\" rel=\"stylesheet\">\n  <!-- Google Webmaster -->\n  <meta name=\"google-site-verification\" content=\"uXQNygijkvw9KqUBVhYTJW7Gl1yBUOwdAiuhFCUGsz4\" />\n  <meta name=\"fragment\" content=\"!\">\n  \n  <!-- TrustArc updated snippet, load first to ensure Zero Tracker Load policies -->\n  <script async=\"async\" src=\"https://consent.trustarc.com/notice?domain=docker.com&c=teconsent&js=nj&noticeType=bb&gtm=1\"></script>\n  \n  <script type=\"text/javascript\">window.ASSET_PATH = 'https://d36jcksde1wxzq.cloudfront.net/';</script>\n  \n  <script type=\"text/javascript\">var analyticsQueue = window.analyticsQueue || [];</script>\n  <!-- Optimizely -->\n  <script src=\"https://cdn-pci.optimizely.com/js/17888640141.js\"></script>\n  <!-- Mouseflow: heatmap and recording tool -->\n  <script type=\"text/javascript\" src=\"https://cdn.mouseflow.com/projects/31c8bb38-cfeb-4bd8-a60c-d5650a6d6f23.js\" async=\"\"></script>\n  \n  <!-- Google Tag Manager -->\n  <script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':\n  new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],\n  j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=\n  'https://www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);\n  })(window,document,'script','dataLayer','GTM-WL2QLG5');</script>\n  \n  <link rel=\"stylesheet\" href=\"https://d36jcksde1wxzq.cloudfront.net/main.53b2cedffc23b1111652.css\">\n</head>\n\n<body>\n  <div id=\"app\"></div>\n  <script>\n    window.dockerVars = {\n      bugsnagApiKey: 'aebb7f3442de072b3209127919cf37c0',\n      environment: 'production',\n      appVersion: '1454.0.0'\n    };\n    window.recaptchaOptions = {\n      useRecaptchaNet: true\n    };\n  </script>\n  <script src=\"https://d36jcksde1wxzq.cloudfront.net/bugsnag.9472738800348d01a133.js\"></script>\n  <script src=\"https://d36jcksde1wxzq.cloudfront.net/main.b2afacc7b5f99e1a6112.js\"></script>\n</body>\n\n</html>\n"
}

TASK [test : Check RAM] *********************************************************************************************************************************************************************************************************************
Monday 16 May 2022  13:42:13 +0000 (0:00:00.063)       0:00:31.328 ************
ok: [host31] => (item={'block_used': 475107, 'uuid': 'N/A', 'size_total': 21003583488, 'block_total': 5127828, 'mount': '/', 'block_available': 4652721, 'size_available': 19057545216, 'fstype': 'ext4', 'inode_total': 1310720, 'options': 'rw,relatime', 'device': '/dev/loop30', 'inode_used': 23499, 'block_size': 4096, 'inode_available': 1287221}) => {
    "ansible_loop_var": "item",
    "changed": false,
    "item": {
        "block_available": 4652721,
        "block_size": 4096,
        "block_total": 5127828,
        "block_used": 475107,
        "device": "/dev/loop30",
        "fstype": "ext4",
        "inode_available": 1287221,
        "inode_total": 1310720,
        "inode_used": 23499,
        "mount": "/",
        "options": "rw,relatime",
        "size_available": 19057545216,
        "size_total": 21003583488,
        "uuid": "N/A"
    },
    "msg": "All assertions passed"
}
ok: [host32] => (item={'mount': '/', 'device': '/dev/loop31', 'fstype': 'ext4', 'options': 'rw,relatime', 'size_total': 21003583488, 'size_available': 18824105984, 'block_size': 4096, 'block_total': 5127828, 'block_available': 4595729, 'block_used': 532099, 'inode_total': 1310720, 'inode_available': 1283881, 'inode_used': 26839, 'uuid': 'N/A'}) => {
    "ansible_loop_var": "item",
    "changed": false,
    "item": {
        "block_available": 4595729,
        "block_size": 4096,
        "block_total": 5127828,
        "block_used": 532099,
        "device": "/dev/loop31",
        "fstype": "ext4",
        "inode_available": 1283881,
        "inode_total": 1310720,
        "inode_used": 26839,
        "mount": "/",
        "options": "rw,relatime",
        "size_available": 18824105984,
        "size_total": 21003583488,
        "uuid": "N/A"
    },
    "msg": "All assertions passed"
}

TASK [test : Check disk space] **************************************************************************************************************************************************************************************************************
Monday 16 May 2022  13:42:13 +0000 (0:00:00.105)       0:00:31.435 ************
ok: [host31] => (item={'block_used': 475107, 'uuid': 'N/A', 'size_total': 21003583488, 'block_total': 5127828, 'mount': '/', 'block_available': 4652721, 'size_available': 19057545216, 'fstype': 'ext4', 'inode_total': 1310720, 'options': 'rw,relatime', 'device': '/dev/loop30', 'inode_used': 23499, 'block_size': 4096, 'inode_available': 1287221}) => {
    "ansible_loop_var": "item",
    "changed": false,
    "item": {
        "block_available": 4652721,
        "block_size": 4096,
        "block_total": 5127828,
        "block_used": 475107,
        "device": "/dev/loop30",
        "fstype": "ext4",
        "inode_available": 1287221,
        "inode_total": 1310720,
        "inode_used": 23499,
        "mount": "/",
        "options": "rw,relatime",
        "size_available": 19057545216,
        "size_total": 21003583488,
        "uuid": "N/A"
    },
    "msg": "All assertions passed"
}
ok: [host32] => (item={'mount': '/', 'device': '/dev/loop31', 'fstype': 'ext4', 'options': 'rw,relatime', 'size_total': 21003583488, 'size_available': 18824105984, 'block_size': 4096, 'block_total': 5127828, 'block_available': 4595729, 'block_used': 532099, 'inode_total': 1310720, 'inode_available': 1283881, 'inode_used': 26839, 'uuid': 'N/A'}) => {
    "ansible_loop_var": "item",
    "changed": false,
    "item": {
        "block_available": 4595729,
        "block_size": 4096,
        "block_total": 5127828,
        "block_used": 532099,
        "device": "/dev/loop31",
        "fstype": "ext4",
        "inode_available": 1283881,
        "inode_total": 1310720,
        "inode_used": 26839,
        "mount": "/",
        "options": "rw,relatime",
        "size_available": 18824105984,
        "size_total": 21003583488,
        "uuid": "N/A"
    },
    "msg": "All assertions passed"
}

PLAY RECAP **********************************************************************************************************************************************************************************************************************************
host31                     : ok=8    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
host32                     : ok=8    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

Monday 16 May 2022  13:42:13 +0000 (0:00:00.140)       0:00:31.575 ************
===============================================================================
Gathering Facts --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 21.65s
test : Check connections to public --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 7.51s
test : Check connection Docker hub --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 1.30s
test : Check SUDO with NOPASSWD ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ 0.73s
test : Check disk space -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 0.14s
test : Check RAM --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 0.11s
test : Print status connection ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 0.06s
test : Print status connection ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 0.06s
Playbook run took 0 days, 0 hours, 0 minutes, 31 seconds



```


