# cert provisioning
##### WIP, not fully tested.

ansible 2.2.0
```
$ git clone git@github.com:jpcarey/cert_provisioning.git
$ cd cert_provisioning
```
Customize `run.yml`:
The `authorities` dictionary consists of the following:
- One or more root level authorities, defined by Common Name `CN`
- Each authority can have `children`
- Each authority can have `servers`
- Each authority can have `clients`

If you generate a string in `./certs/passwd`, this will be used for the private keys.  If not, a random value will be generated on first run.

```
$ ansible-playbook run.yml
```


##### TODO:
- Need to add client cert setup
- SAN for server and client setup
- Generate multiple formats (currently just PEM): pks12, keystore / truststore, DER
- Cleanup & Testing
