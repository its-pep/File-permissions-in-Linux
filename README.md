# File-permissions-in-Linux
<h1>Scenario project description</h1>

In this scenario, my research team at my organization needs to update the file permissions for certain files and directories within the project's directory. The permissions do not currently reflect the level of authorization that should be given. Checking and updating these permissions will help keep their system secure. To complete this task, I performed the following tasks:

### Check file and directory details

The following image demonstrates how I used Linux commands `ls -a -ls` to determine the existing permissions set for a specific directory in the file system.

![use ls -a -ls](https://i.imgur.com/BTkynZM.png)

### Describe the permissions string

The 10-character string can be deconstructed to determine who is authorized to access the file and their specific permissions. The characters and what they represent are as follows:

- 1st character: This character is either a `d` or a hyphen (`-`) and indicates the file type. If it's a `d`, it's a directory. If it's a hyphen (`-`), it's a regular file.
- 2nd-4th characters: These characters indicate the read (`r`), write (`w`), and execute (`x`) permissions for the user. When one of these characters is a hyphen (`-`) instead, it indicates that this permission is not granted to the user.
- 5th-7th characters: These characters indicate the read (`r`), write (`w`), and execute (`x`) permissions for the group. When one of these characters is a hyphen (`-`) instead, it indicates that this permission is not granted for the group.
- 8th-10th characters: These characters indicate the read (`r`), write (`w`), and execute (`x`) permissions for other. This owner type consists of all other users on the system apart from the user and the group. When one of these characters is a hyphen (`-`) instead, that indicates that this permission is not granted for other.

For example, the file permissions for `project_t.txt` are `-rw-rw-r--`. Since the first character is a hyphen (`-`), this indicates that `project_t.txt` is a file, not a directory. The second, fifth, and eighth characters are all `r`, which indicates that the user, group, and other all have read permissions. The third and sixth characters are `w`, which indicates that only the user and group have write permissions. No one has execute permissions for `project_t.txt`.

### Change file permissions

The organization determined that `other` shouldn't have write access to any of their files. To comply with this, I referred to the file permissions that I previously returned. I determined `project_k.txt` must have the write access removed for `other`. I use the Linux command `chmod o-w` to remove the `other`write permissions from `project_k.txt`

![o-w](https://i.imgur.com/D42GIz2.png)

### Change file permissions on a hidden file

The research team at my organization recently archived `project_x.txt`. They do not want anyone to have write access to this project, but the `user` and `group` should have read access.

![u-w,g-w](https://i.imgur.com/oaEUJoy.png)
<br>
To remove the write permissions I used the `chmod u-w,g-w`command
<br>
<br>
![u+r,g+r](https://i.imgur.com/cqMZTnZ.png)
<br>
To give the `group` read permissions I used the `chmod g+r`command

### Change directory permissions

My organization only wants the researcher2 user to have access to the drafts directory and its contents. This means that no one other than researcher2 should have execute permissions.

![dir command](https://i.imgur.com/Q2RgWFB.png)

### Summary

I changed multiple permissions to match the level of authorization my organization wanted for files and directories in the projects directory.

