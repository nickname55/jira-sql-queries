# jira-sql-queries

## get list of issues which is linked to EPIC
```sql
SELECT li.summary AS ISSUES_IN_EPIC,
       I.ID AS EPIC_ID
FROM JIRAISSUE I
INNER JOIN ISSUELINK IL ON IL.SOURCE = I.ID
INNER JOIN ISSUELINKTYPE ILT ON ILT.ID = IL.LINKTYPE
INNER JOIN JIRAISSUE LI ON LI.ID = IL.DESTINATION
INNER JOIN PROJECT PJ ON PJ.ID = I.PROJECT
INNER JOIN ISSUETYPE IT ON IT.ID = I.ISSUETYPE
WHERE IT.PNAME = 'Epic' 
--epic id
AND I.id = 10030
```
