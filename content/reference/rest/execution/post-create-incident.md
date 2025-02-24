---

title: "Create Incident"
weight: 40

menu:
  main:
    name: "Create Incident"
    identifier: "rest-api-execution-post-create-incident"
    parent: "rest-api-execution"
    pre: "POST `/execution/{id}/create-incident`"

---


Creates a custom incident with given properties.


# Method

POST `/execution/{id}/create-incident`


# Parameters

## Path Parameters

<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>id</td>
    <td>The id of the execution to create a new incident for.</td>
  </tr>
</table>

## Request Body

A JSON object with the following properties:

<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>incidentType</td>
    <td>A type of the new incident.</td>
  </tr>
  <tr>
    <td>configuration</td>
    <td>A configuration for the new incident.</td>
  </tr>
  <tr>
    <td>message</td>
    <td>A message for the new incident.</td>
  </tr>
  
</table>


# Result

A JSON object that represents an incident object with the following properties:

<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>id</td>
    <td>String</td>
    <td>The id of the incident.</td>
  </tr>
  <tr>
    <td>processDefinitionId</td>
    <td>String</td>
    <td>The id of the process definition this incident is associated with.</td>
  </tr>
  <tr>
    <td>processInstanceId</td>
    <td>String</td>
    <td>The id of the process instance this incident is associated with.</td>
  </tr>
  <tr>
    <td>executionId</td>
    <td>String</td>
    <td>The id of the execution this incident is associated with.</td>
  </tr>
  <tr>
    <td>incidentTimestamp</td>
    <td>String</td>
    <td>The time this incident happened. Default format* <code>yyyy-MM-dd'T'HH:mm:ss.SSSZ</code>.</td>
  </tr>
  <tr>
    <td>incidentType</td>
    <td>String</td>
    <td>The type of incident.</td>
  </tr>
  <tr>
    <td>activityId</td>
    <td>String</td>
    <td>The id of the activity this incident is associated with.</td>
  </tr>
  <tr>
    <td>failedActivityId</td>
    <td>String</td>
    <td>The id of the activity on which the last exception occurred.</td>
  </tr>
  <tr>
    <td>causeIncidentId</td>
    <td>String</td>
    <td>The id of the associated cause incident which has been triggered.</td>
  </tr>
  <tr>
    <td>rootCauseIncidentId</td>
    <td>String</td>
    <td>The id of the associated root cause incident which has been triggered.</td>
  </tr>
  <tr>
    <td>configuration</td>
    <td>String</td>
    <td>The payload of this incident.</td>
  </tr>
  <tr>
    <td>tenantId</td>
    <td>String</td>
    <td>The id of the tenant this incident is associated with.</td>
  </tr>
  <tr>
    <td>incidentMessage</td>
    <td>String</td>
    <td>The message of this incident.</td>
  </tr>
  <tr>
    <td>jobDefinitionId</td>
    <td>String</td>
    <td>The job definition id the incident is associated with.</td>
  </tr>
</table>

\* For further information, please see the <a href="{{< ref "/reference/rest/overview/date-format.md" >}}"> documentation</a>.

# Response Codes

<table class="table table-striped">
  <tr>
    <th>Code</th>
    <th>Media type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>200</td>
    <td>application/json</td>
    <td>Request successful.</td>
  </tr>
  <tr>
    <td>400</td>
    <td>application/json</td>
    <td>Returned if the incident type is null, the execution does not exist or the execution is not related to any activity.</td>
  </tr>
</table>


# Example

## Request

POST `/execution/anExecutionId/create-incident`

Request Body:

    {
      "incidentType" : "aType",
      "configuration" : "aConfiguration"
    }

## Response

Status 200.

```json
  {
    "id": "anIncidentId",
    "processDefinitionId": "aProcDefId",
    "processInstanceId": "aProcInstId",
    "executionId": "anExecutionId",
    "incidentTimestamp": "2014-03-01T08:00:00.000+0200",
    "incidentType": "failedJob",
    "activityId": "serviceTask",
    "failedActivityId": "serviceTask",
    "causeIncidentId": "aCauseIncidentId",
    "rootCauseIncidentId": "aRootCauseIncidentId",
    "configuration": "aConfiguration",
    "tenantId": null,
    "incidentMessage": "anIncidentMessage",
    "jobDefinitionId": "aJobDefinitionId"
  }
```
