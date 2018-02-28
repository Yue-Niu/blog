# Install Nvidia Driver in Ubuntu 16.04

If we download .run file and try to install this package into the OS, we may encounter some failures, such as * Cannot locate linux source file*. Therefore, we'd better use a more easier and quick way:
bash: ** sudo apt-get install nvidia-* **

This command will automatically install some requiste package required by the Nvidia driver.

## openGL or not

If we use Nvidia Graphic Card as display card, we should choose to install openGL during installing Nvidia driver.

If we use non-Nvidia Graphic Card as dispaly card, such as integrated Intel Graphic Card, we should **NOT** choose to install openGL during installing Nvidia driver. Otherwise, it will overwrite the openGL lib of Intel, and cause endless **login** problem.

In addition, **apt-get intall nvidia-* ** method will automatically install openGL without inquery.