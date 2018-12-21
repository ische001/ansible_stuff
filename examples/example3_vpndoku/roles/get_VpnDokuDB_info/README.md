Role Name
=========

get_VpnDokuDB_info - Get information about a VPN from VPN-Doku-DB

Requirements
------------

No requirements

Role Variables
--------------

vpn_name = Unique name of the VPN for which information shall be requested from VPN-Doku-DB. Expected to be set outside the role.

vpn_doku_db = Dictionary containing information to access VPN-Doku-DB
    vpn_doku_db.description = Brief description
    vpn_doku_db.base_url = Base URL for REST API calls to VPN-Doku-DB
    vpn_doku_db.verify_server = Check HTTPS Certificate of VPN-Doku-DB
    vpn_doku_db.user = use this user name to login to VPN-Doku-DB
    vpn_doku_db.pwd = use this password to login to VPN-Doku-DB

The role will set facts:
vpn_name = Unique name of the VPN
vlan_id = ID of the VLAN used for the user network 
vlan_id_usernet = ID of the VLAN used for the user network
rt = Route Target used for the VPN
vpn_network_list = 

Dependencies
------------

No dependencies

Example Playbook
----------------


  vars_prompt:
    - name: "vpn_name"
      prompt: "Enter the name of the VPN"
      private: no

  tasks:
    - name: "Get VPN information from VPN-Doku-DB" 
      include_role:
        name: get_VpnDokuDB_info

    - name: "Show basic information obtained from VPN-Doku-DB"
      debug:
        msg: "vpn_name = {{vpn_name}}, vlan_id = {{vlan_id}}, vlan_id_usernet = {{vlan_id_usernet}}, rt = {{rt}}"
        verbosity: 1

    - name: "Show network list obtained from VPN-Doku-DB"
      debug:
        var: vpn_network_list
        verbosity: 1

License
-------

Ask DB Systel

Author Information
------------------

erich.gaede@devoteam.com
