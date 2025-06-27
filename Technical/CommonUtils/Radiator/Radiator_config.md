# Radiator Config Note
## Server Request Fail
- ReplyTimeout 5
	- Waiting 5 seconds for reponse every each request.
- Retries 0
	- When request timeout, it will try 0 times.
## Detected Server
- FailureBackoffTime 600
	- If a backend server is marked as failed, it will not send requests to the failed server for 600 seconds.
- MaxFailedRequests 3
	- If backend server is recorded 3 times no-reply, it will be mared as failed.
- MaxFailedGraceTime 60
	- Every 60 seconds will renew re-reply record, meaning backend server need to mared as failed 3 times in 60 seconds, then marked as failed.
- UseStatusServerForFailureDetect yes
	- Active to detect back end if it is alive or not.
- KeepaliveTimeout 10
	- Detect back end server per 10 seconds.