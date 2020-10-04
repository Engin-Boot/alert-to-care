# Alert to Care

## [Segment 1] Web API

This project implements a service that receives measurements from devices that monitor patients.
It is used in the context of providing care in an ICU.

It offers the following APIs:

### User-story: Configuration

A setup-client needs to configure an ICU.
Context: This configuration will be used to relate the alerts to a patient-bed
Acceptance criteria: The configuration needs to include:
-	Number of beds
- Bed-identification
- Layout information

### User-story: Occupancy

An occupancy-management-client needs to set the status of each bed
-	Occupancy of each bed
-	Enter Patient details
-	Discharging a patient

### User-story: Monitoring 
A monitoring-client needs to act on alerts
Subscribers can be a GUI, an SMS service, a mobile app, etc.
-	Turning off alarms

One concern in such a system is security. To start with, implement it to restrict connections from a single client (or known list of clients). This can work if the client is on the same premises, such as the nursing station of an ICU.
As a second step, handle remote-access cases such as remote monitoring. To enable this, a gateway with authentication needs to be provided.

## [Segment 2] User-interface

### User-story: Setup

As Operations, I need to setup the ICU alert-service and its interface
E.g., The hospital has an ICU with 12 beds. I need to setup the server, install the software and configure the number and layout of the beds, using a GUI
Acceptance Criteria:
-	The setup can have a maximum of 4 manual steps. All manual steps shall be at the beginning or the end of installation.
(Manual steps in the middle of installation are confusing for operations)
-	Errors during the setup shall produce logs that lead to repair-actions that can be performed by Operations
-	The layouts provided shall cater to at least 3 common ICU layouts 

### User-story: Occupancy

As a nurse, I need to set the occupancy of beds
E.g., When a patient is admitted or discharged in the ICU, I need a GUI to mark the bed
Acceptance Criteria:
-	There shall be no alerts shown from empty beds. Don’t assume that the patient monitor has a network-interface to shut it down.
-	Admission and discharge shall be possible with a maximum of 3 clicks.

### User-story: Respond

As a nurse, I need to manage and respond to alerts
E.g., After I’ve handled an alert of a patient’s parameter, I need to reset it on the GUI
Acceptance Criteria:
-	Resetting an alert of a patient’s parameter shall be possible with a single click
-	It shall be possible to undo the reset
(a single click can be made by mistake)
-	Optional: Patient-specific alerts: It shall be possible to configure the thresholds per patient
