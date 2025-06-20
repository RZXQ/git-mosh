#### create a new file 

echo hello > logs/dev.log

#### we dont want git to track this directory
#### in the .gitignore file, 

echo logs/ > .gitigore

git add .gitignore

git commit -m "add gitignore"

#### if we already included this file or directory(if it is commited) in the git tracking , we cannot ignore them 

mkdir bin
echo hello > bin/app.bin
git add .
git commit -m "commit app.bin"
git ls-files


