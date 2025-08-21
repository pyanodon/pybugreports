# Contributor Guide
*As of August 16th, 2025*<br>

### How to commit

List of good resources to find out what to do:
  - [Good first Issues](https://github.com/pyanodon/pybugreports/issues?q=is%3Aissue%20state%3Aopen%20label%3A%22good%20first%20issue%22)
  - [Py Roadmap](https://github.com/orgs/pyanodon/projects/2/views/4)

How can I contribute?
  1. Clone the repo you want to commit to
  2. Create a new branch off of main
  3. Create the changes you want to add
  4. Create a pull request describing what you fixed or what you're adding, for simple bug reports you can just say “Fixes <issue link>”
  5. Wait for approval
  6. Make changes if needed
  7. Boom dopamine

### The pY Contributor Feng Shui

You should aim to make your code reusable, extensible.

Docs are located [here](https://pyanodon.github.io/pybugreports/)

If you're adding new functions make sure to document them using [luadoc format](https://stevedonovan.github.io/ldoc/manual/doc.md.html). You should also go into `pybugreports` and edit the `src` folder files and add a new page or edit an existing page to add your new contributions. While editting / creating this new file ensure to change the date at the top saying `As of September 32 1685` to the current date as of editting, do not worry about timezones. Try and make your new contributions to the docs fit the style as the content in the file.

### General Layout

We have 2 branches for different updates: Master or Main and Breaking Changes
- Main or Master is used for bug fixes, general fixes, or non-removing enhancements.
- Breaking changes is used for breaking changes like changing the output of a recipe to have a new byproduct.

The codebase will look something like this typically
```
pytesting
├── control.lua
├── data.lua
├── scripts
│      └── example.lua
└── prototypes
         ├── buildings
         │      └── example-building.lua
         ├── items
         │      └── items.lua
         ├── recipes
         │      └── recipes.lua
         └── technologies
                  └── exmple-technology.lua
```

### Helpful scripts

#### Platform Agnostic

Clones all of the py repos
```
git clone https://github.com/pyanodon/pyalienlife.git
git clone https://github.com/pyanodon/pypostprocessing.git
git clone https://github.com/pyanodon/pycoalprocessing.git
git clone https://github.com/pyanodon/pyfusionenergy.git
git clone https://github.com/pyanodon/pyhightech.git
git clone https://github.com/pyanodon/pyindustry.git
git clone https://github.com/pyanodon/pyrawores.git
git clone https://github.com/pyanodon/pypetroleumhandling.git
git clone https://github.com/pyanodon/pyalternativeenergy.git
```

#### Linux

Simple script to reset all branches to the main/master branch and pull in a directory:
```sh
cd "$(dirname "$0")"

for folder in py*/; do
    if [ -d "$folder" ]; then
        cd "$folder" || continue

        # Get the default remote branch (e.g., origin/main or origin/master)
        default_branch=$(git symbolic-ref refs/remotes/origin/HEAD --short | sed 's|origin/||')

        git checkout "$default_branch"
        git pull --rebase

        cd ..
    fi
done
```

Updates everything from the current branch it's on:
```sh
# Exit on error
set -e

# Loop through each directory starting with "py" that is a git repo
for dir in py*/; do
    if [ -d "$dir/.git" ]; then
        echo "Processing repository: $dir"
        cd "$dir"

        # Pull the latest changes from the remote
        echo "Updating repository..."
        git pull

        # If the ignore revs file exists, configure blame to use it
        if [ -f ".git-blame-ignore-revs" ]; then
            echo "Configuring git to ignore revs in .git-blame-ignore-revs"
            git config blame.ignoreRevsFile .git-blame-ignore-revs
        else
            echo "No .git-blame-ignore-revs file found in $dir"
        fi

        cd ..
    fi
done

echo "All repositories processed."
```

Lists all git branches:
```sh
find . -type d -name ".git" | while read -r gitdir; do
    repo=$(dirname "$gitdir")
    branch=$(git -C "$repo" rev-parse --abbrev-ref HEAD 2>/dev/null)
    echo "$repo: $branch"
done
```


### Frequently Asked Questions

Where are pypostprocessing functions located at?

`pypostprocessing/lib` for in-general stuff<br>
`pypostprocessing/lib/metas` for prototyping functions<br>
`pypostprocessing/lib/events` for control event functions
