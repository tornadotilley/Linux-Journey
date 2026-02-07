
| **Command**              | **Task**                                                                        |
| ------------------------ | ------------------------------------------------------------------------------- |
| systemctl status *unit*  | View information about the unit's current state                                 |
| systemctl stop *unit*    | Stop a running service                                                          |
| systemctl start *unit*   | Start a service                                                                 |
| systemctl restart *unit* | Restart a running service                                                       |
| systemctl reload *unit*  | Reload the configuration of a running service                                   |
| systemctl mask *unit*    | Disable a service from being started                                            |
| systemctl unmask *unit*  | Make the service available again                                                |
| systemctl enable *unit*  | Configure a service to start at boot-time; use `--now` to start the service now |
| systemctl disable *unit* | Disable a service from starting at boot-time; use `--now` to stop the service   |
