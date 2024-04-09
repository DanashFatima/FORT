# The CIF axiomatization of FORT as a group of ontology modules (micro-theories).


## Procedure (CLIF --> conversions):

* create a virtual environment "VirtualEnvironment", in the host directory, using: "py -m venv VirtualEnvironment"

* access the Scripts folder in the VirtualEnvironment to activate the environment using "activate.bat"

* clone the online macleod directory into the github directory locally using: "git clone https://github.com/thahmann/macleod.git "

* access the macleod cloned direcoty and install the dependencies using: "pip install ." and "pip install .[GUI]"

* go back to the Host directory, create a new macleod-local directory using: "mkdir macleaod" and access it "cd macleod"

* in the macleaod- directory, copy the configuration files of the original macleod directory in the github repository using:

	* copy `C:\Users\danashf\github\macleod\conf\logging.conf`
	
  	* copy `C:\Users\danashf\github\macleod\conf\symbols.conf` 
	
  	* copy `C:\Users\danashf\github\macleod\conf\macleod_win.conf`
	
* modify some configuration files to function according to your machine's Host location

* modify some python parser files in the macleod directory in the VirtualEnvironment using "VirtualEnvironment\Lib\site-packages\macleod\":

  	* in the `parsing\parser.py`
	
  	* in the `scripts\parser.py`
	
* in the macleod directory (github), use the translation commands to generate the translated files.



## The tree of folders and their modified files in the host directory should look like the following:
```
Host-directory
|
|_____ github
|	|_____ macleod				==> cloned from the online repository
|
|_____ FORT-CL-ontology
|	|_____ colore
|	|	|_____ mereology
|	|	|_____ mereotopology
|	|	|_____ location-varzi
|	|_____ conversions-tptp
|	|_____ conversions-p9
|	|_____ all_FORT_clif_files
|
|_____ macleod					==> files are copied from the macleod direcoty in the github repository
|	|_____ logging.conf			==> modified
|	|_____ macleod_win.conf			==> modified
|	|_____ symbols.conf
|
|_____ VirtualEnvironment
	|_____ include
	|_____ Lib
	|	|_____ site_packages
	|		|_____ macleod
	|			|_____ parsing
	|			|	|_____ parser.python		==> modified
	|			|_____ scripts
	|				|_____ parser.python		==> modified
	|_____ scripts
```
