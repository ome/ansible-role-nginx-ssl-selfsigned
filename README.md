SSL Certificates
================

Manage SSL certificates for web-servers.

Optionally generate self-signed SSL certificates for internal testing.


Role Variables
--------------

Defaults: `defaults/main.yml`

Optional variables:
- `ssl_certificate_path`: Server path to SSL certificate
- `ssl_certificate_key_path`: Server path to SSL certificate key
- `ssl_certificate_combined_path`: Server path to SSL combined certificate and key (e.g. for Haproxy), set to empty to disable
- `ssl_certificate_content`: Text content of the certificate, for instance from vault
- `ssl_certificate_key_content`: Text content of the certificate key
- `ssl_certificate_selfsigned_create`: Create a self-signed certificate if necessary, default `True`
- `ssl_certificate_selfsigned_subject`: Self-signed certificate subject
- `ssl_certificate_selfsigned_days`: Self-signed certificate validity (days)


Note this role does not configure or restart any webserver for SSL.
This should be handled elsewhere.


Example Playbooks
-----------------

Create a self-signed certificate with defaults:

    - hosts: all
      roles:
        - role: ssl-certificate

Install certificates stored in Ansible vault:

    - hosts: all
      roles:
        - role: ssl-certificate
          ssl_certificate_content: "{{ vault_certificate }}"
          ssl_certificate_key_content: "{{ vault_certificate_key }}"
          ssl_certificate_selfsigned_create: False


Author Information
------------------

ome-devel@lists.openmicroscopy.org.uk
