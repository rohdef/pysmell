PySmell is a python IDE completion helper. 

It tries to statically analyze Python source code, without executing it, and generates information about a project's structure that IDE tools can use.

The first target is Vim, because that's what I'm using and because its completion mechanism is very straightforward.

##Download and Installation

PySmell's code is available at [GitHub](http://github.com/orestis/pysmell/tree/v0.5). You can click 'Download' to get it as a zip/tar if you don't have git installed.

Extract and drop the pysmell package somewhere in your PYTHONPATH. Distutils coming soon!

##Usage

To generate a PYSMELLTAGS file, use:

    cd /root/of/project
    python /dir/of/pysmelltags.py .

If you want to specifically include or exclude some files or directories (eg. tests), you can use:
    python /dir/of/pysmelltags.py [Package Package File File ...] [-x Excluded Excluded ...]

##Partial tags

If there are files that you want to analyze, but have them only be accessible from a specific package, you can create the PYSMELLTAGS file as above, rename it to PYSMELLTAGS.partial, and put it in the directory you want it to be accessible from. 

For example, if you have a bunch of custom test case files in your FunctionalTests package, along with a thousand actual functional tests, you can use:

    cd FunctionalTests
    python /dir/of/pysmelltags.py FunctionalTest.py UndoTestCase.py
    mv PYSMELLTAGS PYSMELLTAGS.partial

The information in FunctionalTest and UndoTestCase will only be accessible when editing a file inside the FunctionalTests package.

##Vim

To use PySmell omnicompletion from inside Vim, you have to have:

1. Python support
2. The pysmell package in your PYTHONPATH (sometimes Vim is silly about this)
3. Source pysmell/pysmell.vim
4. :set omnifunc=pysmell#Complete
Note: If you want to always use pysmell for python, do:
    autocmd FileType python set omnifunc=pysmell#Complete

You can then use ^X^O to invoke Vim's omnicompletion.

##Reporting issues

Look in the [TODO](http://github.com/orestis/pysmell/wikis/todo) first. Vote up!

Send me an email at orestis@orestis.gr. If you can create a unit test that exposes that behaviour, it'd be great!