# Puppet Templates 
Templating is a method of getting things in a standard format, which can be used in multiple locations

<ul>
  <li>Template Combine code and data to render a final document(like PHP)</li>
  <li>Useful for complex configuration files you would like to manage with puppet</li>
  <li>Puppet supports Embedded puppet (.epp) or Embedded Ruby Template(.erb)</li>
  <li>Stores templates in the modules templates/ directory</li>
  <li>Reference in your code with <<module name>>/<<template name>> <br />
    For example np/ntp.conf.epp </li>
    
</ul>  

### Example

Create a file called test.epp and write below code
```
      <% | String $text, Boolean $bool | -%>
      Text value is <%= $text %>

      <% if $bool { -%>
      bool is set to true
      <% } -%>

```

#### Validate the code
```
    puppet epp validate test.epp
```

#### render the code
```
     puppet epp render test.epp --values '{ text => "Hello World", bool => true }'
```
