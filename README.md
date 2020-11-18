# san.cnf
This the configuration file  used for certificate requests (CSR) or Key generation.

In order to create a CSR and generate a  Key, follow the below steps:
1) Create san.cnf with your editor of choice(vi used here)
    vi san.cnf
2) Edit san.cnf and add the following:

[ req ]
default_bits       = 2048
distinguished_name = req_distinguished_name
req_extensions     = req_ext

[ req_distinguished_name ]
countryName                 = Country Name (2 letter code)
countryName_default 		= your 2 country Letter code(US, CA, DE)
stateOrProvinceName         = State or Province Name (full name)
stateOrProvinceName_default = our 2 state Letter code(CA, TX, BC)
localityName               = Locality Name (eg, city)
localityName_default 	   = Vancouver
organizationName           = Organization Name (eg, company)
organizationName_default   = ACME Inc
organizationalUnitName     = Organizational Name (eg, department)
organizationalUnitName_default	= ACME Inc Department
commonName                 = Common Name (e.g. server FQDN or YOUR name)
commonName_default		   = coolserver
[ req_ext ]
subjectAltName = @alt_names
[alt_names]
DNS.1   = coolserver
DNS.2   = coolserver.fqdn
IP.1    = 172.16.11.11

3)Syntax:
penssl req -out sslcert.csr -newkey rsa:2048 -nodes -keyout private.key -config san.cnf
