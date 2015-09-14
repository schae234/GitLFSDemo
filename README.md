# Git LFS Demo
The git Large File Storage system is designed to make version controlling
large files easier. Normally, version controlling large files is problematic
because git will keep whole copies of all changed files. Git is also designed
to work well with txt files, so when you compress data files it doesn't work
very well. When you have test files that are megabytes large, your repo becomes 
too large very quick, espeially if you keep txt files uncompressed.

[Link to project page.](https://git-lfs.github.com/)

### How LFS fixes this
Git LFS is a works as an intermediate between your local repo and the one on
github. It uses [git hooks](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks)
to intercept any large files that would be better stored on the LFS server.
Hooks are really cool and can be made to do other things too!

### Using GitLFS
Git LFS is easy **if** you want to use the github service. However, they have a
limit on repo size that is easy to meet with a biological dataset. Luckily,
the implementation they have is open source! They have source code for the 
[client](https://github.com/github/git-lfs) and the 
[server](https://github.com/github/lfs-test-server) freely available. 

For this demo sake, I set up a server on `lovelace` which will mimic how the
github service works. It doens't take long to set up, it just requires a few
things to be installed (like go) on the server and a way to run it in the 
background (like screen or tmux if you are lazy like me).

Clone this repo; all the necessary files are there to begin! 

### Setting up the Client
Follow the instructions on downloading the [latest client.](https://github.com/github/git-lfs?utm_source=gitlfs_site&utm_medium=source_link&utm_campaign=gitlfs#getting-started)
Everything should be set up from cloning this repository, you should just be
prompted for a username and password for the git-lfs server on lovelace.
Just ask me what the creds are.

The only extra step you would need to follow for setting this up on your own 
server to configure git-lfs to point to your custom server.
Check out the `.gitconfig` file to see  info on pointing git-lfs to the 
server-side process on lovelace.

### Setting up the Server
I set up a git-lfs server at `lovelace.cs.umn.edu:8080`. The instructions to 
do so were on the server source code page. The server listens over HTTP, all
you have to do is make sure your client code is configured to send stuff to
the server.
