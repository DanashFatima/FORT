The CIF axiomatization of FORT as a group of ontology modules (micro-theories).

###Procedure (CLIF --> conversions):

1- create a virtual environment "VirtualEnvironment", in the host directory, using: "py -m venv VirtualEnvironment"
2- access the Scripts folder in the VirtualEnvironment to activate the environment using "activate.bat"
3- clone the online macleod directory into the github directory locally using: "git clone https://github.com/thahmann/macleod.git "
4- access the macleod cloned direcoty and install the dependencies using: "pip install ." and "pip install .[GUI]"
5- go back to the Host directory, create a new macleod-local directory using: "mkdir macleaod" and access it "cd macleod"
6- in the macleaod- directory, copy the configuration files of the original macleod directory in the github repository using:
	"copy C:\Users\danashf\github\macleod\conf\logging.conf" 
	"copy C:\Users\danashf\github\macleod\conf\symbols.conf" 
	"copy C:\Users\danashf\github\macleod\conf\macleod_win.conf"
7- modify some configuration files to function according to your machine's Host location
8- modify some python parser files in the macleod directory in the VirtualEnvironment using "VirtualEnvironment\Lib\site-packages\macleod\":
	a- in the parsing\parser.py
	b- in the scripts\parser.py
9- in the macleod directory (github), use the translation commands to generate the translated files.


The tree of folders and their modified files in the host directory should look like the following:
*danashf/
**********github/
		      **********macleod/	##cloned from the online repository
**********FORT-CL-ontology/
          **********colore/
                    **********mereology/
                    **********mereotopology/
                    **********location-varzi/
		      **********conversions-tptp
          **********conversions-p9
          **********all_FORT_clif_files
**********macleod/	##files in it are copied from the macleod direcoty in the github repository
          **********logging.conf	##modified
          **********macleod_win.conf	##modified
          **********symbols.conf
**********VirtualEnvironment/
          **********Include/
          **********Lib/
                  **********site-Packages/
                        **********macleod/
                              **********parsing/
                                **********parser.python	##modified
                              **********scripts/
                                **********parser.python	##modified
          **********scripts/
