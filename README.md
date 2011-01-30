vim-MakeGreen
=============

makegreen.vim is a vim (http://www.vim.org) plugin that runs make and shows the
test run status with a red or green bar.

Mitechie Fork
-------------
Check the original for the real deal. This is me tweaking how it runs the files
based on my usage. I keep a matching test file for files I'm working on. So for
file `email.py` I'll have `test_email.py`. So it prepends test_ to the
filenames.

I also often want to rerun the tests while I'm on the test file itself, so it
will catch that I'm on a test file and just rerun it.


Installation
------------

Copy all files to your ~/.vim directory or use Tim Pope's excellent pathogen plugin (http://github.com/tpope/vim-pathogen).

Usage
-----

&lt;Leader&gt;t will run make for the current file and show its status with a red or green message bar.

example:

    $ cd <your rails/merb root>
    $ vim test/unit/user_test.rb

    :compiler rubyunit
    press <Leader>t

(&lt;Leader&gt; is mapped to '\' by default)


Default Key Bindings
--------------------

&lt;Leader&gt;t: run make and show red/green bar

You can change default key bindings:

    map <Leader>] <Plug>MakeGreen " change from <Leader>t to <Leader>]

Configuring Vim's Makeprg
-------------------------

MakeGreen expects your make program to accept the current file name as its
argument. Specifically, if `:make %` works, MakeGreen will work.

Using Compilers
---------------

The easiest way to use MakeGreen is with compilers. For instance, vim's ruby
configuration files provide an rspec compiler that sets makeprg and errorformat
appropriately for running specs and parsing their output.

You can tell vim to use the rspec compiler for all *_spec.rb files by adding
this line to your vimrc:

      autocmd BufNewFile,BufRead *_spec.rb compiler rspec

Then `:make %` (make current file) and MakeGreen will work automatically when
you are in a spec.

Credits
-------

- Based on code from the rubytest.vim plugin
  (http://github.com/reinh/vim-rubytest) but considerably refactored and
  modified for this more specific purpose.

- Red/Green bar code borrowed from Gary Bernhardt
  (http://bitbucket.org/garybernhardt/dotfiles/src/tip/.vimrc) and slightly
  modified for my use. Please do check out Gary's coding videos on his blog
  for more awesome vim usage (http://blog.extracheese.org/).

- elik and godlygeek in #vim on irc.freenode.net for vim help

- Jim Remsik (@jremsikjr on twitter) for debugging and typo fixing.
