git switch  -c bugfix/change-password

vi change-password.txt

git add .

git commit -m "update change-password.txt"

git switch main

vi change-password.txt

git add.

git commit -m "update change-password.txt"

git merge bugfix/change-password

git status -s

vi change-password.txt

we can accept current change , accept incoming change , accept both changes

but we should not introduce in code in this file, new lines, otherwise it would be refered as evil change

git add change-password.txt

git status -s

git commit -m "finish merge"