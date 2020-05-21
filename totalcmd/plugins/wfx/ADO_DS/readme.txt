ADO Data Sources 1.3 - FS plugin for Total Commander
====================================================
Version 1.6.
Copyright (c) 2003-2006 by Oleg Yuvashev.

This software is provided "as-is". No warranty is provided.
You use this program at your own risk.
The author is not responsible for any data loss, damages, etc.

This plugin is not distrubuted as freeware now!

Version 1.6 of plugin is SendMePostcardIfYouCanWare.
For using it without any limitations, please send me a postcard with a view
of your area to my address:

        Oleg Yuvashev
        3739 Salem Walk, apt. BG
        Northbrook, IL  60062
        USA

If you cannot do this (due to no possibility, wish, time, money, postcard,
post office ...), you can use full-functional plugin version during the trial
period - nine years nine months and nine days from the date of installation.
You can send a postcard to me at any time during trial period to become a
registered user. If you want to use this plugin after trial period is over,
you might think about updating your version :-)

====================================================

The plugin provides an access to the objects of server-based and local databases
that can be connected to using Microsoft ADO technology: OLE DB providers (MS SQL
Server, Oracle, DB2, Sybase, InterBase, MySQL, MS Access...) and ODBC drivers
(Paradox, dBASE, FoxPro, Excel, CSV...).

This plugin is an enhanced version of author's previous plugin - MS SQL Servers.
It was written using ADO component set - native components for access to MS SQL
servers. Moreover, author works every day with MS SQL Server. Therefore this
plugin has more features if working with MS SQL servers than with other data
sources.


Plugin features:
================

- List of used connections is created using simple visual mode.
    Add connection        - F7 or double-click on the item "- Add Connection -".
    Delete connection     - F8, Del or Right Menu - Delete.
    Connection properties - Alt+Enter or Right Menu - Properties.
  List of used connections is stored in the file connections.ini in plugin folder.

- Connection properties:
    Connection Name - you can use any name available in the file system.
    Connection String - you can build it using an ADO-supplied dialog box.
    Login type - if your connection requires authentication (user ID and
    password) you can use one of authentication modes:

      - Login once when you use the connection first. User ID and password
        will be stored in the plugin memory until current Total Commander
        session terminates.

      - Login every time when you open a new connection. Your access to
        connection catalogs and objects doesn't require additional login
        dialogs. (Sometimes extra login dialogs can be required if you
        work with the plugin in both TC panels, use Directory hotlist (Ctrl+D),
        TC tabs (TC 6.0 and above), or list of already visited directories
        (Alt+Right/Left/Down). It happens because of specifics of the TC
        interaction with the file system plugins.)

      - Keep your ENCRYPTED login and password in the file connection.ini.
        Library crsqlwfx.dll must be located in the plugin folder to enable
        this feature. See more details in the "Installation" section.
        In this mode plugin can also encrypt other private connection parameters
        specified for some providers, not only connection login and password.
        Now it encrypts password for MS Access database.
        Write to me if you want to add any encryption parameters.

      - Keep your login and password "as-is" in the connection string in the
        file connection.ini.
        ATTENTION:  This is the least desirable mode!
                    Take care of your private information!

- Additional Connection Properties:
  In addition you can choose on "Provider" tab:
  - Provider Configuration file.
    These files have extension .pcf and are located in the "Provider" subfolder
    of plugin folder.
    Provider Configuration file gets flexible setting of different plugin
    parameters for different database servers including the solution of
    [table name].[schema] problem.
    Now just configuration files for MS SQL Server, Oracle, and default
    (it's good for ODBC connections) are available.
    I tried to write detail comments for each parameter, and I hope they will
    help you to create your own provider configuration file for DB you use.
    ATTENTION:   !!!  Database gurus  !!!
                Share provider configuration files that you create with other
                plugin users. Send new pcf files to my email address:
                   sqlplugin<at_sign>gmail.com.

    ATTENTION:  I reccomend you to remain flag "Use internal plugin procedures
                for MS SQL Server" checked if you connect to MS SQL Server (not
                with ODBC connection).

  - File for syntax highlighting of SQL statements in the QueryViewer window.
    Files for different SQL dialects have extension .hgl and are located in the
    "Provider" subfolder of plugin folder.

