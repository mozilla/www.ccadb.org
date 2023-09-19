# www.ccadb.org

## Prerequisites

**Note:* This website is now on the current version of Ruby 3.1.4 (as of Aug 26, 2023). The prior version, 2.x, was deprecated and no longer receiving important updates and security patches.

Using `rbenv` (https://github.com/rbenv/rbenv) is an easy way to set up your environment for testing with Ruby, as it allows you to set which version of Ruby you are using.

#### Installation

- [macOS and Linux](https://github.com/rbenv/rbenv#homebrew) 
- [Manually via Git](https://github.com/rbenv/rbenv#basic-git-checkout)

Once you've installed `rbenv`, please be sure to set your environment to use the current version of Ruby 3.1.4, by running:

```
$ rbenv install 3.1.4
$ rbenv global 3.1.4
```

## Running and testing locally

The vendor directory has been removed to comply with best practices, so please run:
```
$ gem install bundler
$ bundle install
$ bundle exec jekyll serve
```

This will serve up the website, which you can now visit at: http://127.0.0.1:4000/

## Updating in the future

If you need to update `github-pages` in the future, [please follow this guide](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/testing-your-github-pages-site-locally-with-jekyll), or possibly do the following:

```
$ bundle update github-pages
```
