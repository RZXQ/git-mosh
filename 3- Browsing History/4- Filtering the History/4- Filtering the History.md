# Git Log Commands Explained Simply

# Lists all the previous changes made in your project.

git log --oneline

# Lists just the most recent 3 changes made in your project.

git log --oneline -3

# Shows all changes made by a specific person named "Mosh."

git log --oneline --author="Mosh"

# Shows all changes made before August 17, 2020.

git log --oneline --before="2020-08-17"

# Shows all changes made after August 17, 2020.

git log --oneline --after="2020-08-17"

# Shows all changes made since yesterday.

git log --oneline --after="yesterday"

# Shows all changes made in the last week.

git log --oneline --after="one week ago"

# Shows all changes where the message includes the word "GUI".

git log --oneline --grep="GUI"

# Shows changes where the text hello() was added or removed in the code.

git log --oneline -S"hello()"

# Shows changes where the word OBJECTIVES was added or removed in the code.

git log --oneline -S"OBJECTIVES"

# Shows changes with OBJECTIVES added or removed, and also shows exactly what was changed in the code.

git log --oneline -S"OBJECTIVES" --patch

# Shows changes between two specific points in history (fb0d184 up to edb3594).

git log --oneline fb0d184..edb3594

# Shows all changes that involved the file called toc.txt.

git log --oneline toc.txt

# Another way to show all changes that involved toc.txt.

git log --oneline -- toc.txt

# Shows all changes (with the details of the changes) that involved toc.txt.

git log --oneline --patch -- toc.txt