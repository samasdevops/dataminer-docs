---
uid: Cube_Feature_Release_10.3.12
---

# DataMiner Cube Feature Release 10.3.12 – Preview

> [!IMPORTANT]
> We are still working on this release. Some release notes may still be modified or moved to a later release. Check back soon for updates!

> [!TIP]
> For release notes for this release that are not related to DataMiner Cube, see [General Feature Release 10.3.12](xref:General_Feature_Release_10.3.12).

## Highlights

*No highlights have been selected yet.*

## New features

#### Alarm templates: Configuration of behavioral anomaly alarms [ID_37148] [ID_37171]

<!-- MR 10.2.0 [CU21]/10.3.0 [CU9] - FR 10.3.12 -->

Up to now, the behavioral anomaly detection feature only allowed users to have alarms generated instead of suggestion events, depending on the parameter and the type of anomaly. From now on, when configuring an alarm template, users will have more options to specify what should happen when behavioral anomalies are detected.

For example, it is now possible to make a distinction between upward and downward behavioral changes (e.g. an upward spike or a downward spike). For example, you can request to have alarms only for upward level shifts and not for downward level shifts. However, in that case, it would still be possible to have suggestions for downward level shifts. Also, you can now fine-tune and decide to have an upward level shift alarm only when the level shift rises more than 10 (i.e. an absolute threshold of 10) or more than 10 percent of the current value (i.e. a relative threshold of 10).

To configure the behavioral anomaly detection for a particular (numeric) parameter, do the following:

1. Open the alarm template in the *Protocols & Templates* app.
1. In the right-most column of the parameter in question, click the *Anomalies* button to open the *Anomaly alarm settings* window.
1. In the *Anomaly alarm settings* window, open the *Select preset* selection box, and select one of the following options:

   - "All disabled" (i.e. no anomaly monitoring)
   - "All smart" (i.e. anomaly monitoring as it existed up to now)

1. Below the selection box, if necessary, you can fine-tune the configuration by specifying how anomaly monitoring should react to anomalies of type level shift, outlier, variance change, trend change and/or flatline.

1. Click *Close* to exit the *Anomaly alarm settings* window.

   > [!IMPORTANT]
   > Closing this window does not yet save the changes you made in this window.

1. Back in the alarm template editor, click *OK* or *Apply* to save the changes you made.

   > [!NOTE]
   > The *Anomalies* button in the right-most column of the parameter in question will indicate the level of anomaly monitoring that has been configured:
   >
   > - "Disabled" (i.e. no anomaly monitoring)
   > - "Customized" (i.e. the new customized anomaly monitoring)
   > - "Smart" (i.e. anomaly monitoring as it existed up to now).

> [!NOTE]
> It is not possible to have both a suggestion event and an alarm generated for the same issue. However, it is possible to have suggestion events generated for e.g. downward spikes, even if downward spikes are disabled in the *Anomaly alarm settings* window.

## Changes

### Enhancements

#### Trending: All trend patterns will now be loaded when you open a trend graph showing data from several parameters [ID_36661]

<!-- MR 10.2.0 [CU21]/10.3.0 [CU9] - FR 10.3.12 -->

Up to now, when you opened a trend graph showing data from several parameters, only the trend patterns of the first parameter would be loaded onto the graph. From now on, the trend patterns of all parameters shown on the graph will be loaded.

The SLAnalytics feature "pattern matching" has now fully been integrated in the Trending module.

#### System Center: New rule with regard to adding agents to a cluster [ID_37075]

<!-- MR 10.2.0 [CU21]/10.3.0 [CU9] - FR 10.3.12 -->

Up to now, it was possible to have a DataMiner System in which some DMAs had been added by IP address while other DMAs had been added by hostname. As this could potentially lead to problems, especially in DataMiner Systems that include Failover pairs, the following rule has now been introduced:

- If the cluster includes any Failover pairs with shared hostname or any DMA with a hostname in its *IP address* field:

  - Allowed to add DMAs either by hostname or by IP address.
  - Allowed to create Failover pairs with shared hostname only.

- If the cluster includes any Failover pairs with virtual IP addresses:

  - Allowed to add DMAs IP address only.
  - Allowed to create Failover pairs with virtual IP addresses only.

- In all other cases:

  - Allowed to add DMAs either by hostname or by IP address.
  - Allowed to create Failover pairs with shared hostname or with virtual IP addresses.

#### Interactive Automation scripts: FileSelector now allows to keep the files that were already uploaded after the UI was shown [ID_37260]

<!-- MR 10.3.0 [CU9] - FR 10.3.12 -->

