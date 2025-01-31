# PA1 Reflection - Peter Boster - 09/03/2019:

This assignment was to import the changes from the [Master CS 112 Repository](https://github.com/acarteas/2019-fall-cs112), and 
merge the changes into [My Github Repository](https://github.com/pab15/2019-fall-cs112), and to create and solve a merge conflict within my own repository. In theory, the assignment seemed like a simple task, however it proved to be quite a bit harder than I assumed it would be. At first, I thought that a pull request sounded like the right way to go, and it seemed like a good idea because there is a tab on the Master Repository's Github page that said "Pull Requests". But because I made the mistake of not looking into what a pull request was, I initiated the pull request just to realize that I asked the professor to incorperate my changes. Quite embarassing. After this mistake I decided I would thoroughly research how to attempt this problem before I started trying things without knowing. From my research, I was able to find several links that would get me through this assingment. 

I solved the first part of the assignment by using a couple resources from the [Github.com Articles Section](https://help.github.com/en/articles/). [The First Article](https://help.github.com/en/articles/pushing-commits-to-a-remote-repository), showed me that I could create an upstream repository for my repository that I would be able to fetch and merge changes from, using terminal. I used this to set the Master CS 112 Repository as the upstream repository for my own:

    git remote -v # Shows the configured remote repositories for the fork
    git remote add upstream https://github.com/acarteas/2019-fall-cs112 # Adds the link as the remote repository "upstream"
    git remote -v # Verifies that the remote repository was added

I then followed the [Second Article](https://help.github.com/en/articles/syncing-a-fork), which showed me how to use terminal to fetch and merge the changes from the upstream repository. I followed these steps:

    git fetch upstream # Fetches the changes in the upstream repository
    git checkout master # Makes sure I am working in the master branch
    git merge upstream/master # Merges the upstream repo to the master repo, locally (Does not push changes)
    git add . # Gets changes ready for a commit
    git commit -m "<commit message>" # Commits the changes
    git push # Pushes the changes

when I tried to push the changes, everything was synced correctly, however I got an error that I had a merge conflict in my readme.md files. For this, I used a [Third Article](https://help.github.com/en/articles/resolving-a-merge-conflict-using-the-command-line), that showed me how to fix the conflicting readmes. I followed the steps, pushed the changes, and everything worked:

    vim README.md # Opens the conflicting file in vim
    # Remove the conflict markers: <<<<<, =====, >>>>>
    # Save and quit (esc + :wq (For Vim))
    git add .
    git commit -m "Fixed README.md conflict"
    git push

For the second part of the assignment, I used an [Article On Creating Branches](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging), created a new branch "SampleConflict", and used skills I learned in the [Github Cheatsheet](https://github.github.com/training-kit/downloads/github-git-cheat-sheet.pdf), and the [Third Article](https://help.github.com/en/articles/resolving-a-merge-conflict-using-the-command-line) to create the conflict, merge the branches, fix the conflict and push the changes:

    git branch SampleConflict # Create branch sample conflict
    git branch # Verifies branch creation
    git checkout Master # Move to master branch
    mv SampleConflict_a.md SampleConflict.md # Renames SampleConflict_a.md
    git add .
    git commit -m "Renamed SampleConflict_a.md"
    git push
    git checkout SampleConflict
    mv SampleConflict_b.md SampleConflict.md # Renames SampleConflict_b.md
    git add .
    git commit -m "Renamed SampleConflict_b.md"
    git push
    git checkout master # Move to master
    git merge SampleConflict # Merge SampleConflict to master
    # Follow steps to remove conflict markers
    git add .
    git commit -m "Fixed Merge Conflict"
    git push

All in all, I learned a lot from this assignment. Not only did I learn how to navigate my way around Github and to complete the tasks assigned, but I also learned a lot about not assuming I know what I'm doing, because I honestly don't. Because I took a step back and acknowledged the fact that I really knew nothing about the task and how to complete it, I was able to find the resources faster, and was able to learn more than I needed to know for this assignment. I also realized that it's okay to fail. Because I failed and submitted a pull request, I was able to find the resources I needed to succeed, and was able to study them in more depth. 

