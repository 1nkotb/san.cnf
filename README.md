# san.cnf
This the configuration file  used for certificate requests (CSR) or Key generation.

In order to create a CSR and generate a  Key, follow the below steps:
1) Create san.cnf with your editor of choice(vi used here)
    vi san.cnf
2) Edit san.cnf and add the following:

[ req ] <br />
default_bits       = 2048 <br />
distinguished_name = req_distinguished_name <br />
req_extensions     = req_ext <br />
<br />
[ req_distinguished_name ] <br />
countryName                 = Country Name (2 letter code) <br />
countryName_default 		= your 2 country Letter code(US, CA, DE) <br />
stateOrProvinceName         = State or Province Name (full name) <br />
stateOrProvinceName_default = our 2 state Letter code(CA, TX, BC) <br />
localityName               = Locality Name (eg, city) <br />
localityName_default 	   = Los Angeles <br />
organizationName           = Organization Name (eg, company) <br />
organizationName_default   = ACME Inc <br />
organizationalUnitName     = Organizational Name (eg, department) <br />
organizationalUnitName_default	= ACME Inc Department <br />
commonName                 = Common Name (e.g. server FQDN or YOUR name) <br />
commonName_default		   = coolserver <br />
<br />
[ req_ext ]  <br />
subjectAltName = @alt_names <br />
[alt_names] <br />
DNS.1   = coolserver <br />
DNS.2   = coolserver.fqdn <br />
IP.1    = 172.16.11.11 <br />
<br />
3)Syntax:
penssl req -out sslcert.csr -newkey rsa:2048 -nodes -keyout private.key -config san.cnf
