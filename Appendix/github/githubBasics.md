
# Basic GitHub commands


---
# Github collaboration and branching


---
# GitHub config files


Contibutions for this markdown document came from Matt Hufford and was modified with permission from his [BCB546](https://github.com/EEOB-BioData/BCB546X-Fall2017/tree/master/Week_03X Fall 2017) course.



---
---
---
---






--

* Example: A grant proposal that involved 5-6 contributors:

--

```
3111123 Aug  2  2015 NSF_Project_Description_Aug2-4PM.pdf
2824531 Aug  2  2015 NSF Panama Grant Draft 2015-08-01_v2_JN.docx
2366621 Aug  2  2015 NSF EAH final revisions 2015-08-02_fin.docx
1581164 Aug  2  2015 NSF Panama Grant Draft 2015-08-01_TAH_working.docx
2908139 Aug  2  2015 NSF EAH revisions 2015-08-02.docx
  32538 Aug  2  2015 Hypothesis4edited by Aafke 010815 RAR.docx
 164430 Aug  1  2015 Hypothesis4edited by Aafke 010815.docx
2905973 Aug  1  2015 NSF Panama Grant Draft 2015-08-01.docx
 157777 Aug  1  2015 Chemical volatile objectives.docx
 708115 Jul 31  2015 NSF Panama Grant Draft 2015-07-31 alt fig.docx
1086603 Jul 31  2015 NSF Panama Grant Draft 2015-07-30 alt fig.docx
 157636 Jul 31  2015 H2 Text.docx
 134487 Jul 30  2015 H1 Text.docx
 688048 Jul 30  2015 NSF Panama Grant Draft 2015-07-30.docx
 509467 Jul 30  2015 NSF Panama Grant Draft 2015-07-29.docx
 482474 Jul 28  2015 NSF Panama Grant Draft 2015-07-28.docx
 241316 Jul 27  2015 NSF Panama Grant Draft 2015-07-27.docx
 258099 Jul 25  2015 NSF Panama Grant Draft 2015-07-25.docx
 265654 Jul 22  2015 NSF Panama Grant Draft 2015-07-22.docx
```

---

# Tracking Your Science

### What are the potential shortcomings of this approach?

```
3111123 Aug  2  2015 NSF_Project_Description_Aug2-4PM.pdf
2824531 Aug  2  2015 NSF Panama Grant Draft 2015-08-01_v2_JN.docx
2366621 Aug  2  2015 NSF EAH final revisions 2015-08-02_fin.docx
1581164 Aug  2  2015 NSF Panama Grant Draft 2015-08-01_TAH_working.docx
2908139 Aug  2  2015 NSF EAH revisions 2015-08-02.docx
  32538 Aug  2  2015 Hypothesis4edited by Aafke 010815 RAR.docx
 164430 Aug  1  2015 Hypothesis4edited by Aafke 010815.docx
2905973 Aug  1  2015 NSF Panama Grant Draft 2015-08-01.docx
 157777 Aug  1  2015 Chemical volatile objectives.docx
 708115 Jul 31  2015 NSF Panama Grant Draft 2015-07-31 alt fig.docx
1086603 Jul 31  2015 NSF Panama Grant Draft 2015-07-30 alt fig.docx
 157636 Jul 31  2015 H2 Text.docx
 134487 Jul 30  2015 H1 Text.docx
 688048 Jul 30  2015 NSF Panama Grant Draft 2015-07-30.docx
 509467 Jul 30  2015 NSF Panama Grant Draft 2015-07-29.docx
 482474 Jul 28  2015 NSF Panama Grant Draft 2015-07-28.docx
 241316 Jul 27  2015 NSF Panama Grant Draft 2015-07-27.docx
 258099 Jul 25  2015 NSF Panama Grant Draft 2015-07-25.docx
 265654 Jul 22  2015 NSF Panama Grant Draft 2015-07-22.docx
```

---

# Tracking Your Science

### With a version control system, the file history looks a lot different.

* Example: A grant proposal involving 4 contributors:

--

```
 18537 Aug  1 2016 aim-models.tex
 13341 Aug  1 2016 aim-plants.tex
 16758 Aug  1 2016 aim-tests.tex
 17750 Aug  1 2016 background.tex
 11421 Aug  1 2016 prior-etc.tex
374875 Aug  1 2016 main.pdf
  1269 Jul 28 2016 approach.tex
  5049 Jul 28 2016 broader.tex
 13356 Jul 28 2016 budget.tex
  7548 Jul 28 2016 data.tex
  4630 Jul 28 2016 facilities.tex
  5283 Jul 28 2016 nsflayout.sty
  6124 Jul 28 2016 postdoc.tex
 35216 Jul 28 2016 pps.pdf
 84726 Jul 28 2016 pps.svg
 88594 Jul 28 2016 refs.bib
```

---

# Version Control

### A version control system improves organization and collaboration
<div style="text-align:center"><img src="https://raw.githubusercontent.com/EEOB-BioData/BCB546X-Spring2017/master/Week_2/images/gource_screen.png" alt="gource" style="width: 500px;" /></div>

--

Imagine a project with many more collaborators...

---

# Version Control

A snapshot of [RevBayes](https://github.com/revbayes/revbayes): 28 contributors; 47,938 files; 5,200,936 lines of code

<div style="text-align:center"><img src="https://raw.githubusercontent.com/EEOB-BioData/BCB546X-Spring2017/master/Week_2/images/gource_screen-rb.png" alt="gource" style="width: 440px;" /></div>

---




# &#x2665; Git &#x2665;

## Remote Git repository hosting services

### There are several options for remote hosts

--

* You can set up your own server and host all of your repositories privately using [Gitolite](https://github.com/sitaramc/gitolite/) or [Gitosis](https://git-scm.com/book/no-nb/v1/Git-on-the-Server-Gitosis) (not recommended)

--

* You can use a web-based Git host

--

    * [GitHub](https://github.com/) <img src="https://assets-cdn.github.com/images/modules/logos_page/Octocat.png" alt="Drawing" width="35" />: free public repositories & paid private repositories, with repositories over 1 GB discouraged

--
    * [Bitbucket](https://bitbucket.org/) <img src="http://image.flaticon.com/icons/png/512/37/37104.png" alt="Drawing" width="25" />: unlimited free public & free private
    repositories, limited at 1-2 GB/repo (register with your *.edu* email to get unlimited
    collaborators on private repositories)
--
    * [GitLab](https://about.gitlab.com/) <img src="https://maxcdn.icons8.com/Share/icon/color/Logos//gitlab1600.png" alt="Drawing" width="25" />: unlimited free public & free private repositories with no limits on collaborators, but limited at 10 GB/repo


---

# &#x2665; Git &#x2665;

## Despite the &#x2665;, Git does have some limitations

Most relevant to this course and our fields are:

* **_Repository size_**: If your repository gets very large, working within it can be a problem.
The network speed will be the main bottleneck. This is why the online Git hosts discourage repos
over 1-2 GB.

* **_File size_**: A single large file can be problematic, particularly if it is frequently being
modified. This can also lead to swollen repositories. GitHub will not allow any file over 100 MB.

* **_File type_**: Git works best with text files, you can have binary files in your
repository, but you lose some functionality of version control (like `diff`). Binary files
are also often very large. Thus, it is
recommended that you keep binary files to a minimum. (This means that it is not practical
to use Git to collaborate on MS Word documents.)


---

# &#x2665; Git &#x2665;

## Demo: Clone a Repository

You become familiar with the concepts by using Git. We will start by cloning [ipyrad](https://github.com/dereneaton/ipyrad).

ipyrad is a python program for interactive assembly and analysis of RAD-seq data sets

--

Start by going to [https://github.com/dereneaton/ipyrad](https://github.com/dereneaton/ipyrad) to get the URL.

--

```
$ git clone git@github.com:dereneaton/ipyrad.git
Cloning into 'ipyrad'...
remote: Counting objects: 11341, done.
remote: Compressing objects: 100% (304/304), done.
remote: Total 11341 (delta 199), reused 0 (delta 0), pack-reused 11037
Receiving objects: 100% (11341/11341), 70.75 MiB | 5.91 MiB/s, done.
Resolving deltas: 100% (8275/8275), done.
Checking connectivity... done.
```

Note that using the url `git@github...` instead of `https://github...` uses SSH
if you haven't configured your key yet, this may not work.

---

# &#x2665; Git &#x2665;

### Some helpful commands for this cloned repository

<div style="text-align:center"><img src="https://imgs.xkcd.com/comics/git_2x.png" alt="xkcd" width="250" /></div>

(image source [https://xkcd.com/1597](https://xkcd.com/1597/))

---

# &#x2665; Git &#x2665;

### Some helpful commands for this cloned repository


**Always** `pull` from the repository before doing anything with the contents

```
$ git pull origin master
```

--

Check the `status` of your local files

```
$ git status
```

--

See the `log` of the snapshots and their commit messages

```
$ git log
```

--

Compare the `diff`erences a file you have modified and the last commit

```
$ git diff README.rst
```

---

# &#x2665; Git &#x2665;

### Some helpful commands for this cloned repository

Replace a file you modified with the most recent commit using `checkout`

```
$ git checkout README.rst
```

--

Find out which `branch` you're on

```
$ git branch
```
--

Change to a different branch

```
$ git checkout h5step7
```

--

Pull to update from `h5step7`

```
$ git pull origin h5step7
```

---

# &#x2665; Git &#x2665;

## What can you do with someone else's GitHub repository?

### If you do not have _push rights_

--

* You can only clone the repository and make changes locally

--

* You can **_fork_** their repository and develop it independently

--

* You can submit a **_pull request_** to their repository if you want to contribute to the original project

--

* You can contact the owner of the repository and ask them to include you as a
contributor and give you push rights (it is recommended that you discuss the nature of your collaboration with them first)

---

# &#x2665; Git &#x2665;

## Creating a Repository

Let's create a new Git repository and host it on GitHub using our accounts (for the demo,
I will create the repo in the [EEOB-BioData](https://github.com/EEOB-BioData) organization
so that everyone will have easy access to it).

<br>

--

But first, let's tell Git who you are

```
$ git config --global user.name "Ada Lovelace"
$ git config --global user.email "adal@analyticalengine.com"
```


---

# &#x2665; Git &#x2665;

### Some helpful commands for your new repository

--

Initialize a new Git repository

```
$ git init
```

--

After a file has been added or modified, you can stage the file

```
$ git add README.md
```

--

Commit the file to your local repository and write a message

```
$ git commit -m "initial commit (README.md)"
```


---

# &#x2665; Git &#x2665;

### Some helpful commands for your new repository

After you have made your commit, the repository is up-to-date locally. Next you need to connect
your local repo to the remote.

--

Add the remote

```
$ git remote add origin git@github.com:username/repo-name.git
```

--

Push your snapshot to the remote

```
$ git push -u origin master
```

---