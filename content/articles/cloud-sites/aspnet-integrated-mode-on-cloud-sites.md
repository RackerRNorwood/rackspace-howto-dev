---
node_id: 518
title: ASP/.NET Integrated Mode on Cloud Sites
type: article
created_date: '2011-03-16 21:57:40'
created_by: RackKCAdmin
last_modified_date: '2011-09-07 15:2109'
last_modified_by: matt.wheeler
product: Cloud Sites
body_format: tinymce
---

The Rackspace Cloud provisions IIS sites in &ldquo;Integrated Mode.&rdquo; Running
sites in Integrated Mode enhances application performance. However, if
you encounter an issue with your ASP.NET site, please review the
following potential errors.

If these potential solutions fail to correct the problem, please contact
a member of our support team and they can assist in moving your site to
a Classic App Pool.

ASP.NET applications require migration when specifying configuration in
\<httpModules\> or \<httpHandlers\>.

You will receive a 500 - Internal Server Error. This can include HTTP
Error 500.22, and HTTP Error 500.23: An ASP.NET setting has been
detected that does not apply in Integrated managed pipeline mode.

It occurs because ASP.NET modules and handlers should be specified in
the IIS \<handlers\> and \<modules\> configuration sections in
Integrated Mode.

You can migrate by moving the custom entries in the
\<system.web\>/\<httpModules\> and \<system.web\>/\<httpHandlers\>
configuration manually to the \<system.webServer\>/\<handlers\> and
\<system.webServer\>/\<modules\> configuration sections, and either
removing the \<httpHandlers\> and \<httpModules\> configuration OR
adding the following to your application&rsquo;s web.config:

\<system.webServer\>

      <validation validateIntegratedModeConfiguration="false" />

\</system.webServer\>

\
 Request URLs containing unencoded &ldquo;+&rdquo; characters in the path (not
querystring) is rejected by default.

You will receive HTTP Error 404.11 &ndash; Not Found: The request filtering
module is configured to deny a request that contains a double escape
sequence.

This error occurs because IIS is by default configured to reject
attempts to doubly-encode a URL, which commonly represent an attempt to
execute a canonicalization attack.

Applications that require the use of the &ldquo;+&rdquo; character in the URL path
can disable this validation by setting the allowDoubleEscaping attribute
in the system.webServer/security/requestFiltering configuration section
in the application&rsquo;s web.config. However, this may make your application
more vulnerable to malicious URLs:

\<system.webServer\>

      <security>
              <requestFiltering allowDoubleEscaping="true" />
      </security>

\</system.webServer\>

\
 Requests with querystrings larger then 2048 bytes will be rejected by
default.

You will receive an HTTP Error 404.15 &ndash; Not Found: The request filtering
module is configured to deny a request where the query string is too
long.

IIS by default is configured to reject querystrings longer than 2048
bytes. This may affect your application if it uses large querystrings or
uses cookieless ASP.NET features like Forms Authentication and others
that cumulatively exceed the configured limit on the querystring size.

NOTE: This breaking change applies to both Classic and Integrated modes.

Increase the maximum querystring size by setting the maxQueryString
attribute on the requestLimits element in the
system.webServer/security/requestFiltering configuration section in your
application&rsquo;s web.config:

\<system.webServer\>

      <security>
          <requestFiltering>
              <requestLimits maxQueryString="NEW_VALUE_IN_BYTES" />
          </requestFiltering>
      </security>

\</system.webServer\>

\
 DefaultHttpHandler is not supported. Applications relying on
sub-classes of DefaultHttpHandler will not be able to serve requests.

If your application uses DefaultHttpHandler or handlers that derive from
DefaultHttpHandler, it will not function correctly. In Integrated mode,
handlers derived from DefaultHttpHandler will not be able to pass the
request back to IIS for processing, and instead serve the requested
resource as a static file. Integrated mode allows ASP.NET modules to run
for all requests without requiring the use of DefaultHttpHandler.

Change your application to use modules to perform request processing for
all requests, instead of using wildcard mapping to map ASP.NET to all
requests and then using DefaultHttpHandler derived handlers to pass the
request back to IIS.

Source:
[http://mvolo.com/blogs/serverside/archive/2007/12/08/IIS-7.0-Breaking-Changes-ASP.NET-2.0-applications-Integrated-mode.aspx](http://mvolo.com/blogs/serverside/archive/2007/12/08/IIS-7.0-Breaking-Changes-ASP.NET-2.0-applications-Integrated-mode.aspx "http://mvolo.com/blogs/serverside/archive/2007/12/08/IIS-7.0-Breaking-Changes-ASP.NET-2.0-applications-Integrated-mode.aspx")

