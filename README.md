# RSA CM to EJBCA migration

You will be happy to find this script if you're migrating a RSA CM PKI infrastructure to EJBCA.
The last step of the data migration is to import the CRLs, but some revoked certificates might not be there.
Why? Because they could be expired or they were revoked after the CRL has been generated.

This script is here to save you life.
To use it, you need to export the RSA CM internal data store to LDIF format and find the jurisdiction IDs used by the CAs you're interrested in.

## Preparation

- Copy the CRL files (PEM format) in the "crls" directory
- Copy the LDIF file in the "ldif" directory
- Adapt `config.conf` according to your needs

## Running the script

Just run it without argument. You must have the "python-ldap" module on your system.
It will generate scripts in the "output" directory.
Copy them on your EJBCA servers and run them.

## Known issues
The script has been tested using Python 2.7 only.
The script only works if the RSA data store was on an external LDAP server. If your RSA data store was NOT on an external LDAP, you will need to adapt the key names in the script.
The name of the keys are different if the RSA data store is on an external LDAP or not...
