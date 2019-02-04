---
layout: post
title:      "The Importance of using Modules"
date:       2019-02-04 15:30:20 +0000
permalink:  the_importance_of_using_modules
---


Like classes, modules allow you to can create methods, however, you can't instantiate objects. Modules bundle objects which are used in classes to inherit its functionality instead of repeatedly re-writing these functionalities into every class. A module is also known as a superclass of a class. It means that you can use any method from the module and call it within another method within your class as long as you use `super` before using the method from the module. Your module might look something like this:

```
module Dog
  attr_accessor :dogs

  def dog_new
    @dogs = Set.new
  end

  def add_dog(dog)
    @dogs << dog
  end

  def remove_dog(dog)
    @dogs.delete(dog)
  end
end
```

And your class would include super to refernce the method from the module within the class:

class DogString < String
  include Dog
  def initialize(*args)
    super
    Dog_setup
  end
end

The super keyword can be used to call a method of the same name in the superclass of the class making the call. It passes all the arguments to parent class method.  It's useful to use for inherited classes so that it has the same functionality and you can add different functionalities to the other classes as well. 






