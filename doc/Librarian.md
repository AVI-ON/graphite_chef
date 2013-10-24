### Librarian

Librarian is like bundle but for chef cookbooks. Since chef has a lot of cookbooks
librarian lets you organize your cookbooks by putting a Cheffile in the root of the
directory where you want to isntall the cookbooks.

For more information read https://github.com/applicationsonline/librarian-chef

Prepare your infrastructure repository:

```
$ cd ~/path/to/chef-repo
$ git rm -r cookbooks
$ echo /cookbooks >> .gitignore
$ echo /tmp >> .gitignore
```

Librarian-Chef takes over your cookbooks/ directory, and will always
reinstall the cookbooks listed the Cheffile.lock into your cookbooks/ directory.
Hence you do not need your cookbooks/ directory to be tracked in Git.
If you nevertheless want your cookbooks/ directory to be tracked in Git, simply don't
.gitignore the directory.

If you are manually tracking/vendoring outside cookbooks within the repository,
put them in another directory such as vendor/cookbooks/ and use the
:path => source when declaring these cookbooks in your Cheffile.
Most people will typically not be manually tracking/vendoring outside cookbooks.

Librarian-Chef uses your tmp/ directory for tempfiles and caches.
You do not need to track this directory in Git.

Make a Cheffile:

````$ librarian-chef init````
This creates an empty Cheffile with the Opscode Community Site API as the default source.

To install new cookbooks (from the directory where the Cheffile is located):

````bundle exec librarian-chef install````

To cleanup cookbooks
````bundle exec librarian-chef clean````