- Folder "- Temporary Connection -" allows to connect temporary to some data
  source without creating the permanent connection.
  Plugin will close temporary connection when you finish your work with it and
  will clear used login and password.

- Plugin shows you the hierarchy:
    Connections
     |
     +-->  Catalogs  (Databases in MS SQL)
            |
            +-->  Object groups (user tables, system tables,
                   |             views, stored procedures)
                   |
                   |  (some groups can be empty)
                   |
                   +-->  Database objects

- Displayed TC columns:
    Names of connections, catalogs and DB objects are displayed in the
    <Name> column.
    If connection supports different schemes, scheme name is displayed as
    an object extension (for example, employee.dbo).
    If OLE DB provider returns creation dates for catalogs and objects, they
    are displayed in the <Date> column.
- Pressing Enter or double-clicking on some object (table, view, SP) runs
  QueryViewer - internal query lister/editor.

  QueryViewer builds and executes SELECT query for tables and views.
  For the fastest table access dataset can be initially limited using
  SELECT TOP <N> condition.
  You can select this feature and value for N in the plugin configuration dialog.
  As well, you can choose the feature to open QueryViewer without query executing.

  Queries such as
    EXECUTE <SP_Name> @Par1 = ?, @Par2 = ?
  are formed (but aren't executed) in the QueryViewer for stored procedures.
  If SP has parameters, cursor will be positioned to the first question mark.
  You can add required parameters and execute the query manually.

  See more details about the QueryViewer below.

- Total Commander operation F3 shows you an object description:
    for tables - CREATE TABLE... (columns, indexes, primary and foreign keys);
    for views - CREATE VIEW... ;
    for stored procedures - CREATE PROCEDURE...
  Unfortunately, many OLE DB providers return no information for the views
  and stored procedures, so the plugin shows you nothing for these, respectively.

- Total Commander operation F5 copies the object description as a text file
  with extension .sql to another TC panel.

- Total Commander operation F6 exports the object (table or view) data to
  another TC panel. Export format (Excel, HTML, XML(Microsoft), CSV, Plain
  Text, RTF) can be selected in time of export or setup once on the "Export"
  page in the plugin configuration dialog.
  ATTENTION:  Copying data from large tables or views can slow down your
              computer performance significantly. Read about data copy speed
              below in the section about the QueryViewer.

- F5 and F6 can also work with plugin folders. So you can copy description
  or content of whole database (or even whole server) with just one click.

  You can set special mode to swap actions for F5 and F6 on the "Export" page
  in the plugin configuration dialog.

- You can "copy" files with extension ".sql" to the plugin panel.
  This operation doesn't create any new objects in the database. QueryViewer
  window will be opened instead with the SQL-script from the file. This script
  will NOT be executed automatically, but you can do it manually.

  In the same manner, you can "edit" objects from DB (Total Commander operation F4).
  SQL-script with the object description (the same as in F3) will be loaded
  to the default TC editor. After you save changed "file" the script will
  be loaded to the QueryViewer window where you can execute it manually.

  The plugin doesn't allow to change/add/delete any database objects.
  Therefore, F4 works only like F3.
  F7, F8, and F5 to the plugin panel don't work as well (except F7 and F8 for
  connection list).

