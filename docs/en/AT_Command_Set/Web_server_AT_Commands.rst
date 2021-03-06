.. _WEB-AT:

Web server AT Commands
==========================================

-  :ref:`AT+WEBSERVER <cmd-WEBSERVER>`: Enable/disable Wi-Fi connection configuration via web server.

.. _cmd-WEBSERVER:

:ref:`AT+WEBSERVER <WEB-AT>`: Enable/disable Wi-Fi connection configuration via web server
-------------------------------------------------------------------------------------------

Set Command
^^^^^^^^^^^

**Command:**

::

    AT+WEBSERVER=<enable>,<server_port>,<connection_timeout>

**Response:**

::

    OK

Parameters
^^^^^^^^^^

-  **<enable>**: Enable or disable web server.

   -  0: Disable the web server and release related resources. 
   -  1: Enable web server, which means that you can use WeChat or a browser to configure Wi-Fi connection information.

-  **<server_port>**: The web server port number.
-  **<connection_timeout>**: The timeout for the every connection. Unit: second. Range:[21,60].

Notes
^^^^^

-  There are two ways to provide the HTML files needed by the web server. One is to use fatfs file system, and you need to enable AT FS command at this time. The other one is to use embedded files to storge HTML files (default setting). 
-  Please make sure that the max number of open sockets is not less than 12, you may change the number by ``./build.py menuconfig`` > ``Component config`` > ``LWIP`` > ``Max bumber of open sockets`` and compile the project (see :doc:`../Compile_and_Develop/How_to_clone_project_and_compile_it`).
-  The default firmware does not support web server AT commands (see :doc:`../Compile_and_Develop/esp-at_firmware_differences`), but you can enable it by ``./build.py menuconfig`` > ``Component config`` > ``AT`` > ``AT WEB Server command support`` and compile the project (see :doc:`../Compile_and_Develop/How_to_clone_project_and_compile_it`).
-  For more examples, please refer to :doc:`../AT_Command_Examples/Web_server_AT_Examples`.

Example
^^^^^^^^

::

    // Enable the web server with port 80, and the timeout for the every connection is 50 seconds:
    AT+WEBSERVER=1,80,50

    // Disable the web server, the command should be:
    AT+WEBSERVER=0

