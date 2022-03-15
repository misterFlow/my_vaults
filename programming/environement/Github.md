[[environement]]

Commands in TERMINAL
This description assume that when creating a repository on Github, the default depository branch is set to `master` and not `main` as per October 2020 upgrade from Github.

To retrieve a project or folder from Github and place it in the current location;
`git clone https://github.com/misterFlow/foldername`
`git clone https://github.com/misterFlow/foldername newname` if you want to rename it

To get information about the git status of a file from my computer location;
`git status`

To add a file from my computer current location to my Github;
`git add <foldername>` or `git add .` to add all files

To commit a new version of my file from my computer location to my Github;
`git commit -m "my comment on this commit"`

To get information about latest commits;
`git log`

To remove your .git from your folder;
`rm -rf .git`

To push the commited file(s) to your Github repository;
`git remote add origin https://github.com/folder_name/subfolder_name.git` necessary once
`git push -u origin master` to finally push

If issue with existing remote origin;
`git remote rm origin`
then `git remote add origin https://github.com/folder_name/subfolder_name.git`