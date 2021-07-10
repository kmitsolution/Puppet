# Puppet Modules
In Puppet, a module can be defined as a collection of resources, classes, files, definition, and templates. Puppet supports easy re-distribution of modules, which is very helpful in modularity of code as one can write a specified generic module and can use it multiple times with very few simple code changes. For example, this will enable default site configuration under /etc/puppet, with modules shipped by Puppet proper in /etc/share/puppet.

## Create a module
```
puppet module generate rp-createuser

#init.pp
 class createuser {
 user { 'user1':
     ensure => present,
    }

}
```
 
##  Create site.pp to call the module

```
 node default {
 include 'createuser'
}
```

