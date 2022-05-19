# gitMigrationMethod
How to move code from one git repo to another with all branches and histories.

Follow the Steps:

1. Clone the original repo that you want to migrate: 

```
$ git clone https://github.com/owner_name/project_name.git
```
2. Go to the project terminal:

```
project_name $ 
```
3. Pull all branches and histories from remote to local

```
project_name $ git branch -r | grep -v '\->' | sed "s,\x1B\[[0-9;]*[a-zA-Z],,g" | while read remote; do git branch --track "${remote#origin/}" "$remote"; done
```

```
project_name $ git fetch --all
```

```
project_name $ git pull --all
```

4. Check current project origin:

```
project_name $ git remote -v
```

5. Remove current origin:

```
project_name $ git remote rm origin
```

6. Add new origin of the repo where we want to migrate:

```
project_name $ git remote add origin https://github.com/owner_name/new_repo_name.git
```
7. Check if the current origin is updated to the new repo:

```
project_name $ git remote -v
```

8. Push the entire codebase with all branches and histories to the new repo:

```
project_name $ git push origin --all
```

9. Go to the repo url and check if everything is added successfully. And your done. 😁
