
### Memo for SSH Connection to Lab's GPU
Due to recently using SSH to connect to the lab's GPU, but with the requirement that all contents must be stored under `/data/username` instead of the default `/home/username`, I encountered a series of problems. Thinking back, the last time I connected to the lab’s GPU, everything went so smoothly that I didn’t write anything down, which caused many difficulties this time. So, I decided to write a memo-style guide to avoid forgetting these steps again in the future.

#### First, install Miniconda.
 If you are working under `home`, the default settings will suffice, but under `data`, you’ll need to add some conditions. The command line is as follows:
```bash
mkdir -p /data/username
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O /data/username/miniconda.sh
bash /data/username/miniconda.sh -b -u -p /data/username/miniconda3
```

#### Next is a critical step, which is adding the conda path.

First, you can confirm whether the installation was successful by using the current conda path:
```bash
path/miniconda3/bin/conda --version
```
If a version is output, then it is indeed a path issue.
Next:
```bash
nano ~/.bashrc
```
At the end of the `.bashrc` file, add the following line:
```bash
export PATH="path/miniconda3/bin:$PATH"
```
Save and exit, then:
```bash
source ~/.bashrc
```
#### After that, you can install PyTorch as usual.
 I recommend using the Tsinghua mirror to speed up the process:
 ```bash
 pip install torch -i https://pypi.tuna.tsinghua.edu.cn/simple
 ```
 That’s it!

(When will I be diligent enough to remember to update my GitHub?)