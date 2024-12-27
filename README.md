# How to Go

# Getting on GitHub

Sign up for a free account, and implement two-factor authentication for your login.
For git command access, set up an SSH key for your GitHub account. Set up your `~/.ssh/config` file to use it. For example, if the SSH key is `github-personal`:

```
Host github-personal
	HostName github.com
        IdentityFile ~/.ssh/github-personal
        User git
```

Then redirect https:// git commands to ssh in your git config:

```bash
git config --global url.ssh://github-personal/.insteadOf=https://github.com/
```

you don't need a credential helper with SSH access. Nor personal access tokens. 

# Forking and managing a GitHub repo

Fork the repo on GitHub. Clone it locally, and run 

```bash
git remote add upstream https://github.com/ORIGINAL_OWNER/REPO_NAME.git
```

You can make changes, push them to your fork, and/or create a PR for upstream. 

# Setting up Go for private package repo access

[Configure your Go environment for private module downloads](https://pkg.go.dev/cmd/go#hdr-Configuration_for_downloading_non_public_code) by setting the Go environment variable GOPRIVATE to `github.com/GITHUB-USER/PRIVATE-REPO-WITH-PACKAGES`. This can also be a comma-separated list. 

You can make this permanent in your Go environment by running:

```bash
go env -w GOPRIVATE=github.com/GITHUB-USER/PRIVATE-REPO-WITH-PACKAGES
```
