# Task 4: Real-World Debug Report – AMR Issue Diagnosis
## Post-Deployment AMR Path Completion Failure

---

## Executive Summary

**Issue**: One AMR occasionally fails to complete its path. It starts slowing near intersections and times out. Logs show inconsistent LiDAR readings and repeated stop-starts near reflective surfaces. No error codes are raised.

**Robot ID**: [Robot Serial Number]  
**Site**: [Client Warehouse Location]  
**Report Date**: [Current Date]  
**Reported By**: [Field Technician Name]  
**Severity**: Medium (affects task completion reliability)

---

## 1. Likely Causes of This Behavior

### 1.1 Primary Suspect: LiDAR Sensor Issues with Reflective Surfaces

**Description**: LiDAR sensors are highly sensitive to reflective surfaces (mirrors, polished floors, glass, metal surfaces). When LiDAR beams hit reflective surfaces, they can:
- Return false readings (ghost obstacles)
- Fail to return (no reading)
- Return from multiple reflections (ambiguous readings)

**Why This Matches Symptoms:**
- **Inconsistent LiDAR readings**: Reflective surfaces cause unpredictable sensor behavior
- **Slowdown near intersections**: Intersections often have multiple reflective surfaces (signs, equipment, floors)
- **Stop-starts**: Robot detects false obstacles, stops, re-plans, moves, detects again (loop)
- **Timeouts**: Robot spends too much time in stop-start cycle, exceeds path timeout
- **No error codes**: System interprets false readings as real obstacles (not a system error)

**Likelihood**: **Very High (80-90%)**

### 1.2 Secondary Suspect: Localization Degradation Near Reflective Surfaces

**Description**: Reflective surfaces can interfere with LiDAR-based localization, causing the robot to lose confidence in its position estimate.

**Why This Matches Symptoms:**
- **Slowdown near intersections**: Robot slows to improve localization accuracy
- **Inconsistent readings**: Localization algorithm struggles with ambiguous sensor data
- **Timeouts**: Low localization confidence triggers safety behaviors (slowing, stopping)

**Likelihood**: **Medium-High (60-70%)**

### 1.3 Other Potential Causes

#### 1.3.1 Dynamic Obstacle Map Corruption
- **Description**: Costmap incorrectly marks reflective surfaces as obstacles
- **Likelihood**: Medium (40-50%)
- **Symptoms Match**: Yes (stop-starts, timeouts)

#### 1.3.2 Path Planning Algorithm Issues
- **Description**: Planner generates paths too close to reflective surfaces
- **Likelihood**: Medium (30-40%)
- **Symptoms Match**: Partial (explains slowdown, but not inconsistent readings)

#### 1.3.3 Safety Sensor Over-Sensitivity
- **Description**: Safety LiDAR triggers false positives on reflective surfaces
- **Likelihood**: Medium (40-50%)
- **Symptoms Match**: Yes (stop-starts, slowdowns)

