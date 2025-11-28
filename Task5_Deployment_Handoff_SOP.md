# Task 5: Deployment Handoff SOP
## AMR Operations and Maintenance Guide for Tier 3 Warehouse

---

## Quick Reference Card - AMR Robot Operations

**Robot Model**: [Model Name]  
**Site**: [Warehouse Name]  
**Deployment Date**: [Date]  
**Support Contact**: [Phone/Email]  
**Emergency Contact**: [Phone]

---

## 1. Starting and Stopping the Robot

### Starting the Robot (Daily Operations)

**Before Starting:**
- [ ] Check charging station is connected to power (green light on)
- [ ] Verify robot is on charging station (charging indicator should be on)
- [ ] Check area around robot is clear (minimum 1.5m clearance)
- [ ] Ensure no obstructions in robot's path

**Starting Procedure:**
1. **Power On**: Press and hold the power button on robot for 3 seconds
2. **Wait for Boot**: Robot will display startup sequence (30-60 seconds)
3. **Check Status Lights**: 
   - Green = Ready
   - Yellow = Initializing
   - Red = Error (see troubleshooting section)
4. **Verify Network**: Check that robot shows "Connected" on display/interface
5. **Confirm Ready**: Robot is ready when status shows "Operational" or "Ready"

**Time Required**: 2-3 minutes

### Stopping the Robot Safely

**Normal Stop (End of Shift):**
1. **Complete Current Task**: Wait for robot to finish current task (if any)
2. **Return to Charging Station**: 
   - Use interface to send robot to charging station, OR
   - Press "Return to Charger" button on robot
3. **Wait for Docking**: Robot will automatically dock at charging station (1-2 minutes)
4. **Power Off**: Once docked and charging, press and hold power button for 3 seconds
5. **Verify Shutdown**: Status lights should turn off

**Emergency Stop:**
- **Immediate Stop**: Press the large RED emergency stop button on robot
- **What Happens**: Robot stops immediately, all movement halts
- **After Emergency Stop**:
  1. Assess the situation (why was emergency stop needed?)
  2. Clear any obstacles or hazards
  3. Release emergency stop (twist/pull to release)
  4. Manually return robot to charging station if needed
  5. Report incident to support team

**Time Required**: 3-5 minutes (normal), immediate (emergency)

---

## 2. Daily Health Check (Before Each Shift)

### Pre-Shift Checklist (5 minutes)

**Visual Inspection:**
- [ ] **Robot Body**: No visible damage, cracks, or loose parts
- [ ] **Wheels**: Properly inflated, no excessive wear, no debris stuck
- [ ] **Sensors**: LiDAR window clean and clear (no dirt, scratches)
- [ ] **Cables**: All cables secure, no fraying or damage
- [ ] **Charging Station**: Clean, properly mounted, power connected

**System Check:**
- [ ] **Battery Level**: Should be >80% (check on display/interface)
- [ ] **Network Connection**: Robot shows "Connected" status
- [ ] **Status Lights**: All showing normal (green/yellow, not red)
- [ ] **Error Messages**: No error codes displayed

**Operational Test:**
- [ ] **Test Movement**: Send robot on short test path (if possible)
- [ ] **Verify Navigation**: Robot should navigate smoothly without hesitation
- [ ] **Check Sensors**: Robot should detect obstacles (test by standing in path)

**If Any Issues Found:**
- Document the issue
- Refer to "Basic Error Recognition" section below
- Contact support if issue persists

---

## 3. Basic Error Recognition and Fault Conditions

### Common Status Indicators

**Status Light Colors:**
- 🟢 **Green (Solid)**: Robot is operational and ready
- 🟡 **Yellow (Blinking)**: Robot is initializing, charging, or processing
- 🔴 **Red (Solid)**: Error condition - requires attention
- 🔴 **Red (Blinking)**: Critical error - stop robot immediately

**Display/Interface Messages:**
- "Ready" / "Operational" = Normal operation
- "Charging" = Robot is charging (normal)
- "Navigating" = Robot is moving (normal)
- "Error" / "Fault" = Problem detected (see troubleshooting)

### Common Error Conditions

#### Error 1: "Low Battery" / Battery Warning
**Symptoms:**
- Battery level below 20%
- Robot automatically returns to charging station
- Yellow/red warning light

**What to Do:**
1. Allow robot to charge (2-3 hours for full charge)
2. Check charging station power connection
3. Verify robot is properly docked
4. If battery doesn't charge, contact support

**Can Continue Operations?** No - wait for charge

---

#### Error 2: "Network Disconnected" / "No Connection"
**Symptoms:**
- Robot shows "Disconnected" status
- Cannot receive tasks
- Yellow/red status light

**What to Do:**
1. Check Wi-Fi router/access point is powered on
2. Verify network credentials are correct (if changed)
3. Restart robot (power off, wait 30 seconds, power on)
4. If persists, contact IT support or robot support team

**Can Continue Operations?** Limited - robot may operate with reduced functionality

---

