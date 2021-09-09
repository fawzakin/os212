---
layout: "layout"
permalink: /TIPS/
---
# Fawzan's useful tips for Operating System Class
Note that this page assumes that you are using Linux (Ubuntu, Arch, or any distro really) as your main OS. Some of the tips here may be able to help you regardless if you are on Windows or MacOS.

Table of Content (use ctrl+f to search them):
- [1] Cannot generate Github page locally
- [2] NEVER use EFI for your debian VM
 
### [1] Cannot generate Github page locally
If you encounter this kind of error when generating your github page locally like this:
```
Configuration file: /drive/Data/git/os212/_config.yml
            Source: /drive/Data/git/os212
       Destination: /drive/Data/git/os212/_site
 Incremental build: disabled. Enable with --incremental
      Generating... 
                    done in 2.9 seconds.
jekyll 3.9.0 | Error:  no implicit conversion of Hash into Integer
/home/fawzan/.local/share/gem/ruby/3.0.0/gems/pathutil-0.16.2/lib/pathutil.rb:502:in `read': no implicit conversion of Hash into Integer (TypeError)
	from /home/fawzan/.local/share/gem/ruby/3.0.0/gems/pathutil-0.16.2/lib/pathutil.rb:502:in `read'
	from /home/fawzan/.local/share/gem/ruby/3.0.0/gems/jekyll-3.9.0/lib/jekyll/utils/platforms.rb:75:in `proc_version'
	from /home/fawzan/.local/share/gem/ruby/3.0.0/gems/jekyll-3.9.0/lib/jekyll/utils/platforms.rb:40:in `bash_on_windows?'
	from /home/fawzan/.local/share/gem/ruby/3.0.0/gems/jekyll-3.9.0/lib/jekyll/commands/build.rb:77:in `watch'
	from /home/fawzan/.local/share/gem/ruby/3.0.0/gems/jekyll-3.9.0/lib/jekyll/commands/build.rb:43:in `process'
	from /home/fawzan/.local/share/gem/ruby/3.0.0/gems/jekyll-3.9.0/lib/jekyll/commands/serve.rb:93:in `block in start'
	from /home/fawzan/.local/share/gem/ruby/3.0.0/gems/jekyll-3.9.0/lib/jekyll/commands/serve.rb:93:in `each'
	from /home/fawzan/.local/share/gem/ruby/3.0.0/gems/jekyll-3.9.0/lib/jekyll/commands/serve.rb:93:in `start'
	from /home/fawzan/.local/share/gem/ruby/3.0.0/gems/jekyll-3.9.0/lib/jekyll/commands/serve.rb:75:in `block (2 levels) in init_with_program'
	from /home/fawzan/.local/share/gem/ruby/3.0.0/gems/mercenary-0.3.6/lib/mercenary/command.rb:220:in `block in execute'
	from /home/fawzan/.local/share/gem/ruby/3.0.0/gems/mercenary-0.3.6/lib/mercenary/command.rb:220:in `each'
	from /home/fawzan/.local/share/gem/ruby/3.0.0/gems/mercenary-0.3.6/lib/mercenary/command.rb:220:in `execute'
	from /home/fawzan/.local/share/gem/ruby/3.0.0/gems/mercenary-0.3.6/lib/mercenary/program.rb:42:in `go'
	from /home/fawzan/.local/share/gem/ruby/3.0.0/gems/mercenary-0.3.6/lib/mercenary.rb:19:in `program'
	from /home/fawzan/.local/share/gem/ruby/3.0.0/gems/jekyll-3.9.0/exe/jekyll:15:in `<top (required)>'
	from /home/fawzan/.local/share/gem/ruby/3.0.0/bin/jekyll:23:in `load'
	from /home/fawzan/.local/share/gem/ruby/3.0.0/bin/jekyll:23:in `<top (required)>'
	from /home/fawzan/.local/share/gem/ruby/3.0.0/gems/bundler-2.2.27/lib/bundler/cli/exec.rb:58:in `load'
	from /home/fawzan/.local/share/gem/ruby/3.0.0/gems/bundler-2.2.27/lib/bundler/cli/exec.rb:58:in `kernel_load'
	from /home/fawzan/.local/share/gem/ruby/3.0.0/gems/bundler-2.2.27/lib/bundler/cli/exec.rb:23:in `run'
	from /home/fawzan/.local/share/gem/ruby/3.0.0/gems/bundler-2.2.27/lib/bundler/cli.rb:477:in `exec'
	from /home/fawzan/.local/share/gem/ruby/3.0.0/gems/bundler-2.2.27/lib/bundler/vendor/thor/lib/thor/command.rb:27:in `run'
	from /home/fawzan/.local/share/gem/ruby/3.0.0/gems/bundler-2.2.27/lib/bundler/vendor/thor/lib/thor/invocation.rb:127:in `invoke_command'
	from /home/fawzan/.local/share/gem/ruby/3.0.0/gems/bundler-2.2.27/lib/bundler/vendor/thor/lib/thor.rb:392:in `dispatch'
	from /home/fawzan/.local/share/gem/ruby/3.0.0/gems/bundler-2.2.27/lib/bundler/cli.rb:31:in `dispatch'
	from /home/fawzan/.local/share/gem/ruby/3.0.0/gems/bundler-2.2.27/lib/bundler/vendor/thor/lib/thor/base.rb:485:in `start'
	from /home/fawzan/.local/share/gem/ruby/3.0.0/gems/bundler-2.2.27/lib/bundler/cli.rb:25:in `start'
	from /home/fawzan/.local/share/gem/ruby/3.0.0/gems/bundler-2.2.27/exe/bundle:49:in `block in <top (required)>'
	from /home/fawzan/.local/share/gem/ruby/3.0.0/gems/bundler-2.2.27/lib/bundler/friendly_errors.rb:128:in `with_friendly_errors'
	from /home/fawzan/.local/share/gem/ruby/3.0.0/gems/bundler-2.2.27/exe/bundle:37:in `<top (required)>'
	from /home/fawzan/.local/share/gem/ruby/3.0.0/bin/bundle:23:in `load'
	from /home/fawzan/.local/share/gem/ruby/3.0.0/bin/bundle:23:in `<main>'