#### 1.3.4 Environmental Lighting Changes
- **Description**: Variable lighting affects camera-based obstacle detection (if used)
- **Likelihood**: Low-Medium (20-30%)
- **Symptoms Match**: Partial (doesn't explain LiDAR inconsistencies)

---

## 2. Step-by-Step On-Site Diagnostic Procedure

### Phase 1: Immediate Visual Inspection (15 minutes)

**Step 1: Identify Reflective Surfaces**
- [ ] Walk the problematic path (especially intersections)
- [ ] Identify all reflective surfaces:
  - Mirrors or reflective signs
  - Polished or wet floors
  - Glass windows or doors
  - Metal equipment or surfaces (forklifts, racks, machinery)
  - Shiny painted surfaces
- [ ] Document locations with photos
- [ ] Note proximity to robot path

**Step 2: Check Robot Physical Condition**
- [ ] Inspect LiDAR sensor window (clean, no damage)
- [ ] Check LiDAR mounting (secure, no vibration)
- [ ] Verify robot is level (no tilt affecting LiDAR angle)
- [ ] Check for physical damage

**Step 3: Review Recent Logs**
- [ ] Check for patterns in stop-start locations
- [ ] Correlate with reflective surface locations
- [ ] Note timing of incidents

### Phase 2: Sensor Data Collection (30-45 minutes)

**Step 4: Enable Enhanced Logging**
```bash
# Enable debug logging
rosbag record /scan /amcl_pose /move_base/status /cmd_vel /odom
```

**Step 5: Test Run on Problematic Path**
- [ ] Run robot on path that typically fails
- [ ] Monitor in real-time:
  - LiDAR scan visualization (RViz or similar)
  - Localization confidence
  - Obstacle detection
  - Path planning decisions
- [ ] Document exact locations where slowdowns occur
- [ ] Note behavior at each reflective surface

**Step 6: Static LiDAR Scan Test**
- [ ] Position robot near known reflective surface
- [ ] Take static LiDAR scan
- [ ] Analyze point cloud:
  - Look for ghost points (false obstacles)
  - Check for missing data (no returns)
  - Identify ambiguous readings
- [ ] Compare with non-reflective surface scan

**Step 7: Compare Normal vs. Problematic Areas**
- [ ] Test robot in area without reflective surfaces (baseline)
- [ ] Test robot in area with reflective surfaces
- [ ] Compare:
  - LiDAR scan quality
  - Localization confidence
  - Navigation behavior

### Phase 3: Configuration and Parameter Check (20 minutes)

**Step 8: Review Navigation Parameters**
- [ ] Check costmap inflation radius (may be too large)
- [ ] Review obstacle detection thresholds
- [ ] Verify safety margins
- [ ] Check path planning parameters (clearance from obstacles)

**Step 9: Check LiDAR Filtering Settings**
- [ ] Review LiDAR noise filtering parameters
- [ ] Check for reflective surface filtering (if available)
- [ ] Verify scan angle limits
- [ ] Check range limits

**Step 10: Localization Parameter Review**
- [ ] Check AMCL parameters (particle count, update frequency)
- [ ] Review localization recovery behaviors
- [ ] Verify map-robot matching tolerance

### Phase 4: Reproducibility Testing (30 minutes)

**Step 11: Attempt to Reproduce Issue**
- [ ] Run robot multiple times on same path
- [ ] Document:
  - Frequency of issue
  - Exact locations
  - Conditions (lighting, traffic, time of day)
- [ ] Note if issue is consistent or intermittent

**Step 12: Test Under Different Conditions**
- [ ] Test at different times of day (lighting changes)
- [ ] Test with different floor conditions (dry vs. wet)
- [ ] Test with varying traffic (people, equipment)
- [ ] Document conditions when issue occurs/doesn't occur

---

## 3. Data Collection for Backend/Dev Team

### 3.1 Essential Data to Collect

#### 3.1.1 LiDAR Scan Data
**What to Collect:**
- Raw LiDAR point clouds from problematic areas
- Point clouds from normal areas (for comparison)
- Multiple scans at same location (to show inconsistency)

**How to Collect:**
```bash
# Record LiDAR scans
rosbag record /scan -O lidar_problematic_areas.bag

# Record for 5-10 minutes while robot navigates problematic path
```

**What to Look For:**
- Ghost points (false obstacles from reflections)
- Missing data (no returns from reflective surfaces)
- Inconsistent readings (varying point clouds at same location)
- Range anomalies (unexpectedly close/far readings)

#### 3.1.2 Navigation Stack Data
**What to Collect:**
- Localization pose and confidence (`/amcl_pose`)
- Navigation status (`/move_base/status`)
- Velocity commands (`/cmd_vel`)
- Odometry data (`/odom`)
- Costmap data (`/move_base/global_costmap`, `/move_base/local_costmap`)

**How to Collect:**
```bash
# Record navigation data
rosbag record /amcl_pose /move_base/status /cmd_vel /odom \
  /move_base/global_costmap /move_base/local_costmap \
  -O navigation_data.bag
```

**What to Look For:**
- Localization confidence drops near reflective surfaces
- Costmap showing false obstacles
- Velocity commands showing stop-start pattern
- Path planning failures or recalculations

#### 3.1.3 System Diagnostics
**What to Collect:**
- System diagnostics (`/diagnostics`)
- CPU and memory usage
- Network connectivity
- Sensor health status

**How to Collect:**
```bash
# Record diagnostics
rosbag record /diagnostics -O system_diagnostics.bag

# System resource monitoring
top -b -n 1 > system_resources.txt
```

#### 3.1.4 Environmental Data
**What to Collect:**
- Photos/videos of reflective surfaces
- Floor plan with marked problematic areas
- Lighting conditions (lux measurements if possible)
- Environmental notes (time of day, traffic, etc.)

### 3.2 Data Package Structure

```
debug_data_package/
├── lidar_data/
│   ├── problematic_area_scans.bag
│   ├── normal_area_scans.bag
│   └── static_scan_comparison.bag
├── navigation_data/
│   ├── navigation_logs.bag
│   └── costmap_snapshots/
│       ├── costmap_before_intersection.png
│       └── costmap_at_intersection.png
├── system_data/
│   ├── system_diagnostics.bag
│   ├── system_resources.txt
│   └── error_logs.log
├── environmental_data/
│   ├── reflective_surfaces_photos/
│   │   ├── intersection_1_mirror.jpg
│   │   ├── intersection_2_polished_floor.jpg
│   │   └── intersection_3_metal_equipment.jpg
│   ├── floor_plan_annotated.pdf
│   └── environmental_conditions.json
├── metadata/
│   ├── incident_timeline.json
│   ├── test_conditions.json
│   └── robot_configuration.json
└── README.txt
```

### 3.3 Metadata Files

**incident_timeline.json:**
```json
{
  "incidents": [
    {
      "timestamp": "2024-01-15T14:32:15Z",
      "location": "Intersection A-B",
      "behavior": "Slowdown, then timeout",
      "duration": 45.2,
      "recovery": "Manual intervention"
    },
    {
      "timestamp": "2024-01-15T15:18:42Z",
      "location": "Intersection C-D",
      "behavior": "Stop-start cycle, timeout",
      "duration": 62.8,
      "recovery": "Automatic (after timeout)"
    }
  ]
}
```

**test_conditions.json:**
```json
{
  "robot_id": "AMR-003",
  "firmware_version": "2.3.1",
  "software_version": "ROS Noetic, Navigation Stack 1.17",
  "test_date": "2024-01-15",
  "test_duration": "2.5 hours",
  "environmental_conditions": {
    "lighting": "Artificial + Natural (windows)",
    "floor_condition": "Dry, polished concrete",
    "temperature": 22.5,
    "traffic_level": "Medium"
  },
  "problematic_areas": [
    {
      "name": "Intersection A-B",
      "reflective_surfaces": ["Polished floor", "Metal rack", "Window"],
      "issue_frequency": "70% of passes"
    }
  ]
}
```

**robot_configuration.json:**
```json
{
  "lidar_settings": {
    "model": "RPLidar A3",
    "scan_frequency": 10,
    "range_max": 25.0,
    "range_min": 0.12,
    "angle_min": -3.14159,
    "angle_max": 3.14159
  },
  "navigation_parameters": {
    "inflation_radius": 0.5,
    "cost_scaling_factor": 5.0,
    "obstacle_range": 2.5,
    "raytrace_range": 3.0
  },
  "localization_parameters": {
    "particle_count": 2000,
    "update_frequency": 10.0,
    "laser_min_range": 0.1,
    "laser_max_range": 30.0
  }
}
```

### 3.4 Data Analysis Notes for Dev Team

**Key Questions to Answer:**
1. Do LiDAR scans show ghost points near reflective surfaces?
2. Does localization confidence drop when approaching reflective surfaces?
3. Does costmap show false obstacles at reflective surface locations?
4. Are there patterns in stop-start behavior (timing, location)?
5. Do navigation parameters need adjustment for reflective surfaces?

**Specific Analysis Requests:**
- Analyze LiDAR point cloud consistency (variance in readings)
- Check for correlation between reflective surface locations and navigation failures
- Review costmap inflation and obstacle detection logic
- Evaluate localization algorithm performance near reflective surfaces
- Assess path planning clearance parameters

---

## 4. Short-Term Fix to Try On-Site

### 4.1 Immediate Workaround: Adjust Navigation Parameters

**Fix 1: Increase Obstacle Detection Range and Adjust Filtering**

**Steps:**
1. **Increase LiDAR noise filtering:**
   - Increase filtering threshold to reduce false positives
   - May reduce sensitivity to real obstacles (trade-off)

2. **Adjust costmap parameters:**
   - Reduce inflation radius slightly (if too aggressive)
   - Increase obstacle detection range (to detect earlier, plan better)
   - Adjust cost scaling factor

3. **Modify path planning clearance:**
   - Increase minimum clearance from obstacles
   - This keeps robot further from reflective surfaces

**Configuration Changes:**
```yaml
# costmap_common_params.yaml
obstacle_range: 3.0  # Increase from 2.5
raytrace_range: 3.5  # Increase from 3.0
inflation_radius: 0.4  # Decrease from 0.5 (if too large)

# local_planner_params.yaml
max_vel_x: 1.2  # Reduce from 1.5 (slower = more time to react)
acc_lim_x: 0.5  # Reduce acceleration
inflation_radius: 0.6  # Increase clearance
```

**Expected Result:**
- Robot maintains greater distance from reflective surfaces
- More time to react to false obstacles
- May reduce but not eliminate issue

**Limitations:**
- May make robot overly cautious
- May not solve root cause (still detects false obstacles)
- May slow down overall operation

### 4.2 Alternative Fix: Mark Reflective Surfaces in Map

**Steps:**
1. **Identify all reflective surfaces** on map
2. **Mark as "no-go zones" or "low-confidence zones"** in costmap
3. **Adjust path planning** to avoid or minimize time in these zones
4. **Increase safety margins** around these zones

**Implementation:**
- Edit costmap to add static obstacles at reflective surface locations
- Or create "keep-out" zones around reflective surfaces
- Re-plan paths to avoid these zones

**Expected Result:**
- Robot avoids problematic areas entirely
- Eliminates issue but may create longer paths

**Limitations:**
- Requires map modification
- May not be feasible if reflective surfaces are in critical paths
- Doesn't solve underlying sensor issue

### 4.3 Quick Fix: Manual Path Modification

**Steps:**
1. **Identify alternative paths** that avoid reflective surfaces
2. **Modify waypoints** to use alternative routes
3. **Test new paths** to verify they work

**Expected Result:**
- Immediate workaround
- Robot completes tasks using alternative paths

**Limitations:**
- May increase path length/time
- Not a permanent solution
- Requires path re-planning

### 4.4 Recommended Short-Term Fix Combination

**Best Approach:**
1. **Increase path clearance** from obstacles (keep robot away from reflective surfaces)
2. **Reduce speed** near known problematic intersections
3. **Increase LiDAR filtering** to reduce false positives
4. **Mark worst reflective surfaces** as keep-out zones (if feasible)
5. **Monitor and collect data** for dev team analysis

**Implementation Priority:**
1. **Immediate (5 minutes)**: Reduce speed, increase clearance
2. **Short-term (30 minutes)**: Adjust costmap parameters
3. **If time permits (1-2 hours)**: Mark keep-out zones, modify paths

**Expected Improvement:**
- 50-70% reduction in incidents
- Not a complete fix, but improves reliability
- Buys time for proper solution from dev team

---

## 5. Long-Term Solution Recommendations

### 5.1 Sensor-Level Solutions
- **Multi-sensor fusion**: Combine LiDAR with cameras or other sensors to validate obstacles
- **Advanced LiDAR filtering**: Implement reflection-aware filtering algorithms
- **Sensor placement**: Adjust LiDAR angle to minimize reflection impact

### 5.2 Algorithm-Level Solutions
- **Reflection-aware obstacle detection**: Detect and filter reflective surface false positives
- **Improved localization**: Use multiple localization methods (LiDAR + visual + odometry)
- **Adaptive path planning**: Dynamically adjust paths based on sensor confidence

### 5.3 Environmental Solutions
- **Modify reflective surfaces**: Apply non-reflective coatings, change materials
- **Lighting adjustments**: Improve lighting to reduce reflections
- **Physical barriers**: Install non-reflective barriers near robot paths

---

## 6. Debug Report Summary

**Root Cause**: LiDAR sensor interference from reflective surfaces causing false obstacle detection and localization degradation.

**Confidence Level**: High (80-90% based on symptom match)

**Immediate Action**: Implement parameter adjustments (clearance, speed, filtering)

**Data Collected**: LiDAR scans, navigation logs, environmental photos, system diagnostics

**Next Steps**: 
1. Send data package to dev team
2. Implement short-term fixes
3. Await algorithm improvements from dev team
4. Consider environmental modifications if feasible

**Timeline**: 
- Short-term fix: Immediate (on-site)
- Data analysis: 2-3 days (dev team)
- Permanent solution: 1-2 weeks (algorithm update + testing)

---

**Report Prepared By**: [Field Technician Name]  
**Date**: [Current Date]  
**Status**: Under Investigation - Short-term fixes implemented

