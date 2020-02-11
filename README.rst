=====
Mflix
=====

This is a short guide on setting up the system and environment dependencies
required for the MFlix application to run.


Project Structure
-----------------

Most of your work will be implementing methods in the **dao** directory, which
contains all database interfacing methods. The API will make calls to Data
Access Objects (DAOs) that interact directly with MongoDB.

The unit tests in **test** will test these database access methods directly,
without going through the API. The UI will run these methods in integration
tests, and therefore requires the full application to be running.

The API layer is fully implemented, as is the UI. The application is programmed
to  run on port **5000** by default - if you need to run on a port other than
5000, you can edit the **dotenv_win** (if on Windows) or the **dotenv_unix** file
(if on Linux or Mac) in the root directory to modify the value of **PORT**.

MFlix uses MongoDB to persist all of its data.

Creating a free tier cluster called "mflix" on mongo atlas cloud:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Running the Application
-----------------------

In order for the application to use Atlas, you will need a file called **.env**
to contain the connection information. In the **mflix-js** directory you can
find two files, **dotenv_unix** (for Unix users) and **dotenv_win** (for Windows
users).

Open the file for your chosen operating system and enter your Atlas SRV
connection string as directed in the comment. This is the information the driver
will use to connect. Make sure **not** to wrap your Atlas SRV connection between
quotes::

  MFLIX_DB_URI = mongodb+srv://...

It's highly suggested you also change the **SECRET_KEY** to some very long, very
random string. While this application is only meant for local use during this
course, software has a strange habit of living a long time.

When you've edited the file, rename it to **.env** with the following command:

.. code-block:: sh

  mv dotenv_unix .env  # on Unix
  ren dotenv_win .env  # on Windows

*Note:* Once you rename this file to **.env**, it will no longer be visible in
Finder or File Explorer. However, it will be visible from Command Prompt or
Terminal, so if you need to edit it again, you can open it from there:

.. code-block:: sh

 vi .env       # on Unix
 notepad .env  # on Windows

In the **mflix-js** directory, run the following commands:

.. code-block:: sh

  # install MFlix dependencies
  npm install

  # start the MFlix application
  npm start

This will start the application. You can then access the MFlix application at
`http://localhost:5000/ <http://localhost:5000/>`_.


Running the Unit Tests
----------------------

To run the unit tests for this course, you will use `Jest
<https://jestjs.io/docs/en/getting-started>`_. Jest has been included in this
project's dependencies, so ``npm install`` should install everything you need.

Each course lab contains a module of unit tests that you can call individually
with ``npm test``. For example, to run the test **connection-pooling.test.js**,
run the command:

.. code-block:: sh

  npm test -t connection-pooling

Each ticket will contain the exact command to run that ticket's specific unit
tests. You can run these commands from anywhere in the **mflix-js** project.
