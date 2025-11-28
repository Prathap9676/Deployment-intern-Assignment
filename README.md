# AMR Deployment Intern Assignment - Deliverables

This repository contains all deliverables for the AMR (Autonomous Mobile Robot) Deployment Intern Assignment.

---

## Assignment Overview

This assignment consists of 5 tasks covering various aspects of AMR deployment, troubleshooting, and operations:

1. **Task 1**: Full Deployment Plan Simulation (3 robots, 2000 sq.m warehouse)
2. **Task 2**: Root Cause Analysis + Report (intermittent path deviation issue)
3. **Task 3**: Deployment Planning & Coordination (2 AMRs, Coimbatore, 3 days)
4. **Task 4**: Real-World Debug Report (path completion failure with reflective surfaces)
5. **Task 5**: Deployment Handoff SOP (operations guide for Tier 3 warehouse)

---

## Deliverables Structure

```
Deployment intern_assignment/
├── README.md (this file)
├── Task1_Full_Deployment_Plan.md
├── Task2_Root_Cause_Analysis.md
├── Task3_Deployment_Planning_Coordination.md
├── Task4_Debug_Report.md
├── Task5_Deployment_Handoff_SOP.md
```

---

## Assumptions Made

### General Assumptions

1. **Robot Specifications**:
   - Standard AMR with LiDAR-based navigation
   - ROS (Robot Operating System) based software stack
   - Typical warehouse AMR capabilities (navigation, obstacle avoidance, fleet management)
   - Battery-powered with charging stations
   - Wi-Fi connectivity for fleet coordination

2. **Infrastructure**:
   - Client warehouses have basic infrastructure (power, network)
   - Standard Indian electrical specifications (220V AC, 50Hz)
   - Wi-Fi networks available (802.11ac or better)
   - Standard business hours (9 AM - 6 PM) unless specified

3. **Team and Resources**:
   - Deployment team has necessary technical expertise
   - Access to diagnostic tools and software
   - Support from engineering/backend teams available
   - Standard shipping and logistics services available in India

4. **Client Environment**:
   - Mixed human-robot environments
   - Standard warehouse operations (forklifts, pallets, staff)
   - Variable lighting conditions (natural + artificial)
   - Standard safety requirements and protocols

5. **Technical Assumptions**:
   - ROS-based navigation stack (AMCL, move_base)
   - LiDAR sensors (typical range 3-30m)
   - Standard safety sensors and emergency stop systems
   - Fleet management system for multi-robot coordination

### Task-Specific Assumptions

#### Task 1 (Full Deployment Plan):
- 7-day deployment timeline is acceptable
- Team of 4-5 people available
- Client can provide site access and coordination
- Standard warehouse layout with multiple zones

#### Task 2 (Root Cause Analysis):
- Issue is intermittent (not constant)
- No error codes suggests software/hardware interaction issue
- Standard diagnostic tools available on-site
- Remote support from engineering team available

#### Task 3 (Deployment Planning):
- Single technician is experienced and self-sufficient
- 3-day timeline is tight but achievable
- Shipping from Bangalore to Coimbatore takes 1-2 days
- Client can provide basic assistance (access, coordination)

#### Task 4 (Debug Report):
- Reflective surfaces are common in warehouse environments
- LiDAR sensors are primary navigation sensors
- Issue is reproducible under certain conditions
- Standard ROS navigation stack in use

#### Task 5 (Handoff SOP):
- Client has limited technical staff
- Basic operations knowledge sufficient
- Support team available for escalations
- Standard safety protocols apply

---


1. **Documentation Structure and Formatting**:
   - AI assisted in creating professional document structures
   - Helped format technical documents consistently
   - Ensured proper markdown formatting and organization

2. **Technical Content Development**:
   - AI provided technical knowledge about AMR systems, ROS, LiDAR, navigation stacks
   - Assisted in creating comprehensive checklists and procedures
   - Helped develop troubleshooting workflows and diagnostic procedures

3. **Content Organization**:
   - AI helped organize information logically across multiple documents
   - Assisted in creating consistent formatting and structure
   - Helped ensure all requirements were addressed

4. **Technical Accuracy**:
   - AI provided industry-standard practices for AMR deployment
   - Assisted in creating realistic timelines and procedures
   - Helped ensure technical terminology is used correctly

### Human Contribution

The following aspects were developed through human judgment and decision-making:

1. **Assumptions and Context**:
   - All assumptions listed above were made by the human author
   - Context-specific decisions (timelines, team sizes, etc.) were human-determined
   - Task interpretation and approach were human-driven

2. **Practical Experience Integration**:
   - Real-world deployment considerations were incorporated
   - Field-level troubleshooting approaches reflect practical experience
   - Client communication strategies based on real-world scenarios

3. **Document Review and Refinement**:
   - All documents were reviewed and refined by the human author
   - Content was validated for completeness and accuracy
   - Final decisions on what to include/exclude were human-made

4. **Task-Specific Customization**:
   - Specific details (locations, timelines, scenarios) were customized
   - Practical constraints and considerations were incorporated
   - Realistic edge cases and contingencies were identified


---

## Document Formats

All deliverables are provided in **Markdown (.md)** format, which:
- Can be easily converted to PDF using tools like Pandoc, Markdown to PDF converters, or online services
- Is readable in any text editor or markdown viewer
- Maintains formatting and structure
- Can be version-controlled and edited easily

### Converting to PDF (if needed)

**Option 1: Online Converters**
- Use services like Markdown to PDF, Dillinger, or similar
- Upload .md files and download PDFs

**Option 2: Pandoc (Command Line)**
```bash
pandoc Task1_Full_Deployment_Plan.md -o Task1_Full_Deployment_Plan.pdf
```

**Option 3: VS Code Extensions**
- Install "Markdown PDF" extension
- Right-click .md file → "Markdown PDF: Export (pdf)"

**Option 4: GitHub/GitLab**
- https://github.com/Prathap9676/Deployment-intern-Assignment
- Print to PDF from browser

---

## Submission Checklist

- [x] Task 1: Full Deployment Plan Simulation
- [x] Task 2: Root Cause Analysis + Report
- [x] Task 3: Deployment Planning & Coordination
- [x] Task 4: Real-World Debug Report
- [x] Task 5: Deployment Handoff SOP
- [x] Assumptions documented
- [x] All deliverables in markdown format
- [x] README with instructions

---

## Contact Information

**Author**: [Prathap naidu]  
**Date**: [28-11-2025]  
**Assignment**: AMR Deployment Intern Assignment

---

## Notes

- All documents are ready for submission
- Documents can be converted to PDF as needed
- All assumptions are clearly documented
- AI usage is fully disclosed and justified
- Documents follow professional standards and best practices

---

**Thank you for reviewing this assignment!**

