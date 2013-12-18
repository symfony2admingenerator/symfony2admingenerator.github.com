---
layout: documentation
title: Check credentials
---

# Security: Check credentials ?

## For actions

Setting up security credentials is now easy, since it integrates with the Symfony security context and uses their terminology. 

**Symfony 1**: 'credentials' required complex expressions like [ A, [[ B, C ]]]

**Admin generator:** uses Symfony 2 ROLEs to directly secure the  route - e.g. hasRole("ROLE_A").

Therefore, for each action, simply define the roles that should be applied.

~~~yaml
builders:
  edit:
    params:
      credentials: 'hasRole("ROLE_A") or (hasRole("ROLE_B") and hasRole("ROLE_C"))'
~~~

This fully secures the edit action for the applicable route , and will throw an AccessDeniedException if the user does not have this role.

If the credential definition is omitted then the security context will be defaulted to the symfony firewall configuration.

Here is another example for the list action::

~~~yaml
builders:
  list:
    params:
      object_actions:
        credentials: 'hasRole("ROLE_Z")'
~~~


## For columns and forms

Security can be defined at the field level using the same format as 'actions';

~~~yaml
params:
  fields:
    fieldName:
      credentials: 'hasRole("ROLE_A") or (hasRole("ROLE_B") and hasRole("ROLE_C"))'
~~~

## Symfony ACL

You'll probably want to use the symfony ACL, for example to check the `OWNER` permission

~~~yaml
params:
  fields:
    fieldName:
      credentials: 'hasPermission(object, "OWNER")'
~~~

>**Tip**<br />You must keep the object variable name DO NOT REPLACE with your model name

For the symfony doc read it :

* [http://symfony.com/doc/2.0/reference/configuration/security.html](http://symfony.com/doc/2.0/reference/configuration/security.html)
* [http://symfony.com/doc/2.0/cookbook/security/acl_advanced.html](http://symfony.com/doc/2.0/cookbook/security/acl_advanced.html)

