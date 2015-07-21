---
title:  "Create your own Dictionaries for OS X"
date:   2014-12-27 13:37
description: Apple's Dictionary is one of the many powerful...
---

Apple's Dictionary is one of the many powerful tools that ship with OS X, but sadly its one of the least used ones. Since the introduction in OS X 10.4 Tiger the number of dictionaries increased in every major version and it always got some love from the Apple engineers.

My favorite and most powerful feature was introduced with OS X 10.7 Lion: by pressing **Shift + CMD + D**  a small WebView popover gets displayed in any application on your Mac. This can be used to display anything you want for example code documenation or cat pictures.

![Dictionary.app]({{ site.url }}/assets/images/dictionary.png)

# Create your own Dictionary
First of all, we need the Dictionary Development Kit. Because of structual changes in Xcode 4 the  Kit got lost in one kf the tool packages. You can find it in the **Auxilliary Tools for Xcode - October 2013** from Apple's Developer Center or [at Github](https://github.com/SebastianSzturo/Dictionary-Development-Kit).


# Project Template
In the Dictionary Development Kit you can find a folder named ```project_templates```. It contains a Makefile, stylesheet and an xml file that contains your dictionary.

You probably want to automate the creation of your dictionary xml file. If you are familiar with ruby, checkout my gem [Inaho](https://github.com/SebastianSzturo/inaho), it could save you a lot of time.

{% highlight ruby %}
dictionary = Inaho::Dictionary.new

entry = Inaho::Entry.new(id: 1, title: "稲穂", yomi: "いなほ")
entry.add_index("稲穂")
entry.add_index("いなほ")
entry.add_index("inaho")
entry.add_index("ear (head) of rice")
entry.body = "稲穂 (いなほ) <ul><li>ear (head) of rice</li></ul>"

dictionary << entry
{% endhighlight %}


# Build your Dictionary
Change the path to your Dictionary Development Kit your ```Makefile``` on line 25 and use it to build and install your dictionary.

{% highlight bash %}
make # Generates a .dictionary bundle.
make install # Copy your bundle to "~/Library/Dictionaries"
{% endhighlight %}

# Additional Documentation
Check out Apple's [Dictionary Services Programming Guide](https://developer.apple.com/library/mac/documentation/UserExperience/Conceptual/DictionaryServicesProgGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40006152-CH1-SW1) for an in-depth guide of all the powerful features of OS X dictionaries like dictionary preferences and support for foreign writing systems.
