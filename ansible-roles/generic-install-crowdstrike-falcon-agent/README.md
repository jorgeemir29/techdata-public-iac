
Techdata Public Ansible Role - Install and Configure Crowdstrike Falcon Agent.
=========

This role is used to install and configure from scratch the Crowdstrike Falcon Agent on Windows Server 2k16 and Linux Servers (RHEL7/Centos7/ Linux AWS).

Requirements
------------

[Winodws]

* Server must be already joined to a windows domain or winrm listener must accept remote connections from any source.
* Installer path for the falcon agent, must be provided according to your environment.
* Customer ID must be provided according to your environment and subcription.

[Windows-Proxy]

* Server must be already joined to a windows domain or winrm listener must accept remote connections from any source.
* Installer path for the falcon agent, must be provided according to your environment.
* Customer ID must be provided according to your environment and subcription.
* Access to HTTP Proxy or Coorporate Proxy.
* HTTP Proxy must be able to reach the crodwstrike falcon cloud controllers.

[Linux RHEL]

* Target server must be already registred and with a valid SKU.
* SSH Public/Private Keys Registred between Satellites and Target Servers.
* Installer path for the falcon agent, must be provided according to your environment.
* Customer ID must be provided according to your environment and subcription.


*_Note: if there is no a valid RHEL subcription, you need to setup Redmin , EPEL and Alternative CentOS repositories._*


[Linux RHEL-Proxy]

* Installer path for the falcon agent, must be provided according to your environment.
* Customer ID must be provided according to your environment and subcription.
* Installer path for the falcon agent, must be provided according to your environment.
* Customer ID must be provided according to your environment and subcription
 
*_Note: if there is no a valid RHEL subcription, you need to setup Redmin , EPEL and Alternative CentOS repositories_*




Role Variables
--------------
Below variables must be defined in the configuration manifest.

windows:
  - csf_exe: WindowsSensor.exe
  - csf_exe_url: "{{ url }}/{{ csf_exe }}"
  - csf_exe_checksum:

linux-rhel7:
  - csf_rpm: falcon-sensor-4.5.0-5015.el7.x86_64.rpm
  - csf_rpm_url: "{{ url }}/{{ csf_rpm }}"
  - csf_rpm_checksum: 


linux-ami2:

  - csf_rpm: falcon-sensor-5.29.0-9402.amzn2.x86_64.rpm
  - csf_rpm_url: "{{ url }}/{{ csf_rpm }}"
  - csf_rpm_checksum: 



Dependencies
------------

No Dependencies.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

[Target Servers Behind a Coorporate Proxy]

    - hosts: servers
      roles:
         - role: generic-install-crowdstrike-falcon-agent 
           vars:
             USE_PROXY: True
             HTTP_PROXY: http://my-overwrite-proxy-server-here.unsecure-world.com:3128
             PROXY_SERVER: my-overwrite-proxy-server-here.unsecure-world.com
             PROXY_PORT: 3128
             MY_GROUPING_TAGS: "YOUR-OVERWRITE-TAGS,YOUR-SUPER-SECURE-SERVER,YOUR-SECURITY-TAG,LANDSCAPE"
             CUSTOMER_ID: "YOUR-CUSTOMER-ID-HERE"

[Target Servers without Proxy]

    - hosts: servers
      roles:
         - role: techdata/generic-install-crowdstrike-falcon-agent 
           vars:
             MY_GROUPING_TAGS: "YOUR-OVERWRITE-TAGS,YOUR-SUPER-SECURE-SERVER,YOUR-SECURITY-TAG,LANDSCAPE"
             CUSTOMER_ID: "YOUR-CUSTOMER-ID-HERE"


License
-------

Techdata OpenSource.

Author Information
------------------

IT Infrastructure Design Team - EUROPE.
