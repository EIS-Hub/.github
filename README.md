# .github
readme repo for EIS group

# Emergent Intelligence Substrates

Hallo Researcher!

Welcome to the Emergent Intelligence Substrates group!

### Getting started with SNN monster

First things first, you need access to INI's VPN. Kindly check out the [IT wiki page](https://services.ini.uzh.ch/wiki/index.php/VPN) and set up your VPN connection! 
Once you found your way into the VPN you need an SNN monster account for yourself! Find Martino and get yourself an account (Just takes 2 mins). Now in the terminal type the following command:

	ssh your_username@snnmonster.ini.uzh.ch
	Enter your password!

And... Voila! 
You are on the SNN monster!

### Working with Conda Virtual Environments

It is always the best practice to create project-specific virtual environments where you can download frameworks, libraries and packages specific to the project you are working on, with the versions that you are most comfortable with.

#### Installing Miniconda

First, download Miniconda, a minimal installer for conda. Type the following commands on the remote terminal:

	curl https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -o Miniconda3-latest-Linux-x86_64.sh

Now, grant executable permission to the script that you downloaded using the following command:

	chmod +x Miniconda3-latest-Linux-x86_64.sh

Then, install Miniconda by running the shell script using bash as shown below:

	bash Miniconda3-latest-Linux-x86_64.sh

Finally, export the path of installation as an env variable to make it visible across the system (use your username in the path). To verify the update use the second command and make sure it prints the path.

	export PATH=$PATH:/home/your_username/miniconda3/bin
	echo $PATH

To test the installation, use the following command:

	conda --version

To make these changes permanent use the following command:

	conda init

### Creating a virtual environment

You can create a conda virtual environment using the following command. Replace "<i>your_environement</i>" with a name of your choice!

	conda create --name your_environment

Use the virtual environment that you created by:

	conda activate your_environment

To exit from the virtual environment use:

	conda deactivate

There you go, you have your own <i>small world!</i> :P 
Install all the packages you ever needed and get started with your project!

### Meet the GPU

Now that you have your own virtual world with your favorite libraries in an immensly powerful computing machine maybe it is time to say hello to the saviour! Use the following command to checkout the monsters waiting to crunch all the data and equations that you are going to throw at it!

	nvidia-smi

The nvidia-smi command also shows all the current processes running on the GPUs on the second table. 'C' denotes computation processes (ML/DL code) and 'G' denotes graphical processes. The SNNmonster has CUDA and cuDNN drivers with correct verions supporting the GPU pre-installed. You just have to export the path to these drivers. Use the following command to do so.

	export LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:/usr/local/cuda/lib64
	export PATH=/usr/local/cuda-11.7/bin${PATH:+:${PATH}}

For most machine learning frameworks that you might want to install, you need the CUDA driver version. Use the following command to check it!

	nvcc --version

If nvcc is not recognised, you can download it using the following command:

	conda install -c nvidia cuda-nvcc

### Installing JAX

You are a part of EIS? Lemme guess.. you are using JAX for your project aren't you?
JAX requires very specific versions of JAX and jaxlib according to the CUDA and cuDNN versions of your GPU. This tutorial is written after two days of failiure and probably 6+ hours of frustration. So it might be wise to follow it blindly.

Do not use PIP installer to install JAX and jaxlib until and unless you know the exact version that needs to be downloaded. The smartest way to install JAX would be to use Conda-forge. Conda-forge is a conda package manager that resolves the package dependencies for you! 

###### <i>Installing conda-forge</i>

	conda config --add channels conda-forge
	conda config --set channel_priority strict

Run the following commands to install the correct verions of jax and jaxlib.

	conda install jax
	conda search jax --channel conda-forge

You can install other packages using conda-forge as well. However, you can also use pip installer for other packages that do not have a lot of dependency issues. 
An example command to install matplotlib using conda-forge is presented below

	conda install -c conda-forge matplotlib


