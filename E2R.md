# Event Retrospective Report (E2R) - 20260926 IRIT 03840

**Incident detail:** Repeated low-temperature alarms and pre-alarms on the cold aisle 4 probes of the B3/B4 data hall, with no identified trigger, resolved by raising the setpoints of the fanwall facing the aisle.

## Summary of the event

On 2026-09-26 the cold aisle 4 of the B3/B4 data hall went repeatedly below the lower SLA temperature limits. No fault, alarm on the surrounding assets or setpoint change was found before the first deviation, so the event was not triggered by a change.

The event developed in three phases:

- **Phase 1, 20:17 - 20:36:** the low-temperature pre-alarm on probe 32 became active at **20:17**. Probe 31, the only probe that reached the low-temperature alarm, went in alarm at **20:18** and stayed in alarm, with one short return to normal at 20:19, until 20:35.
- **Phase 2, 20:36 - 21:07:** probe 31 (alarm) and probe 32 (pre-alarm) alternated between active and normal several times.
- **Phase 3, 21:07 - 21:43:** probe 31 was in continuous alarm from **21:07** to **21:40**. From **21:20** the operator raised the setpoints of the fanwall B4.1 facing the aisle (and, to a lesser extent, of B4.2) with several BMS commands (see Attachment #2). MCIM records the final values: aisle temperature setpoint from 24 °C to 25 °C and minimum supply temperature from 15 °C to 16 °C. The last alarm cleared at **21:40** and the last pre-alarm at **21:43**, when all probes were back within limits.

Overall, the alarm on probe 31 was active for about 74 minutes in 13 intervals, with a minimum temperature of 18.2 °C, and the pre-alarm on probe 32 for about 80 minutes in 11 intervals.

The root cause is **under investigation**. The leading hypothesis is that, at the prevailing IT load, the fanwall B4.1 kept supplying air well below what the aisle required: the minimum supply temperature limit (15 °C) is 3.3 K below the alarm limit (18.3 °C) and the aisle setpoint (24 °C) is 5.7 K above it. This is supported by the recovery that followed the setpoint changes, but it is not proven: it requires the trends of supply temperature, airflow and valve position of the B4.x fanwalls and of the aisle probes. Free-cooling operation on four B3/B4 fanwalls at the time does not explain the event on its own, since two of them had been in free-cooling since the early evening without deviations.

## Impact Analysis

- **Bad Actor:** fanwall B4.1, facing cold aisle 4, whose minimum supply and aisle setpoints allowed the aisle to be overcooled (hypothesis, under investigation). The roof void is shared, so the other B3.x/B4.x fanwalls cannot be excluded.
- **Victims of the event:** cold aisle 4 of the B3/B4 data hall. Probe 31 in low-temperature alarm (below 18.3 °C) for about 74 minutes in 13 intervals between 20:18 and 21:41, the longest continuous interval being 32 minutes (21:07 - 21:40), with a minimum temperature of 18.2 °C. Probe 32 in low-temperature pre-alarm (below 19.3 °C) for about 80 minutes in 11 intervals between 20:17 and 21:43, without exceeding the alarm limit. Durations are taken from the BMS alarm log.
- **Deviation from normal operation:** pre-alarm limits 19.3 °C (low) and 25.7 °C (high), alarm limits 18.3 °C (low) and 26.7 °C (high). Aisle temperature setpoint 24 °C, minimum supply temperature 15 °C before the intervention.
- **Customer impact:** low. Only probe 31 went out of SLA, for about 74 minutes in total, with a minimum of 18.2 °C, 0.1 K below the 18.3 °C alarm limit. The most relevant aspect is the long time before the operator intervened (about 62 minutes after the first alarm).

## Event Timeline

The events reported are those considered most important to understand the dynamics of the incident, while the complete timeline of the area is in Attachment #1 (copy of the BMS events and alarms log, filtered to the B3/B4 and related assets).

- 2026-09-26 20:17 | Low-temperature pre-alarm active on probe 32, cold aisle 4
- 2026-09-26 20:18 | Low-temperature alarm active on probe 31, cold aisle 4 (first alarm)
- 2026-09-26 20:19 | Probe 31 returns to normal (20:19:14) and goes in alarm again (20:19:34)
- 2026-09-26 20:35 | Probe 31 returns to normal (20:35:54)
- 2026-09-26 20:36 | Probe 31 (alarm) and probe 32 (pre-alarm) start to alternate between active and normal
- 2026-09-26 21:06 | Probe 31 returns to normal (21:06:26), last return before the continuous alarm
- 2026-09-26 21:07 | Probe 31 goes in alarm (21:07:51), continuous alarm phase starts
- 2026-09-26 21:20 | First operator command on FW B4.1 (minimum supply temperature setpoint)
- 2026-09-26 21:24 | First operator command on the aisle temperature setpoint of FW B4.1
- 2026-09-26 21:33 | Operator adjusts the aisle temperature setpoint of FW B4.2 (again at 21:38)
- 2026-09-26 21:40 | Last return to normal of probe 31 (21:40:59), after a short alarm at 21:40:38
- 2026-09-26 21:42 | Last operator commands on the setpoints of FW B4.1
- 2026-09-26 21:43 | Probe 32 pre-alarm returns to normal (21:43:09), all probes back within limits

## Event Analysis & 5 Why

1. **How was the event detected (e.g. BMS alarm, site walkthrough, customer reported)?** By BMS: low-temperature pre-alarm on probe 32 at 20:17 and low-temperature alarm on probe 31 at 20:18.
2. **How could time to detection be improved/reduced?** The pre-alarm on probe 32 preceded the first alarm by about one minute and was followed by repeated pre-alarms, so detection was not the limiting factor: the pre-alarms were not treated as an actionable signal.
3. **Was the event triggered by a change? Was the scenario considered in the risk assessment?** No. No setpoint change or fault was found before the first deviation. The operator commands started at 21:20, after the event had begun.
4. **How was the event mitigated?** By raising the aisle temperature setpoint (24 °C to 25 °C) and the minimum supply temperature (15 °C to 16 °C) of the fanwall B4.1, through several BMS commands, with adjustments on B4.2. All probes were back within limits at 21:43.
5. **How could mitigation time be improved/reduced?** The first action came about 62 minutes after the first alarm. Acting on the pre-alarms and defining a response for low-temperature alarms in cold aisles would have shortened the event.
6. **How was the root cause diagnosed?** Not yet. The BMS events show no trigger and no fault, and the recovery followed the setpoint changes on B4.1. A full diagnosis needs the trends of the B4.x fanwalls and of the aisle probes, and is under investigation.

**5 Whys**

1. Why did the low-temperature alarm and pre-alarm occur? Because the air temperature in cold aisle 4 fell below 18.3 °C at probe 31 and below 19.3 °C at probe 32.
2. Why did the aisle fall below its limits? Because the fanwall facing the aisle (B4.1) supplied air colder than the aisle required, as suggested by the recovery after its setpoints were raised (hypothesis).
3. Why did the fanwall supply air that cold? Because its minimum supply temperature limit (15 °C) allowed supply air below the aisle alarm limit (18.3 °C), and the aisle setpoint (24 °C) did not reduce the cooling in time (under investigation).
4. Why did the condition last from 20:18 to 21:40? Because the low-temperature pre-alarms and alarms did not lead to a corrective action on the fanwall setpoints until 21:20.
5. Why did the fanwall control not reduce the cooling while the aisle was below setpoint? Under investigation: control logic and limits of the B4.x fanwalls, IT load and interaction with free-cooling operation.

## Lessons Learned (LL)

- LL1.03840: the low-temperature pre-alarms on the cold aisle probes were active from 20:17 and no corrective action was taken until 21:20, so a response to pre-alarms would have reduced the duration of the event.
- LL2.03840: with the minimum supply temperature and aisle setpoint in place, the fanwall B4.1 allowed cold aisle 4 to fall below the lower SLA limits at the prevailing load (under investigation).

## Action Items (AI)

- AI1.03840 (LL1.03840): define a response to low-temperature pre-alarms of the cold aisle probes (who checks, which fanwall setpoints and parameters to verify, and within what time) and verify that the pre-alarms are visible to the operators. Owner: TBD. Estimated date: TBD.
- AI2.03840 (LL2.03840): investigate why the fanwall B4.1 supplied air far below the aisle setpoint (control logic, minimum supply temperature limit, IT load, free-cooling interaction) and review the minimum supply temperature limit of the B3.x/B4.x fanwalls against the low-temperature alarm limit. Owner: TBD. Estimated date: TBD.

## Attachments

- Attachment #1: BMS events and alarms log, 2026-09-26, transcribed and filtered.
- Attachment #2: MCIM record and BMS command log of the setpoint changes on FW B4.1 (and B4.2).
- Attachment #3: MCIM screenshots and trends of probes 31 and 32 (minimum temperature of 18.2 °C) and of the B4.x fanwalls (to be added).
- Attachment #4: layout of the B3/B4 data hall with fanwalls and probes of cold aisle 4.
