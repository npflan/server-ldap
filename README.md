# LDAP

Basic NPF OpenLDAP Container config, for NPF Helper basic authentication purposes.

## Start the Container

```
docker run --hostname ldap.npf.dk
       --detach
       --env LDAP_ORGANISATION="npf" \
       --env LDAP_DOMAIN="npf.dk" \
       --env LDAP_ADMIN_PASSWORD='<password>' \
       --env LDAP_READONLY_USER=true \
       --env LDAP_READONLY_USER_USERNAME=npf \
       --env LDAP_READONLY_USER_PASSWORD='<password>' \
       --volume <localPath>/data:/var/lib/ldap \
       --volume <localPath>/config:/etc/ldap/slapd.d \
       --env LDAP_TLS_CRT_FILENAME=<someCertificate>
       --env LDAP_TLS_KEY_FILENAME=<someKey>
       --env LDAP_TLS_CA_CRT_FILENAME=<someCACertificate>
       --volume <localPath>/certs:/container/service/slapd/assets/certs \
       --publish 389:389 \
       --publish 636:636 \
       --name openldap \
       osixia/openldap
```

## Fields

```
givenName
middleName
sn
initials
uid - username
title
mobilePhone
displayName
memberOf - groups
employeeNumber - username-independent identifier
emailAddress
department - optionally primary group name
```