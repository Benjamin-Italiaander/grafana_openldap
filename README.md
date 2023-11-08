# grafana_openldap
Using departmentNumber as group in grafana using openldap \

I had serious issues with assigning roles to grafana using openldap. After all it seemed really easy. have a look at my ldap.toml example \

the trick is to assing the attribute at the servers.attributes so in my case 

\[servers.attributes\] \
member_of = "departmentNumber" # this line passes the content of departmentNumber to group_dn at your servers.group_mappings \
email =  "mail" \
name = "givenName" \
surname = "sn" \
username = "displayName" 

\[\[servers.group_mappings\]\] \
group_dn = "sysadmin" # Sysadmin is in this example departmentNumber because i did declare it at servers.attributes \
org_role = "Admin" \
grafana_admin = true \ 

