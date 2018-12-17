---
layout: post
title:      "Ruby Class Methods"
date:       2018-12-17 03:57:41 +0000
permalink:  ruby_class_methods
---

We can think of class methods as factories that outputs objects. In general, Methods are stored in classes while data is stored in objects, which are instances of classes. 

A class method is defined as `def self.method` within a class. An example would be: 

```
class Artist
  attr_accessor :name
	
	def initialize(name)
	  @name = name
	end

def self.create
  artist_name = Artist.new(name)
  artist_name.save
  artist_name
end

end
```

This is a "factory" that creates a new artist where the class creates a new instance of itself. It will then, internally call the method` initialize` on the new object. The `initialize` method is the process of locating and using the defined values for variable data that is used by a program. 

After the class method `self.create` creates a new instance of an artist, it will be assigned to the variable `artist_name`. Then we have to save the variable and then return it. And that is a simple explaination of what a class method does.



