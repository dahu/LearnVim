*learnvim.txt*  A Suggested Path for Learning Vim


		VIM REFERENCE MANUAL	by Barry Arthur (bairui)

                                                               *learnvim*

This help file introduces fundamental concepts, offers concrete advice for
correctly configuring a new Vim instance and outlines a progressive set of
topics for the enthusiastic newcomer to study and practice.

This is not a typical tutorial for Vim in that many topics are merely
introduced here with further study deferred to the excellent Vim Reference
Guide (|reference_toc|) and User Manual (|usr_toc|).

NOTE: If you would like to view this help file in full-screen instead of the
split window that Vim shows for help files by default, type `:only` now.


##############################################################################
THE VIM LEARNING PATH                             *learnvim-path-overview*

|learnvim-Beginner|
|learnvim-Intermediate|
|learnvim-Moderate|
|learnvim-Advanced|

Extras~

|learnvim-Plugins|
|learnvim-External-Resources|

##############################################################################
BEGINNER TOPICS                                 *lv_B* *learnvim-Beginner*

Competencies ~

On completing this section, you will:

|lv_B_I|	Be able to use Vim's extensive help system.

|lv_B_II|	Know where to find fundamental information on using Vim along
		with a legend on understanding how that information is
		presented.

|lv_B_III|	Know where the various configuration files for Vim are
		located, what each one is responsible for, and how to set
		options to control Vim's behaviour and customise its interface.

|lv_B_IV|	Have created your own vimrc and gvimrc configuration files.

==============================================================================
USING HELP                                  *lv_B_I* *learnvim-Using-Help*

Vim's internal help system is comprehensive, well indexed and easy to
navigate.  Beginners however often have difficulty knowing what to search for
in the first place.  Several solutions to that problem are provided here.
First is a guided tour of how to use Vim's help system.  Second is a broader
way to search for information within the help system.

1. Learning how to use Vim's Help        *learnvim-essential-introduction*

To read a help topic, move your cursor to that topic and type |ctrl-]|.  To
return to where you came from, type |ctrl-t|.  Try that now by reading the help
for the command I showed you at the very beginning of this tutorial: |:only|.

QUIZ~

1. What are the two equivalent keyboard shortcuts for the |:only| command?

2. Do you like being quizzed on material as you're learning?
     i. Did you know that quizes increase retention by requiring recall?


Now continue to practice your |ctrl-]| and |ctrl-t| skills by reading the
next three essential (and brief) help topics.  You will think I jest when I
say that a 200 line help file is brief, but I don't actually want you to read
-all- of that file -- just the first section.  Sections are shown in red (with
the default colour scheme) and are usually right-aligned.

|help.txt|	A quick overview of navigating Vim's help system.  Read
                everything in the first section - about 10 lines, and then
		jump back here.

		Note: that same help file is shown if you type the   |:help|
		      command without a topic.

|help-context|	A list of topic prepositions to specify the context of your
		help search.  Again, this is only about 10 lines long.

		Note: The astute reader will notice that not only does it come
		      from the same file (|help.txt|) as the previous section
		      I asked you to read, but it was the very next section!
		      Why didn't I just ask you to keep reading through that
		      file while you were there? Because practising to
		      navigate Vim's help system is the most important skill
		      you first need to learn in mastering Vim.

|notation|	An explanation of how information is presented in the help
		files. -Now- I'm asking you to read 200+ lines in all of
		Section 4 of |intro.txt|.  Actually, you can get away with
		skimming this one - but make sure you get a feel for how Vim's
		help files are layed out.

		Note: You may think that something so usefully named as
		      'intro.txt' should well be read in full.  If you're into
		      reading gobs of documentation, go hard.  However, to save
		      you time and trouble, this section of LearnVim has what
		      is considered to be the essential knowledge you need at
		      this stage.

                                           *pathogen-and-vim-help-sidebar*
----------Only For The Adventurous (Safe To Skip)-----------------------------
Install |learnvim-pathogen| so that you can easily install plugins in Vim. When
you've installed pathogen, test that you've done it right by installing
https://github.com/dahu/vim-help . Use the following to check for successul
installation:

After You Have Installed pathogen and vim-help:~

1. run |:Helptags| -- it should execute silently. If you see an error like: >

  E492: Not an editor command: Helptags
<
  Then you have not successfully installed pathogen. Refer again to its
  installation instructions online.

2. try `:help vim-help` -- it should open the help file for vim-help.

|vim-help| eases navigation within help files. Read its help to see how.
------------------------------------------------------------------------------

2. Trees Within The Forest                  *learnvim-take-apart-commands*

When newcomers see "complicated" commands in a Vim script or someone else's
vimrc and try to search for them in the help system, they often fail to find
what they're looking for.  Take for example the command sequence   gqip   to
reformat a paragraph.  Doing   :help gqip   will return the depressing message,
"Sorry, no help for gqip".  The problem here is in understanding Vim's command
syntax: |gq| and |ip| are separate entities. |gq| is an operator command (one
that takes a |motion|), whereas |ip| is a |text-object|.  The take-away here is
this tip: Learn to 'take apart' commands you see in Vim.  See
|learnvim-nomenclature| for more tips on recognising and understanding Vim
elements.

3. Broadening Your Search                     *learnvim-expand-help-terms*

Use the ctrl-d key when you're typing ":help <term>".  It will list matches
for the term in front of the cursor.  See |c_CTRL-D| for additional uses.

Another useful key is <Tab> which also expands terms on the Vim command line.
Depending on your settings ('wildmode' and 'wildmenu'), <Tab> will either
cycle through available matches or show a similar list to ctrl-d (and allow
you to cycle through that list).

4. Don't Panic!                                 *learnvim-help-bang-terms*

A lot of commands have `!` (bang) variants and are not listed separately in the
help system. The bang variants behave differently to their bare forms, but that
behaviour is different for each command. If you try to search for the bang
form, like `:help :next!` and get an error message like "E149: Sorry, no help
for next!" then you should search again for the bare form, `:help :next` and
read until you find mention of the `!` and its effect.

For a spot of comic relief, try: `:help!`

5. The Shotgun Approach                                *learnvim-helpgrep*

Sometimes you don't know the exact search term you should be using to find
what you need in the help files.  It can be frustrating trying to guess the
precise turn of phrase the help-file author tagged.  Of course, it's obvious
when you get there, but just like a good joke: until you hear the punch-line,
you would never have guessed it would end like that.

To search the help system and return all matches, use the |:helpgrep| command.

Recipe: Using helpgrep to broaden your search   *learnvim-recipe-helpgrep*
------------------------------------------------------------------------------
Problem: ~

You want to search by hexadecimal value, for example the character represented
by the value 0xAE (the ® symbol).  You've tried:
>
	:help hexadecimal
	:help hex
	:help search
	:help / and then searching within the help file for "hex"
<
If you had persisted in searching for subsequent matches in the last attempt,
you would have eventually found a table of |/character-classes| in which the
answer to your problem does indeed lie.  In itself, that is not a bad thing,
and it really didn't take too long to find the answer.  However, knowing that
you should have jumped into the help system with :help /character-classes is
by no means intuitive to the newcomer.

Solution: ~
>
	:helpgrep hex
	:cwindow
	/search

Produces: ~
>
	version7.txt|1018 col 48| |/\%x| \%x1a		search for character with 2 pos. hex number
	version7.txt|1020 col 50| |/\%u| \%u12ab	search for character with 4 pos. hex number
	version7.txt|1022 col 53| |/\%U| \%U1234abcd	search for character with 8 pos. hex number
<
Comments: ~

Admittedly, the information in the version_n_.txt files would probably not be
your primary resource, but it gives a good answer in this case.  The point is,
you can navigate the quickfix window for the answer you're seeking.  All the
normal Vim navigation methods are available, including hjkl, ctrl-f/ctrl-b,
and the method used here, searching with /.  Pressing <enter> on one of the
quickfix lines will open the corresponding file and place the cursor on the
associated line.

Note: Because this helpfile describes this process, the quickfix window will
have entries from here, and because "learnvim" precedes "version",
alphabetically, you will need to repeat your search several times (use the  n
key) to jump past the learnvim entries.
------------------------------------------------------------------------------

6. More Resources                           *learnvim-community-resources*

The Vim community is strong, helpful and polite.  The vim.wikia.com site, IRC
channel and mailing list are all great sources of information in learning Vim.

* IRC channel #vim on irc://irc.freenode.net
* Reddit/Vim - http://www.reddit.com/r/vim
* Mailing Lists - http://www.vim.org/community.php
* FAQ - http://vimhelp.appspot.com/vim_faq.txt.html
* Google - https://www.google.com/search?q=vim+topic
* StackOverflow - http://stackoverflow.com/questions/tagged/vim

IRC channel #vim on irc://irc.freenode.net~

The #vim freenode IRC channel has a fact bot called vimgor with answers to
common problems.
>
  /msg vimgor filetype
<
will show the information behind the fact filetype.

For searching, vimgor supports a listfacts command which returns all known
facts containing the given term, e.g:
>
  /msg vimgor listfacts file
<
will list all known facts containing file.

NOTE: You should explore vimgor using either /msg or /query to limit
      interference on the #vim channel.

Pastebin~

Use a pastebin for more than about 3 lines of data in an example on #vim.

The format of your pastebin is important. Here is an excellent example:
https://gist.github.com/2759774

Describe:~

* What you want to achieve
* Samples of your original data/text
* The outcome you would like
* What you have tried
* The output of:   :set magic? gdefault?
  (where the ? in those commands is essential)