#### Error 3: "Localization Lost" / "Position Unknown"
**Symptoms:**
- Robot stops moving
- Error message about position/localization
- Robot may rotate in place trying to locate itself

**What to Do:**
1. Check for major changes in warehouse layout (new obstacles, moved racks)
2. Ensure robot is in mapped area (not in unmapped zone)
3. Manually drive robot to known location (if interface allows)
4. Restart robot
5. If persists, contact support (may need re-mapping)

**Can Continue Operations?** No - requires support

---

#### Error 4: "Path Blocked" / "Obstacle Detected"
**Symptoms:**
- Robot stops and cannot proceed
- Message about blocked path
- Robot may attempt to find alternative route

**What to Do:**
1. Check for obstacles in robot's path (pallets, people, equipment)
2. Clear the obstacle
3. Robot should automatically resume (wait 30 seconds)
4. If robot doesn't resume, manually send to next waypoint
5. If frequent, check for permanent obstacles that need to be mapped

**Can Continue Operations?** Usually yes - clear obstacle and continue

---

#### Error 5: "Sensor Error" / "LiDAR Error"
**Symptoms:**
- Red status light
- Error message about sensor
- Robot may not move or move erratically

**What to Do:**
1. Check LiDAR window is clean (wipe with soft cloth)
2. Check for physical damage to sensors
3. Restart robot
4. If persists, contact support immediately (hardware issue)

**Can Continue Operations?** No - requires support

---

#### Error 6: "Charging Failed" / "Docking Error"
**Symptoms:**
- Robot cannot dock at charging station
- Charging doesn't start
- Error message about charging

**What to Do:**
1. Check charging station power (green light should be on)
2. Ensure charging station area is clear
3. Manually position robot closer to charging station
4. Check charging contacts are clean (on robot and station)
5. Restart robot and retry docking
6. If persists, contact support

**Can Continue Operations?** Limited - robot will run on battery until depleted

---

#### Error 7: "Task Timeout" / "Path Timeout"
**Symptoms:**
- Robot stops mid-task
- Message about timeout
- Task may be cancelled

**What to Do:**
1. Check if path is blocked (see Error 4)
2. Check if robot is stuck (manually assist if needed)
3. Retry the task
4. If frequent, contact support (may indicate mapping or navigation issue)

**Can Continue Operations?** Usually yes - retry task

---

### When to Contact Support Immediately

Contact support **immediately** if:
- 🔴 Red blinking light (critical error)
- Robot makes unusual sounds (grinding, clicking)
- Smoke or burning smell
- Robot cannot be stopped (emergency stop not working)
- Physical damage to robot
- Safety incident occurred
- Multiple errors occurring simultaneously
- Robot has been non-functional for >1 hour

---

## 4. Reporting Issues - What Information to Provide

### When Calling Support

**Essential Information:**
1. **Robot ID/Serial Number**: [Found on robot label]
2. **Error Message**: Exact text from display/interface
3. **Status Light Color**: Green/Yellow/Red, Solid/Blinking
4. **When Did It Happen**: Date, time, what was robot doing?
5. **Can You Reproduce?**: Does it happen every time or randomly?

**Helpful Information:**
- Photos/videos of error (if safe to take)
- What you tried (restart, cleaning, etc.)
- Recent changes in warehouse (layout, obstacles)
- Battery level when error occurred
- Network status when error occurred

### Information to Have Ready

**Before Calling:**
- [ ] Robot ID/Serial Number
- [ ] Current error message (write it down)
- [ ] Status of lights/indicators
- [ ] Time of incident
- [ ] What task robot was performing
- [ ] Any recent changes in warehouse

**Support Will Ask:**
- "What error message do you see?"
- "What color is the status light?"
- "When did this start happening?"
- "Have you tried restarting the robot?"
- "Is the robot charging properly?"
- "Is the network connected?"

### Log Files to Collect (If Requested)

If support asks for logs:
1. **Access Robot Interface**: Log into robot's web interface or app
2. **Download Logs**: Look for "Download Logs" or "Export Data" option
3. **Send to Support**: Email logs to support team
4. **Note Time Range**: Include date/time range of issue

**Common Log Locations:**
- Robot web interface → Diagnostics → Download Logs
- Support app → Export Data
- USB drive (if robot has USB port for log export)

---

## 5. Safety Do's and Don'ts

### ✅ DO's - Safe Operations

**DO:**
- ✅ **Keep Clear Paths**: Maintain minimum 1.5m clearance for robot paths
- ✅ **Watch for Robot**: Be aware of robot location when working nearby
- ✅ **Use Emergency Stop**: If unsafe situation, use emergency stop immediately
- ✅ **Follow Procedures**: Always follow start/stop procedures
- ✅ **Report Issues**: Report any safety concerns immediately
- ✅ **Keep Sensors Clean**: Regularly clean LiDAR window and sensors
- ✅ **Respect Robot Zones**: Stay out of marked robot-only zones when possible
- ✅ **Train Staff**: Ensure all staff know basic robot safety

### ❌ DON'Ts - Safety Hazards

