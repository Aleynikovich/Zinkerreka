# Zinkerreka - KUKA Robot Control System

This repository contains KUKA Robot Language (KRL) programs for an industrial robot system at **Erreka S. COOP**, developed by **Tekniker**.

## Project Overview

This project implements automated robotic operations for industrial manufacturing, featuring:
- Automated pick and place operations from conveyors
- Complete production cycle management
- Gripper control and tool management
- Safety and collision detection systems
- Maintenance and service routines

## System Information

- **Robot Model**: KUKA KR C
- **Controller**: KRC (KUKA Robot Controller)
- **Software Version**: V8.6.11.567
- **Customer**: Erreka S. COOP
- **Developer**: Tekniker, C. Iñaki Goenaga, 5, 20600, Gipuzkoa

## Repository Structure

```
├── Connections.xml      # Robot connection configuration
├── Modifications.xml    # Project modification tracking
└── KRC/                # KUKA Robot Control files
    ├── R1/             # Robot 1 programs and data
    │   ├── Program/    # Robot programs
    │   │   ├── Work/           # Production programs
    │   │   ├── Service/        # Service and setup programs
    │   │   ├── Maintenance/    # Maintenance routines
    │   │   └── Libraries/      # Custom function libraries
    │   ├── System/     # System configuration files
    │   ├── TP/         # Technology packages
    │   └── Mada/       # Machine data
    └── STEU/           # Controller system files
```

## Main Programs

### Production Programs (`KRC/R1/Program/Work/`)
- **C1_pickConveyorBP**: Pick operation from BP conveyor
- **C2_CicloCompleto**: Complete production cycle

### Service Programs (`KRC/R1/Program/Service/`)
- **C200_gripperChange**: Gripper change procedure
- **C201_freePos**: Free positioning mode
- **C203_LoadLayout**: Layout loading
- **C204_LoadRecipe**: Recipe loading
- **C251_T1_PosAct**: Position actualization for Tool 1
- **C252_TeachingPointsC2**: Teaching points for C2 cycle
- **C253_RESET_CICLO**: Cycle reset

### Maintenance Programs (`KRC/R1/Program/Maintenance/`)
- **C100_maintenanceAxis0**: Axis 0 maintenance routine
- **C101_maintenanceOil**: Oil maintenance routine

### Custom Libraries (`KRC/R1/Program/Libraries/`)
- **IOLib.src**: I/O operations library
- **posCalcLib.src**: Position calculation utilities
- **toolControlLib.src**: Tool control functions

## Technology Packages

- **GripperSpotTech**: Gripper and spot welding technology
- **BrakeTest**: Brake testing routines
- **LDD**: Load Data Determination

## Safety Features

- Collision detection and monitoring
- Safe stop mechanisms
- User-defined collision actions
- Real-time I/O monitoring

## Development Information

**Author**: Alexander Kalis  
**Email**: alexander.kalis@tekniker.es  
**Organization**: Tekniker  
**Phone**: +34 674 05 15 10

## File Types

- `.src` - KUKA Robot Language source files
- `.dat` - Data files (positions, configurations)
- `.sub` - Submit interpreter files
- `.xml` - Configuration and metadata files

## Usage

This repository is designed to be used with KUKA WorkVisual or similar KUKA programming environments. The programs should be deployed to the KUKA controller and can be selected and executed from the robot's teach pendant.

## Version Control

The repository tracks:
- Program modifications via `Modifications.xml`
- Connection settings via `Connections.xml`
- File checksums for integrity verification

## Notes

- All programs follow KUKA KRL programming standards
- Position data is specific to the installed robot configuration
- Tool data and base frames must be calibrated on-site
- Safety configurations must be validated before production use

## License

This project is proprietary software developed for Erreka S. COOP by Tekniker.
