# XV1: Submit to CTAN 

## Goals: 
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

 

## Timeline 

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

# Changes to ximeraLatex @KULeuven:

* Changes in xourse.cls:
   * added \providecommand{\subpart}{}: see xourse.4ht
   * added \newcommand{\activitylink}:   (activity in xourse-PDF with link to external website)

* Changes in xourse.4ht
   * implement \subpart (and titlenumber/sectiontitlenumber; implementation to be verified)
   * overwrite \chapterstyle/\sectionstyle: set \activitytoclabel  (for LaTeX-numbering instead of javascript: see server)
   * overwrite \activity/\practice: set attr data-toc-label to \activitytoclabel
   * \renewcommand{\activitylink}: add extra menuitem/activity to toc, with external link (see server)
   * FIX TYPO in \renewenvironment{graded}

 * Changes to ximera.cfg: none

 * Changes to ximera.cls:
    * add accordion.dtx : \newenvironment{accordion} and {accordion-item}
    * \tikz/external/system call : add ebb (sizing); fix mutool
    * call theoremstyle{definition}  (to prevent italics in tikz-externalize...)
    * add \newtheorem*{exampleNT}  ( No Title...)
    * add \define@key{answer}{onlinenoinput}[false]{}        (only 'reveal answer' option)
    * add \define@key{answer}{onlineshowanswerbutton}[false]{}  (add 'reveal answer' option)
    * \answer prints \ldots\ldots in handout  (was \rm{?})
    * \answer print {\color{blue}\ensuremath{#2}}  (was \fbox{\ensuremath{#2}} )
    
* Changes to ximera.4ht
    * missing \NewEnviron{html}{\HCode{\BODY}}  % Fowler texlive 2020
    * change \ConfigureQuestionEnv: do NOT call \ConfigureEnv 
    * no \ConfigureQuestionEnv for xarmaBoost/shuffle/hint
    * change \ConfigureTheoremEnv: do NOT call \ConfigureEnv 
    * add \ConfigureTheoremEnv exampleNT
    * add accordion/accordion-item
    * \RenewEnviron{hint}  (with expandable)
    * \newenvironment{expandable}  (with accordion; API TO BE CHANGED)
    * MISSING \AtBeginDocument{\renewcommand{\ref}[1]{\HCode{<a class="reference" href="\##1">#1</a>}}}
    * fix \geogebra and \desmos
    * feedback: add [solution]   (but now OBSOLETE with expandable ???)
    * \let\oldlabel\label  \renewcommand{\label}[1]{\oldlabel{#1}\HCode{<a class="ximera-label" id="#1"></a>}}
    * SYNTAX ERROR ungraded corrected (???)

