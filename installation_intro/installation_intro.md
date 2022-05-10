# Installation
(under linux, please everyone add tips for other operating systems)

This is a brain dump of core concepts and practical tips, 
not an exhaustive documentation.

## What is installation?
 - some code to run, a (compiled) executable
 - telling your machine where to find it
 - managing dependencies

### Code that is ready to run

i.e. code you can 'just run' by typing `./<filename>`
in the directory where it exists,
or by typing out the `</full/path/to/filename>`

#### Permissions
It must be an executable file, i.e. have the executable
permission for who ever should run it. Generally that
means setting `chmod u+x <file name>`

See the following for more information
https://opensource.com/article/19/8/linux-chmod-command

#### Interpreted or compiled
If the code is in an interpreted language (e.g. python, R), 
then the interpreter also has to exist / already be installed.

If the code is in a compiled language (e.g. C, Rust), then it must be 
compiled for the OS & CPU architecture (e.g. 32 bit vs 64).

Commands such as `make` or `cargo build` are there to 
compile the code for your machine.

See the following for more information
https://www.freecodecamp.org/news/compiled-versus-interpreted-languages/

### Where to find it
This (under linux) is controlled via the PATH variable. 

For instance, my path variable looks like
```
#$ echo $PATH
/home/ali/.cargo/bin:/home/ali/.cargo/bin:/home/ali/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/opt/extra_programs/bin
```
some of these, like '/usr/local/bin' are standard install directories
for linux, some, like '/home/ali/bin' I have added by running

`export PATH=$HOME/bin:$PATH`

