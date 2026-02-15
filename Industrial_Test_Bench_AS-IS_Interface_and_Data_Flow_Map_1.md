# Industrial Test Bench System

## AS-IS Interface and Data Flow Map

------------------------------------------------------------------------

## 1. Scope

This document maps the **interfaces** and **data flows** of the current
(AS-IS) industrial test bench architecture, including: - Control
interfaces (signals and command paths) - Measurement paths - Data
logging/export paths - Device Under Test (DUT) data interfaces
(including the currently unused API)

The goal is to provide a concrete baseline for deriving TO-BE
architectural requirements.

------------------------------------------------------------------------

## 2. System Boundary (AS-IS)

Included assets: - PLC (local control) - Local HMI - Pressure subsystem
(pump, valves, pressure transducer, mechanical pressure switch) -
Temperature subsystem (stand-alone controller + chamber/heater) -
Stand-alone data logger - DUT with onboard intelligence and logging -
Operator actions (manual coordination and data extraction)

Excluded (AS-IS): - Remote access (PC/tablet supervision) - Central
server / historian / database - Automated report generation pipeline -
OT network segmentation (no OT network in practice)

------------------------------------------------------------------------

## 3. Interface Map (Physical / Logical)

### 3.1 Control and Safety Interfaces (Signals)

  -----------------------------------------------------------------------------------------------------
  Interface   From         To               Type       Signal /    Purpose            Notes
  ID                                                   Protocol                       
  ----------- ------------ ---------------- ---------- ----------- ------------------ -----------------
  IF-01       HMI          PLC              Fieldbus   Profinet    Operator command   Local only
                                                       (HMI        entry, setpoints   
                                                       runtime)                       

  IF-02       PLC          Pump             Digital    DO (24V)    Start/Stop pump    Via
                                                                                      contactor/relay

  IF-03       PLC          Discharge valve  Digital    DO (24V)    Open/Close         Safety chain may
                                                                   controlled         override via
                                                                   depressurization   power removal

  IF-04       PLC          Proportional     Analog     AO 4--20 mA Pressure           Only if installed
                           valve (optional)                        regulation command 

  IF-05       Pressure     PLC              Analog     AI 4--20 mA Pressure           PLC uses for
              transducer                                           measurement        process
                                                                                      control/alarms

  IF-06       Mechanical   Safety relay     Digital    Dry contact Independent        Hardwired
              pressure     chain                                   overpressure       
              switch                                               detection          

  IF-07       E-Stop       Safety relay     Digital    Dry contact Emergency stop     Hardwired
                           chain                                                      

  IF-08       Door         Safety relay     Digital    Dry contact Guard safety       Hardwired
              interlock    chain                                                      

  IF-09       Safety relay Pump/heater      Power      Safety      Remove energy to   Independent from
              chain        power                       contactor   hazardous          PLC
                                                       control     actuators          

  IF-10       Temp         Chamber/Heater   Local      Vendor I/O  Temperature        Internal to temp
              controller                                           actuation          subsystem

  IF-11       PLC          Temp controller  Digital    DI/DO dry   RUN/READY/FAULT    No profile
                                                       contact     status & simple    coordination
                                                                   enabling           

  IF-12       Temp sensors Temp controller  Analog     PT100/TC    Temperature        Not acquired by
                                                                   measurement        PLC in AS-IS


  -----------------------------------------------------------------------------------------------------

------------------------------------------------------------------------

### 3.2 Data Acquisition Interfaces (Measurement to Logger)

  --------------------------------------------------------------------------------------
  Interface   From         To         Type       Signal /   Data          Notes
  ID                                             Protocol                 
  ----------- ------------ ---------- ---------- ---------- ------------- --------------
  IF-20       Pressure     Data       Analog     4--20 mA / Pressure      Logger wiring
              transducer   logger                0--10V     trend         varies by
              (or PLC                                                     bench
              mirror)                                                     

  IF-21       Temp         Data       Analog     4--20 mA / Temperature   Often separate
              controller   logger                PT100/TC   trend         channels
              (analog out)                       module                   
              or dedicated                                                
              probe                                                       

  IF-22       Auxiliary    Data       Mixed      Analog /   Optional      Not
              sensors (if  logger                Digital    signals       standardized
              any)                                                        
  --------------------------------------------------------------------------------------

------------------------------------------------------------------------

