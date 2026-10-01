| Controller tag | Data type | Initial value | Why this value is used |
|---|---|---|---|
| `Fault_High` | BOOL | `0` (False) | No high-level fault is indicated initially. The logic activates it when tank level reaches 95 or higher. |
| `Fault_Low` | BOOL | `0` (False) | No low-level fault is indicated initially. The logic activates it when tank level reaches 5 or lower. |
| `Fault_Reset` | BOOL | `0` (False) | No fault-reset request is active at startup. **The provided reset logic uses `Master_Reset` instead.** |
| `Master_Reset` | BOOL | `0` (False) | Prevents an automatic reset request at startup. The HMI RESET button activates this tag. |
| `Motor_Run` | BOOL | `0` (False) | Starts with no motor-run request. **The shown MainRoutine controls the VFD start tag directly, so this tag is not used there.** |
| `Start_PB` | BOOL | `0` (False) | Represents an unpressed START button, preventing a startup command. |
| `Stop_PB` | BOOL | `0` (False) | Represents an unpressed STOP button. A value of 0 means no stop request; it does not mean the system is running. |
| `System_Fault` | BOOL | `0` (False) | Starts without a latched system fault. Either level fault can latch it during operation. |
| `System_Running` | BOOL | `0` (False) | Keeps the process from starting until a valid START command is received. |
| `System_Stopped` | BOOL | `0` (False) | This is the specified initialization value. **The PLC sets it to 1 when it evaluates that the system is neither running nor faulted.** |
| `Warn_High` | BOOL | `0` (False) | No high warning is needed at the initial level of 50. It activates for levels from 80 up to, but not including, 95. |
| `Warn_Low` | BOOL | `0` (False) | No low warning is needed at the initial level of 50. It activates for levels above 5 through 20. |
| `DepletionRate_SP` | REAL | `50.0` | Provides the initial draining setpoint. With `k_drain = 0.05`, it produces a depletion rate of 2.5 level units/s while the simulation runs. |
| `dt` | REAL | `0.1` | Matches the periodic task’s 100 ms execution interval, expressed in seconds. |
| `FillSpeed_SP` | REAL | `500.0` | Provides the initial filling setpoint and the value used to generate the VFD command. With `k_fill = 0.00083`, it produces 0.415 level units/s of simulated inflow. |
| `HighFault_Limit` | REAL | `95.0` | Stops the process near the full-tank limit, before the simulated level reaches 100. |
| `HighWarn_Limit` | REAL | `80.0` | Gives an early warning before the high-fault threshold is reached. |
| `k_drain` | REAL | `0.05` | Scales the depletion setpoint into a simulated level decrease per second. |
| `k_fill` | REAL | `0.00083` | Scales the fill-speed setpoint into a simulated level increase per second. |
| `LowFault_Limit` | REAL | `5.0` | Stops the process near the empty-tank limit, before the simulated level reaches 0. |
| `LowWarn_Limit` | REAL | `20.0` | Gives an early warning before the low-fault threshold is reached. |
| `Tank_Level` | REAL | `50.0` | Starts the tank halfway full, away from both warning and fault limits. |
| `Tank_Level_Temp` | REAL | `50.0` | Matches the initial tank level so the temporary calculation value is consistent with the starting condition. |
| `Status` | STRING | Blank (`""`) | Starts without status text. `StatusRoutine` writes “Running,” “Stopped,” or “Faulted” when it executes. |
