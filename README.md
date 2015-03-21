<html>
<head>
<meta charset="UTF-8">
<title>Input genjdbc</title>
<link rel="stylesheet" href="http://logstash.net/style.css">
</head>
<body>
<div class="container">

<div id="content_right">
<!--main content goes here, yo!-->

<h2>genjdbc</h2>
<h3>Milestone: <a href="http://logstash.net/docs/1.4.2/plugin-milestones">1</a></h3>
<h3> Synopsis </h3>
Connects to datasources using JDBC driver, executes a select query and for each record returned, emits an event.  
<p>
<pre><code>input {
  scafile {
    <a href="#jdbcHost">jdbcHost</a> => ... # string (required)
    <a href="#jdbcPort">jdbcPort</a> => ... # string (required)
    <a href="#jdbcDBName">jdbcDBName</a> => ... # string (required)
    <a href="#jdbcTargetDB">jdbcTargetDB</a> => ... # string (required)
    <a href="#jdbcDriverPath">jdbcDriverPath</a> => ... # string (required)
    <a href="#jdbcUser">jdbcUser</a> => ... # string (required)
    <a href="#jdbcPassword">jdbcPassword</a> => ... # string (required)
    <a href="#jdbcSQLQuery">jdbcSQLQuery</a> => ... # string (required)
    <a href="#jdbcURL">jdbcURL</a> => ... # string (optional)
    <a href="#jdbcTimeField">jdbcTimeField</a> => ... # string (optional)
    <a href="#jdbcPollInterval">jdbcPollInterval</a> => ... # number (optional), default: 60
    <a href="#jdbcCollectionStartTime">jdbcCollectionStartTime</a> => ... # string (optional)
    <a href="#jdbcPStoreFile">jdbcPStoreFile</a> => ... # string (optional)
    }
 }
</code></pre>
<h3> Details </h3>
<p>
</code>
</p>
</p>
<h4>
<a name="jdbcHost">jdbcHost</a>
</h4>
<ul>
<li> Value type is <a href="http://logstash.net/docs/1.4.2/configuration#string">String</a> </li>
<li> There is no default for this setting </li>
</ul>
<p>jdbc host name. Used to form jdbc url</p>
<h4>
<a name="jdbcPort">jdbcPort</a>
</h4>
<ul>
<li> Value type is <a href="http://logstash.net/docs/1.4.2/configuration#string">String</a> </li>
<li> There is no default for this setting </li>
</ul>
<p>
jdbc port number. Used to form jdbc url
</p>
<h4><a name="jdbcDBName">jdbcDBName</a></h4>
<ul>
<li> Value type is <a href="http://logstash.net/docs/1.4.2/configuration#string">String</a> </li>
<li> The default value is "" </li>
</ul>
<p>
Name of database on server / schema name. Used to form jdbc url
</p>
<h4><a name="jdbcTargetDB">jdbcTargetDB</a></h4>
<ul>
<li> Value type is <a href="http://logstash.net/docs/1.4.2/configuration#string">String</a> </li>
<li>  There is no default value for this item</li>
</ul>
<p>
Target DB name(vendor). used to select appropriate JDBC format.
Supported types Postgres,Oracle,DB2,MySQL,Derby,MSSQL
</p>
<h4><a name="jdbcDriverPath">jdbcDriverPath</a></h4>
<ul>
<li> Value type is <a href="http://logstash.net/docs/1.4.2/configuration#string">String</a> </li>
<li> There is no default value for this item </li>
</ul>
<p>
path to jdbc driver
</p>
<h4><a name="jdbcUser">jdbcUser</a></h4>
<ul>
<li> Value type is <a href="http://logstash.net/docs/1.4.2/configuration#string">String</a> </li>
<li> There is no default value for this item </li>
</ul>
<p>
jdbc user name.  Used to form jdbc url
</p>
<h4><a name="jdbcPassword">jdbcPassword</a></h4>
<ul>
<li> Value type is <a href="http://logstash.net/docs/1.4.2/configuration#string">String</a> </li>
<li> There is no default value for this item </li>
</ul>
<p>
jdbc password.  Used to form jdbc url
</p>
<hr>
</div>
<div class="clear">
</div>
</div>
</div>
<!--closes main container div-->
<div class="clear">
</div>
<div class="footer">
<p>
Hello! I'm your friendly footer. If you're actually reading this, I'm impressed.
</p>
</div>
<noscript>
<div style="display:inline;">
<img height="1" width="1" style="border-style:none;" alt="" src="//googleads.g.doubleclick.net/pagead/viewthroughconversion/985891458/?value=0&amp;guid=ON&amp;script=0"/>
</div>
</noscript>
<script src="/js/patch.js?1.4.2"></script>
</body>
</html>

