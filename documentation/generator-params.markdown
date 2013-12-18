---
layout: base
title: Params section of generator.yml
---

# Params section of generator.yml

## Bundle in Acme/Bundle/TestBundle ?

If you have "non-standard" structure of bundle and your bundles namespaces are Acme/Bundle/TestBundle and not Acme/TestBundle,
you have to update the generator.yml like that :

~~~yaml
params:
  model: ......
  namespace_prefix: Acme
  subfolder: Bundle
  bundle_name: TestBundle
~~~

## Custom stylesheets

Sometimes, you'll want to add your own css in the theme. Two way to do that :

### In the config.yml

~~~yaml
admingenerator_generator:
    stylesheets:
      - { path: bundles/mybundle/css/backend.css }
      - { path: bundles/mybundle/css/print.css, media: print }
~~~

### In the generator.yml

~~~yaml
params:
  model: ......
  stylesheets:
    - bundles/mybundle/css/backend.css
    - { path: bundles/mybundle/css/tv.css, media: tv }
~~~

## Custom javascripts

Sometimes, you'll want to add your own js in the theme. Two way to do that :

### In the config.yml

~~~yaml
admingenerator_generator:
    javascripts:
      - { path: bundles/mybundle/js/backend.js }
      - { route: "fos_js_routing_js", routeparams: { callback: "fos.Router.setData"} }
~~~

### In the generator.yml

~~~yaml
params:
  model: ......
  javascripts:
    - bundles/mybundle/js/backend.js
    - { path: bundles/mybundle/js/backend.js }
    - { route: "fos_js_routing_js", routeparams: { callback: "fos.Router.setData"} }
~~~
