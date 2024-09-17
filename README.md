SOCI 3440

# Quantitative Research Methods

John McLevey<br>
Memorial University

<!-- OLD

# Assets

Large files are stored in [this **Dropbox** folder](https://www.dropbox.com/home/Assets/3440), which contains:

- the full text of Richard McElreath's _Statistical Rethinking_ (SR) in PDF
- the full text of SR split into chapter-specific PDFs
- several Python translations of the SR code
- downloaded video lectures from McElreath's 2023 SR offering
- tutorials, notebooks, and other misc. materials for the most recent edition of Bayesian Analysis with Python

# Setup Using Git Submodules for Course Modules

1. Initialize the main course repository (if not already done)

```zsh
git clone git@github.com:mclevey/SOCI3440.git
cd SOCI3440
```

2. Create the modules directory (if not already existing)

I have a dedicated subdirectory for each of my course modules. Each is it's own self-contained repo, which makes them more portable units that can be incorporated into other courses as needed.

```zsh
mkdir -p modules
cd modules
```

3. Add submodules using SSH

Note that each module repository should already exist on GitHub before you add it as a submodule. The URL used for the repo will be how git refers to this submodule in the future, so changing it later can be tricky and is best avoided. Finally, note that submodules are pinned to a specific commit in the parent repository, which means they can be updated independently of each other.

Each git `submodule add` command does a few things:

- It clones the specified module repository into the current directory (`modules/`).
- It stages the new files in the parent repository.
- It adds a new entry to a hidden `.gitmodules` file, which maps the submodule's path to its URL.

```zsh
git submodule add git@github.com:mclevey/SOCI3440-getting-started.git
git submodule add git@github.com:mclevey/SOCI3440-garden-of-forking-data.git
```

Then add more submodules as needed, e.g.: `git submodule add git@github.com:mclevey/SOCI3440-module3.git`.

4. Update .gitignore to exclude large files (if not already done)

```zsh
echo "*.pdf" >> ../.gitignore
echo "*.csv" >> ../.gitignore
echo "*.json" >> ../.gitignore
echo "*.mp4" >> ../.gitignore
echo "*.mov" >> ../.gitignore
```

5. Commit and push the changes

```zsh
cd ..
git add .
git commit -m "Add submodules using SSH"

git push
```

## When cloning the repository elsewhere

If you want to clone the course repository including all submodules, you'll need to use the `--recursive` flag. This tells git to also clone all the submodules.

```zsh
git clone --recursive git@github.com:mclevey/SOCI3440.git
```

## Updating submodules later

This command updates all submodules to their latest versions on the remote repositories. The `--merge` flag attempts to merge the changes into your current branch.

```zsh
git submodule update --remote --merge
```

## Removing Submodules from the Course

First, remove the submodule entry from `.git/config`.

```zsh
git submodule deinit -f <path/to/submodule>
```

Second, remove the submodule directory from the main project's `.git/modules` directory.

```zsh
rm -rf <.git/modules/path/to/submodule>
```

Third, remove the entry in `.gitmodules` and remove the submodule directory.

```zsh
git rm -f <path/to/submodule>
```

Finally, commit the changes.

```zsh
git commit -m "Removed submodule <name>"
```

A few things to keep in mind about this setup. First, when you're working on a module, you'll need to cd into its directory, make changes, commit, and push those changes. Then, in the parent repository, you'll need to commit the updated submodule reference. Second, each module can have its own branches, tags, and development cycle. This is great for reusability but requires careful management. Third, it is possible for the main course repo to be public but the submodules for each repo to be private. This means that when people clone the main repo, they won't get the private submodules even if they use the `--recursive` flag.

# Automated Course Container Builds

```zsh
mkdir -p computing
cd computing
``` 
-->
