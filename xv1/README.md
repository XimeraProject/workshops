# XV1: Submit to CTAN 

## Goals:  SEE wiki at https://github.com/XimeraProject/workshops/wiki 
* Ensure compatibility of the Ximera document class across all deploying users 
* Resolve all outstanding issues 
* Incorporate any new technology, desmos3d comes to mind 
* Document all behavior 
* Comment all code 
* Review current default styling. The requirements of said styling are:  
  * Display all content by default 
  * Clearly display the ending/nesting of theorem-like environments.  
  * By default,  the "handout" option should produce  a usable handout to be used in typical active learning classroom 
* Provide various robust basic printStyle *.sty files 
* Provide options for randomized numbers/problmes.
* Have a test repo that all future modifications will be tested against. I suggest:  

    https://github.com/XimeraProject/examples 

 

## Timeline : see https://github.com/XimeraProject/workshops/wiki/Timeline

### First 
* Run diffs on current used ximera.cls files.
  * collect the different files in a repo (presumably ximeraLatex)
  * document dependencies on xake and/or ximeraServer changes/versions
  * determine/decide what can.should be in preamble/printstyle (and thus per repo/branch) and what can/should be in ximeraLatex (and thus more global)   
* If anyone is using a version that was created before our initial submisson to CTAN, there will surely be too many differences to be useful 
* Test various document class on test repos.  
* Users will need test repos ready to go. 
* We could all try to use the example repo/beef-up example repo 
* Create a single working document class for OSU, UF, KU Leuven, Yale. 

### Second 
* Add additional features 
* Document 
* Comment 
* Review/edit current styling. 

### Third 
* Submit to CTAN 
* Create a linting system to check PDFs for testing 
* Create additional printStyles.
