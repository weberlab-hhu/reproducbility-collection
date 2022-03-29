# version-control-intro
A first-timer primer on getting started with git (& github/gitlab).

## the core functionality (live tutorial)
Git is a very powerful tool, and it can have quite the
learning curve. To keep it as simple as possible, we 
will focus on the absolute essentials for you to
get your project in version control and linked to a 
cloud repository, i.e. to make your project 'safe'.

### first steps

---
#### make a cloud account
For today, we will use either "git.hhu.de" as our cloud service, because
we (HHU members) all _have_ an account. Or, if you have or what to setup
an account breifly, in the "real world" you'll generally want to use a 
cloud service such as "github.com" or "gitlab.com".

---
#### make a repository
We'll do this with our cloud service (easiest), and `clone`
it to our own machine in a minute.

##### git.hhu.de
Click on the blue "new project" button

![look for "new project" on git.hhu.de](images/gitlab_new.png)

and then on "blank project"


##### github.com

Click on the green "new" button.

![look for "new" on git.hhu.de](images/github_new.png)

##### Both
Fill in project/repository name and other fields
as desired. In particular, it is normally quite important
to decide if it should be Public/Private. What is private,
can later be made public, but what is once public, will 
never truly be private again. 

Click on "create project"/"create repository".

The cloud services will _generally_ try and provide
"next step" instructions. These are _generally_ worth
a read, particularly if you're doing something different
from what we will do today (e.g. setting up an _existing_ repository)

---
#### install git (+)
Alright, we have the "remote" or the "cloud service" setup,
now let's setup our local working space

- OsX, Windows: Download and install git from https://git-scm.com
- Linux: `sudo apt install git`

##### actually using git
Git itself is a command line tool. 
Especially under windows, but optionally elsewhere,
you may want something to help you interface with it / run it.

Options shown in bold will be demoed today.

###### terminal
First of all, any **terminal** or termnial emulator is an option.
So this will work out of the box on linux, mac, and the windows'
linux subsystem. Emulators also come with (probably) _all_ of the
following options.

###### git specific tools
There are tools designed specifically for git.

 - git bash https://www.atlassian.com/git/tutorials/git-bash
 - git desktop https://desktop.github.com/

###### integrated development environments
Most IDEs come with git support. 
 - **Pycharm** https://www.jetbrains.com/pycharm/
 - **Visual Studio** https://code.visualstudio.com/
 - ...

> Recommendation: focus on a tool you like. If you already
> use one of the above or another tool with git support, 
> use it for git as well. If not,
> pick one (e.g. visual studio or git desktop) and focus on it. 
> Complement the intro today with an online tutorial for your
> tool of choice!

---

#### Clone your project (i.e. Download a copy)
Return to the cloud service and 
look for a "code" or "clone button", this will
tell us where to download from.

![blue gitlab clone button](images/clone_gitlab.png)
![green github code button](images/clone_github.png)

When you click this button, it will give you the option
of "https" or "ssh", if you select the latter (which
you should do _in the long run_ or whenever you start
using github.com for your own projects), 
skip ahead to "ssh-keys", and return here once configured.

Otherwise, for git.hhu.de today, just take https.

Now that you've copied the link, run
`git clone <your link here>`
e.g. the final command might look something like
`git clone https://github.com/weberlab-hhu/version-control-intro`
(or navigate to git clone in your software of choice).

#### Start tracking your project history
Congrats, now you have a local copy of your project.

Let's get some work done.

In a text editor of your choice open the `README.md` file,
make some changes, and save them.

##### Look at changes via git
 - `git status`  <- hey look, git is keeping track already
 - `git diff` <- and it knows what changed

##### Snapshot changes
Many services provide snapshots, git provides snapshots
with _control_ and _documentation_. Part of this control
is organizing what will be committed into the staging area.

 - `git add README.md`  <- add to staging
 - `git status` <- check what has been added, this becomes more important if 
   you ever run `git add *` or similar.

For now, we just have the one file, but you can add as
many things as you want.

- `git commit -m "< your documentation here >"`, 
   e.g. `git commit -m "first outline of  introduction"`

The whole documentation part is only as helpful as you make it,
if every commit message (`-m`) says "changed stuff" or "Updated file.txt" 
it won't help you search.

Everything that you have "committed" can be restored in the
future. It is "safe" from your supervisor harshly editing your
favorite paragraph, or from breaking your code in the future and
not remembering how it used to be. It is not safe from hard drive
failure, etc.. (yet).

#### Keep synced with the cloud (backup and access anywhere)

- `git push` <- sync your snapshots _to_ the cloud

Now open README.md via the cloud service. You can see your local
changes now, right? Click the edit button and make some 'remote'
changes.

- `git pull` <- sync snapshots _from_ the cloud 

Now open the local copy of the file and check that the remote
changes are there. 

> Recommendation: READ the log messages! If something has
> gone wrong they will probably have ideas on what to do. 
> When in doubt: if it won't `push`, try to `pull` first

#### access your project history

Alright, no point in keeping a history of everything
if we don't know how to access it. 

In the cloud, there is this nice "History" button,
check it out.

In the terminal:
- `git log` or
- `git log --all --decorate --oneline --graph`



also access (ssh keys)
## muscle building (not live tutorial)
### larger projects and collaboration
#### branches
#### merge conflicts

### data storage
lsf

### keeping it clean
stash, squash, rebase & co
