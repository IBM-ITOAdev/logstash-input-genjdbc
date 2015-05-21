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
  genjdbc {
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
This plugin takes basic JDBC configuration information, an SQL query and some timing control. It then runs that queryr (with some additional timing information applied) in a loop, emitting events corresponding to each row in the returned table. For example 
</p>
<pre><code>
genjdbc {  
  jdbcHost       => 'X.X.X.X'
  jdbcPort       => '50000'
  jdbcTargetDB   => 'db2'
  jdbcDBName     =>'MYDB'
  jdbcUser         => 'myuser' 
  jdbcPassword   => 'mypasswd'
  jdbcDriverPath => '/path/to/my/driver/db2jcc4.jar'
  jdbcSQLQuery    => 'select * from DT_ALARM_HIST where SUPPRESSED_DESC is null'
  jdbcTimeField => 'TSTAMP'
  jdbcPStoreFile => './test.pstore'                        
  jdbcCollectionStartTime => '2015-01-01 00:00:00.000'
}
</code></pre>
<p>
In the above example. the query will have <code>where 'TSTAMP' >= currentTime'</code> appended to it. <code>currentTime</code> is an internal variable maintained by the plugin which will be incremented on each loop with the timestamp of the last record returned from the query. 
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
Supported types 
<li>postgresql </li>
<li>oracle</li>
<li>db2</li>
<li>mysql</li>
<li>derby</li>
<li>mssql</li>
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
<h4><a name="jdbcSQLQuery">jdbcSQLQuery</a></h4>
<ul>
<li> Value type is <a href="http://logstash.net/docs/1.4.2/configuration#string">String</a> </li>
<li> There is no default value for this item </li>
</ul>
<p>
SQL query to execute   or  the path of a text file which contains the query to execute.  
</p>
<p><code>jdbcSQLQuery => "select * from myTable"</code><p>
In the latter case, prefix the filename with 'file:'   e.g. 
<p><code>jdbcSQLQuery => "file:/path/to/my/query.txt"</code></p>

<h4><a name="jdbcURL">jdbcURL</a></h4>
<ul>
<li> Value type is <a href="http://logstash.net/docs/1.4.2/configuration#string">String</a> </li>
<li> There is no default value for this item </li>
</ul>
<p>
jdbc URL - explicitly set the jdbc URL string. Overrides all other URL component settings (e.g jdbcHost, jdbcPort)
</p>
<h4><a name="jdbcTimeField">jdbcTimeField</a></h4>
<ul>
<li> Value type is <a href="http://logstash.net/docs/1.4.2/configuration#string">String</a> </li>
<li> There is no default value for this item </li>
</ul>
<p>
Name of the table column which contains timestamp information. This string will be used in the automatically generated SQL query as part of the <code>where</code> clause.
</p>
<h4><a name="jdbcPollInterval">jdbcPollInterval</a></h4>
<ul>
<li> Value type is <a href="http://logstash.net/docs/1.4.2/configuration#Number">Number</a> </li>
<li> 60 </li>
</ul>
<p>
The number of seconds to wait between query loops. A query loop executes the query, waits for a response, processes the response ( by emitting events). Once these steps are completed, the plugin will wait the specified amount of time before starting again and invoking the query.
</p>
<h4><a name="jdbcCollectionStartTime">jdbcCollectionStartTime</a></h4>
<ul>
<li> Value type is <a href="http://logstash.net/docs/1.4.2/configuration#string">String</a> </li>
<li> There is no default value for this item </li>
</ul>
<p>
This is a timestamp expressed as a string e.g. <code>'2015-01-01 00:00:00.000'</code>. It will be used in direct comparison operations against the specified <code>jdbcTimeField</code> so the precise format depends on the database and the nature of the time column referenced.
</p>
<h4><a name="jdbcPStoreFile">jdbcPStoreFile</a></h4>
<ul>
<li> Value type is <a href="http://logstash.net/docs/1.4.2/configuration#string">String</a> </li>
<li> There is no default value for this item </li>
</ul>
<p>
The pathname of a file which is used to maintain state for this operator. It is useful  to be able to specify this as you may have multiple <code>genjdbc</code> plugins.
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

