# cert provisioning

ansible 2.2.0+
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

```
$ ansible-playbook run.yml
```

This will create a `.openssl` and a `certs` folder in the playbook directory. The `.openssl` contains all the configuration and generated files necessary for cert generation and signing. The `certs` has all the good stuff: certs, cert chains, pkcs8, pkcs12, java keystore. The root / intermediate signing authorities private keys are not copied into the `certs` folder. These can be found in the `.openssl` folder (along with the generated password). The server and client private keys are in the `certs` folder, along with a generated password used for encrypting the pkcs12 and java keystore files.


##### TODO:
- Add truststore generation
- Fix paths to allow for remote path, default to local path. Maybe determine if running as a role?
- Look into supporting updates. Certs, keystores, etc.
