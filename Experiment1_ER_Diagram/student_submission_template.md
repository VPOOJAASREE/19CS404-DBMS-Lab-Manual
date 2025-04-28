# EX:1  ER DIAGRAM

## NAME: V.POOJAA SREE
## REG.NO.: 212223040147

## Scenario Chosen:
Hospital

## ER Diagram:

![ER git](https://github.com/user-attachments/assets/0bf66402-d7db-43b3-a1f1-cbe54362a80f)


## Entities and Attributes:

### Department:

Dept_ID (Primary Key)

Name

Head

### Doctor:

Doctor_ID (Primary Key)

Name

Contact_No

Email

Specialization

Work_Schedule

### Patient:

Patient_ID (Primary Key)

Name

DOB

Gender

Address

Contact_No

Email

Work_Schedule

### Appointments:

App_ID (Primary Key)

Date

Time

Reason

Add_Notes

### Medical Records:

Med_Rec_ID (Primary Key)

Diagnosis

Medications

Treatment

Test Results



## Relationships and Constraints:

### Specialized (Department → Doctor):

One Department can have many Doctors.

A Doctor belongs to one Department. (1:N cardinality)

### Assigned (Doctor → Appointments):

One Doctor can be assigned to multiple Appointments.

An Appointment is assigned to one Doctor. (1:N cardinality)

### Book (Patient → Appointments):

One Patient can book multiple Appointments.

Each Appointment is booked by one Patient. (1:N cardinality)

### Contain (Patient → Medical Records):

One Patient can have multiple Medical Records.

Each Medical Record belongs to one Patient. (1:N cardinality)

### Check (Doctor → Medical Records):

One Doctor can check multiple Medical Records.

Each Medical Record is checked by one Doctor. (1:N cardinality)

## Extension (Prerequisite / Billing):

### Billing (Extension Idea):
Billing could be modeled by adding a new entity called Billing with attributes like Bill_ID, Amount, Payment_Method, and Payment_Status.
It would have relationships with Appointments (each appointment generates a bill) and Patients (patients are billed for their appointments).

## Design Choices:

1. I chose the main entities such as Doctor, Patient, Appointments, Department, and Medical Records because they represent the core operations of a hospital.

2. Relationships like Specialized, Assigned, Book, and Contain were added to represent the real-world interaction between these entities.

3. I assumed that each appointment is uniquely identified and linked to one doctor and one patient.

4. Work schedules for both doctors and patients are stored to manage availability.

5. Medical records are detailed to include diagnosis, medications, treatment, and test results for better patient history tracking.

## Result: 

Thus, the ER diagram for the hospital management system was successfully designed, and the entities, relationships, and constraints were clearly represented.
