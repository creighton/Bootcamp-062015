# Reporting


## Searchable Properties in a Statement
The following table lists the properties of a statement that can be used to query the LRS. See the xAPI spec [for more details](https://github.com/adlnet/xAPI-Spec/blob/master/xAPI.md#stmtapiget).
<table>
  <thead>
    <tr><th>Property</th><th>GET Request Parameters</th></tr>
    <tr><th colspan=2>Example (not URL encoded)</th></tr>
  </thead>
  <tbody>
    <tr>
      <th>id</th><td>statementId</td>
    </tr>
    <tr>
      <td colspan=2>/statements?statementId=9847e454-6ae7-4d00-ba6b-04f209171de6</td>
    </tr>
    <tr>
      <th>actor</th><td>agent</td>
    </tr>
    <tr>
      <td colspan=2>/statements?agent={"mbox":"mailto:learner@example.com"}</td>
    </tr>
    <tr>
      <th>verb</th><td>verb</td>
    </tr>
    <tr>
      <td colspan=2>/statements?verb=http://adlnet.gov/expapi/verbs/experienced</td>
    </tr>
    <tr>
      <th>object<br>(when it is an Activity)</th><td>activity</td>
    </tr>
    <tr>
      <td colspan=2>/statements?activity=http://adlnet.gov/event/2015/xapibootcamp/guess-the-number</td>
    </tr>
    <tr>
      <th>object<br>(when it is an Agent or Group)</th><td>agent and related_agents</td>
    </tr>
    <tr>
      <td colspan=2>/statements?agent={"mbox":"mailto:learner@example.com"}&related_agents=true</td>
    </tr>
    <tr>
      <th>timestamp</th><td>since or until</td>
    </tr>
    <tr>
      <td colspan=2>/statements?since=2015-07-02T11:59:19.353Z</td>
    </tr>
    <tr>
      <th colspan=2>context properties</th>
    </tr>
    <tr>
      <th>registration</th><td>registration</td>
    </tr>
    <tr>
      <td colspan=2>/statements?registration=9bb3f7a2-91eb-44a4-ac18-761b11160292</td>
    </tr>
    <tr>
      <th>instructor<br>team</th><td>agent and related_agents</td>
    </tr>
    <tr>
      <td colspan=2>/statements?agent={"mbox":"mailto:learner@example.com"}&related_agents=true</td>
    </tr>
    <tr>
      <th>contextActivities</th><td>activity and related_activities</td>
    </tr>
    <tr>
      <td colspan=2>/statements?activity=http://adlnet.gov/event/2015/xapibootcamp&related_activities=true</td>
    </tr>
  <tbody>
</table>
