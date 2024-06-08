# Post-Mortem Report

## Issue Summary
On May 14th, 2024, my primary database experienced an unexpected outage that lasted for approximately 3 hours (from 11:00 AM to 2:00 PM GMT+1). During this time, most user requests resulted in 500 errors, with 100% of requests failing at the peak of the outage. The root cause was identified as a failed database update operation that left the database in an inconsistent state.

## Timeline (GMT+ 1)
- **11:00 AM**: Outage began
- **11:15 AM**: I was notified of the issue
- **11:30 AM**: Initial investigation began
- **12:00 PM**: Root cause identified
- **12:30 PM**: Recovery actions initiated
- **2:00 PM**: Service was fully restored

## Root Cause
The outage was caused by a failed database update operation. A script that was meant to update certain records in the database contained a bug that caused it to fail midway. This left the database in an inconsistent state, causing subsequent requests to the database to fail.

## Resolution and Recovery
Once the issue was identified, i rolled back the database to its previous state using a recent backup. This resolved the immediate issue and allowed services to be restored. The faulty update script was fixed and the update operation was successfully rerun at 1:30 PM. By 2:00 PM, all services were fully operational.

## Corrective and Preventive Measures
In response to this incident, i have taken the following corrective and preventive measures:
- Fixed the bug in the database update script.
- Improved our script testing procedures to catch such issues before they reach production.
- Implemented more frequent database backups to minimize potential data loss in the future.
- Planning to implement better monitoring and alerting systems to detect and notify us of such issues sooner.

In the future, i hope improve our incident response by ensuring that i should be more quickly aware of the incident and the recovery actions being taken. This will help in coordinate efforts to more effectively resolve incidents rapidly.

