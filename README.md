# cert provisioning
##### WIP, not fully tested.

ansible 2.2.0
```
$ git clone git@github.com:jpcarey/cert_provisioning.git
$ cd cert_provisioning
```
Customize `run.yml`:
The `authorities` dictionary consists of the following:
- One or more root level authorities, defined by Distinguished Name `DN`
- Each authority can have `children`
- Each authority can have `servers`
- Each authority can have `clients`

If you generate a string in `./certs/passwd`, this will be used for the private keys.  If not, a random value will be generated on first run.

```
$ ansible-playbook run.yml
```


##### TODO:
- Test / fix DN for server and client certs
- Create passwd per authority. Document behavior.
- Server certs do not have X509v3 Authority Key Identifier
- Add truststore generation
- Add server & client cert support for root authority (? maybe)
- Fix paths to allow for remote path, default to local path. Maybe determine if running as a role?
- Look into supporting updates. Certs, keystores, etc.
