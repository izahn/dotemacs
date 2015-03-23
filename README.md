- [Quick start](#quick-start)
  - [What is this?](#what-is-this?)
  - [How to I install it?](#how-to-i-install-it?)
  - [First run](#first-run)
  - [Modified key bindings](#modified-key-bindings)
    - [Completion keys](#completion-keys)
    - [Other key bindings](#other-key-bindings)
  - [Suggested external programs](#suggested-external-programs)
    - [External program download and installation](#external-program-download-and-installation)
    - [External program configuration and use](#external-program-configuration-and-use)
- [Discussion and implementation](#discussion-and-implementation)
  - [What the world needs now&#x2026;](#what-the-world-needs-now&#x2026;)
  - [Requirements](#requirements)
  - [Implementation](#implementation)
    - [Preamble](#preamble)
    - [version Check](#version-check)
    - [Visual tweaks](#visual-tweaks)
    - [Install useful packages](#install-useful-packages)
    - [Load theme](#load-theme)
    - [Add custom lisp director to load path](#add-custom-lisp-director-to-load-path)
    - [Spell checking](#spell-checking)
    - [Fonts](#fonts)
    - [Printing](#printing)
    - [Minibuffer hints and completion](#minibuffer-hints-and-completion)
    - [Auto-complete configuration](#auto-complete-configuration)
    - [Outline-magic](#outline-magic)
    - [Major modes configuration](#major-modes-configuration)
    - [Miscellaneous](#miscellaneous)



# Quick start<a id="sec-1" name="sec-1"></a>

## What is this?<a id="sec-1-1" name="sec-1-1"></a>

This is a drop-in replacement for your .emacs.d. It automatically installs and configures several emacs packages useful for working with LaTeX documents, and for writing code for statistical analysis in R, Stata, SAS, and Julia. It also turns on several built-in features of emacs such as spell checking and syntax highlighting.

## How to I install it?<a id="sec-1-2" name="sec-1-2"></a>

1.  Make sure emacs >= version 24.3 is installed on your computer. See  Suggested-external-programs (See section 1.5) for installation instructions.
2.  Make sure you have [git](http://git-scm.com/downloads) installed on your computer. If you don't know what git is you might be interested in John McDonnell's [git tutorial](http://nyuccl.org/pages/GitTutorial/).
3.  Determine your emacs configuration directory. Open emacs and type `C-x f ~/ RET`. This should open a directory listing buffer. Note the path at the top of this file. This is were your `.emacs.d` should go.
4.  Close Emacs.
5.  Back up your existing `~/.emacs` file and `~/.emacs.d` directory (e.g., rename `.emacs` to `OLD.emacs` and rename `.emacs.d` to `OLD.emacs.d`).
6.  Clone this repository into `~/.emacs.d` by opening a terminal and running `git clone http://github.com/izahn/dotemacs ~/.emacs.d`.

If you don't know how to use git, you can skip step 6 and simply [download the files as a zip archive](https://github.com/izahn/dotemacs/archive/master.zip), extract them, and move them into your .emacs.d directory.

## First run<a id="sec-1-3" name="sec-1-3"></a>

Note that after installing this configuration emacs will be extremely slow to start up the first time. This is due to package installation, and to a one-time scan of the fonts installed on your computer. Just be patient and wait for it to finish&#x2013;subsequent start-ups will be much faster.

## Modified key bindings<a id="sec-1-4" name="sec-1-4"></a>

This configuration loads a lot of useful emacs packages (see here for the list), many of which add key bindings. Documenting them all here would be too much (see the documentation for each package if you need the details), so this section describes only those key bindings that we explicitly added or changed.

### Completion keys<a id="sec-1-4-1" name="sec-1-4-1"></a>

-   **C-TAB:** Mapped to `company-complete`, use for pop-up completion menu.


-   **C-x C-r:** Mapped to `ido-recentf-open` to select recent files in the minibuffer.
-   **M-x:** Remapped to `smex` to interactively search for interactive functions. Use `M-X` (note the capital "X") to restrict to commands for the active major mode.

### Other key bindings<a id="sec-1-4-2" name="sec-1-4-2"></a>

-   **E:** Open in external application (dired mode only)
-   **C-up:** Mapped to `scroll-down-1`.
-   **C-down:** Mapped to `scroll-up-1`.
-   **C-c C-c:** Mapped to functions that execute code in several major modes, including shell mode, python mode, ielm mode, lisp-interaction mode, and ess mode.
-   **M-Q:** Mapped to `unfill-paragraph`, use to remove line breaks from a paragraph.
-   **C-c C-o t:** Mapped to `outline-cycle`, use to hide/show when outline-minor-mode is active (outline-minor mode is enabled in programming modes and in LaTeX-mode).
-   **M-q:** Remapped to `bibtex-fill-entry` (bibtex mode only).
-   **S-M-right:** (shift + meta + right arrow key) mapped to `windmove-right`; selects the window to the right of the currently active window. `S-M-left`, `S-M-up` and `S-M-down` also mapped to the corresponding windmove functions.

## Suggested external programs<a id="Suggested-external-programs" name="Suggested-external-programs"></a>


Some of the requirements listed in Requirements (See section 2.2) make use of software that must be installed outside of emacs. And of course you will need emacs itself! 

### External program download and installation<a id="sec-1-5-1" name="sec-1-5-1"></a>

While emacs alone is very powerful, one of it's most important strengths is its ability to inter-operate with other software programs. Links to the download pages for several programs that can be used from with emacs are provided below (they are also very useful on their own!). Installation of all these programs follows normal conventions on each platform, just download, run the installer, and follow the instructions.

1.  Windows

    -   **Emacs:** <http://vgoulet.act.ulaval.ca/en/emacs/>
    -   **R:** <http://cran.r-project.org/bin/windows/base/>
    -   **LaTeX:** <http://miktex.org/download>
    -   **git:** <http://git-scm.com/download/win>
    -   **Pandoc:** <https://github.com/jgm/pandoc/releases>
    -   **GhostScript:** <http://www.ghostscript.com/download/gsdnld.html> (Make sure to **install the 32 bit version**!)

2.  OSX

    -   **Emacs:** <http://vgoulet.act.ulaval.ca/en/emacs/>
    -   **R:** <http://cran.r-project.org/bin/macosx/>
    -   **LaTeX:** <http://tug.org/mactex/>
    -   **git:** <http://git-scm.com/download/mac>
    -   **Pandoc:** <https://github.com/jgm/pandoc/releases>
    -   **GhostScript:** <http://pages.uoregon.edu/koch/>

3.  Linux

    -   **Emacs:** Use your package manager, or see <http://www.gnu.org/software/emacs/#Obtaining>
    -   **R:** Use your package manager, or see <http://cran.r-project.org/bin/linux/>
    -   **LaTeX:** Use your package manager, or see <https://www.tug.org/texlive/quickinstall.html>
    -   **git:** Use your package manager, or see <http://git-scm.com/download/linux>
    -   **Pandoc:** Use your package manager, or see <http://johnmacfarlane.net/pandoc/installing.html#all-platforms>
    -   **GhostScript:** Use your package manager, or see <http://www.ghostscript.com/download/gsdnld.html>

### External program configuration and use<a id="sec-1-5-2" name="sec-1-5-2"></a>

While a detailed instructions on how to use these programs would take years, you can get started with the quickly. Here are some quick pointers and links to more detailed tutorials.

1.  Emacs

    Emacs configuration is complex, and we will not go into it here except to say that the main configuration file is named `init.el` and can usually be found in a directory named `.emacs.d`, which is usually in your home directory. As mentioned in (See section ) and  (See section ) there are many pre-packaged emacs configurations that you can use simply by copying them to your `.emacs.d` directory.
    
    You can almost just start emacs and start typing as you would in any other text editor, though you should be aware that Emacs uses different keyboard shortcuts than those you may be accustomed to. There is a introductory tutorial built into Emacs that you can access from the Help menu; IBM provides another excellent [emacs tutorial](http://www.ibm.com/developerworks/aix/tutorials/au-emacs1/index.html).

2.  R

    R is a free language and environment for statistical computing. It works well out of the box and does not require much in the way of configuration. If you want to learn more about R the [official R website](http://r-project.org) is a good place to start and includes many excellent [manuals](http://cran.r-project.org/manuals.html) and [tutorials](http://cran.r-project.org/other-docs.html).

3.  LaTeX

    LaTeX is a typesetting system that excels at formatting structured documents. LaTeX files are written in plain text using a markup syntax, and this markup is used to format the typeset document. LaTeX works well out of the box and does not typically require much in the way of configuration. If you want to learn more about LaTeX try [these LaTeX tutorials](http://www.andy-roberts.net/writing/latex) by Andrew Roberts.

4.  git

    1.  Initial configuration
    
        [git](http://git-scm.com/) is a revision control system that allows you to track changes, merge changes with those made by collaborators, revert to previous versions, and more. While git can be used without any configuration, it is a good idea to at least set your user name and email; instructions for doing so are available at <http://git-scm.com/book/en/Getting-Started-First-Time-Git-Setup>; a detailed introduction to git is available at <http://git-scm.com/book/en/>. Once installed you can use git from the command line; on Windows use the `git bash` application, on other platforms use your regular terminal emulator.
        
        It is often convenient to tell git *not* to track some types of files (e.g., temporary files, or large binary files). LaTeX users in particular may be annoyed that git tries to track their .aux, .log, and other ephemeral files produced by LaTeX. You can tell git to ignore certain types of files by listing the in a .gitignore file. Details on .gitignore files are available at <http://git-scm.com/docs/gitignore>, and many useful templates (including one designed for LaTeX users) are available at <https://github.com/github/gitignore>.
    
    2.  github
    
        Many git users host their repositories on <http://github.com>; helpful guides are available at <https://guides.github.com/>. You can [clone from and push to github over https](https://help.github.com/articles/which-remote-url-should-i-use/), and that is the recommended method; no configuration is required. If for some reason you prefer to use ssh you will need an ssh key pair; see <https://help.github.com/articles/generating-ssh-keys/> for instructions.
    
    3.  Using git from emacs
    
        This Emacs configuration includes [magit](https://magit.github.io/), and interface to git for Emacs. Documentation is available at <https://github.com/magit/magit#getting-started>.

5.  Pandoc

    Pandoc is a program for converting markup files from one markup language to another. Documentation and examples are available on the [pandoc website](http://johnmacfarlane.net/pandoc/).

6.  GhostScript

    GhostScript is a program for working the postscript and pdf files. While it can be used on its own it is included in this list only because it makes printing from emacs easier, especially on Windows. No configuration should be required. Note that **on windows you need the 32 bit version**, the 64 bit version will not work. Windows users will also need to add it to their PATH (see <http://www.computerhope.com/issues/ch000549.htm> for instructions).

# Discussion and implementation<a id="sec-2" name="sec-2"></a>

## What the world needs now&#x2026;<a id="sec-2-1" name="sec-2-1"></a>

As of August 5th 2014 there are 2,960 github repositories named or mentioning '.emacs.d', and another 627 named or mentioning "dotemacs". Some of these are just personal emacs configurations, but many take pains to provide documentation and instruction for adopting them as your very own emacs configuration. And that's not to mention the [starter-kits](https://github.com/search?q=emacs-starter-kit&type=Repositories&ref=searchresults), [preludes](https://github.com/search?q=emacs+prelude&type=Repositories&ref=searchresults) and [oh my emacs](https://github.com/search?q=emacs+oh+my&type=Repositories&ref=searchresults) of the world! With all these options, does the world really need yet another emacs configuration? 

No, the world does not need another emacs starter kit. Indeed the guy who started the original emacs starter-kit has concluded that the whole idea is [unworkable](https://github.com/technomancy/emacs-starter-kit), and that if you want to use emacs you're better off configuring it yourself. I agree, and it's not that hard, even if you don't know emacs-lisp at all. You can copy code fragments from others' configuration on [github](http://github.com), from the [emacs wiki](http://emacswiki.org), or from [stackoverflow](http://stackoverflow.com) and build up your very own emacs configuration. And eventually it will be so perfect you will think "gee I could save people the trouble of configuring emacs, if they would just clone my configuration". So you will put it on github, like everyone else (including me). Sigh.

On the other hand it may be that this emacs configuration is what you want after all. It turns on many nice features of emacs, and adds many more. Anyway it does not hurt to give it a try.

## Requirements<a id="Requirements" name="Requirements"></a>


Emacs is many things to many people, being perhaps the most configurable text editor ever created. However, there are some common tools that social scientists often make use of that are not accessible in emacs by default. It is therefore desirable to create a base configuration that enables the features that social scientists are likely to find useful. The table below lists some of these requirements, and describes how they are made available in emacs.

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="left" />

<col  class="left" />

<col  class="left" />

<col  class="left" />

<col  class="left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="left">Requirement</th>
<th scope="col" class="left">Categories</th>
<th scope="col" class="left">Solution</th>
<th scope="col" class="left">Notes</th>
<th scope="col" class="left">&#xa0;</th>
</tr>
</thead>

<tbody>
<tr>
<td class="left">LaTeX editing/compilation</td>
<td class="left">Document prep</td>
<td class="left">AucTeX/RefTeX</td>
<td class="left">Installed and turned on</td>
<td class="left">&#xa0;</td>
</tr>


<tr>
<td class="left">Font locking</td>
<td class="left">Look-n-feel</td>
<td class="left">font-lock-mode</td>
<td class="left">Built-in, turned on</td>
<td class="left">&#xa0;</td>
</tr>


<tr>
<td class="left">Spell checking</td>
<td class="left">Convenience</td>
<td class="left">ispell/flyspell</td>
<td class="left">Built-in, turned on</td>
<td class="left">&#xa0;</td>
</tr>


<tr>
<td class="left">Outline/structure editing</td>
<td class="left">Convenience</td>
<td class="left">outline-minor-mode</td>
<td class="left">Built-in, turned on</td>
<td class="left">&#xa0;</td>
</tr>


<tr>
<td class="left">Revision control</td>
<td class="left">Version management</td>
<td class="left">VC-mode/magit</td>
<td class="left">VC-mode, turned on, magit installed/activated</td>
<td class="left">&#xa0;</td>
</tr>


<tr>
<td class="left">Edit/evaluate R/Stata/SAS</td>
<td class="left">Data analysis</td>
<td class="left">ESS</td>
<td class="left">Installed and activated</td>
<td class="left">&#xa0;</td>
</tr>


<tr>
<td class="left">Easier file/buffer/access</td>
<td class="left">Convenience</td>
<td class="left">ido</td>
<td class="left">Installed, turned on</td>
<td class="left">&#xa0;</td>
</tr>


<tr>
<td class="left">Reproducible research</td>
<td class="left">Data analysis</td>
<td class="left">org-mode, polymode</td>
<td class="left">Installed, polymode (Melpa) not working on RCE</td>
<td class="left">&#xa0;</td>
</tr>


<tr>
<td class="left">Copy/paste with other apps</td>
<td class="left">Convenience</td>
<td class="left">x-select</td>
<td class="left">Built-in, turned on</td>
<td class="left">&#xa0;</td>
</tr>


<tr>
<td class="left">Word wrapping</td>
<td class="left">Look-n-feel</td>
<td class="left">visual-line-mode</td>
<td class="left">Built-in, turned on</td>
<td class="left">&#xa0;</td>
</tr>


<tr>
<td class="left">Command hinting/completion</td>
<td class="left">Convenience</td>
<td class="left">Ista</td>
<td class="left">smex</td>
<td class="left">Installed and turned on</td>
</tr>


<tr>
<td class="left">Programming auto-completion</td>
<td class="left">Convenience</td>
<td class="left">Ista</td>
<td class="left">auto-complete/Company</td>
<td class="left">Installed and turned on</td>
</tr>


<tr>
<td class="left">Keep backup files out of the way</td>
<td class="left">Convenience</td>
<td class="left">Ista</td>
<td class="left">backup-directory-alist</td>
<td class="left">Built-in, turned on</td>
</tr>


<tr>
<td class="left">Cleaner interface</td>
<td class="left">Look-n-feel</td>
<td class="left">Ista</td>
<td class="left">tool-bar-mode</td>
<td class="left">Built-in, off by default</td>
</tr>


<tr>
<td class="left">Highlight matched/mismatched paren</td>
<td class="left">Convenience</td>
<td class="left">Ista</td>
<td class="left">show-paren-mode</td>
<td class="left">Built-in, turned on</td>
</tr>
</tbody>
</table>

## Implementation<a id="Implementation" name="Implementation"></a>


The emacs configuration in the sections below implements the Requirements (See section 2.2) listed above.

### Preamble<a id="sec-2-3-1" name="sec-2-3-1"></a>

```lisp
;;; COMMENTARY

;; This emacs configuration file sets some convenient defaults and activates 
;; emacs functionality useful to social scientists. 


;; NOTE FOR RCE USERS: RCE Emacs has some strange system configuration
;; settings. To use this init file on the RCE you need to start emacs with
;; emacs --no-site-file --no-site-lisp. This is a temporary requirement that
;; will eventually be resolved in cooperation with the RCE team.
```

### version Check<a id="sec-2-3-2" name="sec-2-3-2"></a>

It is difficult to support multiple versions of emacs, so we will pick an arbitrary cutoff and throw an error if the version of emacs is "too old".

```lisp
(when (< (string-to-number 
           (concat 
            (number-to-string emacs-major-version) 
            "." 
            (number-to-string emacs-minor-version)))
          24.2)
  (error "Your version of emacs is very old and must be upgraded before you can use these packages"))
```

### Visual tweaks<a id="sec-2-3-3" name="sec-2-3-3"></a>

Visual changes such as hiding the toolbar need to come first to avoid jarring transitions during startup.

```lisp
;; make sure we start maximized (requires emacs >= 24.4)
(setq initial-frame-alist '((fullscreen . maximized)))
(modify-frame-parameters
   nil
   `((fullscreen ., 'maximized)))

;; hide the toolbar
(tool-bar-mode 0)
;; (menu-bar-mode 0)
;; (setq inhibit-startup-screen t)
```

### Install useful packages<a id="sec-2-3-4" name="sec-2-3-4"></a>

The main purpose of these emacs configuration files is to install and configure useful emacs packages. Here we carry out the installation.

```lisp
;;; Install required packages
(require 'cl)

;; set things that need to be set before packages load
; Less crazy key bindings for outline-minor-mode
(setq outline-minor-mode-prefix "\C-c\C-o")

;; load site-start early so we can override it later
(load "default" t t)
;; prevent site-start from running again later
(setq inhibit-default-init t)

;; load the package manager
(require 'package)

;; Add additional package sources
(add-to-list 'package-archives 
             '("org" . "http://orgmode.org/elpa/") t)
(add-to-list 'package-archives 
             '("melpa" . "http://melpa.milkbox.net/packages/") t)

;; Make a list of the packages you want
(setq my-package-list '(;; gnu packages
                        auctex
                        windresize
                        diff-hl
                        ;; melpa packages
                        multi-term
                        anzu
                        howdoi
                        google-this
                        leuven-theme
                        powerline
                        persistent-soft
                        unicode-fonts
                        dired+
                        mouse3
                        ido-ubiquitous
                        ido-vertical-mode
                        ;; noflet
                        popup-kill-ring
                        smex
                        outline-magic
                        smooth-scroll
                        company
                        company-math
                        ess
                        markdown-mode
                        polymode
                        eval-in-repl
                        pyvenv
                        anaconda-mode
                        exec-path-from-shell
                        company-anaconda
                        htmlize
                        pcmpl-args
                        pcmpl-pip
                        readline-complete
                        magit
                        ;; org-mode packages
                        org-plus-contrib))

;; Activate package autoloads
(package-initialize)
(setq package-initialize nil)

;; make sure stale packages don't get loaded
(dolist (package my-package-list)
  (if (featurep package)
      (unload-feature package t)))
;; Install packages in package-list if they are not already installed
(unless (every #'package-installed-p my-package-list)
  (switch-to-buffer "*scratch*")
  (erase-buffer)
  (setq my-this-buffer (buffer-name))
  (delete-other-windows)
  (insert "Please wait while emacs configures itself...")
  (redisplay t)
  (redisplay t)
  (package-refresh-contents)
  (dolist (package my-package-list)
    (when (not (package-installed-p package))
      (package-install package)))
    (switch-to-buffer "*scratch*")
  (erase-buffer)
  (add-to-list 'fancy-startup-text
               '("Your emacs has been configured for maximum productivity. 
For best results please restart emacs now.
More information about this emacs configuration be found
at http://github.com/izahn/dotemacs. If you have any problems
or have a feature request please open a bug report at
http://github.com/izahn/dotemacs/issues
")))

(add-to-list 'fancy-startup-text
             '("\nYou are running a customized Emacs configuration. See "  :link
               ("here"
                #[257 "\300\301!\207"
                      [browse-url-default-browser "http://github.com/izahn/dotemacs/"]
                      3 "\n\n(fn BUTTON)"]
                "Open the README file")
               "\nfor information about these customizations.\n"))
```

### Load theme<a id="sec-2-3-5" name="sec-2-3-5"></a>

Loading the theme should come as early as possible in the init sequence to avoid jarring visual changes during startup, but must come after loading packages because we use a custom theme that needs to be installed first.

```lisp
;; finally a theme I can live with!
(load-theme 'leuven t) 
;; but it still needs a few tweeks
(setq org-fontify-whole-heading-line nil)

;; mode line theme
(require 'powerline)
;; face for remote files in modeline
(defface my-mode-line-attention
'((t (:foreground "magenta" :weight bold)))
 "face for calling attention to modeline")

;; highlight hostname if on remote
(defconst my-mode-line-buffer-identification
  '(:eval
    (list
     (propertize
      (if (file-remote-p default-directory 'host)
          (progn
      (let ((host-name
             (or (file-remote-p default-directory 'host)
                 (system-name))))
        (if (string-match "^[^0-9][^.]*\\(\\..*\\)" host-name)
            (substring host-name 0 (match-beginning 1))
          host-name)))
        "")
      'face
      (if (file-remote-p default-directory 'host)
          'my-mode-line-attention
        'mode-line-buffer-id))
   (propertize ": %b"
               'face
                 (if (file-remote-p default-directory 'host)
                     'my-mode-line-attention
                   'mode-line-buffer-id)))))

;; powerline theme using above info about remote hosts.
(defun powerline-my-theme ()
  "Setup the default mode-line."
  (interactive)
  (setq-default mode-line-format
                '("%e"
                  (:eval
                   (let* ((active (powerline-selected-window-active))
                          (mode-line (if active 'mode-line 'mode-line-inactive))
                          (face1 (if active 'powerline-active1 'powerline-inactive1))
                          (face2 (if active 'powerline-active2 'powerline-inactive2))
                          (separator-left (intern (format "powerline-%s-%s"
                                                          powerline-default-separator
                                                          (car powerline-default-separator-dir))))
                          (separator-right (intern (format "powerline-%s-%s"
                                                           powerline-default-separator
                                                           (cdr powerline-default-separator-dir))))
                          (lhs (list (powerline-raw "%*" nil 'l)
                                     (powerline-buffer-size nil 'l)
                                     (powerline-raw mode-line-mule-info nil 'l)
                                     (powerline-raw mode-line-remote nil 'l)
                                     (powerline-raw my-mode-line-buffer-identification nil 'l)
                                     (when (and (boundp 'which-func-mode) which-func-mode)
                                       (powerline-raw which-func-format nil 'l))
                                     (powerline-raw " ")
                                     (funcall separator-left mode-line face1)
                                     (when (boundp 'erc-modified-channels-object)
                                       (powerline-raw erc-modified-channels-object face1 'l))
                                     (powerline-major-mode face1 'l)
                                     (powerline-process face1)
                                     (powerline-minor-modes face1 'l)
                                     (powerline-narrow face1 'l)
                                     (powerline-raw " " face1)
                                     (funcall separator-left face1 face2)
                                     (powerline-vc face2 'r)))
                          (rhs (list (powerline-raw global-mode-string face2 'r)
                                     (funcall separator-right face2 face1)
                                     (powerline-raw "%4l" face1 'l)
                                     (powerline-raw ":" face1 'l)
                                     (powerline-raw "%3c" face1 'r)
                                     (funcall separator-right face1 mode-line)
                                     (powerline-raw " ")
                                     (powerline-raw "%6p" nil 'r)
                                     (powerline-hud face2 face1))))
                     (concat (powerline-render lhs)
                             (powerline-fill face2 (powerline-width rhs))
                             (powerline-render rhs)))))))

(powerline-my-theme)
(powerline-my-theme)
```

### Add custom lisp director to load path<a id="sec-2-3-6" name="sec-2-3-6"></a>

We try to install most things using the package manager, but a few things need to be included in a custom lisp directory. Add it to the path so we can load from it easily.

```lisp
;; add custom lisp directory to path
(let ((default-directory (concat user-emacs-directory "lisp/")))
  (setq load-path
        (append
         (let ((load-path (copy-sequence load-path))) ;; Shadow
           (append 
            (copy-sequence (normal-top-level-add-to-load-path '(".")))
            (normal-top-level-add-subdirs-to-load-path)))
         load-path)))

;; on OSX Emacs needs help setting up the system paths
(when (memq window-system '(mac ns))
  (exec-path-from-shell-initialize))
```

### Spell checking<a id="sec-2-3-7" name="sec-2-3-7"></a>

```lisp
;; enable on-the-fly spell checking
(add-hook 'text-mode-hook
          (lambda ()
            (flyspell-mode 1)))

;; prevent flyspell from finding mistakes in the code
(add-hook 'prog-mode-hook
          (lambda ()
            ;; `ispell-comments-and-strings'
            (flyspell-prog-mode)))
;; ispell should not check code blocks
(add-to-list 'ispell-skip-region-alist '(":\\(PROPERTIES\\|LOGBOOK\\):" . ":END:"))
(add-to-list 'ispell-skip-region-alist '("#\\+BEGIN_SRC" . "#\\+END_SRC"))
(add-to-list 'ispell-skip-region-alist '("#\\+begin_src" . "#\\+end_src"))
(add-to-list 'ispell-skip-region-alist '("^#\\+begin_example ". "#\\+end_example$"))
(add-to-list 'ispell-skip-region-alist '("^#\\+BEGIN_EXAMPLE ". "#\\+END_EXAMPLE$"))
(add-to-list 'ispell-skip-region-alist '("^```\\{". "```"))
```

### Fonts<a id="sec-2-3-8" name="sec-2-3-8"></a>

Emacs fonts are "just OK" out of the box. Not bad, but not great either. Here we set fallback fonts for different Unicode blocks, dramatically increasing the number of characters Emacs will display.

```lisp
;; unicode-fonts doesn't work well on emacs < 24.3
(when (>= (string-to-number 
             (concat 
              (number-to-string emacs-major-version) 
              "." 
              (number-to-string emacs-minor-version)))
            24.3)
  (require 'persistent-soft)
  (require 'unicode-fonts)
  (unicode-fonts-setup))
```

### Printing<a id="sec-2-3-9" name="sec-2-3-9"></a>

If you're using [Vincent Goulet's emacs](http://vgoulet.act.ulaval.ca/en/emacs/windows/) on Windows printing should work out of the box. If you're on Linux or Mac the experience of printing from emacs may leave something to be desired. Here we try to make it work a little better by making it easier to preview buffers in a web browser (you can print from there as usual) and by using [gtklp](http://sourceforge.net/projects/gtklp/) on Linux if it is available.

```lisp
(when (eq system-type 'gnu/linux)
  (setq hfyview-quick-print-in-files-menu t)
  (require 'hfyview)
  (setq mygtklp (executable-find "gtklp"))
  (when mygtklp
    (setq lpr-command "gtklp")
    (setq ps-lpr-command "gtklp")))

(when (eq system-type 'darwin)
  (setq hfyview-quick-print-in-files-menu t)
  (require 'hfyview))
```

### Minibuffer hints and completion<a id="sec-2-3-10" name="sec-2-3-10"></a>

There are several different systems for providing completion hints in emacs. The default pcomplete system shows completions on demand (usually bound to tab key) in an emacs buffer. Here we set up ido-mode, which instead shows these completions on-the-fly in the minibuffer. These completions are primarily used to show available files (e.g., with `find-file`) and emacs functions (e.g., with `execute-extended-command`). Completion for in-buffer text (e.g., methods in python-mode, or arguments in R-mode) are handled separately by company-mode.

```lisp
;;; Completion hints for files and buffers buffers
(setq ido-file-extensions-order '(".R" ".r" ".sh" ".tex" ".bib" ".org" 
                                  ".py" ".emacs" ".xml" "org.el" ".pdf"
                                  ".txt" ".html" ".png" ".ini" ".cfg" 
                                  ".conf"))

;; load ido 
(require 'ido)
(setq ido-auto-merge-work-directories-length -1) ;; disable auto-merge
(setq ido-use-virtual-buffers t) ;; show recent files in buffer menu
(ido-mode 1)
(ido-everywhere 1)
(setq ido-enable-flex-matching t)

;; use ido everywhere you can
(require 'ido-ubiquitous)
(ido-ubiquitous-mode 1)

;; present ido suggestions vertically
(require 'ido-vertical-mode)
(ido-vertical-mode 1)

;; set nice ido decorations
(setq ido-decorations '("\n➔ " "" "\n " "\n ..." "[" "]" " [No match]" " [Matched]" " [Not readable]" " [Too big]" " [Confirm]" "\n➔ " ""))

;; don't use ido for dired
(setq ido-read-file-name-non-ido '(dired))

;; color directories blue, firstmatch bold etc.
(set-face-attribute 'ido-first-match nil
                    :weight 'bold 
                    :height '1.125
                    :foreground "red")
(set-face-attribute 'ido-only-match nil
                    :weight 'bold 
                    :height '1.125
                    :foreground "ForestGreen")

(set-face-attribute 'ido-subdir nil
                    :foreground "blue")

;; set sensible keys for id in vertical mode
(setq ido-vertical-define-keys (quote C-n-C-p-up-down-left-right))

;; use ido for kill-ring
;;(require 'kill-ring-ido)
;;(setq kill-ring-ido-shortage-length 20)

;;(global-set-key (kbd "M-y") 'kill-ring-ido)

;; show recently opened files
(require 'recentf)
(setq recentf-max-menu-items 50)
(recentf-mode 1)

(setq ido-use-virtual-buffers 'auto)

(defun ido-recentf-open ()
  "Use `ido-completing-read' to find a recent file."
  (interactive)
  (if (find-file (ido-completing-read "Find recent file: " recentf-list))
      (message "Opening file...")
    (message "Aborting")))

(global-set-key (kbd "C-x C-r") 'ido-recentf-open)

  ;;; Completion hints for emacs functions
;; Horrible work-around to make smex work with emacs < 24.3:
;; remove this part when emacs is updated.
;; Check if Smex is supported
(when (equal (cons 1 1)
             (ignore-errors
               (subr-arity (symbol-function 'execute-extended-command))))
  (defun execute-extended-command (prefixarg &optional command-name)
    "Read function name, then read its arguments and call it."
    (interactive (list current-prefix-arg (read-extended-command)))
    (if (null command-name)
        (setq command-name (let ((current-prefix-arg prefixarg)) ; for prompt
                             (read-extended-command))))
    (let* ((function (and (stringp command-name) (intern-soft command-name)))
           (binding (and suggest-key-bindings
                         (not executing-kbd-macro)
                         (where-is-internal function overriding-local-map t))))
      (unless (commandp function)
        (error "`%s' is not a valid command name" command-name))
      (setq this-command function)
      (setq real-this-command function)
      (let ((prefix-arg prefixarg))
        (command-execute function 'record))
      (when binding
        (let* ((waited
                (sit-for (cond
                          ((zerop (length (current-message))) 0)
                          ((numberp suggest-key-bindings) suggest-key-bindings)
                          (t 2)))))
          (when (and waited (not (consp unread-command-events)))
            (with-temp-message
                (format "You can run the command `%s' with %s"
                        function (key-description binding))
              (sit-for (if (numberp suggest-key-bindings)
                           suggest-key-bindings
                         2)))))))))
;; end horrible hack

(smex-initialize)
(global-set-key (kbd "M-x") 'smex)
(global-set-key (kbd "M-X") 'smex-major-mode-commands)
;; This is your old M-x.
(global-set-key (kbd "C-c C-c M-x") 'execute-extended-command)

;; modify smex so that typing a space will insert a hyphen 
;; (from http://www.emacswiki.org/Smex#toc6)
(defadvice smex (around space-inserts-hyphen activate compile)
  (let ((ido-cannot-complete-command 
         (lambda ()
            (interactive)
            (if (string= " " (this-command-keys))
                (insert ?-)
              (funcall ,ido-cannot-complete-command)))))
    ad-do-it))
```

### Auto-complete configuration<a id="sec-2-3-11" name="sec-2-3-11"></a>

Here we configure in-buffer text completion using the company-mode package. These completions are available on-demand using the `C-TAB` or `M-x company-complete`.

```lisp
;;Use C-TAB to complete. We put this in eval-after-load 
;; because otherwise some modes will try to override our settings.
(eval-after-load "company"
  '(progn
     ;; don't start automatically 
     (setq company-idle-delay nil)
     ;; cancel if input doesn't match
     (setq company-require-match nil)
     ;; complete using C-TAB
     (global-set-key (kbd "<C-tab>") 'company-complete)
     ;; use C-n and C-p to cycle through completions
     ;; (define-key company-mode-map (kbd "<tab>") 'company-complete)
     (define-key company-active-map (kbd "C-n") 'company-select-next)
     (define-key company-active-map (kbd "<tab>") 'company-select-next)
     (define-key company-active-map (kbd "C-p") 'company-select-previous)
     (define-key company-active-map (kbd "<backtab>") 'company-select-previous)
     ;; enable math completions
     (require 'company-math)
     ;; company-mode completions for ess
     (require 'company-ess)
     (add-to-list 'company-backends 'company-math-symbols-unicode)
     ;(add-to-list 'company-backends 'company-math-symbols-latex)
     ;; put company-capf at the beginning of the list
     (require 'company-capf)
     (setq company-backends
          (delete-dups (cons 'company-capf company-backends)))
     ;; theme
     (set-face-attribute 'company-scrollbar-bg nil
                         :background "gray")
     (set-face-attribute 'company-scrollbar-fg nil
                         :background "black")
     (set-face-attribute 'company-tooltip nil
                         :foreground "black"
                         :background "lightgray")
     (set-face-attribute 'company-tooltip-selection nil
                         :foreground "white"
                         :background "steelblue")
     ;; ;; disable dabbrev
     ;; (delete 'company-dabbrev company-backends)
     ;; (delete 'company-dabbrev-code company-backends)
     ))

(add-hook 'after-init-hook 'global-company-mode)

;; completion for kill ring history
(require 'popup)
(require 'pos-tip)
(require 'popup-kill-ring)

(global-set-key "\M-y" 'popup-kill-ring)
```

### Outline-magic<a id="sec-2-3-12" name="sec-2-3-12"></a>

I encourage you to use org-mode for note taking and outlining, but it can be convenient to treat arbitrary buffers as outlines. The outline-magic mode can help with that.

```lisp
;;; Configure outline minor modes
;; Less crazy key bindings for outline-minor-mode
(setq outline-minor-mode-prefix "\C-c\C-o")
;; load outline-magic along with outline-minor-mode
(add-hook 'outline-minor-mode-hook 
          (lambda () 
            (require 'outline-magic)
            (define-key outline-minor-mode-map "\C-c\C-o\t" 'outline-cycle)))
```

### Major modes configuration<a id="sec-2-3-13" name="sec-2-3-13"></a>

1.  Programming mode

    ```lisp
    (add-hook 'prog-mode-hook
              (lambda()
                ;; turn on outline minor mode:
                (add-hook 'prog-mode-hook 'outline-minor-mode)
                 ;; make sure completion calls company-capf first
                (require 'company-capf)
                (set (make-local-variable 'company-backends)
                     (cons 'company-capf company-backends))
                (delete-dups company-backends)
                ))
    ```

2.  General repl (read-eval-print-loop) config

    Load eval-in-repl for bash, elisp, and python interaction.
    
    ```lisp
    ;; require the main file containing common functions
    (require 'eval-in-repl)
    (setq comint-process-echoes t)
    
    ;; truncate lines in comint buffers
    (add-hook 'comint-mode-hook
              (lambda()
                (setq truncate-lines 1)))
    ```

3.  Run R in emacs (ESS)

    ```lisp
      ;;;  ESS (Emacs Speaks Statistics)
    
    ;; Start R in the working directory by default
    (setq ess-ask-for-ess-directory nil)
    
    ;; Scroll down when R generates output
    (setq comint-scroll-to-bottom-on-input t)
    (setq comint-scroll-to-bottom-on-output t)
    (setq comint-move-point-for-output t)
    
    ;; Make sure ESS is loaded
    (require 'ess-site)
    
    ;; disable ehoing input
    (setq ess-eval-visibly nil)
    
    ;; extra ESS stuff inspired by https://github.com/gaborcsardi/dot-emacs/blob/master/.emacs
    (ess-toggle-underscore nil)
    (defun my-ess-post-run-hook ()
      ;; reset output width when window is re-sized
      (add-hook 'inferior-ess-mode-hook
                (lambda()
                  (defun my-ess-execute-screen-options (foo)
                    (ess-execute-screen-options))
                  (add-to-list
                   'window-size-change-functions
                   'my-ess-execute-screen-options)))
      )
    (add-hook 'ess-post-run-hook 'my-ess-post-run-hook)
    (add-hook 'ess-mode-hook (lambda () ))
    ;; truncate long lines in R source files
    (add-hook 'ess-mode-hook
              (lambda()
                ;; don't wrap long lines
                (setq truncate-lines 1)
                ;; better (but still not right) indentation
                (setq ess-first-continued-statement-offset 2)
                (setq ess-continued-statement-offset 0)
                (setq ess-arg-function-offset nil)
                (setq ess-arg-function-offset-new-line nil)
                (setq ess-continued-statement-offset 0)
                (setq ess-expression-offset nil)
                ;; put company-capf at the front of the completion sources list
                (set (make-local-variable 'company-backends)
                     (cons 'company-capf company-backends))
                (delete-dups company-backends)
                ))
    
    (add-hook 'R-mode-hook
              (lambda()
                ;; make sure completion calls company-ess first
                (require 'company-ess)
                (set (make-local-variable 'company-backends)
                     (cons 'company-ess-backend company-backends))
                (delete-dups company-backends)
                ))
    
    ;; enable 
    (setq ess-R-font-lock-keywords
          (quote
           ((ess-R-fl-keyword:modifiers . t)
            (ess-R-fl-keyword:fun-defs . t)
            (ess-R-fl-keyword:keywords . t)
            (ess-R-fl-keyword:assign-ops . t)
            (ess-R-fl-keyword:constants . t)
            (ess-fl-keyword:fun-calls . t)
            (ess-fl-keyword:numbers . t)
            (ess-fl-keyword:operators . t)
            (ess-fl-keyword:delimiters . t)
            (ess-fl-keyword:= . t)
            (ess-R-fl-keyword:F&T . t))))
    
    ;; ;; try to get sane indentation
    ;; (setq ess-first-continued-statement-offset 2)
    ;; (setq ess-continued-statement-offset 0)
    ;; (setq ess-arg-function-offset-new-line 0)
    ;; (setq ess-arg-function-offset nil)
    ;; (setq ess-default-style 'DEFAULT)
    ```

4.  Run python in emacs (anaconda-mode)

    ```lisp
    (when (executable-find "pip")
      (require 'anaconda-mode)
      (require 'company-anaconda)
      (add-hook 'python-mode-hook 'anaconda-mode)
      (add-hook 'python-mode-hook 'eldoc-mode)
      (add-hook 'python-mode-hook
                (lambda()
                  (setq-local company-backends
                              (cons 'company-anaconda company-backends))))
      ;; use ipython if available
      (if (executable-find "ipython")
          (setq python-shell-interpreter "ipython")))
    ```

5.  emacs lisp REPL (ielm)

    ```lisp
    ;; ielm
    (require 'eval-in-repl-ielm)
    ;; For .el files
    (define-key emacs-lisp-mode-map "\C-c\C-c" 'eir-eval-in-ielm)
    ;; For *scratch*
    (define-key lisp-interaction-mode-map "\C-c\C-c" 'eir-eval-in-ielm)
    ;; For M-x info
    (define-key Info-mode-map "\C-c\C-c" 'eir-eval-in-ielm)
    
    ;; Set up completions
    (add-hook 'emacs-lisp-mode-hook
              (lambda()
                 ;; make sure completion calls company-elisp first
                 (require 'company-elisp)
                 (set (make-local-variable 'company-backends)
                      (cons 'company-elisp company-backends))
                 (delete-dups company-backends)
                 ))
    ```

6.  Light-weight markup language (Markdown mode)

    ```lisp
    ;;; markdown mode
    
    ;; Use markdown-mode for files with .markdown or .md extensions
    (add-to-list 'auto-mode-alist '("\\.markdown\\'" . markdown-mode))
    (add-to-list 'auto-mode-alist '("\\.md\\'" . markdown-mode))
    ```

7.  Typesetting markup (AucTeX)

    ```lisp
    ;;; AucTeX config
    ;; turn on math mode and and index to imenu
    (add-hook 'LaTeX-mode-hook 
              (lambda ()
                 (turn-on-reftex)
                 (TeX-PDF-mode t)
                 (LaTeX-math-mode)
                 (TeX-source-correlate-mode t)
                 (imenu-add-to-menubar "Index")
                 (outline-minor-mode)
                 ;; completion
                 (setq-local company-backends
                             (delete-dups (cons 'company-files
                                                company-backends)))
                 (setq-local company-backends
                             (delete-dups (cons '(company-math-symbols-latex company-latex-commands company-math-symbols-unicode)
                                                company-backends)))
                 ;; Allow paragraph filling in tables
                 (setq LaTeX-indent-environment-list
                       (delq (assoc "table" LaTeX-indent-environment-list)
                             LaTeX-indent-environment-list))
                 (setq LaTeX-indent-environment-list
                       (delq (assoc "table*" LaTeX-indent-environment-list)
                             LaTeX-indent-environment-list))))
    ;; Misc. latex settings
    (setq TeX-parse-self t
          TeX-auto-save t)
    (setq-default TeX-master nil)
    ;; Add beamer frames to outline list
    (setq TeX-outline-extra
          '(("\\\\begin{frame}\n\\|\\\\begin{frame}.*{.*}\\|[       ]*\\\\frametitle\\b" 3)))
    ;; reftex settings
    (setq reftex-enable-partial-scans t)
    (setq reftex-save-parse-info t)
    (setq reftex-use-multiple-selection-buffers t)
    (setq reftex-plug-into-AUCTeX t)
    (add-hook 'bibtex-mode-hook
              (lambda ()
                 (define-key bibtex-mode-map "\M-q" 'bibtex-fill-entry)))
    ```

8.  Note taking and outlining (Org-mode)

    ```lisp
    (require 'org)
    (set-face-attribute 'org-meta-line nil
                        :background nil
                        :foreground "#B0B0B0")
    (setq org-startup-indented t)
    ;; increase imenu depth to include third level headings
    (setq org-imenu-depth 3)
    ;; Load additional export formats
    (require 'ox-odt)
    (require 'ox-md)
    ;; (require 'ox-freemind)
    (require 'ox-bibtex)
    
    ;; Update images from babel code blocks automatically
    (add-hook 'org-babel-after-execute-hook 'org-display-inline-images)
    
    ;; Enable common programming language support in org-mode
    (org-babel-do-load-languages
     'org-babel-load-languages
     '((R . t)
       (python . t)
       (matlab . t)
       (emacs-lisp . t)
       (sh . t)
       (dot . t)
       (latex . t)
       (octave . t)
       (ditaa . t)
       (org . t)
       (perl . t)
       (julia . t)
    ))
    
    ;; Set sensible mode for editing dot files
    (add-to-list 'org-src-lang-modes '("dot" . graphviz-dot))
    
    ;; Fontify code blocks in org-mode
    (setq org-src-fontify-natively t)
    (setq org-src-tab-acts-natively t)
    (setq org-confirm-babel-evaluate nil)
    
    (require 'org-capture)
    (require 'org-protocol)
    (require 'ob-stata)
    
    ;; set up capture
    (setq org-default-notes-file (concat org-directory "/notes.org"))
    
    (setq org-capture-templates
          '(("t" "Todo" entry (file+headline "~/org/notes.org" "RT Tasks")
             "* TODO %?\n  %i\n  %a")))
    
    (define-key global-map "\C-cc" 'org-capture)
    ```

9.  Multiple modes in one "buffer" (polymode)

    ```lisp
    ;;; polymode
    
    ;; polymode requires emacs >= 24.3, does not work on the RCE. 
    (when (>= (string-to-number 
               (concat 
                (number-to-string emacs-major-version) 
                "." 
                (number-to-string emacs-minor-version)))
              24.3)
      ;; Activate polymode for files with the .md extension
      (add-to-list 'auto-mode-alist '("\\.md" . poly-markdown-mode))
      ;; Activate polymode for R related modes
      (add-to-list 'auto-mode-alist '("\\.Snw" . poly-noweb+r-mode))
      (add-to-list 'auto-mode-alist '("\\.Rnw" . poly-noweb+r-mode))
      (add-to-list 'auto-mode-alist '("\\.Rmd" . poly-markdown+r-mode))
      (add-to-list 'auto-mode-alist '("\\.rapport" . poly-rapport-mode))
      (add-to-list 'auto-mode-alist '("\\.Rhtml" . poly-html+r-mode))
      (add-to-list 'auto-mode-alist '("\\.Rbrew" . poly-brew+r-mode))
      (add-to-list 'auto-mode-alist '("\\.Rcpp" . poly-r+c++-mode))
      (add-to-list 'auto-mode-alist '("\\.cppR" . poly-c++r-mode)))
    ```

10. File browsing (Dired+)

    ```lisp
    ;;; Dired and Dired+ configuration
    ;; show git status in dired
    (require 'diff-hl)
    (add-hook 'dired-mode-hook 
              (lambda()
                (diff-hl-dired-mode)
                (diff-hl-margin-mode)))
    
    ;; show details by default
    (setq diredp-hide-details-initially-flag nil)
    ;; load dired+ and mouse3
    (require 'dired+)
    (require 'mouse3)
    
    ;; set dired listing options
    (setq dired-listing-switches "-alDhp")
    
    ;; more subdued colors
    (set-face-attribute 'diredp-ignored-file-name nil
                        :foreground "LightGray"
                        :background nil)
    (set-face-attribute 'diredp-read-priv nil
                        :foreground "LightGray"
                        :background nil)
    (set-face-attribute 'diredp-write-priv nil
                        :foreground "LightGray"
                        :background nil)
    (set-face-attribute 'diredp-other-priv nil
                        :foreground "LightGray"
                        :background nil)
    (set-face-attribute 'diredp-rare-priv nil
                        :foreground "LightGray"
                        :background nil)
    (set-face-attribute 'diredp-no-priv nil
                        :foreground "LightGray"
                        :background nil)
    (set-face-attribute 'diredp-exec-priv nil
                        :foreground "LightGray"
                        :background nil)
    (set-face-attribute 'diredp-file-name nil
                        :weight 'bold
                        :background nil)
    (set-face-attribute 'diredp-dir-priv nil
                        :weight 'bold)
    (set-face-attribute 'diredp-file-suffix nil
                        :foreground nil)
    
    ;; make sure dired buffers end in a slash so we can identify them easily
    (defun ensure-buffer-name-ends-in-slash ()
      "change buffer name to end with slash"
      (let ((name (buffer-name)))
        (if (not (string-match "/$" name))
            (rename-buffer (concat name "/") t))))
    (add-hook 'dired-mode-hook 'ensure-buffer-name-ends-in-slash)
    (add-hook 'dired-mode-hook
              (lambda()
                 (setq truncate-lines 1)))
    
    ;; open files in external programs
    ;; (from http://ergoemacs.org/emacs/emacs_dired_open_file_in_ext_apps.html
    (defun xah-open-in-external-app (&optional file)
      "Open the current file or dired marked files in external app.
    
    The app is chosen from your OS's preference."
      (interactive)
      (let (doIt
            (myFileList
             (cond
              ((string-equal major-mode "dired-mode")
               (dired-get-marked-files))
              ((not file) (list (buffer-file-name)))
              (file (list file)))))
        (setq doIt (if (<= (length myFileList) 5)
                       t
                     (y-or-n-p "Open more than 5 files? "))) 
        (when doIt
          (cond
           ((string-equal system-type "windows-nt")
            (mapc
             (lambda (fPath)
               (w32-shell-execute "open" (replace-regexp-in-string "/" "\\" fPath t t)))
             myFileList))
           ((string-equal system-type "darwin")
            (mapc
             (lambda (fPath)
               (shell-command (format "open \"%s\"" fPath)))
             myFileList))
           ((string-equal system-type "gnu/linux")
            (mapc
             (lambda (fPath)
               (let ((process-connection-type nil))
                 (start-process "" nil "xdg-open" fPath))) myFileList))))))
    ;; open files from dired with "E"
    (define-key dired-mode-map (kbd "E") 'xah-open-in-external-app)
    ;; use zip/unzip to compress/uncompress zip archives
    (eval-after-load "dired-aux"
     '(add-to-list 'dired-compress-file-suffixes 
                   '("\\.zip\\'" "" "unzip")))
    ```

11. Shell modes (term, shell and eshell)

    ```lisp
    ;; term
    (require 'multi-term)
    (define-key term-mode-map (kbd "C-j") 'term-char-mode)
    (define-key term-raw-map (kbd "C-j") 'term-line-mode)
    ;; shell
    (require 'essh) ; if not done elsewhere; essh is in the local lisp folder
    (require 'eval-in-repl-shell)
    (add-hook 'sh-mode-hook
              (lambda()
                 (local-set-key "\C-c\C-c" 'eir-eval-in-shell)))
    
    
    ;; Automatically adjust output width in commint buffers
    ;; from http://stackoverflow.com/questions/7987494/emacs-shell-mode-display-is-too-wide-after-splitting-window
    (defun comint-fix-window-size ()
      "Change process window size."
      (when (derived-mode-p 'comint-mode)
        (let ((process (get-buffer-process (current-buffer))))
          (unless (eq nil process)
            (set-process-window-size process (window-height) (window-width))))))
    
    (defun my-shell-mode-hook ()
      ;; add this hook as buffer local, so it runs once per window.
      (add-hook 'window-configuration-change-hook 'comint-fix-window-size nil t))
      ;; auto-complete for shell-mode (linux only)
    (if (eq system-type 'gnu/linux)
        (progn 
          (setq explicit-shell-file-name "bash")
          (setq explicit-bash-args '("-c" "-t" "export EMACS=; stty echo; bash"))  
          (ansi-color-for-comint-mode-on)
          (add-hook 'shell-mode-hook
              (lambda()
                 ;; make sure completion calls company-readline first
                 (require 'readline-complete)
                 (set (make-local-variable 'company-backends)
                      (cons 'company-readline company-backends))
                 (delete-dups company-backends)
                 ))
          (add-hook 'rlc-no-readline-hook (lambda () (company-mode -1)))))
    
    (add-hook 'shell-mode-hook
              (lambda()
                 ;; add this hook as buffer local, so it runs once per window.
                 (add-hook 'window-configuration-change-hook 'comint-fix-window-size nil t)))
    
    ;; extra completion for eshell
    (add-hook 'eshell-mode-hook
              (lambda()
                 (require 'pcmpl-args)
                 (require 'pcmpl-pip)
                 ;; programs that don't work well in eshell and should be run in visual mode
                 (add-to-list 'eshell-visual-commands "ssh")
                 (add-to-list 'eshell-visual-commands "tail")
                 (add-to-list 'eshell-visual-commands "htop")
                 (setq eshell-visual-subcommands '(("git" "log" "diff" "show")))))
    ```

### Miscellaneous<a id="sec-2-3-14" name="sec-2-3-14"></a>

```lisp
;;; Misc. Conveniences

;; show number of matches in mode line when searching
(global-anzu-mode +1)

;; get help from the web
(require 'google-this)
(google-this-mode 1)
(require 'howdoi)

;; window arrangement history
;; (setq winner-dont-bind-my-keys t) 
(winner-mode 1)

;;; set up unicode
(prefer-coding-system       'utf-8)
(set-default-coding-systems 'utf-8)
(set-terminal-coding-system 'utf-8)
(set-keyboard-coding-system 'utf-8)
(setq buffer-file-coding-system 'utf-8)                      
(setq x-select-request-type '(UTF8_STRING COMPOUND_TEXT TEXT STRING))

;; ;; use regex search by default
;; (global-set-key (kbd "C-s") 'isearch-forward-regexp)
;; (global-set-key (kbd "C-r") 'isearch-backward-regexp)

;; Use spaces for indentation
(setq-default indent-tabs-mode nil)

;; Make sure copy-and-paste works with other programs
;; (not needed in recent emacs?)
;; (setq x-select-enable-clipboard t
;;       x-select-enable-primary t
;;       save-interprogram-paste-before-kill t)

;; Text pasted with mouse should be inserted at cursor position
(setq mouse-yank-at-point t)

;; Mouse scrolling behavior
  (setq mouse-wheel-scroll-amount '(1 ((shift) . 1))) ;; one line at a time
  (setq mouse-wheel-follow-mouse 't) ;; scroll window under mouse

;; Put backups in a separate folder
(setq backup-directory-alist `(("." . ,(concat user-emacs-directory
                                               "backups"))))

;; Apropos commands should search everything
(setq apropos-do-all t)

;; Store the places file in the emacs user directory
(setq save-place-file (concat user-emacs-directory "places"))


;; better naming of duplicate buffers
(require 'uniquify)
(setq uniquify-buffer-name-style 'forward)

;; put cursor in last used position when re-opening file
(require 'saveplace)
(setq-default save-place t)

;; Use y/n instead of yes/no
(fset 'yes-or-no-p 'y-or-n-p)

(transient-mark-mode 1) ; makes the region visible
(line-number-mode 1)    ; makes the line number show up
(column-number-mode 1)  ; makes the column number show up

(setq global-font-lock-mode 1) ; everything should use fonts
(setq font-lock-maximum-decoration t) ;; decorate as much as possible
(show-paren-mode 1) ;; highlight matching paren

;; smooth scrolling with C-up/C-down
(require 'smooth-scroll)
(smooth-scroll-mode)
(global-set-key [(control down)] 'scroll-up-1)
(global-set-key [(control up)] 'scroll-down-1)
(global-set-key [(control left)] 'scroll-right-1)
(global-set-key [(control right)] 'scroll-left-1)

;; enable toggling paragraph un-fill
;; from http://www.emacswiki.org/emacs/UnfillParagraph
(defun unfill-paragraph ()
  "Takes a multi-line paragraph and makes it into a single line of text."
  (interactive)
  (let ((fill-column (point-max)))
    (fill-paragraph nil)))

(define-key global-map "\M-Q" 'unfill-paragraph)

;; line wrapping
(setq visual-line-fringe-indicators '(left-curly-arrow right-curly-arrow))
(add-hook 'text-mode-hook 'visual-line-mode 1)
(add-hook 'prog-mode-hook
          (lambda()
              (setq truncate-lines 1)))

;; don't require two spaces for sentence end.
(setq sentence-end-double-space nil)

;; Use CUA mode only for handy rectangle features
(cua-selection-mode t)

;; use windresize for changing window size
(require 'windresize)

;; use windmove for navigating windows
(global-set-key (kbd "<M-S-left>")  'windmove-left)
(global-set-key (kbd "<M-S-right>") 'windmove-right)
(global-set-key (kbd "<M-S-up>")    'windmove-up)
(global-set-key (kbd "<M-S-down>")  'windmove-down)
;; The beeping can be annoying--turn it off
(set-variable 'visible-bell t)

;; save settings made using the customize interface to a sparate file
(setq custom-file (concat user-emacs-directory "custom.el"))
(unless (file-exists-p custom-file)
  (write-region ";; Put user configuration here" nil custom-file))
(load custom-file 'noerror)
```