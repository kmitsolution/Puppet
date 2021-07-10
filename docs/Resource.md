# Puppet Resource

Resources are one of the key fundamental units of Puppet used to design and build any particular infrastructure or a machine. They are mainly used for modeling and maintaining system configurations. Puppet has multiple type of resources, which can be used to define the system architecture or the user has the leverage to build and define a new resource.</ br>
The block of Puppet code in manifest file or any other file is called a resource declaration. The block of code is written in a language called Declarative Modelling Language (DML). Following is an example of how it looks like.
```
        user { 'testuser': 
           ensure => present, 
           uid    => '552', 
           shell  => '/bin/bash', 
           home   => '/home/testuser', 
        }
```
<ul>
  <li><b>Resource Type</b> − In the above code snippet, it is the user.</li>
  <li><b>Resource Parameter</b> − In the above code snippet, it is testuser.</li>
  <li><b>Attributes</b> − In the above code snippet, it is ensure, uid, shell, home.</li>
   <li></b>Values</b> − These are the values that correspond to each property.</li>
</ul>  

## Resource Type
There are different types of resources available in Puppet which have their own way of functionality. These resource types can be viewed using the “describe” command along with the “-list” option.
```
      puppet describe --list
```

## Resource Title
In the above code snippet, we have resource title as testuser which is unique for each resource used in the same file of the code. This is a unique title for this user resource type. We cannot have a resource with the same name because it will cause conflicts.

Resource command can be used to view the list of all the resources using type user.
```
      puppet resource user 
      #Listing the Resources of a Particular User
      puppet resource user tomcat 
```

## Attributes & Values
The main body of any resource is made up of a collection of attribute-value pairs. Here one can specify the values for a given resource’s property. Each resource type has its own set of attributes that can be configured with the key-value pairs.

 In the following example, we have the details about the user resource along with all its configurable attributes.
 ```
    puppet describe user 
 ```
 
 ## Resource Abstraction Layer
 In Puppet, Resource Abstraction Layer (RAL) can be considered as the core conceptualized model on which the whole infrastructure and Puppet setup works. In RAL, each alphabet has its own significant meaning which is defined as follows.

### Resource [R]
A resource can be considered as all the resources which are used to model any configuration in Puppet. They are basically in-built resources which are by default present in Puppet. They can be considered as a set of resources belonging to a pre-defined resource type. They are similar to OOP concept in any other programming language wherein the object is an instance of class. In Puppet, its resource is an instance of a resource type.

### Abstraction [A]
Abstraction can be considered as a key feature where the resources are defined independently from the target OS. In other words, while writing any manifest file the user need not worry about the target machine or the OS, which is present on that particular machine. In abstraction, resources give enough information about what needs to exist on the Puppet agent.

Puppet will take care of all the functionalities or magic happening behind the scene. Regardless of the resources and OS, Puppet will take care of implementing the configuration on the target machine, wherein the user need not worry how Puppet does behind the scenes.

In abstraction, Puppet separates out the resources from its implementation. This platformspecific configuration exists from providers. We can use multiple subcommands along with its providers.

### Layer [L]
It is possible that one defines an entire machine setup and configuration in terms of collection of resources, and it can be viewed and managed via Puppet’s CLI interface.

<b>Example for User Resource Type</b>
```
   puppet describe user --providers 
```