Unlike other UI block types, *FileSelector* does not allow setting an [InitialValue](xref:Skyline.DataMiner.Automation.UIBlockDefinition#Skyline_DataMiner_Automation_UIBlockDefinition_InitialValue). However, from now on, during an interactive Automation script session, it is possible to keep the files that were already uploaded after the UI was shown.

When an interactive Automation script is executed **in Cube**, the UI block needs to keep the same [DestVar](xref:Skyline.DataMiner.Automation.UIBlockDefinition#Skyline_DataMiner_Automation_UIBlockDefinition_DestVar) within the session. If there is no file selector block with the same [DestVar](xref:Skyline.DataMiner.Automation.UIBlockDefinition#Skyline_DataMiner_Automation_UIBlockDefinition_DestVar) when the UI is shown again, the information about the uploaded files is lost.

See also [DataMiner web apps Feature Release 10.3.12](xref:Web_apps_Feature_Release_10.3.12#interactive-automation-scripts-fileselector-now-allows-to-keep-the-files-that-were-already-uploaded-after-the-ui-was-shown-id_37260)

#### Alarm Console: Button to show focused alarms now shows the number of focused alarms [ID_37455]

<!-- MR 10.2.0 [CU21]/10.3.0 [CU9] - FR 10.3.12 -->

From now on, the button to only show the focused alarms in the current alarm tab will show the number of focused alarms in the current alarm tab and will only be visible when the alarm tab actually contains focused alarms.

#### Surveyor: Enhanced processing of alarm statistics [ID_37552]

<!-- MR 10.2.0 [CU21]/10.3.0 [CU9] - FR 10.3.12 -->

In the Surveyor, statistical alarm data can be displayed next to elements, services and views. A number of enhancements have now been made to enhance the processing of those alarm statistics.

#### Caching enhancements [ID_37553]

<!-- MR 10.2.0 [CU21]/10.3.0 [CU9] - FR 10.3.12 -->

A number of general enhancements have been made with regard to cache management.

### Fixes

#### Trending: Trend graph would disappear when panning [ID_37453]

<!-- MR 10.4.0 - FR 10.3.12 -->

When you panned a trend graph, in some cases, the graph would suddenly disappear.

> [!NOTE]
> From now on, trending errors will also be logged in the main Cube logging (*System Center > Logging*).

#### Alarm Console: Alarm tab filter would not be re-evaluated when the focus score of an alarm was updated [ID_37475]

<!-- MR 10.2.0 [CU21]/10.3.0 [CU9] - FR 10.3.12 -->

When an alarm in a filtered alarm tab received a focus score update, the system would incorrectly not re-evaluate whether that alarm still matched the filter that was applied.

#### Alarm Console: Display issues when a correlation alarm was based on another correlation alarm [ID_37497]

<!-- MR 10.2.0 [CU21]/10.3.0 [CU9] - FR 10.3.12 -->

When a correlation rule was based on another correlation rule, display issues could occur in the Alarm Console.

When the main correlation alarm got cleared, the base alarm would no longer be shown in the alarm tab, and when the base alarm got updated, it would be shown twice: once as the source of the other correlation alarm and once as a regular alarm.

#### Problem when trying to display broadcast messages while being used as a service [ID_37524]

<!-- MR 10.2.0 [CU21]/10.3.0 [CU9] - FR 10.3.12 -->

When Cube tried to display a broadcast message it had received from the DataMiner Agent while being used as a service by SLHelper, an error could occur in the latter.

From now on, Cube will disregard broadcast messages while being used as a service (e.g. when displaying a visual overview on a mobile device).

#### Spectrum Analysis: Problem when making changes to a spectrum monitor [ID_37542]

<!-- MR 10.2.0 [CU21]/10.3.0 [CU9] - FR 10.3.12 -->

When you create a spectrum monitor, you can define a parameter and select a number of measurement points. Each combination of a parameter and a measurement point then is assigned an ID.

Up to now, when you made a change to a spectrum monitor, in some cases, the ID of certain parameter/measurement point combinations could change even when the parameter or the measurement points had not been changed.

#### Alarm Console: Problem when changing the alignment of an alarm property column [ID_37574]

<!-- MR 10.2.0 [CU21]/10.3.0 [CU9] - FR 10.3.12 -->

When, in the Alarm Console, you add a column showing an alarm property you are allowed to edit, all cells in that column will display a pencil icon you can click to update a particular value.

Up to now, when you changed the alignment of such a column, the pencil icons would disappear and the new alignment would not be applied. From now on, when you change the alignment of a column showing an alarm property you are allowed to edit, the new alignment will be applied correctly and the pencil icons will stay visible. However, regardless of the alignment, the pencil icons will stay on the left, and when you change a value, the text box will also be aligned to the left.

#### Alarm Console: Text-to-speech button would overlap the counter showing the number of alarms with severity 'Suggestion' [ID_37590]

<!-- MR 10.2.0 [CU21]/10.3.0 [CU9] - FR 10.3.12 -->

In the footer of the Alarm Console, the button to cancel the current text-to-speech operation would overlap the counter showing the number of alarms with severity "Suggestion" in the current alarm tab.

#### Alarm Console: Focus score would not be updated correctly when an alarm was duplicated [ID_37600]

<!-- MR 10.2.0 [CU21]/10.3.0 [CU9] - FR 10.3.12 -->

When, in the Alarm Console, an alarm was duplicated, in some cases, its focus score would not be updated correctly.
