# Visual Index

This page can help you find syntax elements when you can’t remember their names.
```
    file {'ntp.conf':
      path    => '/etc/ntp.conf',
      ensure  => file,
      content => template('ntp/ntp.conf'),
      owner   => 'root',
      mode    => '0644',
    }
```

A resource declaration.

* file: The resource type
* ntp.conf: The title
* path: An attribute
'/etc/ntp.conf': A value; in this case, a string
* template('ntp/ntp.conf'): A function call that returns a value; in this case, the template function, with the name of a template in a module as its argument

```
 package {'ntp':
      ensure => installed,
      before => File['ntp.conf'],
    }
    service {'ntpd':
      ensure    => running,
      subscribe => File['ntp.conf'],
    }
```

Two resources using the before and subscribe relationship metaparameters (which accept resource references).
```
    Package['ntp'] -> File['ntp.conf'] ~> Service['ntpd']
```

 Chaining arrows forming relationships between three resources, using resource references.
```
    $package_list = ['ntp', 'apache2', 'vim-nox', 'wget']
```