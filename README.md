# Zinkerreka - KUKA Robot Programming Repository

This repository contains KUKA Robot Language (KRL) programs and configuration files for the R1 LASER robot system at Erreka S. COOP. The project is managed using KUKA WorkVisual 6.0 and includes production programs, maintenance routines, and service utilities.

## Table of Contents

- [Overview](#overview)
- [Repository Structure](#repository-structure)
- [System Information](#system-information)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Program Categories](#program-categories)
- [Configuration Files](#configuration-files)
- [Development Guidelines](#development-guidelines)
- [Authors](#authors)
- [License](#license)

## Overview

This repository manages the robot control programs for a KUKA KR C industrial robot (R1 LASER) running KUKA System Software (KSS) version 8.6.11.567. The robot is equipped with:

- GripperSpotTech technology (v5.0.3.51)
- PROFINET MS communication (v5.0.4.44)
- Load Data Determination (v7.2.4.228)
- Safety diagnostics (v3.1.7.65)
- EtherCAT diagnostics (v1.0.4.160)

## Repository Structure

```
Zinkerreka/
├── KRC/                          # KUKA Robot Controller files
│   ├── R1/                       # Robot R1 programs and configuration
│   │   ├── Mada/                 # Machine data files
│   │   │   ├── $machine.dat      # Robot configuration
│   │   │   └── $robcor.dat       # Robot correction data
│   │   ├── Program/              # Robot programs
│   │   │   ├── Work/             # Production programs
│   │   │   ├── Libraries/        # Shared function libraries
│   │   │   ├── Maintenance/      # Maintenance programs
│   │   │   └── Service/          # Service and teaching programs
│   │   ├── System/               # System programs and configuration
│   │   └── TP/                   # Technology packages
│   │       ├── BrakeTest/        # Brake test programs
│   │       ├── GripperSpotTech/  # Gripper and spot welding tech
│   │       └── LDD/              # Load Data Determination
│   └── STEU/                     # Controller configuration
│       └── Mada/                 # Controller machine data
├── ConfigMon.ini                 # Configuration monitor settings
├── Connections.xml               # WorkVisual connection settings
├── Modifications.xml             # Project modifications tracking
├── actions.log                   # Change history log
└── README.md                     # This file
```

## System Information

**Robot Controller**: KUKA KR C  
**System Software**: V8.6.11.567  
**Robot Name**: R1 LASER  
**Controller**: PCRC-MDEUSGC7HF  
**Network**: 192.168.1.21 / 172.29.1.138  

### Installed Options and Technologies

- **DiagnosisSafety** v3.1.7.65 - Safety system diagnostics
- **DiagnosisServiceEtherCAT** v1.0.4.160 - EtherCAT diagnostics
- **GripperSpotTech** v5.0.3.51 - Gripper and spot welding technology
- **KUKA.BoardPackage** v2.2.4.1 - Board package
- **KUKA.DeviceConnector** v2.1.10.288 - Device connectivity
- **KUKA.PROFINET MS** v5.0.4.44 - PROFINET communication
- **LoadDataDetermination** v7.2.4.228 - Load data calculation
- **UserTech** v4.0.16.2571 - User technology package

## Prerequisites

To work with this repository, you need:

1. **KUKA WorkVisual 6.0** or later
   - Official KUKA development environment
   - Required for editing and deploying programs

2. **KUKA System Software** compatible with v8.6.11.567
   - Must match or be compatible with the robot controller

3. **Network Access** to the robot controller
   - IP: 192.168.1.21 or 172.29.1.138
   - Appropriate permissions and user rights

4. **Knowledge Requirements**
   - KUKA Robot Language (KRL) programming
   - KUKA robot operation and safety procedures
   - Industrial robot safety standards

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/Aleynikovich/Zinkerreka.git
cd Zinkerreka
```

### 2. Open in WorkVisual

1. Launch KUKA WorkVisual 6.0
2. Open the project by loading the repository folder
3. Review `Connections.xml` for controller connection settings
4. Check `Modifications.xml` to see tracked changes

### 3. Connect to Robot Controller

1. Ensure network connectivity to the robot controller
2. Use WorkVisual's connection manager
3. Select the appropriate connection profile from `Connections.xml`
4. Verify access rights and safety permissions

### 4. Deploy Programs

 **Safety Warning**: Always follow proper safety procedures when deploying programs to an industrial robot. Ensure the work area is clear and all safety systems are active.

1. Select the program files to deploy
2. Use WorkVisual's deploy function
3. Verify program integrity on the controller
4. Test programs in T1 mode before production use

##  Program Categories

### Work Programs (`KRC/R1/Program/Work/`)

Production programs for normal operation:

- **C1_pickConveyorBP** - Pick operations from conveyor belt with base position
- **C2_CicloCompleto** - Complete production cycle

### Library Functions (`KRC/R1/Program/Libraries/`)

Shared function libraries:

- **IOLib.src** - Input/Output operations library
- **posCalcLib.src** - Position calculation utilities
- **toolControlLib.src** - Tool control functions

### Maintenance Programs (`KRC/R1/Program/Maintenance/`)

Maintenance and diagnostic routines:

- **C100_maintenanceAxis0** - Axis 0 maintenance routine
- **C101_maintenanceOil** - Oil maintenance tracking

### Service Programs (`KRC/R1/Program/Service/`)

Service, setup, and teaching programs:

- **C200_gripperChange** - Gripper change procedure
- **c201_freePos** - Free positioning mode
- **C203_LoadLayout** - Load layout configuration
- **C204_LoadRecipe** - Recipe loading
- **C251_T1_PosAct** - T1 mode position activation
- **C252_TeachingPointsC2** - Teaching points for C2 cycle
- **C253_RESET_CICLO** - Cycle reset

## Configuration Files

### ConfigMon.ini

Configuration monitor settings defining:
- Variable display configuration
- Access levels (Expert/Operator)
- Monitored system variables ($BASE, $TOOL, $POS_ACT)

### Connections.xml

WorkVisual connection profiles for the robot controller including:
- Controller hostname and IP addresses
- Software version information
- Installed options and packages

### Modifications.xml

Tracks all file modifications with:
- Original and current checksums
- File change status (Changed/None)
- Change history and timestamps

## Development Guidelines

### Code Style

1. **Follow KUKA KRL Standards**
   - Use FOLD sections for code organization
   - Include program headers with author information
   - Comment complex logic clearly

2. **Documentation**
   - Update program headers when modifying files
   - Include creation and modification dates
   - Document author contact information

3. **Version Control**
   - Commit logical units of work
   - Write clear commit messages
   - Track changes through Modifications.xml

### Safety Considerations

 **Critical**: All programs must comply with:
- ISO 10218 (Robot Safety Standards)
- Local safety regulations
- KUKA safety guidelines
- Customer-specific safety procedures

Always test new programs in T1 mode with reduced speed before production use.

### Testing Procedures

1. **Simulation**: Test in WorkVisual offline mode
2. **T1 Testing**: Manual mode testing with teach pendant
3. **T2 Testing**: Automatic mode with reduced speed
4. **Production**: Full automatic operation (only after approval)

## Authors

**Primary Developer**:  
Alexander Kalis  
Tekniker, C. Iñaki Goenaga, 5, 20600, Gipuzkoa  
+34 674 05 15 10  
alexander.kalis@tekniker.es

**Customer**:  
Erreka S. COOP

## License

This repository contains proprietary robot control programs developed for Erreka S. COOP. 

**Copyright Notice**: The programs and configurations in this repository are the property of their respective owners. Unauthorized copying, modification, or distribution is prohibited.

For licensing inquiries, please contact the repository owner or Erreka S. COOP.

---

## Additional Information

### Support and Issues

For technical support or to report issues:
1. Check the KUKA documentation for system-specific help
2. Contact your KUKA representative
3. Reach out to the development team (contact information above)

### Updates and Maintenance

This repository is actively maintained. Check the commit history and `actions.log` for recent changes and updates.

**Last Updated**: Check the most recent commit date for the latest updates.

---

**Note**: This is an industrial robot control system. Always prioritize safety and follow proper procedures when working with robot programs.

