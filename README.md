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


I would like to extend my sincere thanks to Denis for his swift support in helping us successfully apply and stabilize the 19.28 patch on OCAC. Despite the extremely short notice and the urgency due to critical project deadlines, Denis expedited the process seamlessly and ensured minimal disruption.

Thanks to his timely intervention and technical expertise, the environment is now back to normal operations, enabling our teams to stay on track with deliverables.

Since I’m a contractor, I have limited access to TD appreciation tools and couldn’t send one formally, but I truly wanted to acknowledge and thank Denis for his outstanding effort.
