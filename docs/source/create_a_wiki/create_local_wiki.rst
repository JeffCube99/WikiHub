==========================
How to Create A Local Wiki
==========================

Creating a Local Wiki
=====================

There are many different ways to create your own wiki. The following examples will
create a wiki using `sphinx <https://www.sphinx-doc.org/en/master/index.html>`_ installed
inside a `conda <https://docs.conda.io/en/latest/>`_ environment. This can be done
from the terminal or by using `PyCharm <https://www.jetbrains.com/pycharm/>`_:

    ..  tabs::

        ..  group-tab:: Windows

            ..  tabs::

                ..  group-tab:: Terminal


                    ..  code-block:: bash

                        # Create and navigate to a directory that will house your wiki
                        $ mkdir wiki_test
                        $ cd wiki_test/

                        # Create a new conda environment
                        $ conda create --name wiki_test python=3.8

                        # Activate the conda environment you just created
                        $ conda activate wiki_test

                        # Install Sphinx
                        $ conda install sphinx

                    ..  note::

                            When installing packages conda will ask for your permission you to proceed
                            (``Proceed ([y]/n)?``). To continue just type ``y``

                    ..  code-block:: bash

                        # Initialize a default sphinx project by running the command ``sphinx-quickstart``
                        # Follow the instructions in the command prompt. You can accept all of the defaults
                        # (displayed to you within brackets) but you still have to specify Project and Author names.
                        $ sphinx-quickstart

                        # Build HTML docs inside the newly created ``_build`` directory.
                        $ make html

                    *   From this point you can navigate to ``_build/html/index.html`` and open index.html in your browser of choice to see
                        your newly created documentation.
                    *   You can now start writing documentation inside of your base directory (``wiki_test``).


                ..  group-tab:: PyCharm

                    #.  With PyCharm open select **File > New Project...**
                    #.  Choose your project location. (e.g. ``C:\PycharmProjects\test_wiki``)
                    #.  Under **Python Interpreter** create a new environment using Conda
                    #.  Select your python version (For this example we will use ``3.8``)
                    #.  Click the **Create** button to create your project.
                    #.  Select the terminal tab at the bottom of the PyCharm window. From the terminal run the followng:

                    ..  code-block:: bash

                        # Install Sphinx.
                        # During this process conda will ask for your permission you to proceed (``Proceed ([y]/n)?``).
                        # To continue just type ``y``
                        $ conda install sphinx

                        # Initialize a default sphinx project by running the command ``sphinx-quickstart``
                        # Follow the instructions in the command prompt. You can accept all of the defaults
                        # (displayed to you within brackets) but you still have to specify Project and Author names.
                        $ sphinx-quickstart

                        # Build HTML docs inside the newly created ``_build`` directory.
                        $ make html

                    *   From this point you can navigate to ``_build/html/index.html`` and open index.html
                        from PyCharm or in your browser to view your newly created documentation.
                    *   You can now start writing documentation inside of your base directory (``wiki_test``).

        ..  group-tab:: Mac

            ..  tabs::

                ..  group-tab:: Terminal

                    ..  error::

                        No Documentation Avaliable Yet

                ..  group-tab:: PyCharm

                    ..  error::

                        No Documentation Avaliable Yet

.. _Viewing A Local Wiki:

Viewing A Local Wiki
====================

After you create HTML files from your documentation, you could simply select them from your file explorer / finder window and open them
in your browser. However when using sphinx's search functionality the results may not be comprehensive, with only document
names being listed in the search results page. This differs from the search results you see
when searching through sphinx documentation hosted online, which includes snippets of text from the documents that contain
the words you search. This difference occurs because browsers limit displaying the contents of local
files in the sphinx search. If you happen to open the console in chrome you may see errors like the following:

..  error::

    ..  code-block::

            Access to XMLHttpRequest at
            'file:///<path to index.html>'
            from origin 'null' has been blocked by CORS policy: Cross origin requests are only supported for
            protocol schemes: http, data, chrome, chrome-extension, chrome-untrusted, https.

To avoid this error and get a more verbose result you can start a
`Simple Local HTTP server <https://developer.mozilla.org/en-US/docs/Learn/Common_questions/set_up_a_local_testing_server>`_
or piggyback off PyCharm's built in ability to display html files in the browser. Guides for both are
below:

..  tabs::

    ..  group-tab:: Windows

            ..  tabs::

                ..  group-tab:: Terminal

                    ..  code-block:: bash

                        # Navigate to your documentation's root directory
                        $ cd wiki_test

                        # Start a local HTTP server
                        # The terminal will then display a message like "Serving HTTP on :: port 8000"
                        $ python -m http.server


                    ..  note::

                        When running the http.server command, A popup may appear asking you to enable some permissions.
                        Acceptthe permissions for the command to continue execution.

                    *   From this point you can open your browser to `http://localhost:8000/ <http://localhost:8000/>`_.
                    *   In the browser you can navigate to ``_build/html/``. From there you can open up your
                        documentation html pages.

                ..  group-tab:: PyCharm

                    To learn more check out `PyCharms built-in HTML preview <https://www.jetbrains.com/help/pycharm/editing-html-files.html#ws_html_preview_output_built_in_browser>`_

                    *   Open a ``.html`` file built by your project directory (e.g. ``test_wiki/_build/html/index.html``)
                    *   Move your mouse inside the file window. In the upper left hand part of the window you
                        should be able to see icons for different browsers. Select a browser of your choice
                        and pycharm will open the page for you in the browser.
                    *   Alternatively you can select **View > Open in Browser** and select the browser
                        of your choice.

    ..  group-tab:: Mac

        ..  tabs::

            ..  group-tab:: Terminal

                ..  error::

                    No Documentation Avaliable Yet

            ..  group-tab:: PyCharm

                ..  error::

                    No Documentation Avaliable Yet