Play nice: Patience & courtesy yields better results, faster.

NOTE: Regularly throughout LearnVim, you will be quizzed to help reinforce your
      learning. You're welcome.

QUIZ~

1. Quick! What one thing would you really like to know more about in Vim right
   now? Make a note of it and we'll return to this later.

2. What does the following command do? >

     FodFox
<
     i. What methods will you use to find the answer?
    ii. What mistakes did you make when searching?

3. What two methods can you use to show the choices available for commands on
   the |Cmdline| ?

4. How do you navigate inside a Vim help file? How do you follow links and
   return back from followed links? Name one plugin that eases Vim help file
   navigation.

5. How do you find help for `:write!` ?

NOTE: Move your cursor to the QUIZ ANSWERS line below and press |zo| to see
     inside |folds|

QUIZ ANSWERS {{{1~

2. FodFox is not a command in Vim. Well, not a single command.

** If you used Google, you failed. Most Vim commands are simply not searchable
   online.

** If you tried `:help FodFox`, you failed. Most Vim commands that you will see
   in the wild are actually a collection of commands and they are not separated
   for your convenience. You need to learn to separate them yourself.  Refer
   back to |learnvim-take-apart-commands| for a refresher.

** If you tried various different :help searches on the various pieces within
   the command, \o/ for you. The actual pieces are: |F| |d| |x|

3. Use |ctrl-d| and |<tab>| to show completion options on the |Cmdline|

4. |ctrl-]| follows a link (tag) in a help file. |ctrl-t| jumps back.

   The https://github.com/dahu/vim-help plugin is one way to ease help
   navigation. See |pathogen-and-vim-help-sidebar| if you skipped it earlier.
   All vimmers should be adventurous.

5. If you tried `:help :write!`, Vim told you "E149: Sorry, no help for
   :write!". Look up the bare form and read until you find mention of `!`.

1. Did you note down earlier the answer to this question: >

   What one thing would you really like to know more about in Vim right now?
<
   Using your newfound Vim help skills, try now to find out about that one
   thing you wrote down.

}}}1

==============================================================================
THE FUNDAMENTALS OF VIM          *lv_B_II* *learnvim-Fundamental-Concepts*

1. Climbing the Vim Learning Curve                   *learnvim-beginnings*

Vim has a steep learning curve that will take several days or weeks to even
begin turning from vertical.  Here is a good place to start:

|tutor|		The vimtutor is an interactive tutorial which teaches the
		fundamentals of Vim in around 30 minutes of hands-on fun.

|quickref|	Vim's Quick Reference:  An awesome overview and cheat-sheet.
		Of particular interest are the |option-list|, text objects
		(|Q_to|), pattern search summary (|Q_pa|), Repeating commands
		(|Q_re|), and Undo/Redo commands (|Q_ur|).

|vim-modes|	Vim is a modal editor.  Understanding the consequences and
		advantages of that is essential to mastering Vim.  Be sure to
		read the subsequent section on |mode-switching| too.

|user-manual|	The Table of Contents for Vim's User Manual.

There are also some really good Beginner Tutorials available online for Vim:

* http://blog.interlinked.org/tutorials/vim_tutorial.html
* http://derekwyatt.org/vim/tutorials/novice/

2. Definitions                                *learnvim-basic-definitions*

screen		The whole area that Vim uses to work in.  This can be a
		terminal emulator window.  Also called "the Vim window".

buffer		A buffer is just the word for the contents of a file.  Each
		buffer may be associated with one file path (the file it will
		be written to when you :w).  A buffer might not have an
		associated file path (like the empty buffer you get when you
		first start Vim).

window		A window is a place where a buffer can be displayed.  There is
		always at least one window open.  A buffer can be displayed in
		any number of windows simultaneously.  Having a buffer that
		isn't displayed in a window is useful when switching between
		different tasks, letting you walk away from half-finished work
		(See 'hidden').  Having a buffer that is displayed in two
		windows can be useful when trying to work on one part of the
		buffer based upon some context provided in another part of the
		buffer that's far away.

tab page	A tab page is a place to put a group of windows.  There is
		always at least one tab page open.  Each tab must always have
		at least one window in it.  The maximum number of windows is
		bounded only by the size of the Vim window.

Note: Trying to create a one-to-one relationship between tab pages and buffers
      is asking for trouble.  Lots of Vim commands change the buffer displayed
      in the current window, and some others create a new window in the
      current tab page.  Trying to lock a buffer to a single window inside a
      single tab page won't work; at least, not without cutting you off from
      many useful commands.

2. Nomenclature                                    *learnvim-nomenclature*

Like any large and complex system, Vim has a dense vocabulary of terms
surrounding its interface, operation and configuration.  Understanding this
terminology is essential for you to make significant progress in learning Vim.

When you see:		It means:

<CR>			Carriage Return, specifically, but realise that this
			is how Vim and vimmers talk about special keys in Vim.
			For example, the Escape key is written as <Esc>.  See
			|keycodes| for a list of these special keys.

i_CTRL-G_j		This term consists of three separate parts.  The
			leading i_ tells us this key is used in insert mode.
			Find more about these in |help-context|.  The CTRL-g
			tells us the first key to type and the _j tells us
			that this is a key sequence, and that we should type
			j   after the CTRL-g.

==============================================================================
CONFIGURING VIM                      *lv_B_III* *learnvim-Configuring-Vim*

Vim has many options which can be set at runtime or put in configuration files
to make them permanent.

1. Files                                    *learnvim-configuration-files*

/usr/share/vim/vimrc	The system-wide configuration file for both terminal
			and GUI Vim.  This file is used only if the user does
			not have a personal $HOME/.vimrc file.

/usr/share/vim/gvimrc	The system-wide configuration file for GUI Vim.  This
			file is used only if the user does not have a personal
			$HOME/.gvimrc file

$HOME/.vimrc		Personal configuration file for both terminal and GUI
			Vim.  You should create your own $HOME/.vimrc file to
			enable certain essential features, give sane values to
			important options and customise Vim to your
			preferences.  See |learnvim-vimrc| below for an
			annotated example .vimrc file you can use to get
			started.

$HOME/.gvimrc		Personal configuration file for GUI Vim.  You should
			create your own $HOME/.gvimrc file for the same
			reasons as with the .vimrc file.  The $HOME/.gvimrc
			file is also used to store GUI-specific settings like
			your GUI colorscheme, font and menu & toolbar options.
			See |learnvim-gvimrc| for an annotated example .gvimrc
			file you can use to get started.

                                        *learnvim-personal-vimrc-filename*
Note: The table above refers to the personal vimrc file as $HOME/.vimrc, and
      this is true for Linux and Mac systems, but in Windows it's located in
      $HOME/_vimrc.

2. Configuration Options                  *learnvim-configuration-options*

Vim is highly configurable through what are referred to as |options|.  Read
through the beginning of that help file to understand how to show and set
options.  As a quick overview:

- :set option=value	Sets "option" to "value"
- :set option?		Shows the current value of "option"
- :echo &option		An alternate way to show the value of "option"

E.g. To check the current value of 'shiftwidth' and then change it to 4:
>
	:set shiftwidth?
	:set shiftwidth=4
