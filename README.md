在此查看[中文版](./README.zh-hans.md)
# Assignment Oriented Programming

## Visual Studio Code
That's where the dream starts. Almost all the configurations/operations mentioned in this article require and on top of VS Code.

Just go to [VS Code Official Website](https://code.visualstudio.com/), download the installer, click next on each page.

## WSL2
If you have latest Windows 10 or 11, you only need to enter
```powershell
wsl --install
```
in your `Windows PowerShell`.

For details, just follow the official document [Set up a WSL development environment](https://docs.microsoft.com/en-us/windows/wsl/setup/environment), which is really easy to follow.
## LaTeX
Of course you can use [Overleaf](https://www.overleaf.com/) especially when you need to collaborate with someone who may not be willing to toss themselves to try the content mentioned in this article.

However, there does exist some benefits for building a local LaTeX environment.
* First, you do not need network connection for writing in LaTeX.
* Second, when your assignment involves some images/plots output from code, it is quite common that you may replace old flawed ones with newly correct ones. A local LaTeX environment will automatically recompile without your effort to upload to Ovealeaf again. 
* Third, it is actually not that hard to install a local LaTeX environment.


For `macOS`, download `MacTeX` from [The MacTeX-2021 Distribution](https://tug.org/mactex/).
For other sysmtems like ``Linux` and `Windows`, download `TeX Live` from [TeX Live availability](https://www.tug.org/texlive/acquire.html).

TODO: Step by step installation guide...


## Programming Language

### Python
First check if your computer already has `Python` installed:
```shell
python3 --version
```
It should output something like: `Python 3.8.12`. If you do have `Python` installed already, then you may want to read [Miniconda](#miniconda) next.

If not, then one of the easiest way to install Python is through [Python's official website](https://www.python.org/). Just click the `Downloads` button, wait for the downloading and then run the installer.

However, if you are using `Windows` and want to install `Python` in `WSL2`, you might consider some other ways. For example, if you are using `Ubuntu`, you can install `Python` by opening your terminal and enter:
```shell
sudo apt install python
```

#### Miniconda
After that, I would recommend you install [miniconda](https://docs.conda.io/en/latest/miniconda.html), with which you can create multiple independent virtual environments and manage different packages you might use in different projects.

Go to [miniconda's website](https://docs.conda.io/en/latest/miniconda.html) and download the appropriate version. For example, for `WSL2 Linux`, enter:
```shell
wget https://repo.anaconda.com/miniconda/Miniconda3-py38_4.11.0-Linux-x86_64.sh
```
Then execute the shell scripts:
```shell
sh Miniconda3-py38_4.11.0-Linux-x86_64.sh -b
```
Next, initialize the shell for `conda`:
```shell
~/miniconda3/bin/conda init
```

#### Jupyter Notebook in VS Code
Open your `VS Code`, click the fifth button `Extensions` or enter `Ctrl + Shift + X`, search `Jupyter` and install the first three extensions from `Microsoft`: `Jupyter`, `Jupyter Keymap`, `Jupyter Notebook Renderers`.

Then create a new file with a suffix of `.ipynb`, for example, `playground.ipynb`.
Open this file and follow instructions from `VS Code`, like installing a ipynb kernel.
Then choose a kernel corresponding to your Python version. Most of the time, the suggested version would be fine.
### C++
If you have successfully installed `WSL2`, you should already have `gcc`. Then for using `C++` in `VS Code` I would recommend you to read [Using C++ on Linux in VS Code](https://code.visualstudio.com/docs/cpp/config-linux) or [Using Clang in Visual Studio Code](https://code.visualstudio.com/docs/cpp/config-clang-mac).

Here I would like to introduce how to write `C++` in Jupyter Notebook within VS Code, just like `Python`.
#### Install `xeus-cling`
We first follow [xeus-cling's official installation guide](https://github.com/jupyter-xeus/xeus-cling).

Install `mamba` via `conda`:
```shell
conda install mamba -n base -c conda-forge
```

Use `mamba` to create a new virtual environment for `cling`:
```shell
mamba create -n cling
source activate cling
```

Install `xeus-cling` and its dependencies within the new virtual environment `cling`:
```shell
mamba install xeus-cling -c conda-forge
```

#### Configure for VS Code
Activate `cling` virtual environment and install missing Jupyter related dependencies:
```shell
conda activate cling
mamba install notebook jupyterlab ipywidgets  -c conda-forge
```
> I am not quite sure whether we need all the three packages. 

Use `code` command to open your project. For example, you could create a `playground` directory as your project directory.
```shell
mkdir playground
code playground
```
Use VS Code GUI to create a file with `.ipynb` suffix, for example, `playground.ipynb`.
Open the file, switch the kernel to `C++14` (or one of the other two), and now enjoy the interactive C++ programming!

## `aop-start`: A starting point for each assignment

### `gh`: GitHub CLI

### Git branch
Here are some very basic commands that you may need to collaborate using git branch and GitHub.
#### Create a new branch
You can create a new branch locally and then push it to GitHub.
```shell
git checkout -b [name_of_your_new_branch]
git push origin [name_of_your_new_branch]
```

#### Get update from main branch
```shell
git checkout [name_of_your_new_branch]
git merge origin/main
git push origin [name_of_your_new_branch]
```

> In [this link](https://stackoverflow.com/questions/3876977/update-git-branches-from-master), you may learn more about how to get update from `main` branch.

#### Merge your branch to main branch
```shell
git checkout main # Switch to the main branch
git merge [name_of_your_branch] # Merge your branch to the main branch
git push # Push the local merge to remote repository (like GitHub)
```

> You may refer to [this link](https://gist.github.com/nanusdad/7e516743e5e709073f7e) for more information about how to use branch.