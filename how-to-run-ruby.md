# Running your Ruby Scripts

You'll interact with your .rb files in a very similar way to your .js files.

You'll use the `ruby` command and the repl `pry` instead of using $`node` like you might do for JavaScript. <br>
REPL stands for Read-Evaluate-Print-Loop

### REALLY IMPORTANT

Ruby *DOES NOT* run in the browser. It is *purely* a server side. You will only be able to load it into the terminal.


## Running ruby files

1. touch a file `test.rb`

2. add a line `puts "Hello from test.rb"`

3. run the file using ruby from the terminal $`ruby test.rb`

## Running ruby in the REPL

Ruby comes with a REPL called `irb` (Interactive Ruby Shell).  This is similar to us using the `node` command to write JS in the command line.  While irb is good for basic ruby, there is another option called `pry` which is like irb with superpowers.

## Gems

RubyGems is a package manager for Ruby that provides a standard format for distributing
Ruby libraries (in a self-contained format called a "gem"), a tool designed to easily
manage the installation of gems, and a server for distributing them. It was created in
2004.

![](images/rubygems.jpg)

Let's install some not so useful Gems.

```bash
gem install lolcat
gem install cowsay
```