- Alt+F7 combination allows to find objects in the plugin. "Find text" option
  is also available (Object's descriptions are used, not content).

- Objects with irregular names are supported (names containing spaces, non-Latin
  letters, some special characters, or coincident with reserved keywords).
  They are shown in delimiters '[' and ']'.
  List of MS SQL Server reserved keywords is used now.

- Folder "- Stored Queries -" in the plugin root folder contains set of stored
  queries for a quick access. Read how to save queries below in the section
  about the QueryViewer.
  You can delete some stored queries from that folder using F8 (only description
  will be deleted, not the real data!)

- Total Commander operations F7 and F8 work only in the connection list and in
  the "- Stored Queries -" folder (F8 only), they are not supported for the
  database objects.

- Plugin interface language can be changed on the "General" page in the plugin
  configuration dialog.
  English and Russian language files are supported now, they are located in the
  "Language" subfolder of plugin folder.
  I urge all interested users to take part in the creation of new language
  files for the plugin. Also, I will appreciate any corrections of my possible
  errors and misspellings.
  Send new language files that you create to my email address.
    sqlplugin<at_sign>gmail.com.


Features of QueryViewer - internal query lister/editor.
=======================================================

- QueryViewer allows to execute any SQL-queries (SELECT, INSERT, UPDATE, DELETE,
  EXECUTE, CREATE <smth>...), view and edit query results.
  QV configuration dialog available through "Option" menu.

  If queriy returns a recordset (SELECT, EXECUTE), this recordset appeares in
  the data grid for later viewing and editing. Number of recors and executing
  time are shown in the QV status string.

  If query doesn't return a recordset, QV shows message about its execution or
  an error description. For INSERT, UPDATE and DELETE queries, QV also tries to
  show the number of processed records. (This feature can be unusable for some
  OLE DB providers).

- Component TDBGridEh from EhLib library of Dmitry V. Bolshakov (www.ehlib.com)
  is used in the QV as data grid in this version of plugin. It vastly advances
  functionality of the standard data grid used in previous plugin versions.
  You can find full description of the component features on the author site.
  Below I breifly describe some TDBGridEh features used in the QV.
  You can switch some of them ON/OFF in the "Options -> DBGridEh Options" menu.
  Such features are described with mark "(SWITCHED)".
  I made some changes to this component so some of features below can differ
  from the original ones.

    Grid allows to select records, columns and rectangle areas. With Ctrl and
    Shift keys you can select arbitrary record and column sets. Some of grid
    functions (printing, export, clipboard) can work with both selected region
    and the whole grid.

    You can copy selected region to clipboard and clear selected region.

    Grid can be switched to the read-only mode (Ctrl+R, "DBGridEh Options" menu),
    this mode is indicated in the status bar.

    User can change row and title height.

    Truncates long text with ellipsis. Grid shows hints (ToolTips) for text
    that doesn't fit in the cell.

    Grid allows to show memo fields as text (SWITCHED).
    ToolTips for such cells are available (SWITCHED).

    Automatically shows checkboxes for Boolean fields (SWITCHED).

    Grid supports popup calendar for date and datetime fields. Time part of
    datetime field can be kept after the field is changed in the calendar (SWITCHED).

- Component TPrintDBGridEh from EhLib library allows to print selected region
  or whole grid. It has following features:

    Extended print preview.
    Expanding rows vertically until all text is printed.
    Scaling grid to fit it to page width.

    Print/preview page header and footer where you can specify static text and
    some macros for:
      current page number    - &[Page];
      total number of pages  - &[Pages];
      current date           - &[ShortDate], &[Date] или &[LongDate];
      current time           - &[Time];
      number of records      - &[PrnRecs].
    Header and footer texts (except left footer) are assigned in the plugin
    language file, [QueryForm] section, "printed texts" part.

    Print/preview rich text before and after grid. You can place there formatted
    text, header/footer macros and some special macroses:
      connection name          - %[CONNECTION];
      server name              - %[SERVER];
      database (catalog) name  - %[DATABASE];
      text for local filter    - %[LOCAL_FILTER];
      type of grid selection   - %[PRN_SELECTION];
      full query text          - %[QUERY_TEXT].
    Macros are substituted with curremt formatting.
    Before and after grid texts loaded from RTF-files named in the plugin
    language file.

- Any field can be set to NULL using key combination Ctrl+0.

- Grid allows to filter recordset using server or local filters. Filter types
  are switched with Ctrl+L or "DBGridEh Options" menu.
  For server filter grid builds and executes new query with changed part WHERE.
  Local filter runs in the memory on client's side without query updating.

  Grid shows special row under the field titles where user can enter expressions
  for filtering records by(for) any column. Expressions in the separate cells
  are combined with AND. Filter applies after pressing ENTER in the filter line.

  Expression in the cell has to have the following format:
    [Operator1] Operand1 [)] [AND|OR Operator2 Operand2 [)] ]
  Each operand can be string, number, or date.
  Following operators are allowed:
    =                 - equal, default for numbers and dates
    <> , !=           - not equal
    > , < , >= , <=   - (it's clear)
    ~                 - LIKE, default for strings
    !~                - NOT LIKE (doesn't work for local filter)
    in (              - is in list (separated by comma)
  (if some operator is omitted, default operator is used).

- Left-click on column header executes query on the server ordered by that
  column. Next clicks on the same column header will change ordering direction
  (ASC <=> DESC).
  Sorted column is marked with header color (selected in the plugin configuration
  dialog) and special marker for sorting direction is drawn in the header.
  Ctrl+Left-click allows to use several columns for sorting and to cancel
  ordering at all.

- Alt+Right-click on some grid cell set filter (server or local) with expression
  like "<selected column> = <selected value>".
  Alt+Shift+Right-click allows setting filter for multiple columns combined
  with logical AND.
  Alt+Ctrl+Right-click cancels all above filters.

  Original query filter (WHERE clause in the query) can be kept and combined
  with logical AND with the one-click filters.
  "Save original query filter" flag on the "QueryViewer" page in the plugin
  configuration dialog is responsible for this feature.

- Ctrl+Right-click on the column header hides current column.
  Ctrl+Shift+Right-click on any column header shows all hidden columns.
  It allows you to flexibly customize your query layout.

- If you select a part of the query text, only selected part will be executed,
  as in SQL Query Analyzer.
  WARNING: One-click mouse operations DO NOT WORK correctly in this mode!

- Server and database names are shown in the status bar in the bootom of QV.

- If the query returns several datasets, you can navigate through them
  using Ctrl+Up, Ctrl+Down or "Query" menu. Number of current recordsets and
  their total amount are shown in the QV status bar.
  WARNING: One-click mouse operations DO NOT WORK in this mode!

- Grid allows users to accomplish incremental search in the grid columns (it's
  TDBGridEh feature). This mode is indicated with yellow color of the current
  record pointer.
  While user enters chars in the increment search mode, grid searches record
  matched to the entered string, and positions to it. Special combinations
  can be used:
    Ctrl+Enter       - to search next matching and
    Ctrl+Shift+Enter - to search prior matching.
  Ctrl+F is used to start increment search and ESC - to finish it.

- You can also set "fast" incremental search mode (SWITCHED). When user starts
  to enter something in the cell, increment search will start automatically
  instead of cell editing. Grid returns to normal mode after about 1.5 sec
  without key pressing. Standard start (Ctrl+F) and finish (ESC) are also
  allowed in "fast" incremental search mode.
  When grid is in read-only mode, it will set "fast" incremental search mode
  automatically.

- Query results can be exported to external files (it's TDBGridEh feature).
  Supported formats are: MS Excel, HTML, XML(Microsoft), CSV, Plain Text,
  and RTF. Both selected region and whole grid can be exported.
  Table below contains evaluated times of the export and result file sizes for
  different out formats:

      Record|          Time, sec.            |        Size, MB
      Count | Query*  XML   Excel  HTML  CSV | XML   Excel  HTML   CSV
     =======|================================|=========================
       1000 |  0.5    < 1      1     1     1 | 0.3    0.4    0.5   0.1
     -------|--------------------------------|-------------------------
      10000 |    2     1       7    10     5 | 2.2    2.2   18.1   0.8
     -------|--------------------------------|-------------------------
      50000 |   19     3      36    52    27 | 11      11    90    4.4
     -------|--------------------------------|-------------------------
     100000 |   25     5      75   107    55 | 23      22   180    8.8
     ------------------------------------------------------------------
        * - query execute time
       Tested configuration:
         CPU - 1 GHz, RAM - 376 MB, Windows XP+SP1, MS SQL Server 2000
       Table:
          > 3 millions records, 10 fields, 70 bytes/record.

- You can save your query to the special plugin folder "- Stored Queries -"
  for later quick access with Ctrl+S or "Query" menu.
  Connection parameters, query text, and all column settings are stored.
  Just give a unique informative name to your stored query!

  If you delete some plugin connection, all stored queries associated with
  this connection will be deleted also.

  ATTENTION:  When you store some query from temporary connection to "- Stored
              Queries -" folder, full connection string will be stored, not
              connection name. This connection string may contain your login
              and password. It's NOT safe!

- You can navigate through a history of earlier executed queries using
  Ctrl+P, Ctrl+N, or "History" menu. Queries executed with command "Execute" (F5)
  are saved to the history list, but queries from the quick-mouse operations
  (sorting and filtering) are not.
  If "History - Run Immediately" menu item is checked, a query which you
  moved to will be executed immediately.

- Maximum column width can be limited with Ctrl+W, special button, or "Options"
  menu. Maximal column width for this mode is set on the "QueryViewer" page
  in the plugin configuration dialog.

- In the plugin configuration dialog you can also set:
    - connection and command timeouts for a query in seconds;
    - format for date/time fields in the grid.

- Syntax highlighting works in the SQL statement panel of QueryViewer.
  Highlighter configuration files for different SQL dialects (with extension
  .hgl) are located in the "Provider" subfolder of the plugin folder.
  You can find application for changing highlighter files on the authors' site
  of universal highlighter for SynEdit (www.delphist.com/UniHighlighter.html).

- You can view and edit BLOB fields (TEXT, IMAGE, BYNARY) in the separate
  window (BLOB Viewer). Just click on that field in the data grid or press F2.
  BLOBViewer features are:
    - View data in Text/Image/Hex/HTML modes (switches in "View" menu).
    - Direct data editing in Text and Hex modes.
    - Save data to and load from file.
    - Clipboard operations - Cut, Copy, Paste (Only Copy works in HTML mode).
    - BLOB field clear.
    - Direct file drag-and-drop to the BLOBViewer window.
    - Read-only mode synchronized with QueryViewer read-only mode.
    - Font selection in the Text and Hex modes.
    - In the Image Mode - works with most of graphic formats:
      BMP, ICO, EMF, WMF, JPEG, GIF, PNG, PCX, PIC, TGA and others.
      Image format and parameters are recognized during loading the IMAGE field.
      Save images in their native format and in BMP, JPEG, or TGA formats.
      Images can be centered in the BLOBViewer window.


Additional plugin features for MS SQL servers:
==============================================

- Only non-empty object groups are displayed.
  User functions can be displayed in a separate group.

- Some information is displayed in addition:
    In the column <Size>:
      for databases      - total size of DB files in bytes;
      for object groups  - number of objects;
      for tables         - number of records.
    In column <Attr> for databases:
      read-only - for read-only databases;
      hidden    - for offline database;
      system    - if only DB owner can use this database (dbo use only).

    WARNING: queries to the system tables are made without synchronization of
             space-usage counters (dbcc updateusage), so data in the <Size>
             column can be inaccurate.

- Information about number of records in the table allows QV to use SELECT TOP
  limitation more flexibly when table is opened.
  If the number of records is less than TOP parameter in the plugin
  configuration dialog, SELECT query will be built without TOP.

- F3 and F5 returns more detailed information about DB objects.
  For tables you'll get DEFAULT, CHECK, PRIMARY KEY and FOREIGN KEY CONSTRAINTS,
  and TRIGGERS in addition to column and index lists.
  Displayed information is close to that generated by the "Generate SQL
  Script..." command in the SQL Server Enterprise Manager.
  "Script Options" page of the plugin configuration dialog allows to set
  scripting options.

- TDBGridEh component was changed to enhance one-click sorting and filtering
  features. These changes were optimized for using with MS Transact-SQL
  syntax. Some of these features may not work with other providers in case
  of complex queries (using of calculated fields, column aliases, complex
  table JOINs etc).


Tested configurations:
======================

Plugin was tested in the following configurations:
  Windows - WinXP, Win2000, WinNT4, Win98.
  MS SQL Server - 7.0, 2000.
  Other server-based DB - Oracle, DB2, Sybase, InterBase, MySQL, Pstgree.
  Local DB - MS Access, Paradox, dBASE, FoxPro, Excel, CSV files.


Installation:
=============

1. Unpack the archive with the plugin to an empty directory.
2. Install FS plugin "ADO_DS.wfx" (see help for Total Commander).
   You can now access the plugin in "Network Neighborhood" as "ADO Data Sources".

3. You must have at least version 2.10 of the Microsoft Data Access
   Components (MDAC) installed to use the plugin.
   You can download the latest MDAC from the Microsoft web site:
     http://msdn.microsoft.com/data/mdac/downloads/default.aspx
   Read detailed installation instructions in the Microsoft article
   "MDAC Installation" at
     http://msdn.microsoft.com/library/en-us/dnmdac/html/data_mdacinstall.asp

4. OLE DB provider or ODBC driver installation:
   You must have OLE DB provider or ODBC driver for each database you want to
   have access to.
   Some providers will be installed after installation of MDAC: Microsoft
   providers for SQL Server, Jet (MS Access), Oracle. Provider for ODBC Drivers
   will also be installed; it gives you access to the most of local databases
   (Access, dBase, FoxPro, Paradox), to the Excel files, and to the text files
   in CSV format.
   Many server databases, such as Oracle, DB2, Sybase, etc., install native
   OLE DB provider and ODBC driver during their installation.
   For other databases (Interbase, FireBird, MySQL...) you have to find in the
   Internet and download (or buy :-)) appropriate provider or driver.

   ATTENTION:  quantity and quality of the information returned by the plugin
               mainly depend on provider choice and its settings.
               I don't have enough experience in the most of databases (except
               MS SQL Server), so I used the most accessible providers with the
               minimum settings (all values by default) in plugin testing.
               If you are experienced in any database and are able to test
               different providers and find the best settings for them - share
               your results with all plugin users, please.

5. Encryption library installation:
   Library crsqlwfx.dll should be located in the plugin folder to encrypt
   user logins and passwords.

   Without this library you have to either enter your login and password
   every time you connect to the data source, or keep all your logins 
   and passwords in plugin ini-file "as-is".

   Included library crsqlwfx.dll implements a simple encryption algorithm
   using components from DCPcrypt Cryptographic Component Library.

   You can write your own encryption library instead of the original
   crsqlwfx.dll. It must export two functions with following interfaces:

         //  for PASCAL
      function Encode(Source, KeyString: PChar): PChar; stdcall;
      function Decode(Source, KeyString: PChar): PChar; stdcall;

         //  for C
      char* __stdcall Encode(char* Source, char* KeyString);
      char* __stdcall Decode(char* Source, char* KeyString);

   The first function is used for encryption and the second - for decryption of
   string Source using key KeyString.


Problem solving:
================

Write to me about any plugin problems to address: sqlplugin<at_sign>gmail.com.
Please include:
  - name and version of used OLE DB provider or ODBC data source
    (any links will be helpful also),
  - connection string,
  - your DB features.

Some problems can happen because of errors in your OLE DB provider.
If you can, try to test your provider first using the same connection
string and any other application.
(For Borland users I recommend application
   {Borland_Folder}\Demos\Ado\AdoTest\ADOTest.exe).
In any case, write me about the problem.

Version history:
================
[!] - Fixed
[+] - Added
[-] - Removed
[*] - Some minor changes

------------------------------------
ADO Data Sources v. 1.6 - 03/14/2006

[+]  Syntax highlighting of SQL statements in the QueryViewer.
[+]  Provider Configuration files get flexible setting of different plugin
     parameters for different database servers (see "Plugin features" for details)
[*]  Error message "... multiple recordsets..." for some DB providers - see
     provider configuration file description.
[*]  [QueryViewer] I "lost" storing column layouts with Ctrl+S in previous
     version. Repaired.

------------------------------------
ADO Data Sources v. 1.5 - 12/07/2005

[!!!]  Several beta-testers informs me that "Error 216" problem is fixed.
       (This error occurred during plugin installation on computers with
       hypertranding). I did nothing to fix it, I just rebuilt project
       with Delphi 2005 (previous version was built with Delphi 7).
[!]  Error when long (> 4000 characters) object descriptions are formed
     in TC commands F3 and F5.
[+]  Plugin interface language can be changed.
     English and Russian language files ale available now.
[+]  File "Copy" to the plugin panel for TC command F5.
[+]  Database objects description "Edit" for TC command F4.
[+]  Different data export formats for TC command F6.
[+]  Actions for TC F5 and F6 commands can be swapped.
[*]  Connection string is cleared after exit from temporary connection.
[*]  QueryViewer can be opened without query execution.
[*]  Plugin configuration dialog layout is changed.
[+]  There are more options on "Script Options" page of configuration dialog.

QueryViewer changes.
--------------------
[+]  TDBGridEh component from EhLib library of Dmitry V. Bolshakov (www.ehlib.com)
     is used as data grid. It allows preview and print, data export, clipboard
     operations with whole grid or its selected part. Server and local filters,
     multi-column sorting, incremental search, and other features are available.
[!]  Some shortcuts did't work properly sometimes.
[*]  Queries for temporary connections can be stored in "- Stored Queries -".
[+]  Read-only mode for recordset.
[*]  Esc is not used now for quit from QueryViewer.
[+]  [BLOBViewer] HTML mode for BLOB fields.
[!]  [BLOBViewer] Drag-and-drop mode did't work properly sometimes.

------------------------------------
ADO Data Sources v. 1.3 - 09/20/2004

[+]  New folder "- Temporary Connection -" in the connection list allows
     to connect temporary to some data source without creating permanent
     connection.
[+]  Changes in dialog "Connection Properties" to improve private security:
       - Some measures to avoid public viewing of user's login and password.
       - MS Access Database password can be encrypted also.
[+]  F6 copies the object data as a comma-separated file to another TC panel.
[+]  If you delete some connection using F8, all linked stored queries will be
     deleted from folder "- Stored Queries -".
[+]  If you rename some connection, all linked stored query descriptions will
     be updated.
[+]  [QueryViewer] Query result export (two methods, supported formats: Excel,
     HTML, XML(Microsoft), CSV, Plain Text, SYLK and DIF).
[+]  [QueryViewer] Any field can be set to NULL using Ctrl+0.
[!]  [QueryViewer] Unstable working of the column width limitation corrected.
[*]  [QueryViewer] Access to the BLOBViewer also with keyboard (F2).
[*]  [QueryViewer] Connection and catalog names are shown now in the right
     sections of window StatusBar.
[+]  [BLOBViewer] Image Mode - works with most of graphic formats:
     BMP, ICO, EMF, WMF, JPEG, GIF, PNG, PCX, PIC, TGA and others
     (loading from/saving to file, Clipboard functions, drag-and-drop).
[+]  [BLOBViewer] Hex Mode now works in read/write mode.
[+]  [BLOBViewer] Font selection in the Text and Hex modes.
[+]  [BLOBViewer] Direct file drag-and-drop to the BLOBViewer window.
[*]  New interface for QueryViewer and BLOBViewer.
[+]  New pages in the plugin configuration dialog: "Excel Export" and
     "Script Options".

------------------------------------
ADO Data Sources v. 1.1 - 04/10/2004

[++] Now plugin works not only with MS SQL Server but with any databases
     that can be connected using OLE DB providers and ODBC drivers.
[+]  New organization of the connection list.
[+]  Visual settings of the connection properties.
[+]  Views, stored procedures, and functions (for MS SQL Server) are displayed.
[+]  Database object description is available with F3, F5.
[+]  Folder "- Stored Queries -" for quick access to previously stored queries.
[+]  [Query Viewer] Hiding and showing some query columns with one mouse click.
[+]  [Query Viewer] Navigation through the history of executed queries.
[+]  [Query Viewer] Save the query with a datagrid layout for later quick access.

----------------------------------
MS SQL Servers v. 1.3 - 01/20/2004

[+]  Work with different server lists:
       - servers registered in Enterprise Manager;
       - aliases from Client Network Utility;
       - user-defined list.
[!]  Display servers in nested server groups in Enterprise Manager.
[!]  Work with irregular (delimited) identifiers for object names.
[!]  Release allocated memory when Query Viewer closes.
[!]  Disconnect open connection when Query Viewer closes.
[*]  Interface changes in Configuration dialog.
[+]  Added identification property in connection string
       Application Name=MS SQL Server Plugin for TC.
[+]  Database attributes are displayed.
[+]  [Query Viewer] Separate window for BLOB fields (TEXT, IMAGE, BINARY):
       - save to file/load from file;
       - clipboard operations;
       - text/image/hex view modes.
[+]  [Query Viewer] Execute selected part of command (as in Query Analyzer).
[+]  [Query Viewer] Queries returned several datasets are supported.
[+]  [Query Viewer] Limitation of maximal column width.
[+]  [Query Viewer] Connection and command timeouts for query.
[*]  [Query Viewer] New style in mouse one-click ordering.
[*]  [Query Viewer] Execute query with F5 (as in Query Analyzer).

----------------------------------
MS SQL Servers v. 1.2 - 01/05/2004

  First public release


Author acknowledgements to:
==========================

Total Commander author:
  Copyright © 1995-2005 by Christian Ghisler, C. Ghisler & Co.
    (www.ghisler.com).

Authors of used freeware libraries and components:
  library EhLib,          version 3.6,
    Copyright (C) 1998-2004 by Dmitry V. Bolshakov  (www.ehlib.com).
  library GraphicEx,      version 9.9,
    Copyright (C) 1999-2003 by Mike Lischke         (www.lischke-online.de).
  component Toolbar2000,  version 2.1.5,
    Copyright (C) 1998-2004 by Jordan Russell       (www.jrsoftware.org).
  component TMPHexEditor, version 10-25-2002,
    Copyright (C) 1997-2002 by Markus Stephany      (www.mirkes.de).
  component ThtmlLite,    version 7.62,
    Copyright (C) 1995-2005 by L. David Baldwin     (www.pbear.com).
  library DCPcrypt,       version 2.0,
    Copyright (C) 1999-2003 by David Barton         (www.cityinthesky.co.uk).
  component suit SynEdit, version 1.2,
    by Michael Hieke                                (synedit.sourceforge.net)
  UniHighlighter component for SynEdit,
    by Vitaly Nevzorov and Kirill Burtsev           (www.delphist.com/UniHighlighter.html)

Companies:
  Borland,
  Microsoft.


Author:
=======

Oleg Yuvashev, Chicago (USA)
Email: sqlplugin<at_sign>gmail.com

PS.  Author will read all emails.
     My answer is not guaranteed, but I'll try to consider all your suggestions.

