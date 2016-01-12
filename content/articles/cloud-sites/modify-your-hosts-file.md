---
node_id: 629
title: Modify your hosts file
permalink: article/modify-your-hosts-file
type: article
created_date: '2011-03-16 21:57:40'
created_by: RackKCAdmin
last_modified_date: '2015-09-18 21:0739'
last_modified_by: kyle.laffoon
products: Cloud Sites
body_format: tinymce
---

Modifying your **hosts**file allows you to override the DNS for a
domain, on that particular machine. This is useful when you want to test
your site without the test link, prior to going live with SSL; verify
that an alias site works, prior to DNS changes; and for other
DNS-related reasons. Modifying your **hosts**file causes your local
machine only to look directly at the IP address specified.

You need to add two entries to your **hosts**file that contain the IP
address that you want the site to resolve to and the address. Adding the
following two lines, for example, point **www.domain.com** and
**domain.com** to our current PHP5-ITK ("Refreshed" PHP5) cluster:

    64.49.219.194 www.domain.com
    64.49.219.194 domain.com

The following sections provide instructions for locating and editing the
hosts file on several operating systems. After you add the domain
information and save the file, your system begins resolving to the
specified IP address. After testing is finished, remove these entries.

-   [Windows 8, Windows 7, and Windows Vista](#Windows_Vista)
-   [Windows NT, Windows 2000, and Windows XP](#Windows_NT2000XP)
-   [Linux](#Linux)
-   [Mac OS X 10.0 through 10.1.5](#Mac_OS_X_100_through_1015)
-   [Mac OS X 10.6 through 10.8](#macosx10.6)

Windows 8, Windows 7, and Windows Vista {#Windows_Vista}
---------------------------------------

Windows 8, Windows 7, and Windows Vista use User Account Control (UAC),
so Notepad must be run as Administrator.

### For Windows 8

1.  Press the Windows key.
2.  Type **Notepad**in the search field.
3.  In the search results, right-click **Notepad**and select **Run as
    administrator**.
4.  In Notepad, open the following file:
    **c:\\Windows\\System32\\Drivers\\etc\\hosts**
5.  Make the necessary changes to the file.
6.  Click **File \> Save** to save your changes.

### For Windows 7 and Windows Vista

1.  Click **Start \> All Programs \> Accessories**.
2.  Right-click **Notepad**and select **Run as administrator**.
3.  Click **Continue**on the **Windows needs your permission** UAC
    window.
4.  When Notepad opens, click **File \> Open**.
5.  In the **File name** field, type
    **C:\\Windows\\System32\\Drivers\\etc\\hosts**.
6.  Click **Open**.
7.  Make the necessary changes to the file.
8.  Click **File \> Save** to save your changes.

Windows NT, Windows 2000, and Windows XP {#Windows_NT2000XP}
----------------------------------------

1.  Click **Start \> All Programs \> Accessories \> Notepad**.
2.  Click **File \> Open**.
3.  In the **File name** field, type
    **C:\\Windows\\System32\\Drivers\\etc\\hosts**.
4.  Click **Open**.
5.  Make the necessary changes to the file.
6.  Click **File \> Save** to save your changes.

Linux {#Linux}
-----

1.  Open a terminal window.
2.  Open the **hosts** file in a text editor (you can use any text
    editor) by typing the following line:

        sudo nano /etc/hosts

3.  Enter your domain user password.
4.  Make the necessary changes to the file.
5.  Press **Control-x**.
6.  When asked if you want to save your changes, answer **y**.

Mac OS X 10.0 through 10.1.5 {#Mac_OS_X_100_through_1015}
----------------------------

1.  Open **/Applications/Utilities/NetInfo Manager**.
2.  To allow editing of the NetInfo database, click the padlock in the
    lower-left corner of the window.
3.  Enter your domain user password and click **OK**.
4.  In the second column of the browser view, select the node named
    `machines`.\
     You will see entries for `-DHCP-`, `broadcasthost`, and `localhost`
    in the third column.
5.  In the third column, select `localhost`.
6.  From the **Edit** menu, select **Duplicate**. (The quickest way to
    create a new entry is to duplicate an existing one.)\
     A confirmation alert appears.
7.  Click **Duplicate**.\
     A new entry called `localhost copy` appears, and its properties are
    shown below the browser view.
8.  Double-click the value of the `ip_address` property and enter the IP
    address of the other computer.
9.  Double-click the value of the `name` property and enter the hostname
    you want for the other computer.
10. Click the `serves` property and select **Delete** from the **Edit**
    menu.
11. From the **File** menu, select **Save**.\
     A confirmation alert appears.
12. Click **Update this copy**.
13. Repeat steps 6 through 12 for each additional host entry that you
    want to add.
14. From the NetInfo Manager menu, select **Quit**.\
     You do not need to restart the computer.

Mac OS X 10.6 through 10.8 {#macosx10.6}
--------------------------

1.  Open **Applications \> Utilities \> Terminal**.
2.  Open the **hosts** file by typing the following line in the terminal
    window:

        sudo nano /private/etc/hosts

3.  Type your domain user password when prompted.
4.  Edit the **hosts** file.\
     The file contains some comments (lines starting with the `#`
    symbol), and some default hostname mappings (for example, 127.0.0.1
    &ndash; local host). Add your new mappings after the default mappings.
5.  Save the hosts file by pressing **Control+x** and answering **y**.
6.  Make your changes take effect by flushing the DNS cache with the
    following command:

        dscacheutil -flushcache

    The new mappings should now take effect.



de 6 a 12 para cada entrada de host adicional
    que voc&ecirc; deseja adicionar.\
     \
     14. Selecione Sair do menu de NetInfo Manager. N&atilde;o h&aacute; necessidade
    de reiniciar o computador.\
      

Mac OS X 10.6 - 10.8 {#macosx10.6}
--------------------

1.  1. Abra Aplicativos\> Utilit&aacute;rios\> Terminal.\
     \
     2. Abra o arquivo hosts, digitando o seguinte na janela Terminal:\
     \
     sudo nano / privado / etc / hosts\
     \
     Digite sua senha quando solicitado.\
     \
     3. Edite o arquivo hosts. O arquivo hosts cont&eacute;m coment&aacute;rios
    (linhas que come&ccedil;am com \#), e alguns nomes de host de mapeamento
    padr&atilde;o (por exemplo, 127.0.0.1 - host local). Fixe seus novos
    mapeamentos abaixo os mapeamentos padr&atilde;o.\
     \
     4. Salve o arquivo hosts pressionando Control + xy e resposta.\
     \
     5. Para que as altera&ccedil;&otilde;es tenham efeito, esvaziar o cache DNS com o
    seguinte comando:\
     \
     dscacheutil -flushcache\
     \
     6. Agora, aplique o novo mapeamento.



