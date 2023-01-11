## Contributing to Swiss Data Custodian

These are all activities we’d like to get help with:

- Code maintenance and development
- Community coordination
- DevOps
- Developing educational content & narrative documentation
- Website design and development
- Writing technical documentation

If you are interested in these other activities, please contact us! You can do this via on GitHub.

## Development process - summary

If you are a first-time contributor:



- Go to:

```bat
https://gitlab.com/data-custodian/custodian
```
 and click the “fork” button to create your own copy of the project.

- Clone the project to your local computer:
```bat
git clone https://github.com/your-username/custodian.git
```

- Change the directory:
```bat
cd custodian
```


## Develop your contribution:

Pull the latest changes from upstream:

```bat
git checkout develop
```

```bat
git pull develop
```
- Create a branch for the feature you want to work on. Since the branch name will appear in the merge message, use a sensible gitname.

```bat
git checkout -b name
```

- Commit locally as you progress (git add and git commit) Use a properly formatted commit message, write tests that fail before your change and pass afterward, run all the tests locally. Be sure to document any changed behavior.

## To submit your contribution:

Push your changes back to your fork on GitHub:

```bat
git push origin gitname
```
- Enter your GitHub username and password (repeat contributors or advanced users can remove this step by connecting to GitHub with SSH).
- Go to GitHub. The new branch will show up with a green Pull Request button. Make sure the title and message are clear, concise, and self- explanatory. Then click the button to submit it.
- If your commit introduces a new feature or changes functionality, post on the mailing list to explain your changes. For bug fixes, documentation updates, etc., this is generally not necessary, though if you do not get any reaction, do feel free to ask for review.