### 3.3 Data Export Interfaces (Files)

  ------------------------------------------------------------------------------------------------------
  Interface   From         To         Medium      Format              Timing          Notes
  ID                                                                                  
  ----------- ------------ ---------- ----------- ------------------- --------------- ------------------
  IF-30       Data logger  Operator   SD / USB    CSV                 End of test     Manual extraction

  IF-31       HMI (values) Operator   Manual      Notes / photo /     Any time        Often
                                                  manual copy                         non-structured

  IF-32       Temp         Operator   USB / local CSV / proprietary   End of test or  Vendor-dependent
              controller              export                          per batch       

  IF-33       DUT          Operator   SD card     Log files           End of test     Manual removal
                                                  (CSV/proprietary)   (after log      
                                                                      finalization)   

  IF-34       DUT          Operator   Ethernet    File transfer       End of test     Used occasionally
                                      (direct)    (SMB/FTP/HTTP       (after log      
                                                  download)           finalization)   

  IF-35       Operator     Report     PC          Excel workbook      Post-test       Manual aggregation
                           Template   (offline)                

  ------------------------------------------------------------------------------------------------------

------------------------------------------------------------------------

### 3.4 DUT Real-Time Data Interface (Present but NOT used)

  --------------------------------------------------------------------------------------
  Interface   From       To         Protocol    Capability      Status in  Risk/Note
  ID                                                            AS-IS      
  ----------- ---------- ---------- ----------- --------------- ---------- -------------
  IF-40       DUT        External   REST/HTTP   Read live       Not used   Requires
                         client     or TCP      measurements,              client
                                                status, event              software +
                                                stream                     network
                                                                           integration

  IF-41       External   DUT        REST/HTTP   Start/stop      Not used   Must be
     client       or TCP      logging, fetch  constrained  partial logs               to avoid  unintended      control

  --------------------------------------------------------------------------------------

------------------------------------------------------------------------

## 4. Data Flow Map (End-to-End)

### 4.1 During Test Data Flows

**DF-01 Process control (pressure)** - Operator inputs parameters on HMI
→ PLC executes basic sequence. - PLC commands pump/valves. - Pressure
feedback is read by PLC for process regulation and alarms.

**DF-02 Temperature evolution** - Temperature controller executes
locally configured profile. - PLC may receive coarse READY/FAULT states
(if wired). - Temperature data is not natively centralized.

**DF-03 Trending and recording** - Data logger records pressure and
temperature channels. - DUT records its own internal sensors
independently. - There is no shared test identifier across sources.

------------------------------------------------------------------------

### 4.2 End of Test Data Flows

**DF-10 Logger export** - Operator extracts CSV from logger via
SD/USB. - Files are manually named or placed in folders (non-standard
naming).

**DF-11 DUT export** - Operator finalizes log on DUT. - Data extracted
via SD removal or Ethernet file download. - Typically performed only
after the test is fully completed.

**DF-12 Temperature controller export (optional)** - Operator exports a
profile or trend file, sometimes in vendor format.

**DF-13 Report assembly** - Operator manually correlates: - DUT
serial/batch - test parameters (HMI notes/recipe) - logger CSV
(pressure/temp) - DUT log file(s) - controller export (optional) -
Report is built in Excel (copy/paste, calculations, charts).

------------------------------------------------------------------------

## 5. Correlation Points and Gaps

### 5.1 Correlation Points

-   Test start time (operator-defined)
-   Test duration / hold time
-   Pressure ramp shape
-   Temperature profile milestones
-   DUT internal timestamps (if present)

### 5.2 Current Gaps

-   No automatic **Test ID** propagated across subsystems.
-   No guaranteed time synchronization between:
    -   data logger clock
    -   DUT internal clock
    -   PLC/HMI timestamps (if any)
-   Manual file naming is a single point of failure for traceability.
-   Data is multi-source and post-correlated manually.
-   DUT API capability is unused, preventing near-real-time integration.

------------------------------------------------------------------------

## 6. Operator Touchpoints

-   Start/stop sequencing across multiple devices.
-   Manual confirmation of readiness states.
-   Manual export from logger/controller/DUT.
-   Manual association of files to a test.
-   Manual calculations and report compilation.

These touchpoints are the main operational variability and error sources
in the AS-IS model.

------------------------------------------------------------------------

## 7. Summary Diagram (Textual)

**Control Path** - HMI → PLC → (Pump / Valves) - Safety Relay Chain →
(Power removal to Pump/Heater) \[independent override\] - Temp
Controller → (Chamber/Heater) \[independent\]

**Measurement Path** - Pressure Transducer → PLC (process feedback) -
Pressure/Temp signals → Data Logger (recording) - DUT internal sensors →
DUT internal log (recording)

**Export Path** - Data Logger → SD/USB → Operator - Temp Controller →
USB/export → Operator (optional) - DUT → SD/Ethernet download →
Operator - Operator → Excel → Report

**Unused Capability** - DUT API (live data) exists but is not part of
the operational workflow.

------------------------------------------------------------------------

## 8. Baseline Drivers for TO-BE

-   Introduce a unique **Test ID** and propagate it across data sources.
-   Reduce manual export steps through structured ingestion paths.
-   Improve correlation and traceability (timestamps, metadata, operator
    actions).
-   Decide if and how to use DUT real-time APIs while preserving safety
    independence.
-   Preserve safety independence from supervisory/data layers.
