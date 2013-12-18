---
layout: base
title: Generators
---

# Choose your generator

Each orm/odm can provide their own generator service that can replace the admingenerator.
 
Thereby greatly increasing the scope and flexibility including things which are not strictly for an admin site.

## Propel

Enable propel services in your `config.yml` :

~~~yaml
admingenerator_generator:
    use_propel: true
~~~
 
And in your generator.yml :
    
~~~yaml
generator: admingenerator.generator.propel
~~~

## Doctrine ORM

Enable doctrine orm services in your `config.yml` :

~~~yaml
admingenerator_generator:
    use_doctrine_orm: true
~~~
 
And in your generator.yml :

~~~yaml
generator: admingenerator.generator.doctrine
~~~

## Doctrine ODM mongo

Enable doctrine odm services in your `config.yml` :

~~~yaml
admingenerator_generator:
    use_doctrine_odm: true
~~~
 
And in your generator.yml :

~~~yaml
generator: admingenerator.generator.doctrine_odm
~~~