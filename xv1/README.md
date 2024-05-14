# Ximera Virtual Workshop 1: Submit to CTAN

## General information
* **Dates:** 5/3, 5/6-5/8/2024
* **Participants:** Bart Snapp, Jim Fowler, Jason Nowell, Wim Obbles, Andrew Yarmola, Claire Merriman, Anna Davis. 
* **Goals:** Align the deploying Ximera document classes; Fix critical bugs and implement easy features; Submit the Ximera document class to CTAN; Plan next workshop for deploying in Docker.

## Friday 5/3/2024

We presented and discussed Ximera documentclass development. While the
goal of this workshop is "submission to CTAN" it is pointed out, that
if we are deploying with a Docker App, then the Ximera documentclass
can be installed there, thus making local installation redundant.

### Activites
* *.cls files and *.4ht files were submitted by all deploying institutions. 
* Diffs were run and analyzed on the files to produce a "combined" branch of ximeraLatex
* Example files from UF and OSU will be used to make a master example directory.
* Discussed various feature requests, including geogebra scaling and `\desmosThreeD'

## Monday 5/6/2024

At this point we had a combined branch of the ximera documentclass.

### Activites
* Fixed critical bugs in the documentclass.
* `\handoutAnswerFormat{}' was created
* Example files from UF and OSU will be used to make a master example directory.
* Discussed various feature requests, including geogebra scaling and `\desmosThreeD'
* Example repo was developed, see https://go.osu.edu/ximera-examples
* Discussed how to implement common user requests, such as hiding environments:
```
%% Redefine environment
\let\freeResponse\relax
\let\endfreeResponse\relax
\ifhandout
\NewEnviron{freeResponse}{}
\else
\newenvironment{freeResponse}{STUFF DEFINING EVIRONMENT}{END STUFF}
\fi

%% hide an environment
\ifhandout
\let\freeResponse\suppress
\let\endfreeResponse\endsuppress
\fi
```


## Tuesday 5/7/2024



Some points to consider (please add and or comment!) 

The priority for workshop XV1 (5/2024) is:

#  Get ximeraLatex ready for CTAN

* identify the (CTAN-policy-related) problem(s) to submit the current 'master' branch version to CTAN 
  * I heard something about complex C-code ...?)
  * https://ctan.org/help/upload-pkg?lang=en
  * which texlive version(s) to support ...? KULeuven uses a recent texlive now.
* identify differences Ohio/UFlorida/KULeuven version
* identify key issues with the current deploy process:
  * The version of tikz on OSU's Ubuntu server is incompatible with the (newer) version of tikz on Bart's machine. 
  * SVG-viewer missing issues
  * Incompatibilities of the current xake version and tex.
* identify supported/deprecated/obsolete/optional/wanted functionality. 
   * This will include a discussion on what should go in ximeraLatex (general, for *all* Ximera's, depending on Ximera-versions/releases) and what could go in a preamble.tex (per repo). 


## Essentials of the Ximera document class
* By default, the Ximera document class must display all content. All environments should indicate their beginning and ending, as well as their nesting. 
* It needs to support all syntax for interactive elements. Sub-problems must be supported-numbering is necessary here.
* By adding the option `handout` a PDF should be produced that is usable as a paper worksheet in an active learning classroom.
* It must be easy to combine activities into a Xourse, to make a basic course package with a table of contents (I.e. a workbook).
* Commands are camelCased, and usually not abbreviated. 




See also the [[Timeline]], and the extended/extra topics infra.

## Other things to consider/discuss
* explain/discuss some core concepts:
  * xloud: how is it supposed to work, what does exist, what is the planning?
  * gradebook: how is it supposed to work, what does exist, what is the planning?
  * xake: what are the main issues, and which ones can potentially be solved by a dockerized-xake?
  * sage: current status? (KULeuven docker image does not contain sage ..)
  * long-term support of ximeraServer: 
    * Mathjax/npm/bootstrap/... all get (very) old
    * dockerized server should make maintenance and deployment much easier
  * documentation: 
    * overview of existing author-documentation (Ohio/UFlorida/KULeuven)
    * overview of existing more technical documentation  (xloud/ximeraLatex/docker/... ?)
    * end-user documentation (if needed: could/should be self-evident, and if not repo-specific ...?)
    * FAQ/...?
* Resolve all outstanding issues 
* Review current default styling. The requirements of said styling are:  
  * Display all content by default 
  * Clearly display the ending/nesting of theorem-like environments.  
  * By default,  the "handout" option should produce  a usable handout to be used in typical active learning classroom 
* Provide various robust basic printStyle *.sty files 
* Have a test repo that all future modifications will be tested against. I suggest:  

    https://github.com/XimeraProject/examples
* Document all behavior 
* Comment all code 
* Incorporate any new technology, desmos3d comes to mind 
* Provide options for randomized numbers/problems.

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
