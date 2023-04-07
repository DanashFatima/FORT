# FORT
The Foundational Ontological Relations Theory

Requirements:
first we make sure that we have python on the machine, and the virtual environment package. 
Second; the main direcoty e.g. FORT which contains all the modules shall be contained in the main Host directory e.g. C:/Users/danashf/, where all the following will take place

  1- Create a python virtual environment using the command: |py -m venv MyVE|
  
  2- Go to this virtual environment, access the scripts directory, and activate the bat file using the commands: |cd MyVE/Scripts|, followed by |activate.bat|
  
  3- go back to the Host directory, access the github directoty, and clone the online macleo tool using the following command: |git clone https://github.com/thahmann/macleod.git |. Then access the cloned macleod directory, and install the dependencies using; |pip install .|, and |pip install .[GUI]|
  
  4- Go back to the host directory, create a new macleod directory in which we will copy the configuration files of the macleod directory of the virtual environment. This will enable us to alter them according to our machine's Host local location. We apply then the following commands: 
    * |mkdir macleaod|, |cd macleod|, 
    * |copy C:/Users/danashf/MyVE/macleod/conf/logging.conf | , 
    * |copy C:/Users/danashf/MyVE/macleod/conf/symbols.conf |, 
    * |copy C:/Users/danashf/MyVE/macleod/conf/macleod_win.conf |
    
   5- do some modifications in the configuration files; 
      a) in the |logging.conf| file: on line 30; change the the args variable to be the path of created macleod directory on the main host location i.e. |args = ('C:/Users/danashf/macleod/log.txt',)|
      b) in the |macleod_win.conf| file: on line 3 and 4; change the home path to be the path of our host i.e. |home: C:/Users/danashf/|, and the path variable to be that of the thoeyr in the host directory i.e. |path: %(home)sg-FORT/|

  5- fix a bug in the python parser file of the macleod directory in  the virtual environment i.e. |C:\Users\danashf\ve\Lib\site-packages\macleod\parsing\parser.py|. Originally this python triggered an error whenever we parsed a clif file that included an importation of another clif file. the imported file format shall be a URI (on the web stating by https://...) and not a URI of a local folder i.e; an import command shall have the following format: |(cl-imports https://raw.githubusercontent.com/DanashFatima/FORT/main/colore/m_mereology.clif )|. However, in the parser python file, there is a function on line 529 called ``\verb|parse_file|'' which concatenated the base path ``\verb|C:/Users/danashf/g-FORT/|'' before the URI of the imported clif ontology. So we had to add an if condition which checks if the processed path is URI to be imported, and we modify the concatenation to take only the directory name and file name from the URI (URI to a GitHub file) e.g. taking only |colore/m_mereology.clif| and concatenate it to the base path yielding in having a path which is the location of the imported file on the local machine i.e. |(cl-imports C:/Users/danashf/g-FORT/colore/m_mereology.clif )|.
  
   6- fix another bug in the parser file of the scripts in macleod in the virtual environment i.e. |C:\Users\danashf\ve\Lib\site-packages\macleod\scripts\parser.py|. On line 236, the |onto = ontology.to_owl(args.full)| is changed to |onto = ontology.to_owl(0)|. This is because, originally is issuing an error, where no "full" attribute is given to the args variable. After following the args.full value, it turned out that can be 4 options depending on the type of the owl translation that we want i.e. one of the following; |args.full = Owl.Profile.OWL2_FULL, args.full = Owl.Profile.OWL2_RL, args.full = Owl.Profile.OWL2_QL, args.full = Owl.Profile.OWL2_EL, args.full = Owl.Profile.OWL2_DL|, and in turn, each of the following is a integer between 0 and 3 referring to the intended translation key. for us, the only owl translation that we want is to OWL2 FULL which has the key 0. So we made a static 0 value that the ontology onto is taking |onto = ontology.to_owl(0)|.
    
   7- Parsing the files that we have in the FORT directory, from the macleod directory in GitHub where the main tool is present. So we go to the macleod directory |cd github/macleod/|, and then we can issue our parsing commands as following;
      a) To ladr syntax of Prover9; |parse_clif -f C:\Users\danashf\g-FORT\colore\m_mereology.clif --ladr --resolve|
      b) To tptp syntax; |parse_clif -f C:\Users\danashf\g-FORT\colore\m_mereology.clif --tptp --resolve|
      c) To an approximated owl syntax; |parse_clif -f C:\Users\danashf\g-FORT\colore\m_mereology.clif --owl --resolve|
