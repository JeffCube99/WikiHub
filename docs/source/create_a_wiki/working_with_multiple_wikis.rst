===========================
Working With Multiple Wikis
===========================

..  contents::
    :local:

Background
==========

When starting out making a wiki for yourself you may have files for every topic you wanted to cover. You may have
organized those files into different directories each one containing documents on different topics. If however you
wanted to publish these wikis online it may be unwise to place them in a wiki as users searching for documents
from topicA may retrieve documents from topicB that reference topicA.
Another issue was the managing of changes applied to the different topics. For wikis managed in git, having pull
requests to a wiki contain additions and subtractions across a variety of different topics may be overwhelming to
manage / moderate. Because of this we propose a structure where each wiki gets its own repository. This leads to
its own issue however, how to manage all of these different repositories. To get a global view of the documentation
as well as provide a easy way to dip into and edit documentation in any wiki we propose a repository that initializes submodules
for each of the different wikis. This is the structure we use for WikiHub

..  note::

    Credit to David Fischer's
    `sphinx-with-submodules <https://sphinx-with-submodules.readthedocs.io/en/latest/index.html>`_ project for
    its ideas on handling submodules within Read the Docs projects.


Create A Global Wiki (WikiHub)
==============================

#.  We first start by creating a new wiki we can host online with Read the Docs. To do so follow the steps in the section
    :ref:`Create Your Online Documentation From A Template`.
#.  Next we create a ``.readthedocs.yaml`` file at the root of our new global wiki project. For more information
    on this configuration file visit https://rtd-docs-single-version.readthedocs.io/config-file/v2.html. Inside the
    file we add the following:

    ..  code-block:: yaml

        # .readthedocs.yaml
        # Read the Docs configuration file
        # See https://docs.readthedocs.io/en/stable/config-file/v2.html for details

        # Required
        version: 2

        # Submodules
        submodules:
          include: all
          recursive: true

        # Python Requirements
        python:
           install:
           - requirements: docs/requirements.txt

    With this file, we inform Read the Docs to include submodules we add to our project. These submodules
    will contain other wikis that we wish to reference.
#.  Next we add submodules we want to include in our global wiki:

    ..  code-block:: bash

        # git submodule add <project url>
        $ git submodule add https://github.com/JeffCube99/GitWiki.git

#.  Next we will create a new directory related to each of our submodules within ``docs/source/``.
    Within each directory we will create a ``index.rst`` file that has an ``..  include::`` directive with
    a path to the root ``index.rst`` file of the submodule. We also add extra information linking to the
    wiki's source.:

    ..  code-block:: rst

        # inside of docs/source/GitWiki/index.rst

        #######
        GitWiki
        #######

        Wiki Source: https://gitwiki.readthedocs.io/en/latest/

        .. include:: ../../../GitWiki/docs/source/index.rst

#.  Now navigate to your main page ``docs/source/index.rst`` file and add a link to the
    submodule's index.rst file within the toctree directive:

    ..  code-block:: rst

        ..  toctree::
            :maxdepth: 2
            :hidden:

            GitWiki/index

    From this point the submodules documents should be viewable when generating the documents
    of the global wiki.


