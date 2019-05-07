# Git-pair

This is a simple utility to add co-workers to your commits.

# Why?

Git added the possibility for co-authors in 2018: https://github.blog/2018-01-29-commit-together-with-co-authors/  
Since we are pairing a lot at my day job, it's easy to automate the process of adding co-authors to your commits.

This is a simple shell script that modiefies your global git commit message template (`git config commit.template`) and appends the co-authors at the end of the file. You can also remove the co-authors when you are done pairing.

## Installation

1. Clone this repository
2. cd into the project directory
3. `chmod +x pair.sh`
4. `ln -s "$(pwd)/pair.sh" /usr/local/bin/git-pair`

## Usage

### Start pairing

Siply run `git-pair` and you are prompted with some questions.

```shell
> git-pair
Give the name of the coworker
Jens Trio
Give the e-mail of the coworker
jens@trio.sexy

Add another coworker? [Y/n]y

Give the name of the coworker
Jens Duo
Give the e-mail of the coworker
jens@trio.sexy

Add another coworker? [Y/n]n

You are now pairing with
Jens Trio <jens@trio.sexy> Jens Duo <jens@trio.sexy>
```

The co-authors are now added to your global git commit template file.

### Stop pairing

```
> git-pair stop
stopped pairing
```
