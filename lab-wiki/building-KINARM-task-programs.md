# Building KINARM Task Programs #
----
## **File & Folder Organization** ##
- The folder containing all Matlab and DTP files must have the exact same name as the Simulink model. Use only underscores for the Simulink file names (using hyphens will cause an error)

- To see your task in Dexterit-E and test it on the Kinarm robot, your task folder must be in the 'Dexterit-E 3.11 Tasks' folder on the robot computer.

- Once a task/model is built in Matlab, the file (and therefore folder) name cannot be changed after the fact — renaming means creating a new folder, moving the Simulink model and DTP files into it, and rebuilding the model.

- Always make a backup before committing big changes via copy-and-paste task program into a new folder within the current task folder.
---
## **In-Progress vs. Final Tasks** ##
To keep the shared task folder on the robot computer from getting cluttered:
- While a task is in progress, name it:

```<Initials>-WIP-<TaskName>     ```

e.g. JD-WIP-Localization

- Once the task is finalized, drop the initials and "WIP" from the name.
- Move all previous/in-progress/backup versions into a folder within the finalized task folder
- Remember: renaming a task still requires creating a new folder and rebuilding the model
---
## **Naming Conventions** ##
These naming conventions are established to avoid mismatches (for example when using the create_csv script):

| **Category** | **Constant Name Format** |**Label Format** |
| ----------- |  :-----------: | :------------: |
| Targets/TP table  | UPPERCASE\_WITH_UNDERSCORES | UPPERCASE_WITH_UNDERSCORES |
| Events | E_UPPERCASE_WITH\_UNDERSCORES, prefixed with "E_"| UPPERCASE_WITH\_UNDERSCORES, same as constant name minus the "E_" prefix |
---
We also standardize a few commonly used variable names to help with readability and debugging. 

```{admonition} **See our current list of standardized variable names below:**

| **Item** | **Label** |**Constant Name** |
| ----------- |  :-----------: | :------------: |
| Home Position  | HOME | HOME |
| Goal Target | TARGET | TARGET |
|Start of Trial|TRIAL_START | E_TRIAL_START|
|Target Presentation|TARGET_ON|E_TARGET_ON|
|Movement Onset|MOVEMENT_ONSET|E_MOVEMENT_ONSET|
|Movement End|MOVEMENT_END|E_MOVEMENT_END|
|End of Trial|TRIAL_END| E_TRIAL_END|
```
---
##  ⚠️Considerations When Building⚠️
- **Emergency Stop:** Ensure the emergency stop button is readily accessible when testing new tasks! If you are messing with forces or loads, this is commonly where bad things may happen...

- **Feed-forward Estimate:** KINARM by default uses a feed-forward estimate (value of 0.02) for the display of hand feedback. If your study requires this removal, look into `Hand_Feedback` block by clicking the ↓ arrow, then click the bottom left lock to unlock the `FeedFwdArm` script, then set `feedfwd = 0` on line 32 and save.

---
## **Trial Structure — Stateflow & Simulink Conventions** ##
- Treat "return to home" as part of the next trial, not the ending of the current trial.

- Require participants to hold at the starting position for at least a few hundred milliseconds — this makes it much easier to distinguish target presentation from movement onset.

- Comment your blocks so it's clear which came from Kinarm by default versus which were added or modified by a lab member.

- Rename Simulink blocks and Stateflow states from their defaults — e.g., a "show target" block should clearly say whether it's showing a target, the home position, a cursor, etc. Use the standardized names in the list above such as "Target", "Home", "Cursor".

- Organize your Simulink by grouping blocks that work together to perform a function together through creating Subsystems and Areas. This makes reading your task program much easier in the future.

- Abstract as many variables as possible into the task protocol or task-wide parameters. Anything constant per trial (e.g., hold duration at start) belongs there — it makes debugging much easier since you won't need to rebuild the whole model to test a different parameter value.