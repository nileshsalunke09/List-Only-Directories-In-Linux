# **List-only-directories**

The ls command in Linux is used for listing the contents of any directory.

By default, it lists all the contents, be it a file or a directory or a link or a named pipe.

But what if you want to list only the directories? How do you that?

Like anything in Linux, there are several ways to accomplish the same task. Listing only the directories is no different:

- ls -d */
- ls -l | grep '^d'
- find . -maxdepth 1 -type d
- echo */
- tree -d -L 1

We will see the above in detail.

## Use ls command to list directories only

It is always good to do it with the familiar ls command because this is the command you use for displaying the content of a directory.

To list only the subdirectories, use the -d option with ls command like this:

- ls -d */
    
Here's the output it shows:

![Screen Shot 2021-02-03 at 9.11.02 AM.png]({{site.baseurl}}/Screen Shot 2021-02-03 at 9.11.02 AM.png)


Why */? Because without it, ls -d will only return the directory name. The -d option list directories not its contents (which includes file, directories etc).

The */ is a pattern. With *, you list all the content (including contents of the subdirectories) and the / restricts the pattern to directories.

You may combine it with long listing option -l and most other options:

![Screen Shot 2021-02-03 at 9.12.49 AM.png]({{site.baseurl}}/Screen Shot 2021-02-03 at 9.12.49 AM.png)


If you do not want the trailing slash (/) at the end of the directory names, you can use the cut command to cut it out:

![Screen Shot 2021-02-03 at 9.13.35 AM.png]({{site.baseurl}}/Screen Shot 2021-02-03 at 9.13.35 AM.png)


## List only subdirectories in a specific directory

The above command works in the current directory. What if you are not in the same directory?

In this situation, you can use */ at the end of the path of the directory with ls -d:

- ls -d Path/To/Dir/*/

Here's an example where I move out of the Documents directory and then list only the directories inside Documents directory:

![Screen Shot 2021-02-03 at 9.15.09 AM.png]({{site.baseurl}}/Screen Shot 2021-02-03 at 9.15.09 AM.png)


Did you notice that it doesn't list the hidden directory? That's one shortcoming of this method. You may use ls -d .*/ to display hidden directories, but it only displays hidden directories.


## Use combination of ls and grep command

You can always rely on the good old grep command for filtering the output for specific content.

If you long list the contents, you can identify the directories because start with d.

You can use grep to filter the contents that start with d:

- ls -l | grep '^d'

But this gives you a lot more fields than just the directory names:

![Screen Shot 2021-02-03 at 9.17.54 AM.png]({{site.baseurl}}/Screen Shot 2021-02-03 at 9.17.54 AM.png)


## Use find command to list only directories

Here's how to use the find command to list only the subdirectories:

- find directory_path -maxdepth 1 -type d

With type d, you ask the find command to only look for directories.

With maxdepth 1 you ask the find command to keep the search at the current level only (and not go inside the subdirectories).


![Screen Shot 2021-02-03 at 9.19.48 AM.png]({{site.baseurl}}/Screen Shot 2021-02-03 at 9.19.48 AM.png)


## Use tree command to list only directories

If your aim is to list only the directories, you may also use the tree command.

By default, the tree command gives you the complete directory structure. You can modify it to show only directories and only at the current level.

tree -dai -L 1

- d - look for directories only
- a - look for hidden files and directories as well
- i - remove the tree structure from the display
- L 1 - don't go into the subdirectories


![Screen Shot 2021-02-03 at 9.22.41 AM.png]({{site.baseurl}}/Screen Shot 2021-02-03 at 9.22.41 AM.png)


## Using echo command for listing directories

The unlikely candidate? You'll be surprised to know that echo command in Linux can also be used for displaying the contents of a directory. Try using echo * and see for yourself.

Similar to the ls command, you can also use the */ pattern to list only the directories in the current working directory.

echo */

Here's the output which is identical to what you got with the ls -d command:

![Screen Shot 2021-02-03 at 9.24.25 AM.png]({{site.baseurl}}/Screen Shot 2021-02-03 at 9.24.25 AM.png)








