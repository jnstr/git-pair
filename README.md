# Git-pair

This is a simple utility to add co-authors to your commits.

# Why?

Git added the possibility for co-authors in 2018: https://github.blog/2018-01-29-commit-together-with-co-authors/  
Since we are pairing a lot at my day job, it's easy to automate the process of adding co-authors to your commits.

This is a simple shell script that modifies your global git commit template (`git config commit.template`) and appends the co-authors at the end of the file. It can also remove the co-authors when you are done pairing.

## Installation

1. Clone this repository
2. cd into the project directory
3. `chmod +x git-pair.sh`
4. `ln -s "$(pwd)/git-pair.sh" /usr/local/bin/git-pair`

## Usage

### Start pairing

Siply run `git-pair` and you are prompted with some questions.

```shell
> git-pair
Give the name of the coworker
John Doe
Give the e-mail of the coworker
john.doe@example.com

Add another coworker? [Y/n]y

Give the name of the coworker
Foo Bar
Give the e-mail of the coworker
foo.bar@example.com

Add another coworker? [Y/n]n

You are now pairing with
John Doe <john.doe@example.com> Foo Bar <foo.bar@example.com>
```

The co-authors are now added to your global git commit template file:
```
... (original content of your global commit template)
#autogenerated coworkers
Co-authored-by: John Doe <john.doe@example.com>
Co-authored-by: Foo Bar <foo.bar@example.com>
```

### Stop pairing

```
> git-pair stop
stopped pairing
```

### Add the co-authors to your last commit 

By using the `amend` option, the co-authors are added to your last commit as well.  

Note: The global commit template is also updated when you use this option, so it behaves just like the normal `git-pair` but it adds extra functionality.  

```
> git-pair amend
```

## Note

Since `git commit -m` doesn't use the global commit template, this script won't work if you use `git commit -m`