<
To search for options in Vim, always remember to use a single quote ( ' )
character at the start of the option name to make sure your search doesn't
clash with other entries in the help system. E.g.   :help 'exp   will find the
'expandtab' option, but   :help exp   will find the |expression| evaluation
entry.  The use of help prefixes like ( ' ) is explained in |help-context|

Knowing Where a Setting Was Last Set~

Use the |:verbose| command to show where a setting was last set from. This is
very useful for tracking down the source of unexpected option values.
>
  :verbose set sw?
<

3. GUI Option Browser                            *learnvim-option-browser*

Use the |:options| command to show an interactive window of all Vim's settings
including their current values and a brief description, grouped by function.

Recipe: Using the Options Browser to search for and change a Vim setting ~
------------------------------------------------------------------------------
Problem: ~

You want to change the behaviour of something in Vim (like the tab & indent
settings, or how the Toolbar is displayed in the GUI), but you don't know the
option name and searching the help system doesn't appeal to you.

Solution: ~

For tabs and indents:
>
	:options
<
Scroll down the Table of Contents and press Enter on the '15 tabs and
indenting' line.  This will jump you to the set of options controlling how Vim
manages indentation.

Likewise, for the GUI Toolbar problem:
>
	:options
<
Scroll down or search for GUI (/GUI) and press Enter on the '10 GUI' line.

Comments: ~

Changing a value on any of the 'set' lines and pressing Enter will update your
current settings.  Add the 'set' line to your ~/.vimrc file (see
|learnvim-vimrc| below) to make the change permanent.  Actually, you should
clean up the set line by removing the initial, unset version of the option
before adding it to your ~/.vimrc file.

Example: ~

Say you're browsing the options and decide that you want to enable 'smarttab'.
You see the line:
>
	set nosta	sta
<
If you press Enter on that line then you will enable smarttabs.  Copying that
line to your ~/.vimrc file will work, but it's unnecessary and unsightly to
have the option turned off and then on like that.  So, when adding this to your
~/.vimrc, change the line like this:
>
	set sta
<
Actually, it is a good practice to use the full name of an option so that when
you come back to your ~/.vimrc file in six months' time you will be able to
understand what the setting means.  So, change that line to:
>
	set smarttab
------------------------------------------------------------------------------

==============================================================================
MAKING SETTINGS PERMANENT          *lv_B_IV* *learnvim-permanent-settings*

1. Your Own vimrc File                                    *learnvim-vimrc*

Put this in your personal vimrc file (|learnvim-personal-vimrc-filename|):
>
	set nocompatible               " NEVER change this! Use Vim mode, not vi mode.
	filetype plugin indent on      " Enable automatic settings based on file type
	syntax on                      " Enable colour syntax highlighting

	""""""""""
	" Options
	""""""""""
	" Use :help 'option (including the ' character) to learn more about each one.
	"
	" Buffer (File) Options:
	set hidden                     " Edit multiple unsaved files at the same time
	set confirm                    " Prompt to save unsaved changes when exiting
				       " Keep various histories between edits
	set viminfo='1000,f1,<500,:100,/100,h

	" Search Options:
	set hlsearch                   " Highlight searches. See below for more.
	set ignorecase                 " Do case insensitive matching...
	set smartcase                  " ...except when using capital letters
	set incsearch                  " Incremental search

	" Insert (Edit) Options:
	set backspace=indent,eol,start " Better handling of backspace key
	set autoindent                 " Sane indenting when filetype not recognised
	set nostartofline              " Emulate typical editor navigation behaviour
	set nopaste                    " Start in normal (non-paste) mode
	set pastetoggle=<f11>          " Use <F11> to toggle paste modes

	" Status / Command Line Options:
	set wildmenu                   " Better commandline completion
	set wildmode=longest:full,full " Expand match on first Tab complete
	set showcmd                    " Show (partial) command in status line.
	set laststatus=2               " Always show a status line
	set cmdheight=2                " Prevent "Press Enter" messages
				       " Show detailed information in status line
	set statusline=%f%m%r%h%w\ [%n:%{&ff}/%Y]%=[0x\%04.4B][%03v][%p%%\ line\ %l\ of\ %L]

	" Interface Options:
	set number                     " Display line numbers at left of screen
	set visualbell                 " Flash the screen instead of beeping on errors
	set t_vb=                      " And then disable even the flashing
	set mouse=a                    " Enable mouse usage (all modes) in terminals
	" Quickly time out on keycodes, but never time out on mappings
	set notimeout ttimeout ttimeoutlen=200

	" Indentation Options:
	set tabstop=8                  " NEVER change this!
	" Change the '2' value below to your preferred indentation level
	set shiftwidth=2               " Number of spaces for
	set softtabstop=2              " ...each indent level

	"""""""
	" Maps
	"""""""
	"
	" F1 to be a context sensitive keyword-under-cursor lookup
	nnoremap <F1> :help <C-R><C-W><CR>

	" Reformat current paragraph
	nnoremap Q gqip

	" Move cursor between visual lines on screen
	nnoremap <Up> gk
	nnoremap <Down> gj

	" Map Y to act like D and C, i.e. to yank until EOL, rather than act as yy,
	" which is the default
	map Y y$

	" Map <C-L> (redraw screen) to also turn off search highlighting until the
	" next search
	nnoremap <C-L> :nohl<CR><C-L>

	" Toggle search highlighting
	nnoremap <C-Bslash>       :set hls!<bar>:set hls?<CR>
	inoremap <C-Bslash>       <Esc>:set hls!<bar>:set hls?<CR>a

	""""""""""""""""
	" Auto commands
	""""""""""""""""
	"
	if has("autocmd")
	  augroup filetype
	    " Remove ALL autocommands for the current group.
	    autocmd!

	    " Jump to last-known-position when editing files
	    " Note: The | character is used in Vim as a command separator (like ; in C)
	    autocmd BufReadPost * if line("'\"") > 1 && line("'\"") <= line("$") | exe "normal! g`\"" | endif
	  augroup END
	endif
<
2. Additional Options to Investigate   *learnvim-vimrc-additional-options*

Read about the following options and consider adding them to your $HOME/.vimrc
too:

- 'backup'	To keep backups of your files.  There are several other related
		options with "backup" in their name.

- 'expandtab'	Use spaces instead when inserting a <Tab>. The choice of
		whether to use <Tab> characters or <space> characters to denote
		indentation is a personal one and can lead to heated dispute
		among programmers.  http://www.jwz.org/doc/tabs-vs-spaces.html

- 'colorscheme'	See |:syn-default-override|.  There are many more themes to
		choose from at htp://www.vim.org/scripts/

- 'spell' and	Enable spell checking in your preferred language.
  'spelllang'

- 'undofile'	Enable |persistent-undo|, allowing you to undo across Vim
		sessions.

- 'whichwrap'	Control which keys allow you to wrap around start and end of
		lines.

3. Your Own gvimrc File                                  *learnvim-gvimrc*

Put this in your $HOME/.gvimrc :
>
	set t_vb=                      " Disable screen flash on error
<
Note: Some options, like t_vb, need to be set in both $HOME/.vimrc and
$HOME/.gvimrc because they are reset when the GUI is started.

4. Additional Options to Investigate  *learnvim-gvimrc-additional-options*

- 'colorscheme'	If you want to have the GUI use a different scheme to terminal
		Vim.

- 'guifont'	Font (or list of fonts to try) to use in the GUI.  See the tip
		below about setting your guifont.

- 'guioptions'	Control which components and options of the GUI to use.


##############################################################################
INTERMEDIATE TOPICS                         *lv_I* *learnvim-Intermediate*

|learnvim-motion|                 Motion
|learnvim-repeat|                 Repeating Changes
|learnvim-completion|             Completion
|learnvim-marks|                  Marks And Mark Motions
|learnvim-visual-mode|            Visual Mode
|learnvim-buffers-args|           Buffers And Args
|learnvim-windows|                Windows
|learnvim-tabs|                   Tabs
|learnvim-registers|              Registers
|learnvim-ranges|                 Ranges
|learnvim-searching-replacing|    Searching And Replacing
|learnvim-large-edits|            Large Edits
|learnvim-format-indent|          Formatting And Indenting
|learnvim-tags|                   Tags
|learnvim-quickfix|               Quickfix
|learnvim-folding|                Folding
|learnvim-diffing|                Diffing
|learnvim-spell-check|            Spell Check
|learnvim-maps-abbreviations|     Maps And Abbreviations

You don't need to worry about competencies anymore -- you have your Vim
Driver's license, provisional plates.  You're allowed to drive solo, but
you're still on zero tolerance conditions and cautioned against excessive
night driving until you develop the necessary reflexes to handle yourself in
challenging environments.  You can get yourself around town, but you lack the
refined strategies of more accomplished drivers.  In the world of Vim, you're
ready to learn about expert |navigation|.

==============================================================================
MOTION                                                   *learnvim-motion*

If you haven't read all of |motion.txt| yet, now would be a good time.  I
know, though, right? It's like 1300 lines long! That'd take hours to read, let
alone absorb...  Well, I could say the journey of a thousand miles begins with
the first step, or the secret to eating an elephant is to do so bite at a
time, but I won't.  Instead, I offer this path through the motion morass:

Operators & Text Objects ~

One of Vim's most powerful features is its ability to perform an action over a
specific portion of text.  In Vim speak, the action is called an |operator|
and the portion of text is called a |text-object|.  Get to know these
operators first:

|c|	(change) To delete a portion of text and enter insert mode immediately.
|d|	(delete) To delete a portion of text.
|y|	(yank) To copy a portion of text to Vim's internal clipboard (unnamed
	register,  |quotequote|)

And start using them with this motion:

|w|	(word) To operate from the current word under the cursor.  See
	|word-motions| for the others in this category.

EXERCISES:~

Copy the following line to your practice file (|setting-up-a-practice-file|):
>
  Angels and ministers of grace defend us.
<
TARGET:~
>
  Angels and Vimmers of grace defend us.
<
Start with your cursor anywhere on that line in your practice buffer.
Type the following commands:

Commands:             Description: ~

1. 0                  - move to the first character on the line |0|
2. 3w                 - move forward three words (to "ministers")
3. cwVimmers<Esc>     - change the word "ministers" to "Vimmers"

* Continue practicing with the change-word command on other words within the
  sentence.
* Experiment with the delete-word (dw) command on various words. Use |p| to
  paste a deleted word after the cursor.
* Experiment with the yank-word (yw) command. Again, |p| to paste what you've
  yanked (copied).
* Experiment with counts, like 3dw or 2ywP.
* Copy the original line again and try the following commands:
>
  0fm3dw^Pdt Ep^~
<
  TARGET:~
>
  Ministers of grace and Angels defend us.
<
The breakdown of this command into its constituent pieces is:
>
  0
  fm
  3dw
  ^
  P
  dt<space>
  E
  p
  ^
  ~
<
Where the new commands are: |0| |f| |^| |P| |t| |E| |~|

NOTE: A seasoned Vim Golfer ( http://www.vimgolf.com/ ) will be able to make
this text change with even less strokes. It is better though that you learn the
regular commands first. The instructions in
|learnvim-setting-up-a-practice-file| suggest https://github.com/dahu/VimGym as
an alternative to vimgolf. The rationale for that is given in
http://of-vim-and-vigor.blogspot.com/2014/04/seconds-count-not-keystrokes.html

QUIZ~

1. What is an |operator|? What is a |motion|?
     i. What do operators do?
    ii. What do motions do?
   iii. Which comes first, the operator or the motion?
    iv. What extra modifier can operators and motions take? How do they
        compose?
     v. How would you change the text on a line from the cursor to the end of
        line?
    vi. Why is it efficient to edit using the operator+motion paradigm?

2. What is a |text-object|?
     i. What is the semantic difference between "a" and "i" in text-object
        names?
    ii. How would you search for a text-object for paragraphs?
   iii. Why are text-objects a powerful way to edit text?

3. Can you explain the order of commands for the edit above? Why did we move
   the "ministers of grace" chunk before moving the "Angels" chunk?

4. Can you find a smaller set of commands to effect this edit?


==============================================================================
REPEATING CHANGES                                        *learnvim-repeat*

We often need to repeat a change, insert or command many times. Doing this
manually is boring, frustrating and prone to mistakes.

* Use |.| to repeat the prior normal mode change command.

* Use |;| to repeat the prior |f| |F| |t| |T| command in the same direction.

* Use |,| to repeat the prior |f| |F| |t| |T| command in the opposite direction.

EXERCISE: ~

Copy the following line to your practice file (|setting-up-a-practice-file|):
>
  It's type, write, might, flight fun, fun, fun, fun, fun!
<
TARGET:~
>
  It's typey, writey, mighty, flighty fun, fun, fun, fun, fun!
<

Start with your cursor anywhere on that line in your practice buffer.
Type the following commands:

Commands:             Description: ~

1. ^         - move to the first non-whitespace character on the line |^|
2. fe        - find the next 'e' character                            |f|
3. ay<esc>   - append a 'y' character                                 |a|
4. ;         - repeat the prior find in the same direction            |;|
5. .         - repeat the prior change (insert 'y')                   |.|
6. ft        - find the next 't' character
7. .         - repeat the prior change (insert 'y')
8. ;.        - repeat the prior find and change commands


* Use <c-r>. in insert mode to repeat the prior insert. See |i_ctrl-r| for
  others.

* Use @: in normal mode to repeat the last |ex-cmd|

* Use |n| and |N| to repeat the prior search in the same/opposite direction
  respectively.

* Use @@ in normal mode to repeat the prior macro. See |learnvim-Macros| for an
  introduction to macros.

QUIZ~

1. How do you repeat the prior normal mode text change?

2. How do you repeat the prior insert? There are two answers.

3. How do you repeat the prior ex command?

4. How do you repeat the prior macro?

5. How do you repeat the prior find command?

6. How do you repeat the prior search command?

7. What is the difference between a find and a search?


==============================================================================
COMPLETION                                           *learnvim-completion*

TODO

==============================================================================
MARKS AND MARK MOTIONS                                    *learnvim-marks*

Vim has marks (bookmarks) -- places you can quickly return to later.  See
|mark-motions| for a good coverage of the many available builtin marks and how
to set your own user marks.

Pay special attention to the difference between lower-case marks {a-z} versus
uppercase marks {A-Z}.

The two symbol marks, ' (quote) and ` (backquote) are very frequently used by
accomplished vimmers.  Experiment with double-tapping these keys to see the
difference in their behaviour.

Law of the Instrument ~

"It is tempting, if the only tool you have is a hammer, to treat everything as
if it were a nail."                                   -- Abraham Maslow (1966)

Marks are great, but don't fall into the trap of over using your shiny new
toys for every problem at hand.  Take for example the operation of deleting
everything from the current cursor to a word you can see a few lines below in
your document.  Having just learned about marks, it might seem like a good idea
to do this:
>
    ma/foo<CR>d`a
<
But there's a much better way to do that:
>
    d/foo<CR>
<
You're going to jump to your practice file and try that out now, aren't you? ;)
See |setting-up-a-practice-file| if you haven't done so already.

Becoming an Expert Navigator~

What else is there to learn from |motion.txt|?

* |object-motions|	Larger objects, like sentences, paragraphs and
			sections.
* |jump-motions|	Moving up and down the jump list as well as the
			related |change-list-jumps|.

There are many other motions in |motion.txt| than mentioned here.  It really
would pay to eventually work your way through that text.

QUIZ~

1.  What is a mark? Why are they useful?

2.  What is the difference between ' and ` with respect to marks?

3.  What are the '[,'] and '<,'> marks?

4.  What is the difference between lower-case and upper-case marks?

5.  Can you think of some good uses for upper-case marks?

6.  How do you return to the position before the latest jump?

7.  What is the difference between   (   and   `(   ?

8.  Which commands are considered jump-motions? What does that mean?

9.  How do you move up and down the jump-list?

10. How do you move up and down the change-list?


==============================================================================
VISUAL MODE                                         *learnvim-visual-mode*

TODO

==============================================================================
BUFFERS AND ARGS                                   *learnvim-buffers-args*

Read |windows-intro| for an overview of buffers, windows and tab-pages in Vim.

A visual introduction to Vim's Buffers, Windows and Tabs:
http://i.imgur.com/3ULsNaX.jpg

An excellent explanation of buffers, windows and tabs in Vim:
http://stackoverflow.com/questions/26708822/why-do-vim-experts-prefer-buffers-over-tabs/26710166#26710166

Editing Files~

The reference for this section is |editing.txt|.

Commands of interest:
|:edit|   |:enew|    |:find|
|:write|  |:saveas|  |:quit|
|CTRL-^|  |gf|

Read:
|07.1| - Editing multiple files
|07.2| - Listing files
|07.3| - Jumping between files

NOTE: The author does not recommend the use of the |:next| and |:previous|
commands for navigating between files. Use the method shown in
|learnvim-buffer-list| Instead.


Working Directory and Paths~

Points of interest:
'path'  |file-searching|
|:cd|     |:lcd|     |:pwd|

The default unix 'path' is ".,/usr/include,," which is not terribly useful to
many, especially if you're not a C programmer. Instead, use this as your default
path:
>
  set path=.,**
<
And override it with more specific details on a per-project basis.

The |:find| command searches your 'path', however it is still limited (like
the |:edit| command) to opening only one file at a time. Use the |:args| command
to open multiple files simultaneously.

Browsing Files~

The |netrw| plugin comes standard with Vim and is useful as a file browser. It
can also be used to edit remote files through SSH, HTTP, FTP and other protocols.

Fuzzy File Finders~

There are several external plugins available for quickly finding and editing
files in your project. Two recommended ones are:

* https://github.com/kien/ctrlp.vim
* https://github.com/dahu/VimFindsMe                     |learnvim-vim-finds-me|

                                                          *learnvim-buffer-list*
The Buffer List~

Use the |:ls| command to show the list of buffers (files) that you're currently
editing.

If you have the 'hidden' option enabled, you can have multiple modified
buffers open concurrently.

Use the |:b| command to switch between buffers. You can use a buffer number, or
the partial name of a buffer as the argument to the :b command. Use |c_ctrl-d|
to show a list of possible buffer names.

These three things (two commands and the 'hidden' option) combine together to
provide a very effective buffer workflow within Vim.  In fact, comics have been
created about this powerful combination: Entry #4 - Flying is faster than
cycling ( http://of-vim-and-vigor.blogspot.com/p/vim-vigor-comic.html )

The map from the Flying cartoon:
>
  nnoremap <leader>l :ls<cr>:b<space>
<

Operating On All Buffers~

To perform a series of commands on all open buffers, use |:bufdo|.

Example: To search for `something` in all buffers:
>
  :call setqflist([])
  :bufdo grepadd! something %
<

Buffer List Problems~

There are two problems with the buffer list:
1. It isn't able to be reordered,
2. It isn't able to be renumbered.

Ordering~

We sometimes wish we could re-order the buffers so that we can group related
ones together: all text files together and all source files before them, say.
The buffer number is fixed at the time the buffer is created and can never be
changed throughout the lifetime of the Vim session - it'd be much nicer to be
able to re-order these as and when we see fit. We can't do this with the buffer
list.

Numbering~

When buffers are removed from the buffer list, they leave holes in the
numbering of listed buffers. Many plugins use temporary buffers (some a LOT)
which can leave huge holes in the numbering of buffers. If you like to jump to
buffers by remembering their buffer number, it can be a bit unsettling to know
that you need to jump to buffers 1, 2, 6 and 11 - it'd be much nicer to (even
if only temporarily) renumber those buffers to: 1, 2, 3, and 4 respectively. We
can't do this with the buffer list.

While the buffer list is and always will be useful, to solve these two
problems, we have the Argument List.

Argument List~

Read |arglist| for details not covered here.

Each window can have a separate argument list. You're free to set and reset the
argument list as and when you see fit.

Useful Arglist Commands~

To set the current window's argument list to the .c files in the src/
directory:
>
  :args src/*.c
<

To do that recursively within all of the subdirectories:
>
  :args src/**/*.c
<

To see your current argument list:
>
  :args
<

To add the .h files to the argument list:
>
  :argadd src/**/*.h
<

To jump to an argument by partial buffer (file) name match:
>
  :argedit {partial name}
<

To jump to an argument by (1-based) index:
>
  :argument {index}
<

To perform an operation on all of your arguments in a single command:
>
  :argdo %s/Long live \zsthe buffer list\ze!/argument lists/ge | update
<

If you |:quit| before visiting all of the files in your argument list, Vim will
ask you to confirm. To prevent that, use |:qa| instead.

Local vs Global~

If you open a new window, it will inherit the parent window's argument list.
There are functions which will attach to the global argument list or create a
new local argument list for the current window.
See |:argglobal| and |:arglocal|

Plugin Support via VFM~

These commands are useful but a little frustrating to use in their native form.
The VimFindsMe (|learnvim-vim-finds-me|) plugin has support for the argument
list, removing these frustrations.

Other Buffer Commands~

The list of commands from |:badd| onwards in the |windows.txt| help file show
the other buffer commands. Another excellent normal-mode command for navigating
buffers is |ctrl-6| to switch between the |current-file| and the
|alternate-file|.


QUIZ~

1. What is a buffer? What is the buffer list?

2. What are the two big disadvantages of the buffer list?

3. What is the argument list?

4. How do you show the argument list?

5. How do you set the argument list?

6. How do you add a file to the argument list?

7. How do you jump to a file in the argument list?
    i. by name?
   ii. by number?

8. How does the VFM plugin make using the argument list easier?


==============================================================================
WINDOWS                                                 *learnvim-windows*

See the user manual section |usr_08.txt| for an introduction to using windows in
Vim. The reference manual for this section is |windows.txt|.

A visual introduction to Vim's Buffers, Windows and Tabs:
http://i.imgur.com/3ULsNaX.jpg

An excellent explanation of buffers, windows and tabs in Vim:
http://stackoverflow.com/questions/26708822/why-do-vim-experts-prefer-buffers-over-tabs/26710166#26710166

QUIZ~

1. What command should you use to prevent accidentally exiting Vim when closing
   a window?

2. The normal mode command |CTRL-W_f| edits the file under the cursor in a new
   window.
    i. What CTRL-W command is equivalent to the |:only| command?
   ii. Do all of Vim's Window ex commands have a counterpart through CTRL-W?

3. What single command is equivalent to:
>
    :split | enew
<

4. |:vsplit| and |:vnew| are explicit commands for working with vertical
   windows. What can you use if there is no explicit `:v...` command for a
   window operation that you'd like to do vertically?

5. What's the difference between |CTRL-W_h| and |CTRL-W_H|?


Operating on Multiple Windows~

You would have found |:qall| and |:wall| in |08.6| but there was no mention
there about performing an action other than closing or saving on all windows. To
do this, we need to use the |:windo| command.

'colorcolumn', 'cursorcolumn', 'cursorline', 'list', 'number' and
those controlling |folding| are all examples of useful options to set for all
windows simultaneously.

Example: To reload all of the buffers in the currently visable windows:
>
  :windo e
<

Compare |:windo| with |:bufdo|. How does the following command differ from the
:windo one above?
>
  :bufdo e
<


Statusline~

Most applications have a statusline at the bottom of windows containing various
pieces of useful information about current state. Vim provides this in two ways:

1. The more simplistic 'ruler', and
2. The more featureful 'statusline'.

Scrooloose has a colourful introduction to Vim's statusline:
http://got-ravings.blogspot.sg/2008/08/vim-pr0n-making-statuslines-that-own.html

A suggested statusline is:
>
  set statusline=%f%m%r%h%w\ [%n:%{&ff}/%Y]\%{&paste?'\ paste':''}%=[0x\%04.4B][%03v][%p%%\ line\ %l\ of\ %L]
<
See 'statusline' for details about the chosen options.

NOTE: The 'laststatus' option determins which windows show a statusline.
      To see a statusline in all windows:
>
        set laststatus=2
<


==============================================================================
TABS                                                       *learnvim-tabs*

See the user manual section |08.9| for an introduction to using tabs in
Vim. The reference manual for this section is |tabpage.txt|.

A visual introduction to Vim's Buffers, Windows and Tabs:
http://i.imgur.com/3ULsNaX.jpg

An excellent explanation of buffers, windows and tabs in Vim:
http://stackoverflow.com/questions/26708822/why-do-vim-experts-prefer-buffers-over-tabs/26710166#26710166

NOTE: Trying to force one buffer to stay in one tab page is highly unrecommended
because it violates Vim's natural workflow. See tabpages instead as separate
workspaces. Open a new tab page when you need to perform a task that will
interfere with the window layout or buffer positions you're currently working
with. Some typical examples where a new tab page is suggested:

1. Opening a different help file to the one you're currently browsing.
2. Temporarily working on a different project.
3. Creating a pristine environment for a diff.

QUIZ~

1. Why is "tabpage" such a bad name for this feature in Vim? What are some
   better names?

2. If |:bufdo| operates on all buffers and |:windo| operates on all windows,
   what command do you think operates on all tab-pages?

3. What is the normal mode command similar to |CTRL-W_f| for opening the file
   under the cursor in a new tab page?


==============================================================================
REGISTERS                                             *learnvim-registers*

Registers are covered in sections |04.6| and |09.3| in the user manual.

Most applications use the "clipboard" to handle cut, copy and paste operations.
In Vim, the location for such operations is not called the clipboard, but rather
a "register". Vim has 48 such |registers| (and counting! -- A recently submitted
patch proposes adding a new register to Vim that will hold the last |f||F||t|T|
search).

The registers are accessed through the notation `"<register>` -- that is, in
normal mode, press the double-quote key followed by the desired single-letter
register identifier. For example, to delete the current word (|diw|) into
register 'a', use: >
  "adiw
<

CLIPBOARD~

The |quotestar| ("*) register corresponds to the X selection buffer (pasted with
<MiddleClick>), and the |quoteplus| ("+) register corresponds to the system
clipboard (pasted with <C-v> or Edit->Paste). On windows, both registers are for
the system clipboard. To use the clipboard in terminal vim, vim must be built
with |+xterm_clipboard|.

To copy the whole buffer to the system clipboard, use: >
  :%y+
<

Read |clipboard| for further details.

OPTIONS~

The following options influence register use in Vim:
'clipboard'
'paste'
'pastetoggle'
'mouse'

With `:set mouse=a` you can middle-click to paste without worrying about setting
paste / nopaste / pastetoggle.

APPENDING~

Using the lower-case form of the 26 named registers (a-z) will overwrite the
register with the new content specified. Using the upper-case form (A-Z) will
append instead. A common use for this is to combine it with the |:global|
command (discussed later in |learnvim-large-edits|) as shown here: >
  qaq:g/^\C[A-Z]\{2,}/y A
<
Will collect into register "a" all lines starting with two or more upper-case
letters. This could be used in a Vim help file, for example, to quickly create a
TOC from existing helpfile content.

For more information on the commands used there, see |q| and |:yank|.
NOTE: The idiom "qaq" is a quick way to clear register "a". Likewise, "qqq"
clears register "q".

SCRIPTING~

In VimScript, access to the registers is via the `@` symbol instead of the `"`
symbol because `"` is the comment character. You can assign to registers with
the |:let-@| command. For example, to explicitly set the current search term,
use: >
  :let @/ = 'example'
<
You can assign to all of the named variables as well as the clipboard variables.
If you have collected lines matching a pattern into register "a" and would like
to paste that into an external application through the system clipboard, use: >
  :let @+ = @a
<

An infographic on Vim's registers:
http://of-vim-and-vigor.blogspot.sg/2012/01/rap-on-vims-registers.html


==============================================================================
RANGES                                                   *learnvim-ranges*

Section |10.3| in the user manual covers |cmdline-ranges|.

A good introduction to ranges: http://vim.wikia.com/wiki/Ranges

An infographic: http://of-vim-and-vigor.blogspot.sg/2012/02/vim-ranger.html


==============================================================================
SEARCHING AND REPLACING                     *learnvim-searching-replacing*

Vim uses regular expressions (regex) for searching and replacing. And it uses
its own regex flavour -- NOT PCRE. The technical details are covered in
|pattern.txt|.

                                                          *learnvim-magic*
Magic~

Regular expressions are designed for complex searches within text, requiring the
use of several special characters to specify complex matches. These special
characters do not represent their literal value but are considered to have
"magical" meaning within the regex. For example, the `.` character does not
match a '.' (period) but rather matches any single character (except for a
newline). Vim has several magic modes but the beginner is strongly urged to use
Vim's regular magic setting and experiment with the other modes after they have
become comfortable and competent with the default.

CAUTION:

* Do not modify the 'magic' setting; leave it as the default.
* Do not use the 'gdefault' setting.
* Start by learning standard |/magic| mode in Vim's regular expressions.

                                                      *learnvim-searching*
Searching~

To initiate a forward search in Vim, use |/|. Use |?| to search backwards from
the cursor.


Read |03.9| now to learn about three special characters (atoms) in regular
expressions.

Quiz~

1. What were the three special atoms introduced in |03.9|?

2. How would you search for a literal '.' character?

3. What's the difference between |/| and |?|?

Read |usr_27.txt| now for a more thorough coverage of searching with regex in
Vim.

Jump to your practice file now and try various search patterns. Try searching
for special characters too -- remember how to represent them in a search
pattern?
See |setting-up-a-practice-file| if you haven't done so already.

Quiz~

1. Show two different ways to handle case matching (ignoring / honouring) with
   Vim regexes.

2. What is the option for allowing pattern searches to wrap around the
   top/bottom of the buffer? When wouldn't you want this option enabled?

3. How do you jump to the end of a pattern match?

4. How do you simply repeat the prior search pattern? Show two ways. Consider
   forward and backward solutions.

5. '\n' and '\r' are not the same thing!
    i. What's the difference between '\n' and '\r' in |/character-classes|?
   ii. What's the story with '\n' and '\r' in |sub-replace-special|?
  iii. Which one would you use to replace something with a newline?
   iv. Which one would you use to match a newline?
    v. Which one of the following splits colon separated pieces on the current
       line into multiple lines.
>
         :s/:/\n/g
         :s/:/\r/g
<
   vi. Which one of the following joins multiple lines together?
>
         :1,10 s/\n/ /
         :1,10 s/\r/ /
<
  vii. Why is the `/g` flag useless here?
>
         :1,10 s/\n/ /g
<

Regex Tutor~

https://github.com/dahu/VimRegexTutor will gently guide you through learning
Vim's regular expression language more completely.

                                                      *learnvim-replacing*
Replacing~

In Vim, "replacing" is performed with the |:substitute| command (often
abbreviated to just |:s|):
>
  :s/from/to
<
Where `from` is a regular expression as covered in |learnvim-searching|.

Jump to your practice file now and try a few |:s| commands.

HINT: By default, the |:s| command acts on the current line only. You should
practice using some ranges as covered earlier in |learnvim-ranges|.

See |setting-up-a-practice-file| if you haven't done so already.


Read |10.2| now to learn about simple search and replace in Vim.

Quiz~

1. We covered |learnvim-ranges| earlier.
   i. What is a range?
  ii. What range does '%' represent?
 iii. How would I specify a range that covered the current cursor through to the
      end of the buffer?

2. All lines vs all occurrences on a line.
   i. How do I perform a substitution on all lines in the file?
  ii. How do I perform a substitution on all occurrences of the current line
      only?
 iii. How do I perform a substitution on all occurrences of all lines?

3. How cool is the |:s_c| flag?

Complex Replacements~

Read |sub-replace-special| and then try various special replacements in your
practice file.

Quiz~

1. How do you use the whole matched text in the replacement?

2. How do you specify pieces to capture in the `from` part of |:substitute|?

3. How do you refer to captured pieces in the `to` part?

4. How would you swap every pair of 'word_1:word_2' in the file so that it
   resulted in 'word_2:word_1'.

5. How would you change the case of all words in a line to Title Case?

Read |sub-replace-expression| and then try to use the `\=` replacement in your
practice file.

Quiz~

1. How would you insert the line number at the start of every line in
   the buffer?

2. How would you number (starting from 1) a range of lines somewhere in a file?


==============================================================================
LARGE EDITS                                         *learnvim-large-edits*

Section |10.4| in the user manual covers the |:global| command discussed here.

The |:substitute| command discussed in the prior section has the following
form: >
  :[range]s[ubstitute]/{from}/{to}/[flags]
<
where the default range is the current line only.

The |:global| command has the following form: >
  :[range]g[lobal]/{pattern}/{command}
<
where the default range is the whole buffer.

The |:global| command takes three things:
1. A range (defaulting to the whole buffer)
2. A pattern to match lines within the specified range.
3. A command to perform against every matched line.

The following two commands are identical: >
  :%s/foo/bar/g
  :g/foo/s//bar/g
<

However the |:global| version is more flexible. Consider: >
  :g!^\s*//!s!fahren/Fahren/g
<
Which corrects spelling mistakes in comments without disrupting code.

So, one feature of |:global| is that it turns single-line commands into ranged
commands, but that is its least useful attribute. The |:global| command actually
accepts a set of |:bar| separated commands, allowing multiple operations on each
match. Compare these two commands: >

  :% substitute /apples/bananas/g | substitute /cherries/oranges/g

  :global /apples\|cherries/ substitute /apples/bananas/g | substitute /cherries/oranges/g
<
The first command is probably not what the developer intended because
|:substitute| does not take a set of commands, so the second substitute uses its
default range, which is the current line. BUT BE CAREFUL: The current line is
not what you think it is. The current line will be wherever the prior command
leaves it. In the case given, it will be on the final line in the buffer that
had "apples". IF that line also contained "cherries" THEN the second substitute
would apply.

GREP -- The Default Command~

The default command for |:global| is |:print|, making the mnemonic:

  :g/re/p

Indeed, |:g| is very often used to quickly show lines from the current buffer
that match a pattern, like: >
  :g/^func
<

Any Command~

The |:global| command can be used to execute any text editing |ex-cmd| which
includes the |:normal| command for executing normal mode commands. This command
lets you execute macros within the |:global| command. Example: >

  :let @a = "0Wyiw:-pu\<CR>gcc"
  :g/^func/normal @a
<
Assuming you had a macro in register "a" that duplicated the second word on a
line into a comment line prior to it, then the global command shown will execute
that macro on all function definitions in the buffer.

NOTE: The `gcc` command there is from Tim Pope's Commentary plugin.
      See |learnvim-commentary|.

Deleting Blank Lines~
>
  :g/^$/d
  :g/^\s*$/d
<
|:delete|

Reversing Line Order~
>
  :g/^/m0
<
|:move|

Move Matches To End Of File~
>
  :g/^func/m$
<
|move|

Copy Matches To End Of File~
>
  :g/^func/t$
<
|:copy| |:t|

Collect Matches Into Register A~
>
  qaq:g/^func/y A
<
|q| |:yank|
NOTE: The idiom "qaq" is a quick way to clear register "a". Likewise, "qqq"
clears register "q".

Some more examples are shown at http://vim.wikia.com/wiki/Power_of_g

                                                            *learnvim-waz*
WAZ~

http://dahu.github.io/vim_waz_ere/

The Walter Alan Zintz Vim tutorial is a comprehensive exploration of the
|:substitute| and |:global| commands. It has quizzes too!


==============================================================================
FORMATTING AND INDENTING                          *learnvim-format-indent*

                                                     *learnvim-formatting*
FORMATTING~

Formatting is the process of modifying the layout of a block of text to make it
flow better. Adjusting a paragraph to have all lines wrapped at 'textwidth',
indenting lines within a list and automatically prepending the comment leader
are all examples of formatting.

Vim provides several methods of reformatting your text. The commands and options
are quickly covered here. Read more about this in:
|formatting|
|ins-textwidth|

Automatic~

Using the "a" value of 'formatoptions' will enable automatic formatting as you
type. This can cause unexpected and unwanted modifications to the layout of your
text and should only be used for non-code prose. Read |auto-format| for more
details.

Manual~

Text~

A common formatting action in word processors is to change the paragraph to:

|:left| aligned.
							       |:right| aligned.
				Or |:center|ed.
Programmers don't need this feature often, but it's nice to know Vim has it.

The |gq| command will reformat the selected lines using either an internal
algorithm, a script-defined expression (function) or an external tool.

The |gw| command uses an internal algorithm to reformat the selected lines and
puts the cursor back at the same position in the text afterwards.

For a more comprehensive coverage of using Vim as a text (prose) writing tool,
see http://www.drbunsen.org/writing-in-vim/

Asciidoc ( http://asciidoc.org/ or http://asciidoctor.org/ ) is an excellent
text processor. The https://github.com/dahu/vim-asciidoc plugin provides better
formatting support among other features.

Code~

A more typical formatting requirement for programmers is to reflow or beautify
code. If all you want to do is reindent your code nicely, see
|learnvim-indenting|. If you want to alter the way parentheses and braces are
used in expressions and blocks within your code, you will need either a plugin
that provides the necessary 'formatexpr' or an external tool used by the
'formatprg' option.

On linux, the `indent` tool is one such example. Another is the Artistic Style
tool: http://astyle.sourceforge.net/

The following options are related to formatting:
'textwidth'      The maximum width of the line as you're typing.
'formatoptions'  Control how automatic formatting is done.
'formatlistpat'  Support the "n" flag in 'formatoptions' for formatting lists.
'formatprg'      An external program to format lines operated on by the |gq|
                 command.
'formatexpr'     An expression (function) to format lines operated on by the
                 |gq| command.
'paste'          Formatting is temporarily disabled while "paste" is enabled.


                                                      *learnvim-indenting*
INDENTING~

Nicely indented code looks better, reads better and feels better. There are many
tools available for reindenting source code. The `indent` tool for C style
languages and the Artistic Style tool ( http://astyle.sourceforge.net/ ) are two
examples. Search for an indent tool for your preferred language.

Vim has built-in support for |C-indenting| and 'lisp'.

Vim also supports indenting many languages through 'filetype' plugins. Make sure
that the |:filetype| command says: >
  filetype detection:ON  plugin:ON  indent:ON
<
and if it doesn't, add the following line to your $MYVIMRC: >
  filetype plugin indent on
<

Use the |=| command to reindent lines within Vim. The |>>| and |<<| keys
increase and decrease indent respectively.

Some options related to indenting:
'equalprg'    An external program to reindent lines operated on by the |=|
              command.
'indentexpr'  An expression (function) to reindent lines operated on by the
              |=| command.
'cindent'     Force Vim's internal indenting to C style (uses 'cinkeys' and
              'cinoptions').
'cinkeys'     Keys that trigger C style indenting.
'cinoptions'  Options to control how C style code is indented.
'autoindent'  A recommended option that provides good default indenting and is
              used by many of the filetype-specific indent plugins.
'smartindent' DEPRECATED. SHOULD NO LONGER BE USED. Use 'autoindent' and
              "filetype plugin indent on" in your $MYVIMRC instead.
'expandtab'
'shiftwidth'  Default indent amount. Also affects |=|, |>>|, |<<|
'tabstop'     Changes the width of the TAB character. You should usually leave
              this as the industry default of 8 spaces.
'softtabstop' Affects the <TAB> and <BS> keys.

For the complete set of indenting options in Vim, see section 15 (Indenting and
Tabs) in |:options|.

A deeper introduction to indenting source code is covered in
http://vim.wikia.com/wiki/Indenting_source_code .


==============================================================================
TAGS                                                       *learnvim-tags*

Read |tags-and-searches| for extra detail not covered here.

Setting Up Your Tags Environment~

You will need:

1. A ctags generated tags file (Exuberant Ctags is the choice for most cases)

Typically this is as easy as:
>
  ctags -R
<

in the root of your project.

But if you need anything fancier than that, consult  `man ctags`  for guidance.

2. A correctly set 'tags' option

The Vim default of "./tags,tags" is probably sufficient for most projects but
you might want to include library tag files or a project-common tags file.

3. A correctly set 'path' option

A good default is:
>
  set path=.,**
<

Which searches the directory of the current file and all directories beneath
the current directory. See |file-searching| for more details.

These options can be set in your |$MYVIMRC| or, better, within filetype
specific plugins in "~/.vim/ftplugin/<the-filetype>.vim" or
"~/.vim/after/ftplugin/<the-filetype>.vim"

With the right setup, you will enjoy a happy tagging lifestyle.

The Tag Power Commands~

There are many tag commands available in Vim, but I'm going to share with you
only a select few -- a mere dozen or so. These are the most frequently reached
for. You can learn the other |tag| commands later.

|ctrl-]|	Jump to the definition of the keyword under the cursor. Tag
		jumps are recorded on a |tag-stack|.

|ctrl-t|	Jump to older tag in the stack.

|:ta|		Jump to newer tag in the stack.

:0ta or :0tn	Jump to previously jumped-to tag. Use this to return to the tag
		after wandering away from it. See |:tag| and |:tnext|

:ts /something	Show a list of tags matching the pattern something. See
		|:tselect|

TIP: Use |c_ctrl-d| to show a list of tag candidates. This works with partial
		matches too.

Do you remember how to read "c_ctrl-d"? Remember what that means in Vim-speak?
The "c_" part is the context, in this case the |command-line-mode|. "ctrl-d"
then is the key sequence CTRL + D. See |learnvim-take-apart-commands| for a
refresher.

|g]|		Show a list of tags matching the keyword under the cursor.

:tj /something   Show a list of tags matching the pattern something. If there
		is only one tag in the list, don't show the list but instead
		jump directly to it. See |:tjump|

|g_ctrl-]|	Show a list of tags matching the keyword under the cursor. If
		there is only one tag in the list, don't show the list but
		instead jump directly to it.

|[I|		Ordinarily, this just shows all lines in the file matching the
		keyword under the cursor — a shortcut to ":g/<c-r><c-w>"

TIP: This map (taken from the Vim help) lets you jump to one of the matches:
>
  :map <F4> [I:let nr = input("Which one: ")<Bar>exe "normal " . nr ."[\t"<CR>
  <

NOTE:	Use |ctrl-c| to cancel the choice if you don't want to jump to any of
	them.
	Use |``| to jump back to where you were if you accidentally pressed
	|<esc>| or |<enter>| instead.

While not strictly tagging commands, these little gems are semantically
related:

|gd| and |gD|	Jump to the local or global declaration of the keyword under
		the cursor, respectively.

|gf|		Jump to the file under the cursor.

While these commands may not be in your daily tag toolbox, you might call upon
them occasionally:

|:tags|		To see your current tag stack.

:ptj /something	To show the tag match in the |preview-window|. See |:ptjump|

|ctrl-w_ctrl-i|	and
|ctrl-w_ctrl-d|	To split the window, showing the associated first line or
		definition, respectively.

Using tags within Vim will speed up your editing by making it easy for you to
jump around your pile of files.

While there are heavy plugins that aim to make this prettier, the seasoned
vimmer knows that the extra bling doesn't add any real value to their edits.

Vanilla, when done right, is a classy choice.

QUIZ~

1. What is a tag? Why are they useful?

2. With respect to options like 'path' and 'tags' what do the following
   mean:
     i. .
    ii. *
   iii. **
    iv. an empty list element, expressed as two successive commas: ,,

3. How do you jump to the definition of the keyword under the cursor?

4. How do you jump back to older tags in the tag-stack?

5. How do you return to the last tag-jump position? Why is this useful?

6. Give two methods for expanding/completing tag names on the command-line.

7. How do you create a tags file? How do you keep it up to date?


==============================================================================
QUICKFIX                                               *learnvim-quickfix*

TODO


  - make
    :cn / :cp

==============================================================================
FOLDING                                                 *learnvim-folding*

TODO



==============================================================================
DIFFING                                                 *learnvim-diffing*

TODO



==============================================================================
SPELL CHECK                                         *learnvim-spell-check*

TODO

==============================================================================
MAPS AND ABBREVIATIONS                       *learnvim-maps-abbreviations*

TODO

	map \x :tabe <c-r>=expand('%:h')<CR>/


------------------------------------------------------------------------------

Recipe: Setting Up A Practice File   *learnvim-setting-up-a-practice-file*
------------------------------------------------------------------------------
New!:~
You can use the instructions below to set up a practice file, OR you can
install https://github.com/dahu/VimGym , a plugin designed for this exact
purpose.

The Manual Way:

Problem: ~
There's just too much to learn with Vim, and every time you learn a new thing,
it seems that the last cool tip you learned slips from memory.

Solution: ~
Have a practice file.  It's a good idea to have a file you can jump to whenever
you want to test a newly learned Vim feature or continue to practice
previously learned material so that it doesn't fade away.  Here's a short
recipe on how to do that:

1. Choose a location, say: ~/.vim/practice.txt (Create the directory if it
   doesn't exist - you'll be using it in a later tip.)
2. Edit that file in Vim and type the following command:
>
   mP
<
That sets the global P mark (|learnvim-marks|) on line one of your practice
file.  The great thing about global marks ([A-Z]) is that not only do they
remember the line on which they were set (like local marks [a-z]), but they
also remember the file in which they were set.  So, now at any time when you're
in Vim and you'd like to jump to your practice file, just type:
>
   'P
<
You can use |ctrl-o| to jump back to where you came from when you've finished
practising.

Note: You should practice that a few times now so you get the hang of it.
      Open your ~/.vimrc file and then type   'P   to jump to your practice
      file, and then |ctrl-o| to jump back.  You could use   'P   to jump
      forward again, but this is a great opportunity to mention |ctrl-i| which
      is used to jump forward in the |jumplist| The astute reader will have
      noticed the help file that entry is located in and hence the importance
      placed upon reading |motion.txt| within the intermediate section of
      LearnVim.

Tip: You might like to set another global mark, 'V, for your ~/.vimrc file.

Now, type |ctrl-o| enough times until you get back to wherever it was you
jumped here from. :)
------------------------------------------------------------------------------

##############################################################################
MODERATE TOPICS                                 *lv_M* *learnvim-Moderate*

MACROS                                          *lv_M_I* *learnvim-Macros*

1. Recording Macros                            *learnvim-recording-macros*

Macros are referred to as complex repeats in the Vim docs.  See |q| for the
mechanics of recording and then read on for playing back macros.

q{0-9a-zA-Z"} begins recording into the specified register.  All movements,
insertions, deletions, :ex commands, etc, are recorded until you press   q
again.  So, the command   qagUwWq   creates a macro that upper-cases the
current word (from the cursor forward) and then moves to the next WORD
(skipping whitespace and punctuation).  To run this macro on the next word, we
use the command   @a   and after that, to run it on another word we only need
to use   @@   (which repeats the last macro command, conveniently.)

If you've already got a partial command in a lettered register (a-z), you can
append more command to it by using the   q   command with the upper-case form
of the lettered register (A-Z)

There are quite a few other nifty tricks you can pull with macros, so I
implore you to read |:@|.

2. Recursive Macros                            *learnvim-recursive-macros*

Recursive macros are macros that call themselves.  Recursive macros are one way
to repeat a series of commands across multiple chunks of text all
automatically so you don't have to hit   @a   or even   @@   repeatedly to
execute the macro in all the places you need it to run.

Stop Condition~

If you don't provide an action within the body of your macro that causes an
error, the macro will run from the point of execution until the end of the
file.  This may be what you want; it may not.  To have it stop somewhere
specific, you'll have to ensure it errors at that point.  Using the    FfTt
commands are a common way to force a failed search.  If you use a pattern
search with the   /   command, you may need to use anchors to cause failures.

Clearing the Register Beforehand~

Because a recursive macro executes itself with the command   @a   (assuming
the macro is being recorded in register a), then at the point in time that the
macro is being created, the contents of register   a   before this recording
began will be inserted into the macro body when it sees   @a.  Unless you know
what you're doing, you probably want this to be empty.  Use   qaq   as a fast
way to empty register a.  By recording nothing into   a   , we effectively
empty it.  The subsequent   qa   in the command string   qaqqa   begins the
real recording.

Start in the Right Place~

To allow the recursive invocation of your macro to be actually useful, you have
to arrange for it to start in the right place.  This could be on the next line,
or at the next word, or next paragraph, or block, or...  etc.  The command j0
moves down a line and to the first column of the screen, ready for the
subsequent recursive invocation with the command   @a   and switching off
recording with   q   hence   j0@aq

You're done recording.  Use   @a   to run it.

QUIZ~

1.  What is a macro?

2.  When is a macro a good solution?

3.  What type of tasks are better done using plain ex commands instead of a
    macro?

4.  How do you record a macro?

5.  How do you finish recording a macro?

6.  How do you continue recording a macro after having stopped previously?

7.  How do you recursively call macros?

8.  What is a quick way to clear a macro register?

9.  How do you run a macro? What is a shortcut for running the previous macro
    again?

10. How are you using macros to improve your editing experience?

------------------------------------------------------------------------------

[UNFINISHED: The following list of topics are planned for this section]

:h key-notation

paste into document with "ap to edit commands
re-read into register with 0"ay$ when cursor is on the line of commands

:h expand()
:h filename-modifiers

:w !sudo tee %
:earlier + :later

reopen the file with different encodoings (when working with legacy files)
:e ++enc=cp1250

[/UNFINISHED]

##############################################################################
ADVANCED TOPICS                                 *lv_A* *learnvim-Advanced*

|lv_A_I|	Becomming a VimL Master~

------------------------------------------------------------------------------
                                           *lv_A_I* *learnvim-viml-master*

Becomming a VimL Master~

Everybody wants to be a grey-beard master vimmer, mind-wielding Vim like a
jedi, jumping around buffers like vimjas and scripting changes like wicked
vizzards. Walk this path to VimL mastery and be the victor of your Vim,
envy of your peers, idol to your fans.

Skill Progression: Trainee -> Novice -> Worker -> Professional -> Expert

Trainee~

* Read the following parts of |cmdline.txt|
** |cmdline-lines|
** |cmdline-ranges|
** |cmdline-special|

* Read the following parts of |options.txt|
** |set-option|
** The following specific options:
*** 'debug'
*** 'eventignore'
*** 'ignorecase'
*** 'magic'
*** 'maxfuncdepth'
*** 'runtimepath'
*** 'verbose'

* Read all of |pattern.txt|

* Read the following parts of |eval.txt|
** |variables|
** |expression-syntax| (skim)
** |internal-variables|
** |user-functions|
** |expression-commands|
** |eval-examples|

* Read the following sections of |usr_41.txt|
** |41.1|
** |41.2|
** |41.3|
** |41.4|
** |41.5|
** |41.6|
** |41.7|
** |41.8|

* Read |function-list| (Vim’s built-in VimL library)

* Read http://www.ibm.com/developerworks/linux/library/l-vim-script-1/index.html

* Read http://learnvimscriptthehardway.stevelosh.com/

Novice~

* Contribute bug fixes and small enhancements to existing plugins.

* Read |map.txt|

* Read 'timeout' option

* Read 'maxmapdepth' option

* Read |usr_40.txt|

* Read |autocmd.txt|

* Read |filetype.txt|

* Read |various.txt|

* In regard to |:normal|, read |motion.txt|

Worker~

* Read |eval.txt|

* Read |usr_41.txt| (again)

* Create three or more plugins under the supervision of a Professional or
  Expert

* Assist Novices

Professional~

* Actively support five or more peer-reviewed, fully |usr_41| compliant plugins

* Thoroughly document all supported plugins

* Supervise Workers

* Assist in the development of reference & resource materials

* Participate in discussions about best practice for VimL development

Expert~

* Create new tools and libraries for VimL development

* Create new/interesting/engaging/fun reference material or tutorials for an
  aspect of Vim/VimL

* Mentor, guide and train other VimLers

* Maintain a regular presence on Stack Overflow, the vim-dev mailing lists,
  #vim or #viml as an authority and guide on advanced Vim and VimL topics

------------------------------------------------------------------------------

[UNFINISHED: The following list of topics are planned for this section]

custom commands
vim scripting
variable scope (g: s: a:, etc)
writing plugins
:h feature-list - know if we're running in vim or gvim  --  if has("gui_running")

[/UNFINISHED]

##############################################################################
PLUGINS                                                 *learnvim-Plugins*

1. Plugin Management                          *learnvim-Plugin-Management*

Vim is awesome.  It has so much goodness baked right into it, it could very
well meet all your editing needs, right out of the box.  What it -also- has is
an awesome plugin system for extending every possible aspect of Vim you would
want.  http://www.vim.org/scripts is the canonical source of Vim plugins.

https://github.com/vim-scripts is a mirror of the canonical list. Many plugin
developers also share through their own github accounts.

2. Recommended Plugins                      *learnvim-Recommended-Plugins*

* Matchit   |learnvim-matchit|
* Pathogen  |learnvim-pathogen|
* Surround  |learnvim-surround|

Matchit                                                 *learnvim-matchit*

The Matchit plugin provides extended |%| matching in Vim.

DOWNLOAD~

Matchit comes bundled with Vim, so there is nothing to download.  All you need
to do is enable it as described below.

INSTALL~
Put the following line in your ~/.vimrc file:
>
  runtime macros/matchit.vim
<


Pathogen                                               *learnvim-pathogen*

Created by the venerable, tpope, this plugin is a light-weight plugin manager
for Vim.  It allows you to install, test, upgrade and uninstall plugins much
more easily than the default Vim approach.

DOWNLOAD ~
>
  http://www.vim.org/scripts/script.php?script_id=2332
<
Or get it from github at:
>
  https://github.com/tpope/vim-pathogen
<

INSTALL ~

Install instructions are available from the same places above for downloading
this plugin.


Surround                                               *learnvim-surround*

Surround is another tpope creation used for adding, changing or deleting the
text surrounding a text-object.  Typical surround text includes quotes,
brackets and tags.

DOWNLOAD ~
>
  http://www.vim.org/scripts/script.php?script_id=1697
<
Or get it from github at:
>
  https://github.com/tpope/vim-surround
<

INSTALL ~

Install instructions are available from the same places above for downloading
this plugin.


VimFindsMe                                         *learnvim-vim-finds-me*

The light-weight file finder, VimFindsMe ( https://github.com/dahu/VimFindsMe )
now supports the argument list. By default, the <leader>ga map will open the
current argument list into a scratch buffer (See |mapleader|). You can add and
remove files and reorganise them as you see fit. You can see their positional
index by enabling the :setlocal number option. When you press <enter> in this
scratch buffer, VFM will set your argument list to these files, in this order.

The |:VFMEdit| command (mapped to <leader>ge by default.) lets you filter a
find result on your 'path' option. If you press |<enter>| on a file from this
window, it will be opened as a new buffer (but not added to your argument
list). If you'd like to set your argument list to the files in the VFM scratch
window, type:
>
  :VFMArgs
<

If instead you'd like to add all of the files to your argument list, type
within the VFM scratch window:
>
  :VFMArgadd
<

The cumbersome combination of |:argument| and |:argedit| have been combined
into one convenient function called VFMArgument(arg) where arg can be either an
argument index or partial buffer name. Remember that the argument index is not
the buffer number. You can see the list of arguments with either the |:VFMArgs|
command or the builtin |:args| command. The buffer name given must exist in the
current argument list. This function has a corresponding command:
>
  :VFMArgument {arg} <

Which is triggered by <plug>vfm_argument (mapped to <leader>gg by default). The
command supports argument list buffer name completion.


3. Additional Plugins Worth Looking At       *learnvim-Additional-Plugins*
                                                     *learnvim-commentary*
* Commentary      - Comment/uncomment code efficiently
                    https://github.com/tpope/vim-commentary
* Ultisnips       - Code Snippets
* SearchParty     - Extended Search, Replace, Highlight and Match commands
* Fanf,ingTastic; - FftT;, across lines
* vim-KWEasy      - Jump to any character on the screen


##############################################################################
EXTERNAL RESOURCES                           *learnvim-External-Resources*

Community ~

* Mailing Lists - http://www.vim.org/community.php
* IRC channel #vim on irc://irc.freenode.net

Tutorials ~

  Beginner ~

  * http://vim.wikia.com/wiki/Learn_to_use_help
  * http://openvim.com/tutorial.html
  * http://vi-improved.org/tutorial.php
  * http://blog.interlinked.org/tutorials/vim_tutorial.html
  * http://derekwyatt.org/vim/tutorials/novice/
  * https://github.com/dahu/VimRegexTutor
  * http://vimhelp.appspot.com/vim_faq.txt.html

  Intermediate ~

  * https://github.com/dahu/vim_waz_ere
  * http://derekwyatt.org/vim/tutorials/intermediate/
  * http://www.moolenaar.net/habits.html

  Advanced ~

  * http://derekwyatt.org/vim/tutorials/advanced/

Plugins ~

* www.vim.org/search.php
* https://github.com/vim-scripts

Unsorted ~

* http://vim.wikia.com/wiki/Vim_Tips_Wiki
* http://vim.wikia.com/wiki/Example_vimrc
* http://vim.wikia.com/wiki/New_to_Vim
* http://vim.wikia.com/wiki/Vim_IRC_FAQ
* http://vim.wikia.com/wiki/VimTip882
* http://vim.wikia.com/wiki/Vim_documentation
* http://vim.wikia.com/wiki/Creating_new_text_objects
* http://vimdoc.sourceforge.net/
* http://github.com/loota/vimfiles/blob/master/vim_usual_options.txt
* http://blog.interlinked.org/tutorials/vim_tutorial.html


##############################################################################
CREDITS                                                 *learnvim-Credits*

LearnVim is written and maintained by Barry Arthur (bairui).

Thanks to the good people at FreeNode#vim for patiently answering my
questions, and their many great suggestions.

Special thanks to Zathrus for giving a detailed list of topics for this
tutorial.

The buffer, window and tab-page definitions were shamelessly copied from the
following resource created by godlygeek: http://vim.pastey.net/115548.

Large parts of the vimrc file were copied from the very helpful
http://vim.wikia.com (http://vim.wikia.com/wiki/Example_vimrc).  A more
annotated version of the vimrc options can be found at
http://github.com/loota/vimfiles/blob/master/vim_usual_options.txt.

 vim:noet:sw=8:nosmarttab:sts=0:fo=tcq2:isk=!-~,^*,^\|,^\":ts=8:fen:fdm=marker:ft=help:norl:noro:modifiable:
