---
title:  "Managing multiple Test Suites in your CI"
date:   2016-01-15 13:37
description: Sometimes you are forced to use multiple test...
---

Sometimes you are forced to use multiple test suites in one project. Travis and CircleCI are usually
really good at detecting all your different test suites in your project. But if your mix technologies
like [rails and ember-cli](https://github.com/thoughtbot/ember-cli-rails), things can get a little messy.

The easiest way to run multiple tests suites on your CI is to manage the tasks you want to execute yourself.
For this example we will combine all of our test suite runners in one "rake ci" command.
At CircleCI you can override the default inferred commands in your **circle.yml**:

{% highlight yaml %}
test:
  override:
    - bundle exec rake ci
{% endhighlight %}

There are [several different ways](http://tech.natemurray.com/2007/03/ruby-shell-commands.html) to run shell commands in ruby. We will use the **system** commands provided by ruby's standard library.
It will start the process in a subshell and print them to stdout. The command returns false if the command exited with a non-zero status code and true otherwise.

{% highlight ruby %}
task :ci do
  rspec = system("bundle exec rspec")
  minitest = system("bundle exec rake test")
  ember_test = system("./frontend/ember test")

  all_tests_passed = rspec && minitest && ember

  build_ember if ember_test
  trigger_deployment if all_tests_passed && ENV["CI"]
end
{% endhighlight %}

We can easily add post-build commands to our CI and make sure our changes only get deployed if all test suites pass.