```
That means you have ruby version 3.0.0. Jekyll, currently, doesn't support such version. You should install the version 2.7.3.

Steps to fix it in Linux using `rbenv`:
1. Install `rbenv` and `ruby-build` (I'm using Arch so I follow what this [page](https://wiki.archlinux.org/title/rbenv) says)
2. Run `rbenv init` and do what it says
3. Run `rbenv install 2.7.3` , wait for it to install, run `rbenv global 2.7.3` to change your ruby version globally
4. Set the [environment variables](https://wiki.archlinux.org/title/Environment_variables#Per_user) for `GEM_HOME` and `GEM_PATH` as the output of `ruby -e 'puts Gem.user_dir'` (apostrophe included) or just don't set them/leave them empty (I'm not really sure about the latter)
5. Reload your shell or terminal and run `ruby -v` . You should run the version 2.7.3. 
6. Reinstall all the tools required for github page again
```
gem install github-pages jekyll jekyll-sitemap jekyll-seo-tag
```
Now go back to your repo and run `bundle exec jekyll serve` again

### [2] NEVER use EFI for your debian VM
If you export your debian VM with EFI enabled and import it as separate guest, it may **NOT BOOT** even if you change the disk or use an ISO. I honestly have no idea why this happens but [this askubuntu page](https://askubuntu.com/questions/454557/virtualbox-virtual-machines-wont-boot-after-cloning) may give some clue. 

If you like using EFI, QEMU + Virt-Manager is a better option although this OS class mandates you to use VirtualBox. So, don't enable EFI in VirtualBox for your time and sanity.

![just don't please](https://fawzakin.github.io/os212/assets/images/no-efi.png)

