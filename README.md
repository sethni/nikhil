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

Subject: Heads-Up: Patch Discrepancy and Deployment Timeline

Dear Team,

This is a quick heads-up regarding the patch version discrepancy identified between the legacy and target environments (Legacy: 19.27.0.0.0, Target: 19.26.0.0.0).

We are actively working with the patching team to address this, with the current approach being a rollback of the patching to bring both environments in sync. Denis will keep us posted on the patching schedule and progress.

In the event of any delays in completing the rollback and validation, we may need to consider pushing the PROD Go-Live (currently planned for August 23rd) to a later date to ensure stability and avoid risks.

We’ll continue to share updates as we move forward.