(in fact adding this line to my '$HOME/.bashrc' file, so that it's ran for every shell)

**test your `export PATH=<your/path/here>:$PATH` command before
adding it to your $HOME/.basrc file!**

Any executable file in any of the folders in '$PATH' can 
simply be ran by typing it into the terminal `<command>`.

For more info: https://linuxize.com/post/how-to-add-directory-to-path-in-linux/

---
> Interactive: A manual, non-sudo user install of a simple script.
> 
> Create a script (or take one you already have). For instance,
> a script called 'test.py' with the following content.
> 
> ```
> #!/usr/bin/env python3
> print('hello installation world')
> ```
> 
> Make the script executable, for instance by running `chmod u+x test.py`. 
> 
> Test that you can run the script when you provide the full or relative 
> path (e.g. `./test.py`), but not when you provide no path (e.g. `test.py`).
> 
> Make a directory for local installation and add it to your path
> e.g. `mkdir $HOME/bin` and then `export PATH=$HOME/bin:$PATH`.
> 
> Copy your script into your local installation directory.
>
> Test that you can now run the script without providing a path `test.py`
---

### Managing Dependencies
Alright the above is _sufficient_ to install a little demo script,
or even a binary, but what about dependencies? 

If your target code wants to use some other code base 
(i.e. to avoid reinventing the wheel & associated maintenance).
Then that code base that your code has as a dependency too needs to exist,
have the right permissions, and be findable. 

Of course your dependencies can have dependencies,
and this of course is where 'make a file executable 
and add it to your $PATH' really starts to break down.

This brings us to package managers

## Package managers
To install things 'right' you want a package manager, generally there is one
main one `apt` for ubuntu & co., `dnf` or `yum` for fedora & co.
`brew` for mac, `snap` is also widely spread...

Additionally, there are language specific
package managers `pip` for python and `cargo` for rust.
When you call `install.packages("<package>")` in R,
it's the same idea, even if there is no stand-alone CLI.

These are associated with a repository 
(note that 'package repository' != 'git repository'), 
where code is maybe
more-or-less vetted & comes with standardized installation
instructions and dependency lists; and so long as all the
dependencies are available from one repository, these work
wonders. For instance the major python repository is PyPI
"The Python Package Index", while the major R repository
is CRAN. Ultimately, trusted repositories are configurable,
if a package is only available from elsewhere (e.g. Bioconductor
instead of CRAN); then you can still install it with a package
manager, there's generally instructions.

Package managers largely default to using root rights.

e.g. `sudo install lolcat`

This is so they can copy the files into locations like '/usr/local/bin'
that are in everyone's $PATH, and that are not writable by
normal users. This is of course also very important from a security
standpoint, so you can never install code for _other users_ unless
you're intentionally using `sudo` or logged in as root!

However, many allow you to make a local installation 
without root rights, where
the package is installed, but only for you (same idea
as adding it to a path available to just _your_ $PATH variable)

e.g. `pip install --user numpy` instead of `sudo pip install numpy`

So package managers help a lot, and you should (ask the admin to) use them!

For any additional info, please google the package managers
relevant to your system...

But, what to do when one package lists e.g. numpy <= 1.16.5 as a dependency
and another package lists numpy >= 1.17.4, or any other impossible
to satisfy dependency conflict? Now we need one more tool to help
us out, virtual environments.

## Virtual environments

To run rough-shod over all the details, virtual environments
are a way to have things installed _sometimes_, a controlled
and wonderful way to move software and all it's dependencies
in and out of your $PATH at will. So if you have one tool
that wants numpy <= 1.16.5, and another that wants numpy >= 1.17.4,
then you can have them both installed, but in two different
virtual environments, and you can turn said virtual environments
on and off ("activate" and "deactivate") and thus switch 
between them at will.

Ideally, keep your virtual environments _**project specific**_.

### R: renv
Packrat is the major alternative to renv, but we'll focus on renv.

https://www.rstudio.com/blog/renv-project-environments-for-r/

One time: `install.packages("renv")`

Create your virtual environment _from R_ with `renv::init()`

Your virtual environment is then associated with your current
directory. So start R in your project directory, and the
virtual environment is active. Start R from some other directory,
your virtual environment is not active. 

When active, install things just in this virtual environment
as always (e.g. while running R, enter `install.packages("viridis")`)

If you want to record what is installed for prosperity or sharing
`renv::snapshot()`. Then include that 'renv.lock' file in your repository
or ARC!

### Python: virtualenv
There are _many_ alternatives for making virtual environments
in python. I like the simplicity of `python3-venv` or `virtualenv`,
or maybe I like them just because I've been using them for a while.
I've yet to use `pipenv`, but it's clearly a current recommendation.  
In any case `pyenv` or `conda` is called for if you also want
to have many different versions of python itself installed. 

For more: https://docs.python-guide.org/dev/virtualenvs/

Here an intro to `virtualenv`

Can be installed with `sudo apt install virtualenv`, or
`pip install --user virtualenv`

Create a virtual environment `virtualenv <environment_name>`.
This will create the directory `<environment_name>`.
Classically, you do this from your project folder `virtualenv venv`.

Activate or 'turn on' a virtual environment: `source <enrironment_name>`

Installation in the active environment works the same as always for
python e.g. `pip install numpy`.

Record what's installed `pip freeze > <filename>`, where `<filename>`
is classically requirements.txt

Deactivate or 'turn off' environment `deactivate`.


### Python +: conda

`conda` is a special case in that it looks like a python
virtual environment tool and package manager, but takes an 
abrupt turn towards a tool to install-all-the-things.
(you can use it for things that are normally system packages, or
R, or just get some binaries, or whatever).

> As an aside, it is not always great to have multiple package managers working
> in a domain, they don't necessarily "play well with friends" 
> and `conda` overlaps with, well, basically everything.
> So take it with a grain of salt, but I recommend deactivating
> their base environment by default.

Install anaconda or miniconda:

https://docs.anaconda.com/anaconda/install/

https://conda.io/projects/conda/en/latest/user-guide/install/index.html

(I then add `conda deactivate` to the end of my $HOME/.bashrc file,
so it's not 'on' until I want it to be)

Create a virtual environment `conda create --name <environment_name>`

Activate: `conda activate <environment_name>`, in contrast to 
`virtualenv`, you will not have to provide the full path to get
to `<environment_name>`.

Install things: `conda install <package>`

Install more things, conda is attached to different repositories,
the largest of which you can use with: `conda install -c conda-forge <package>`.

Install even more things, but do this last and avoid when you can:
`pip install <package>`. The former will work in a conda environment, but
it won't have mutually compatible dependency checking.

Record what's installed `conda list > <your_file>`

Deactivate `conda deactivate`

##### conda vs pip?
https://pythonspeed.com/articles/conda-vs-pip/

---
> Interactive: use our first virtual environment (renv, because it's fastest to install).
> 
> Open R(studio), run `install.packages("renv")`
> 
> Make a mock project directory, and with your R 
> working dir in this directory, run `renv::init()`
>
> Restart R
> 
> install something else you don't yet have
> (e.g. `install.packages("ggplot2")`), and load (`library(ggplot2)`)
> 
> Close R, go to any other directory (so your project doesn't load) and restart R
> try to load your package see that it was only installed in that virtual environment, 
> not everywhere `library(ggplot2)`
---

## What about installing on the HPC?
A lot is installed already, and available with `module load <package>`.

Get a list with `module avail`.

This can get you libraries that run faster, and is certainly less work than a local install.
You can also ask for the HPC team to install things that then become
available in this way.

Otherwise, local installation works with virtual environments or
putting executables into your $PATH, particularly if it's
something very specific to you, or it's Friday at 5pm and the 
deadline is Monday.

## Still not enough isolation?
Beyond virtual environments, you can get even more isolation
between installs, data, and processes by escalating to containers
(Docker being the big one and Singularity being important
in bioinformatics as it doesn't need `sudo` rights at run time), or even to 
full virtual machines. 

Look them up when you need it.

Until then:

https://www.reddit.com/r/ProgrammerHumor/comments/cw58z7/it_works_on_my_machine/

## Finally
Last, but certainly not least:

**generally software ships with recommended installation instructions,
  _read them!_**


---
> Interactive: let's install things together
> 
> send a link for anything you've been having trouble getting installed
> and together we will 1) talk about the best way to install it,
> and 2) try to do so
---
