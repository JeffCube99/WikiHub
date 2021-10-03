==========================
How to Create A Local Wiki
==========================

To create your own wiki, do the following:

#.  Create a new folder / directory to house your wiki. (For our example we will call the directory ``wiki_test``)
#.  Initialize a `conda <https://docs.conda.io/en/latest/>`_ environment with a recent
    version of`python3 <https://www.python.org/>`_. (For our example we will be using python 3.8)
    This can be done from the terminal or using `PyCharm <https://www.jetbrains.com/pycharm/>`_.

    ..  tabs::

        ..  group-tab:: Windows

            ..  tabs::

                ..  group-tab:: Terminal

                    #.  Navigate to your directory that will house your wiki::

                            $ cd wiki_test/

                    #.  Create a new conda environment::

                            $ conda create --name wiki_test python=3.8

                        ..  note::

                            When installing packages conda will ask for your permission you to proceed
                            (``Proceed ([y]/n)?``). To continue just type ``y``

                    #.  Activate the conda environment you just created::

                            $ conda activate wiki_test

                    #.  Install Sphinx::

                            $ conda install sphinx

                    #.  Initialize a default sphinx project by running the command ``sphinx-quickstart``::

                            $ sphinx-quickstart

                        Follow the instructions in the command prompt. You can accept all of the defaults (displayed
                        to you within brackets) but you still have to specify Project and Author names.

                    #.  Build HTML docs inside the newly created ``_build`` directory.::

                            $ make html

                    #.  Navigate to ``_build/html/index.html`` and open index.html in your browser of choice to see
                        your newly created documentation.

                    #.  You can now start writing documentation inside of your base directory (``wiki_test``).


                ..  group-tab:: PyCharm

                    ..  error::

                        No Documentation Avaliable Yet

        ..  group-tab:: Mac

            ..  tabs::

                ..  group-tab:: Terminal

                    ..  error::

                        No Documentation Avaliable Yet

                ..  group-tab:: PyCharm

                    ..  error::

                        No Documentation Avaliable Yet


..  note::

    Navigating to your local files and opening them in your browser is sufficient to see your documentation,
    however the search functionality of sphinx
    will be restricted when running on browsers like chrome. The search results listed will only include document
    names and will not include the snippet of text from the document that contain the words you search.
    When you open the console when searching your local documents you may see errors like the following

    ..  error::

            Access to XMLHttpRequest at
            'file:///<path to index.html>'
            from origin 'null' has been blocked by CORS policy: Cross origin requests are only supported for
            protocol schemes: http, data, chrome, chrome-extension, chrome-untrusted, https.

    To avoid this error and get a more verbose result you can start a
    `Simple Local HTTP server <https://developer.mozilla.org/en-US/docs/Learn/Common_questions/set_up_a_local_testing_server>`_
    or piggyback off PyCharm's built in ability to display html files in the browser

    ..  tabs::

        ..  group-tab:: Windows

                ..  tabs::

                    ..  group-tab:: Terminal

                        #.  Navigate to your documentation's root directory::

                                $ cd wiki_test

                        #.  Start a local HTTP server::

                                $ python -m http.server


                            The terminal will then display a message like
                            ``Serving HTTP on :: port 8000 (http://[::]:8000/)``

                            ..  note::

                                When running this command, A popup may appear asking you to enable some permissions. Accept
                                the permissions for the command to continue execution.


                        #.  Open your browser to `http://localhost:8000/ <http://localhost:8000/>`_.
                        #.  Navigate to ``_build/html/``. From here you can open up  your documentation html pages in the browser.

                    ..  group-tab:: PyCharm

                        ..  error::

                            No Documentation Avaliable Yet

        ..  group-tab:: Mac

            ..  tabs::

                ..  group-tab:: Terminal

                    ..  error::

                        No Documentation Avaliable Yet

                ..  group-tab:: PyCharm

                    ..  error::

                        No Documentation Avaliable Yet

..
    ..  tab:: Terminal

        #.  Run ``conda create -n documentation python=3.8``

    ..  tab:: Pycharm on Windows

        #.  Navigate to **File > Settings > Project > Python Interpreter**.
        #.  Click the cog icon in the upper right side of the window and select **Add..**
        #.  Select the **Conda Environment** section on the left side of the window
        #.  Select **New Environment**.
        #.  Make sure to select Python version **3.8**.
        #.  Click **OK**

