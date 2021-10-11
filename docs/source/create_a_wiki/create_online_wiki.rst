===========================
How to Create A Online Wiki
===========================

..  contents::
    :local:


Overview
========

In our examples we create a Online Wiki by using `Read the Docs <https://readthedocs.org/>`_
to host our documents online. In our examples we also sign into Read the Docs using
a `GitHub <https://github.com/>`_ account and create and use repositories with the account.

..  note::

    Be prepared to give Read The Docs some admin privileges on your GitHub account. If you do not feel comfortable
    with this on your existing account I suggest creating a new one. There are alternatives like
    `Manually importing your docs <https://docs.readthedocs.io/en/stable/intro/import-guide.html#manually-import-your-docs>`_
    but that is not currently covered in our examples here.

Test Read The Docs by Loading a Demo Project
============================================

..  note::

    The following example only has you create a demo project using a `template repository <https://github.com/readthedocs/template.git>`_.
    You do not own the template repository, so you cannot make edits to it. If you want to start
    your own documentation see :ref:`Create Your Online Documentation From A Template`.

#.  After you have setup your Read the Docs account open your profile.
#.  If you have no projects, your dashboard should display a link to **Import our own demo project**. Clicking this link
    will cause Read the Docs to create a demo project and take you to a
    url like ``https://readthedocs.org/projects/<username>-demo/`` which is the new project's overview page.
#.  From the overview page you can view the generated documentation by clicking on the **View your documentation**
    button. There you will see that the docs are viewable at a url like
    ``https://<username>-demo.readthedocs.io/en/latest/``.


.. _Create Your Online Documentation From A Template:

Create Your Online Documentation From A Template
================================================

If you have not created your own documentation, you can begin by using the template provided by Read The Docs. This
section is based of the `Getting Started <https://docs.readthedocs.io/en/stable/tutorial/index.html#getting-started>`_
section from the Read The Docs tutorial documentation.

Starting Your Repository From A Template
----------------------------------------

#.  Go to the `Read The Docs GitHub template <https://github.com/astrojuanlu/tutorial-template/>`_.
#.  While signed into GitHub, click the **Use this template** button.
#.  Give the repository a name.
#.  Set it's visibility to **Public**
#.  Click the **Create repository from template** button.

Setting Repository up with ReadTheDocs
--------------------------------------

#.  Go to `readthedocs.org <https://readthedocs.org/>`_ and sign in
#.  Go to your dashboard and click on the **Import a Project** button
#.  Click the **refresh** button so that Read the Docs can search through your public repositories.
#.  Click the **plus** button next to the repository you want to import into Read the Docs
#.  The next page allows you to set details about your project. Click the checkbox towards the end of the details
    page to see more advanced options.
#.  Click the **Next** button. This will direct you to the project homepage

..  note::

    *   After creating your project, Read the Docs will try to build the documentation. You can see the build logs
        by clicking on the **Build** section in your project page.
    *   You can view your documentation by clicking on the **View Docs** Button in your project page. By default
        the url for your docs will be formatted as ``<project_name>.readthedocs.io/en/latest``

Once the project is created, you will need to update its configurations:

#.  Click the ⚙ **Admin** button to go to the settings page
#.  Add text to the empty Description section.
#.  If you have a homepage, put the url here.
#.  Add any relevant tags to your project. For example if your project is food based the tags you enter could be
    "food, veggies".
#.  To save your changes click the **Save** button at the bottom of the page.
#.  Click on the **Nofifications** section on the left hand side of the settings page. Put an email under the
    email notifications section to get notifications when the build of your project fails.
#.  Click on the **Advanced Settings** section on the left hand side of the settings page. Check the
    **Build pull requests for this project** box. This means that Read the Docs will build the documents
    when a pull request is open and when a new commit has been pushed.
#.  Save the settings by click the **Save** button at the bottom of the page.

..  note::

    *   Building pull requests is useful as it allows you to preview changes to your documents in Read the Docs
    *   If you want to preview the build locally instead of having Read the Docs build it do the following::

            # Install sphinx. If you have a conda environment simply run the following
            $ conda install sphinx

            # If you are using the default sphinx_rtd_theme install it
            $ conda install sphinx_rtd_theme

            # Navigate to your docs folder
            $ cd docs

            # Build the HTML Files
            $ make html

    *   The html files will be built to ``docs/build/html`` and can be viewed in the browser.
        for more information see :ref:`Viewing A Local Wiki`.

    ..  note::

        If bullets are not rendering in your locally generated document you may need to install docutils by running
        ``conda install docutils=0.16`` from the terminal.
        *   `Link to Stack Overflow Issue <https://stackoverflow.com/questions/67542699/readthedocs-sphinx-not-rendering-bullet-list-from-rst-file>`_

Make the Template Your Own
--------------------------

..  note::

    If you decided to create a new github account when creating your project, remember to adjust your git config settings
    so any changes you commit to the repository are attached to the new account. For example:

    ..  code-block:: bash

        # set local git username
        $ git config --local user.name "JeffCube99"

        # set local git user email
        $ git config --local user.email jeffcube99@gmail.com

If you have followed the above instructions and built the documentation from the
`Read The Docs GitHub template <https://github.com/astrojuanlu/tutorial-template/>`_ you can follow these steps to
start making the project your own by doing the following:

#.  Remove the ``lumanche.py`` file from your repository. If your documentation repository includes a python package you
    can refer to the Read the Docs `Folder Structure <https://sphinx-rtd-tutorial.readthedocs.io/en/latest/folders.html>`_
    pages on how to structure your repository for documentation and your python project.
#.  Update the README.rst file
#.  Add a new directory ``_static`` to ``docs/source``. This file is specified inside ``docs/source/conf.py`` and can
    be used to hold custom static files. To learn more about the static directory visit sphinx's documentation on
    the `html_static_path option <https://www.sphinx-doc.org/en/master/usage/configuration.html#confval-html_static_path>`_
    for the ``conf.py`` file
#.  Inside ``pyproject.toml``, Update the project name and authors.
#.  Inside the ``docs/source/`` folder, remove ``api.rst`` and ``usage.rst`` since those
    files were part of the template documentation.
#.  Inside ``docs/source/conf.py`` update the project and author names and change the copyright name to the author name.
    For example::

        project = 'WikiHub'
        copyright = '2021, JeffCube'
        author = 'JeffCube'

    Also change the version number (to ``0.0.1`` if you are just starting) and set the release number equal to the version
    number::

        version = '0.0.1'
        release = version

#.  Update the contents of ``docs/source/index.rst`` This is the homepage of your documentation.
#.  Start adding ``.rst`` files and directories of your own to ``docs/source``.

..  note::

    If you want your documentation to support tabs install `sphinx-tabs <https://sphinx-tabs.readthedocs.io/en/latest/>`_
    Add add sphinx-tabs to requirements.txt at the root of the project or in your docs folder.