**DON'T:**
- ❌ **Don't Block Paths**: Never leave obstacles in robot paths
- ❌ **Don't Ride Robot**: Never attempt to ride or sit on robot
- ❌ **Don't Modify Robot**: Never open robot casing or modify hardware
- ❌ **Don't Disable Safety Sensors**: Never cover or disable safety sensors
- ❌ **Don't Force Movement**: Never manually push/pull robot (except emergency)
- ❌ **Don't Ignore Errors**: Never ignore error messages or warning lights
- ❌ **Don't Use Near Water**: Keep robot away from water, wet floors
- ❌ **Don't Overload**: Don't exceed robot's weight capacity
- ❌ **Don't Bypass Safety**: Never bypass safety systems or emergency stops

### Emergency Procedures

**If Robot Malfunctions:**
1. **Press Emergency Stop** (large red button)
2. **Assess Situation**: Is anyone in danger? Is there property damage?
3. **Clear Area**: Ensure area is safe
4. **Contact Support**: Call support immediately
5. **Document**: Take photos if safe, note what happened

**If Someone is Injured:**
1. **Press Emergency Stop** immediately
2. **Provide First Aid**: Follow first aid procedures
3. **Call Emergency Services**: If serious injury (ambulance: 108/102)
4. **Contact Support**: Notify support team immediately
5. **Do Not Move Robot**: Leave robot as-is until investigation

**Fire or Electrical Issue:**
1. **Press Emergency Stop**
2. **Disconnect Power**: Unplug charging station if safe
3. **Evacuate Area**: If fire, follow fire evacuation procedures
4. **Call Emergency Services**: Fire department if needed
5. **Contact Support**: Notify support team

---

## 6. Basic Maintenance Tasks

### Daily Maintenance (5 minutes)
- [ ] Clean LiDAR window (soft, dry cloth)
- [ ] Check wheels for debris
- [ ] Verify charging station is clean
- [ ] Check for visible damage

### Weekly Maintenance (15 minutes)
- [ ] Thorough cleaning of robot exterior
- [ ] Check wheel condition and inflation
- [ ] Inspect cables for damage
- [ ] Clean charging contacts (robot and station)
- [ ] Check for loose screws or parts

### Monthly Maintenance (30 minutes)
- [ ] Deep clean all sensors
- [ ] Check battery health (via interface)
- [ ] Review error logs for patterns
- [ ] Verify network connectivity
- [ ] Test emergency stop functionality
- [ ] Contact support for preventive maintenance (if scheduled)

**Note**: For major maintenance or repairs, always contact support team. Do not attempt to repair hardware yourself.

---

## 7. Quick Troubleshooting Guide

| Problem | Quick Check | Solution |
|---------|-------------|----------|
| Robot won't start | Power connected? | Check power, restart |
| Robot stops moving | Obstacle in path? | Clear obstacle, wait 30 sec |
| Low battery warning | Charging station working? | Ensure proper docking |
| Network disconnected | Wi-Fi working? | Restart robot, check network |
| Error message | What does it say? | Refer to error section above |
| Robot won't dock | Area clear? | Clear area, retry docking |
| Unusual sounds | Physical damage? | Stop robot, contact support |

---

## 8. Contact Information

### Support Contacts

**Technical Support:**
- **Phone**: [Support Phone Number]
- **Email**: [Support Email]
- **Hours**: [Support Hours, e.g., 9 AM - 6 PM, Mon-Fri]
- **Emergency**: [24/7 Emergency Number]

**On-Site Contact:**
- **Name**: [Local Contact Name]
- **Phone**: [Local Contact Phone]

**Management Escalation:**
- **Phone**: [Management Contact]
- **Email**: [Management Email]

### When to Call Each Contact

**Technical Support**: For all robot issues, errors, questions
**On-Site Contact**: For site access, coordination, local issues
**Management**: For critical issues, escalations, major problems

---

## 9. Additional Resources

### Documentation Available
- Full user manual (digital copy)
- Video tutorials (if available)
- FAQ document
- Troubleshooting guide (detailed)

### Training Materials
- Operations training video
- Safety training materials
- Basic troubleshooting guide

**Note**: Request these from support team if not already provided.

---

## 10. Important Notes

### Key Reminders
- ⚠️ **Always use emergency stop** if unsafe situation
- ⚠️ **Never ignore error messages** - they indicate real problems
- ⚠️ **Keep paths clear** - obstacles cause delays and errors
- ⚠️ **Regular cleaning** prevents many issues
- ⚠️ **Contact support** if unsure - better safe than sorry

### Updates and Changes
- This SOP may be updated as needed
- Check with support team for latest version
- Notify support if you notice issues not covered in this guide

---

## Document Information

**Version**: 1.0  
**Date**: [Deployment Date]  
**Prepared By**: [Deployment Technician]  
**For**: [Client Name] - [Warehouse Location]  
**Next Review**: [Date - recommend 3 months]

---

**Remember**: When in doubt, contact support. It's better to ask than to risk damage or safety issues.

**Safety First, Always!**

