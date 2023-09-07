### isp-mail-bookworm

- Before performing any action, choose two domains :

  - the first for your fqdn and webmail (for example : mail.domain.tld and webmail.domain.tld)
  - the second for your virtual domain (future mail adress)

- Don't forget to add fqdn server and webmail subdomains in dns zone (A record target your vps ipv4 
  wait 24h after A record creation in your dns zone)

- Also reverse dns is very important to configure (usualy on your vps) before working with this playbook

- This playbook was succefully tested on OVHcloud vps (starter is perfect for few mail adress)

- In this playbook version ansible host connects to the server with ssh key (some actions have to be performed before launching the playbook)

- ipv4 is disabled on this playbook version. Feel free to remove ipv4 deactivation and manage both ipv4/6

- certicates creation is managed (don't launch the playbook before 24h propagation of dns change)

- security role is just a start and/or example for your future security policy

- monitoring will be add in future version of this playbook


### Vars file with some explanations


	Base config

	  hostname: #hostname you will define for your server ex: mail

	  ipv4_adress: #ipv4 of your server

	  localdomain: #domain you will use for server fqdn and/or webmail

	  server_admin: Machtorn

	  admin_ip: #your public ip (access to rspamd interface)

	  ssh_port: 22


	Apache config

	  webmail: #name of your webmail (usually webmail)

	  mailadministrator: #your admin email

	  roundcube_vhost: webmail-http.conf


	Mariadb credentials

	  mariadb_root: #mariadb root passwd

	  mailadmin: #mariadb admin passwd

	  mailserver: #mariadb server passwd


	Rspamd interface password

	  rspamdpwd: #passwd rspamd gui


	dkim configuration

	  selector: #selector for your public key in dns zone


	Add domain and user

	  virtualdomain: #domain you want to use with your mail adress

	  emailadress: #your future mail adress

	  password: #default password defined for your mail adress (user should change it after email creation)


- Don't forget to declare public key of dkim on your "virtual domain" dns zone.
