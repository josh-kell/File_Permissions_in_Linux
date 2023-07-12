<h1>File Permissions in Linux</h1>


<h2>Description</h2>
The research team at this company needed to update the file permissions for certain files and directories within the projects directory. The permissions did not reflect the level of authorization that should have been given. Checking and updating these permissions will help keep their system secure. To complete this task, I performed the following tasks:

<h2>Check File and Directory Details</h2>
The following code demonstrates how I used Linux commands to determine the existing permissions set for a specific directory in the file system.
<br/>
<br/>

![Linux1](https://github.com/josh-kell/images/assets/139269185/a31efcf9-344d-423d-beba-1974860919e1)

The first line of the screenshot displays the command I entered, while the other lines display the output. This code lists all contents of the projects directory. I used the ls command with the -la option to display a detailed listing of the file contents that also returned hidden files. The output of my command indicates that there is one directory named drafts, one hidden file named .project_x.txt, and four other project files. The 10-character string in the first column represents the permissions set on each file or directory.

<h1>Describe the Permissions String</h1>
The 10-character string can be utilized to determine who possesses authorization to access the file and their specific permissions. The characters and what they represent are as follows:

- <b>1st character:</b> This character is either a d or hyphen (-) and indicates the file type. If it’s a d, it’s a directory. If it’s a hyphen (-), it’s a regular file.
- <b>2nd-4th characters:</b> These characters indicate the read (r), write (w), and execute (x) permissions for the user. When one of these characters is a hyphen (-) instead, it indicates that this permission is not granted to the user.
- <b>5th-7th characters:</b> These characters indicate the read (r), write (w), and execute (x) permissions for the group. When one of these characters is a hyphen (-) instead, it indicates that this permission is not granted for the group.
- <b>8th-10th characters:</b> These characters indicate the read (r), write (w), and execute (x) permissions for other. This owner type consists of all other users on the system apart from the user and the group. When one of these characters is a hyphen (-) instead, that indicates that this permission is not granted for other.

For example, the file permissions for project_r.txt are -rw-rw-r--. Since the first character is a hyphen (-), this indicates that project_r.txt is a file, not a directory. The second, fifth, and eighth characters are all r, which indicates that user, group, and other all have read permissions. The third and sixth characters are w, which indicates that only the user and group have write permissions. No one has execute permissions for project_r.txt.


<h2>Describe the Permissions String</h2>

The organization determined that other shouldn't have write access to any of their files. To comply with this, I referred to the file permissions that I previously returned. I determined project_k.txt must have the write access removed for other.
<br>
</br>
The following code demonstrates how I used Linux commands to do this:
<br/>
<br/>

![Linux2](https://github.com/josh-kell/images/assets/139269185/2fa1dd29-85b3-486e-9589-022f30846abe)

The first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. The chmod command changes the permissions on files and directories. The first argument indicates what permissions should be changed, and the second argument specifies the file or directory. In this example, I removed write permissions from other for the project_k.txt file. After this, I used ls -la to review the updates I made.

<h2>Change file permissions on a hidden file</h2>
The research team at my organization recently archived project_x.txt. They do not want anyone to have write access to this project, but the user and group should have read access. 
<br>
</br>
The following code demonstrates how I used Linux commands to change the permissions:
<br/>
<br/>

![Linux3](https://github.com/josh-kell/images/assets/139269185/ed5e29e7-825b-4fd6-89d4-2497b90e2fb1)

The first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. I know .project_x.txt is a hidden file because it starts with a period (.). In this example, I removed write permissions from the user and group, and added read permissions to the group. I removed write permissions from the user with u-w. Then, I removed write permissions from the group with g-w, and added read permissions to the group with g+r. 
<br>
</br>
<h2>Change directory permissions</h2>

My organization only wants the researcher2 user to have access to the drafts directory and its contents. This means that no one other than researcher2 should have execute permissions.
<br>
</br>
The following code demonstrates how I used Linux commands to change the permissions:
<br/>
<br/>

![Linux4](https://github.com/josh-kell/images/assets/139269185/82926d73-41ff-42d7-9787-569a51de8bb6)

The first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. I previously determined that the group had execute permissions, so I used the chmod command to remove them. The researcher2 user already had execute permissions, so they did not need to be added.

<h2>Summary</h2>

I utilized Linux to change multiple permissions to match the level of authorization my organization wanted for directories and files in the projects directory. The first step in this was using ls -la to check the permissions for the directory. This informed my decisions in the following steps. I then used the chmod command multiple times to change the permissions on the required files and directories.
