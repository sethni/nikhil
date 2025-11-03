Business Benefit:

The AWS Oracle migration project successfully transitioned multiple interdependent legacy applications to the new Oracle Cloud@Customer (OCAC) environment. Applications were migrated from VMC1 to VMC2 with improved performance, scalability, and resilience. The modernization reduced infrastructure overhead, enhanced operational efficiency, and supported future cloud integration.

TCS Engagement:

The team executed the migration with minimal downtime, ensuring seamless transition of all databases and application components. The migration was completed without any post-migration issues, and a Disaster Recovery (DR) test was successfully validated from the database perspective, confirming system reliability and business continuity.





Summary:
Imran has demonstrated gaps in core Oracle DBA skills, technical knowledge, and due diligence. Multiple complaints and production issues have been reported over recent weeks, indicating insufficient understanding of critical database administration practices. Despite prior feedback and support, expected improvements have not been observed. This PIP aims to provide a final opportunity for Imran to show measurable progress and meet performance expectations.

⸻

Key Focus Areas (Bulk Points)
	•	Strengthen Oracle DBA fundamentals and troubleshooting proficiency.
	•	Improve production incident handling and root cause analysis.
	•	Demonstrate consistent due diligence in technical changes and deployment activities.
	•	Enhance documentation quality and adherence to operational standards.
	•	Communicate effectively and escalate risks or blockers in a timely manner.
	•	Participate actively in team discussions and technical reviews.
	•	Complete assigned action items within agreed timelines.
	•	Attend mentoring sessions and technical workshops as scheduled.
	•	Show measurable reduction in recurring production issues.
	•	Maintain a professional and accountable approach toward deliverables.



	------







Imran
	•	September was a productive month with an average of 6–7 working hours per day.
	•	Proactively acknowledged team members’ messages on Teams.
	•	Maintained good rapport with both customers and team members.
	•	TD trainings are currently on hold; coordinating with TD HR to resume them.
	•	Continue to stay active and available on Teams — Imran acknowledged.

⸻

Rahul
	•	Fully occupied with work and utilized spare time for training and conducting KT sessions for the offshore team.
	•	Proactively acknowledged team members’ updates on Teams.
	•	Averaged 6–7 productive hours per day.
	•	Continue to stay active and available on Teams — Rahul acknowledged.

⸻

Nishant
	•	September had relatively less workload, averaging 6–7 productive hours per day, with 3 days off.
	•	Always proactive in responding to team members on Teams.
	•	Continue to stay active and available on Teams — Nishant acknowledged.


alter session set NLS_DATE_FORMAT='DD-MON-YYYY HH24:mi:ss';
set lines 333
col TABLE_OWNER for a30
col TABLE_NAME for a30
SELECT TABLE_OWNER,TABLE_NAME,TIMESTAMP AS LAST_CHANGE
FROM DBA_TAB_MODIFICATIONS
where table_owner not like 'SYS%' and TIMESTAMP like '%SEP%25%' order by 3 ;



SELECT s.sid,
       s.serial#,
       s.username,
       s.machine,
       s.status,
       TO_CHAR(s.logon_time, 'YYYY-MM-DD HH24:MI:SS') AS logon_time,
       TO_CHAR(s.sql_exec_start, 'YYYY-MM-DD HH24:MI:SS') AS sql_exec_start
FROM   v$session s
WHERE  s.username IS NOT NULL
ORDER BY s.machine, s.status, s.logon_time DESC;






SELECT s.sid,
       s.serial#,
       s.username,
       s.machine,
       s.status,
       TO_CHAR(s.sql_exec_start, 'YYYY-MM-DD HH24:MI:SS') AS sql_start_time,
       q.sql_text
FROM   v$session s
JOIN   v$sql q
ON     s.sql_id = q.sql_id
WHERE  s.username IS NOT NULL
  AND  s.status = 'ACTIVE'
ORDER BY s.sql_exec_start DESC;




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
