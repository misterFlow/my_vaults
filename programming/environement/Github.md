[[environement]]

Commands in TERMINAL
This description assume that when creating a repository on Github, the default depository branch is set to `master` and not `main` as per October 2020 upgrade from Github.

To retrieve a project or folder from Github and place it in the current location;
```js
git clone https://github.com/misterFlow/foldername
```
if you want to rename it:
```js
git clone https://github.com/misterFlow/foldername newname
```

To get information about the git status of a file from my computer location;
```js
git status
```


To add a file from my computer current location to my Github;
```js
git add <foldername>
```
 or  to add all files;
 ```js
git add .
```

To commit a new version of my file from my computer location to my Github;
```js
git commit -m "my comment on this commit"
```


To get information about latest commits;
```js
git log
```


To remove your .git from your folder;
```js
rm -rf .git
```


To push the commited file(s) to your Github repository;
only once
```js
git remote add origin https://github.com/folder_name/subfolder_name.git
```
to finally push
```js
git push -u origin master
```

If issue with existing remote origin;
```js
git remote rm origin
```
then;
```js
git remote add origin https://github.com/folder_name/subfolder_name.git
```

To pull from Github without caring about local changes;
```js
git fetch
git reset --hard HEAD
git merge origin/<current_branch>
```

or

```js
git fetch --all
git reset --hard origin/master
```

