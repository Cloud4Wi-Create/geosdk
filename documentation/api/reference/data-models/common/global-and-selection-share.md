# GlobalAndSelection-Shares

Name        |Type      | Description
------------|----------|------------
global | `Number` | Computed as ratio between the value assumed by the Specific Metric *M* (which the Object is associated to) for the specific Resource Segment and the value assumed by the same Metric if the no Selection Condition had been requested for the specific Dimension *D* (or all Selection Conditions for all Dimensions when associated to the Overall case) were not be requested; i.e., if the field `"select.<D>.<OP>"` (`"select"` for the Overall case) had not been provided or had been set to `null` or to an empty Object.
selection | `Number` | Computed as ratio between the value assumed by the Specific Metric *M* (which the Object is associated to) for the specific Resource Segment and the value assumed by the same Metric if no Segmentation had been requested for the specific Selection Condition on the specific Dimension *D* (or for all Selection Conditions on all Dimensions when associated to the Overall case); i.e, if the field `"segmentation.<D>.<OP>"` (`"select"` for the Overall case) had not been provided or had been set to `null` or to an empty Object.
