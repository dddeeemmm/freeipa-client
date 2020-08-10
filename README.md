freeipa-client
=========

    Join hosts to FreeIPA domain

Requirements
------------

    FreeIPA Domain
    User with Enroll Permitions

Role Variables
--------------

    freeipa_client_dns_server               [not required]  list of dns servers for preconfigure resolv.conf
  
    freeipa_client_install_base_command     [default: ipa-client-install --unattended]  prefix join-command
    
    freeipa_client_install_options          [default:
                                              - '--domain={{ freeipa_client_domain }}'
                                              - '--server={{ freeipa_client_server | random }}'
                                              - '--realm={{ freeipa_client_realm }}'
                                              - '--principal={{ freeipa_client_principal }}'
                                              - '--password={{ freeipa_client_password }}'
                                              - '--hostname={{ freeipa_client_fqdn }}'
                                              - '--mkhomedir'
                                              - '--enable-dns-updates'
                                              - '--force-join'] suffix join-command
                                              
    freeipa_client_domain                   [default: {{ freeipa_client_realm | lower }}]   domain name
    freeipa_client_realm                    [required]  realm name for kerberos
    freeipa_client_principal                [required]  principal with enroll permitions
    freeipa_client_password                 [required]  principal password
    freeipa_client_fqdn                     [default: '{{ ansible_fqdn }}'] host fqdn

Dependencies
------------

    FreeIPA Domain
    Principal with enroll permitions

Example Playbook
----------------

    - hosts: servers
      vars:
        freeipa_client_realm: DOMAIN.ORG
        freeipa_client_principal: admin
        freeipa_client_password: password
      roles:
         - openvpn-client

License
-------

    MIT

Author Information
------------------

    Dmitrij Petrov
