# nikhil
html
grep "ORA-01017" $ORACLE_HOME/diag/tnslsnr/*/trace/listener.log

select username, machine, program, logon_time
from v$session
where username is not null
order by logon_time desc;

SELECT sid,
       serial#,
       username,
       machine,
       program,
       status,
       logon_time
FROM   v$session
WHERE  status = 'ACTIVE'
AND    username IS NOT NULL
ORDER BY logon_time DESC;

SELECT COUNT(*) AS rows_today
FROM rpmopen.<table_name>
WHERE TRUNC(created_date) = TRUNC(SYSDATE);
