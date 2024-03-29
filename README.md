# Add nginx proxy configuration

This role adds and enables a reverse proxy configuration to an existing nginx
instance.

## Requirements

* `nginx`
* An SSL cert for the domain.
* In your local machine:

  ```bash
  pip install -r requirements.txt
  ```

## Role Variables

* `domain`: domain (or subdomain) for the reverse proxy to bind to.
* `binded_port`: Internal binded port of the service we want the proxy to reach
   .
* `external_port`: External binded port through which the proxy will be
   accessible (with SSL/TLS).
* `ssl_certificate`: Path to the SSL cert file.
* `ssl_certificate_key`: Path to the SSL private key file.
* `template_path`: Path to the template for the nginx vhost configuration.

## Dependencies

None.

## Example Playbook

```yaml
- name: Add nginx proxy configuration
  hosts: all
  vars:
    binded_port: 8000
    domain: anarres.local
  roles:
    - role: add_nginx_proxy_conf
```

**Note**: by default this role will use the SSL cert files found in
*/etc/letsencrypt/live/{{ domain }}/*.

## Testing

To test the role you need [molecule](http://molecule.readthedocs.io/en/latest/),
**docker** and some python requirements that can be installed wwith
`pip install -r requirements-dev.txt`.

```bash
molecule test
```

or

```bash
make test
```

## License

GPLv3

## Author Information

* m0wer: m0wer (at) autistici (dot) org
