# Exercise: Setting up the repository

# ****Overview****

In this Capstone project, you need to upload your work on a GitHub repository. You will clone the GitHub repository to your machine, and push your code at the end of each exercise of this course.

# Scenario

In this exercise, you will create a repository on GitHub, clone it to a local repository, add a test file in it and commit the changes.

# Prerequisites

You should have completed Version control course to perform the steps in this exercise.

# Steps

## Step 1

Download and install Git for your OS and architecture from [https://git-scm.com/download](https://git-scm.com/download).

## Step 2

Sign up for [https://github.com/](https://github.com/)and create a new repository. Name your repository as **`LittleLemon`**. Use the example shown below:

![Untitled](Exercise%20Setting%20up%20the%20repository%2085bd6cee02e3412d8edd711ca2c3bf3a/Untitled.png)

## Step 3

Open the Git terminal on your machine.

## Step 4

Copy the GitHub repository URL

![Untitled](Exercise%20Setting%20up%20the%20repository%2085bd6cee02e3412d8edd711ca2c3bf3a/Untitled%201.png)

## Step 5

Make a new directory for the local repository.

```jsx
$ mkdir littlelemon
```

## Step 6

Enter the directory.

```jsx
$ cd littlelemon
```

## Step 7

Use the copied URL in the git clone command.

```jsx
$ git clone https://github.com/malharSS/first-repo.git
```

![Untitled](Exercise%20Setting%20up%20the%20repository%2085bd6cee02e3412d8edd711ca2c3bf3a/Untitled%202.png)

## Step 8

Enter the repository and check the list of files.

```jsx
$ cd first-repo
$ ls -la
total 5
drwxr-xr-x 1 **********4096  0Dec  209:58 ./
drwxr-xr-x 1 **********4096  0Dec  2 09:58 ../
drwxr-xr-x 1 **********4096  0Dec  209:58 .git/
-rw-r--r-- 1 ********** 4096 14 Dec  2 09:58 README.md
```

## **Step 9**

Open a **`newfile.txt`** file with vi

```jsx
$ vi newfile.txt
```

Save Hello World message text in it.

To save a file created using **`vi`** in macOS, follow these steps:

1. Open the terminal and start **`vi`** with the name of the file you want to create or edit, for example: **`vi Newfie.txt`**
2. Once in **`vi`**, enter insert mode by pressing the **`i`** key. This allows you to start editing the file.
3. Make the necessary changes to the file.
4. To save the changes, press the **`Esc`** key to exit insert mode.
5. Type **`:w`** to save the changes to the file.
6. To exit **`vi`**, type **`:q`** and press **`Enter`**.
7. To save changes and exit **`vi`** in one step, type **`:wq`** and press **`Enter`**.

That's it! Your file **`Newfie.txt`** should now be saved with the changes you made in **`vi`**.

## Step 10

Check the git status.

```jsx
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        newfile.txt

nothing added to commit but untracked files present (use "git add" to track)
```

## Step 11

Add the **`newfile.txt`** to the stage.

```jsx
$ git add newfile.txt
```

## **Step 12**

Commit the changes.

```jsx
$ git commit -m "first commit"
```

## **Step 13**

Check the status again.

```jsx
$ git status
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
```

## Step 14

Push the changes.

```jsx
$ git push origin main
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 294 bytes | 294.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/malharSS/first-repo.git
   7ecff08..44d2a2e  main -> main
```

**Note:** You may be required to enter the GitHub username and password.

## Step 15

Refresh the GitHub repository page to check that the pushed file appears. Edit the file on GitHub, add some text and commit changes.

![Untitled](Exercise%20Setting%20up%20the%20repository%2085bd6cee02e3412d8edd711ca2c3bf3a/Untitled%203.png)

## Step 16

Go back to Git bash shell and pull the repository to update the local repository.

```jsx
$ git pull
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), 686 bytes | 14.00 KiB/s, done.
From https://github.com/malharSS/first-repo
   44d2a2e..091e422  main       -> origin/main
Updating 44d2a2e..091e422
Fast-forward
newfile.txt | 1 +
1 file changed, 1 insertion(+)
```

# Conclusion

In this exercise, you created a GitHub repository and cloned it as a local repository in your machine. Then you added a file and committed the changed status. You then pushed the changes back to the remote repository. After making changes remotely, you pulled it to update the local repository.