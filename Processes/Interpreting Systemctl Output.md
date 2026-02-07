# Service Unit Information


| **Field** | **Description**                                                |
| --------- | -------------------------------------------------------------- |
| Loaded    | Whether the service is loaded into memory                      |
| Acive     | Whether the service is running                                 |
| Docs      | Where to find more information                                 |
| Main PID  | The main process ID of the service, including the command name |
| Status    | More information about the service                             |
| Process   | More information about the related processes                   |
| CGroup    | More information about the related control groups              |

---

# Service States 


| **Keyword**      | **Description**                                                                 |
| ---------------- | ------------------------------------------------------------------------------- |
| loaded           | The unit configuration is processed                                             |
| active (running) | The service is running with continuing processes                                |
| active (exited)  | The service completed a one-time configuration                                  |
| active (waiting) | The service is running but waiting for an event                                 |
| inactive         | The service is not running                                                      |
| enabled          | The service starts at boot time                                                 |
| disabled         | The service is not set to start at boot time                                    |
| static           | The service cannot be enabled, but an enabled unit might start it automatically |
