# nikhil
html
grep "ORA-01017" $ORACLE_HOME/diag/tnslsnr/*/trace/listener.log

select username, machine, program, logon_time
from v$session
where username is not null
order by logon_time desc;
