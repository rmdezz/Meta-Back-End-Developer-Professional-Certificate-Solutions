# Reading: Setting up a MySQL database on Mac

# Introduction

MySQL is an open-source relational database management system and it’s one of the most widely used databases for both personal and industry use.

## Step 1

To install MySQL on Mac, you first need to first establish which OS X version is in use. Click the Apple icon in top right corner and select **About This Mac.** It should open a window like this:

![Untitled](Reading%20Setting%20up%20a%20MySQL%20database%20on%20Mac%20d12e1056f801446cb63bc95b7d1c28f0/Untitled.png)

In the example above, the **`macOS`** version is **`Ventura 13.0.1`**.

For most users, the versions will either be **Ventura (13)** or **Monterey (12)**.

<aside>
🤔 **Note:** *In the example above,* **Apple M1** *is the chip in use which is* **ARM 64-bit***. The Intel based chips will be x86 64-bit architecture.*

</aside>

Currently, Apple has support for the following versions:

![Untitled](Reading%20Setting%20up%20a%20MySQL%20database%20on%20Mac%20d12e1056f801446cb63bc95b7d1c28f0/Untitled%201.png)

Additionally, the minimum requirements recommended by the official website are as follows:

![Untitled](Reading%20Setting%20up%20a%20MySQL%20database%20on%20Mac%20d12e1056f801446cb63bc95b7d1c28f0/Untitled%202.png)

## Step 2

Once you’ve confirmed these details, proceed to the official [MySQL website](https://dev.mysql.com/downloads/mysql/) to download the **MySQL Community Server.**

<aside>
🤔 **Note:** *The packages for version 12 are compatible with both versions 11 and 13.*

</aside>

Press the **Download** button specific to your OS and chip version.

![Untitled](Reading%20Setting%20up%20a%20MySQL%20database%20on%20Mac%20d12e1056f801446cb63bc95b7d1c28f0/Untitled%203.png)

It will download a **`dmg`** file like the following:

```jsx
mysql-8.0.31-macos12-arm64.dmg
```

Double-click and open the package installer. You will be presented with the image below:

![Untitled](Reading%20Setting%20up%20a%20MySQL%20database%20on%20Mac%20d12e1056f801446cb63bc95b7d1c28f0/Untitled%204.png)

If you receive an error, open the **Privacy and Security** settings in your **System Preferences** and scroll down until you see the **Security** option.

![Untitled](Reading%20Setting%20up%20a%20MySQL%20database%20on%20Mac%20d12e1056f801446cb63bc95b7d1c28f0/Untitled%205.png)

Under the error message, press on the **Open Anyway** button and proceed with the installation.

Acknowledge the warning message once again and press **Open**.

![Untitled](Reading%20Setting%20up%20a%20MySQL%20database%20on%20Mac%20d12e1056f801446cb63bc95b7d1c28f0/Untitled%206.png)

## Step 3

A screen like the one below should appear that welcomes you to the MySQL server. Click **Continue**.

![Untitled](Reading%20Setting%20up%20a%20MySQL%20database%20on%20Mac%20d12e1056f801446cb63bc95b7d1c28f0/Untitled%207.png)

Proceed with the setup by clicking **Allow** and adding a system password if prompted.

You will come to a screen such as the one below where you need to set a password for the **root** user:

![Untitled](Reading%20Setting%20up%20a%20MySQL%20database%20on%20Mac%20d12e1056f801446cb63bc95b7d1c28f0/Untitled%208.png)

Keep the checkbox that says **StartMySQLServer once the installation is complete** selected and complete the installation.

<aside>
🤔 **Note:** *It is very important to keep a note of the root password because if you forget it you'll have to reset it which takes time and effort.*

</aside>

## Step 4

Go to **System Preferences** once again and search for MySQL in the search box.

![Untitled](Reading%20Setting%20up%20a%20MySQL%20database%20on%20Mac%20d12e1056f801446cb63bc95b7d1c28f0/Untitled%209.png)

Press the **Start MySQL Server** button.

Note that the red dots have changed to green on the screen below.

![Untitled](Reading%20Setting%20up%20a%20MySQL%20database%20on%20Mac%20d12e1056f801446cb63bc95b7d1c28f0/Untitled%2010.png)

****Your MySQL server and database are ready for use on the local machine.****

## Step 5

You can confirm the status by opening the terminal and typing the following command:

```jsx
mysql -u root -p
```

Press **`Enter`** and enter the root password you created.

The terminal prompt will change as follows:

![Untitled](Reading%20Setting%20up%20a%20MySQL%20database%20on%20Mac%20d12e1056f801446cb63bc95b7d1c28f0/Untitled%2011.png)

# Conclusion

Sometimes you may encounter some problems during your installation. Some of these queries are addressed on the official website for MySQL. It also consists of useful information about using MySQL database on your local machine.

<aside>
🤔 **Note:** *It is recommended to use the latest stable version of MySQL (5.7 at present) for your installation. However, you can use any earlier version that is compatible with the OS in use and your project requirements.*

</aside>

The MySQL Community Edition that you may encounter is a free downloadable toolset used with the MySQL database server that includes a host of tools as listed in the image below taken from the official website.

![Untitled](Reading%20Setting%20up%20a%20MySQL%20database%20on%20Mac%20d12e1056f801446cb63bc95b7d1c28f0/Untitled%2012.png)

There are also other ways to install mysql such as using binary files and third-party package installers like homebrew. These can be pursued in case the installation from the official package manager file encounters some errors.

In addition to the steps outlined in this reading, specific connectors may be required to use MySQL with different tools like VS Code and languages such as Python. For example, you need to install the package mysqlclient using pip for Python before using mysql.

More information about installation and setup can be found in the additional resources of this lesson.