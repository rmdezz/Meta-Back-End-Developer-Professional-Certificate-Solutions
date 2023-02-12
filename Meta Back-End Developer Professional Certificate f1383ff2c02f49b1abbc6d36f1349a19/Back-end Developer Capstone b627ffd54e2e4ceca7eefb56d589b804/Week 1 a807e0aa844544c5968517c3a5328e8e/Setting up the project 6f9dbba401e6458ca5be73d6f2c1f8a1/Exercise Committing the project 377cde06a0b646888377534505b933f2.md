# Exercise: Committing the project

# Overview

You have already cloned the GitHub repository to a local repository named **Capstone-project** in your machine's workspace directory.

You have also created a Django project with the name **LittleLemon**. Inside it, you created a Django app named **Restaurant**.

In this exercise, you will commit the project to the remote repository on GitHub.

# ****Scenario****

For the capstone project, you will build a REST API for ordering food and table reservation.

# ****Prerequisites****

You have set up a repository on GitHub and cloned it into the workspace directory. You should already have created a Django project called **Littlelemon** with an app named **Restaurant** in it.

# Steps

## **Step 1: Create a new branch of local repository**

Open the terminal and use the command **`git checkout –B**  <branch-name>` to create a new git branch.

## **Step 2: Add the project folder to the stage**

Enter the command **`git add .`**

## Step 3: **Check the status**

In the Git terminal enter the **`git status`** command.

## **Step 4: commit the changes**

Next, commit the changes using the git command **`git commit –m "message"`**.

## Step 5: **Push the changes to the GitHub repository**

Use the command **`git push –u origin <branch-name>**.`

## **Step 6: Login to GitHub and open the repository**

The repository page should show the **Compare & pull request** button. Go ahead and press it.

![Untitled](Exercise%20Committing%20the%20project%20377cde06a0b646888377534505b933f2/Untitled.png)

![Screenshot 2023-02-09 at 3.48.39 PM.png](Exercise%20Committing%20the%20project%20377cde06a0b646888377534505b933f2/Screenshot_2023-02-09_at_3.48.39_PM.png)

## **Step 7: Create pull request**

On the repository page, you’ll see the changes committed, and the **Create & pull request** button.

![Untitled](Exercise%20Committing%20the%20project%20377cde06a0b646888377534505b933f2/Untitled%201.png)

![Screenshot 2023-02-09 at 3.49.04 PM.png](Exercise%20Committing%20the%20project%20377cde06a0b646888377534505b933f2/Screenshot_2023-02-09_at_3.49.04_PM.png)

## **Step 8: Merge pull request**

Review the changes and confirm by pressing the **Merge pull request** button.

![Screenshot 2023-02-09 at 3.49.32 PM.png](Exercise%20Committing%20the%20project%20377cde06a0b646888377534505b933f2/Screenshot_2023-02-09_at_3.49.32_PM.png)

![Screenshot 2023-02-09 at 3.49.50 PM.png](Exercise%20Committing%20the%20project%20377cde06a0b646888377534505b933f2/Screenshot_2023-02-09_at_3.49.50_PM.png)

![Screenshot 2023-02-09 at 3.50.13 PM.png](Exercise%20Committing%20the%20project%20377cde06a0b646888377534505b933f2/Screenshot_2023-02-09_at_3.50.13_PM.png)

## **Step 9: Login to the main branch of local repository**

Go back to the Git terminal and enter the command **`git checkout main`**.

## **Step 10: Update the main branch**

Use the **`git pull`** command.

# Conclusion