# HELPMI – Device/Detector/Component (DDC) Library

*All definitions/designations within are subject to change depending on what metadata standard is chosen by the community.*

## Contents
- [Template](#template) .....................................................................................................................................................
- [Feedback](#feedback) ....................................................................................................................................................
- [Detectors](#detectors) ....................................................................................................................................................
  - [Standard CCD/CMOS](#standard-ccdcmos) ............................................................................................................................
  - [Focus Diagnostic](#focus-diagnostic) ....................................................................................................................................
  - [Wavefront Sensor](#wavefront-sensor) ...................................................................................................................................
  - [Gateable CCD](#gateable-ccd).........................................................................................................................................
  - [Streak Camera](#streak-camera) ........................................................................................................................................
  - [Spectrometer – Photon](#spectrometer-–-photon) ...........................................................................................................................
  - [Spectrometer – Electron](#spectrometer-–-electron) .......................................................................................................................
  - [Spectrometer – Proton/Ion](#spectrometer-–-protonion)..................................................................................................................
  - [Thomson Parabola Spectrometer](#thomson-parabola-spectrometer).......................................................................................................
  - [Wizzler](#wizzler) ...................................................................................................................................................
  - [Dazzler](#dazzler)..................................................................................................................................................
  - [SPIDER](#spider) .................................................................................................................................................
  - [FROG](#frog)...................................................................................................................................................
  - [2nd Order Autocorrelator](#2nd-order-autocorrelator) .......................................................................................................................
  - [2nd Order Autocorrelator for Measurement of Pulse Front Tilt, e.g., TiPa from Light Conversion](#2nd-order-autocorrelator-for-measurement-of-pulse-front-tilt-eg-tipa-from-light-conversion) .....
  - [3rd Order Autocorrelator (Sequoia, Tundra)](#3rd-order-autocorrelator-sequoia-tundra) ..................................................................................................
  - [Scintillator Screen (electron pointing diagnostic)](#scintillator-screen-electron-pointing-diagnostic) .............................................................................
  - [Temperature Sensor](#temperature-sensor) ..............................................................................................................................
  - [Vibration Sensor](#vibration-sensor) ....................................................................................................................................
  - [Humidity Sensor](#humidity-sensor) ....................................................................................................................................
  - [Photodiode](#photodiode) ............................................................................................................................................
  - [Quadrant Detector](#quadrant-detector) ..............................................................................................................................
  - [Vacuum Sensor](#vacuum-sensor) .....................................................................................................................................
- [Devices](#devices) .....................................................................................................................................................
  - [Linear Motor Stage (stepper, piezo, etc.)](#linear-motor-stage-stepper-piezo-etc) .............................................................................................
  - [Rotation Stage](#rotation-stage) ......................................................................................................................................
  - [Mechanical Shutter (only template)](#mechanical-shutter-only-template) .....................................................................................................
  - [Electro-Optical Shutter (only template)](#electro-optical-shutter-only-template) .............................................................................................
  - [Spatial Filter](#spatial-filter) .........................................................................................................................................
  - [Spectral Filter (only template)](#spectral-filter-only-template) .................................................................................................................
  - [Amplitude Filter (only template)](#amplitude-filter-only-template) ...............................................................................................................
  - [Polarizer Filter](#polarizer-filter) .........................................................................................................................................
  - [Beam Splitter (only template)](#beam-splitter-only-template) .................................................................................................................
  - [Generic Optic (only template)](#generic-optic-only-template) ................................................................................................................
- [Targets](#targets) ......................................................................................................................................................
  - [Nozzle Target (Gas/Liquid/Cryogenic and Sheet/Filament/Droplet/Capillary)](#nozzle-target-gasliquidcryogenic-and-sheetfilamentdropletcapillary) .................................................
  - [Foil (Metal, Plastic, etc.)](#foil-metal-plastic-etc) ..........................................................................................................................
- [Laser](#laser) ........................................................................................................................................................
  - [Laser Oscillator](#laser-oscillator) .....................................................................................................................................
  - [Regenerative Amplifier](#regenerative-amplifier) .......................................................................................................................
  - [Multi-pass Amplifier (pretty much same as regenerative amplifier)](#multi-pass-amplifier-pretty-much-same-as-regenerative-amplifier) ................................................
  - [Stretcher](#stretcher) .................................................................................................................................................
  - [Compressor](#compressor) .............................................................................................................................................
  - [XPW System](#xpw-system) .........................................................................................................................................
- [Probe](#probe) .........................................................................................................................................................
  - [Optical Probe Beam](#optical-probe-beam) .............................................................................................................................
  - [Particle Probe Beam](#particle-probe-beam) ............................................................................................................................

## Template

### A. Technical Metadata
i. Data that rarely changes, describes the device/instrument/component and would be useful to have later for data analysis
ii. Examples
1. Pixel size of a CCD camera
2. FWHM of a bandpass filter
3. Thickness of a BBO crystal
4. Surface coating of front/rear sides of an optic
5. Calibration file and date of a spectrometer

### B. Procedural Metadata
i. Data that could change based on use of device/instrument/component in the laboratory.
ii. Examples
1. Location of measurement in laser or target area
2. Start and end date of use
3. Parameters of beam incident on device (diameter, polarization, energy, pulse duration)
4. What filters were used in front of device
5. Number of measurements per output
6. Integration time of detector

### C. Access/Security Metadata
i. Data describing who is allowed access and when
ii. Examples
1. Quality assurance/Maintenance data from laser can be kept secure (non-publishable)
2. Experimental Scans can be marked as publishable (open access)

### D. Data
i. Data that is actually recorded by the device/instrument/component and is desired for scientific analysis

## Feedback

1. General interest in work is positive
2. For smaller laboratories, who is responsible for maintaining any future Metadata standard/system
   - More bureaucratic tasks without the necessary manpower to perform them
   - If done by PhD students, system will fall apart at end of PhD cycle
   - If User facilities have IT/Data Management groups, then Helmholtz should finance/employ such groups FIRST and then have us develop these standards
3. Does the Tango and EPICs control systems have a native/preferred Metadata standard and if yes, why don’t we use that?
   - No standard is integrated, the user can use/define their own Metadata standard
4. Border between Metadata Library, Databank and electronic notebook is unclear
   - How detailed does the metadata library reflect the experimental setup, or should this be recorded in an electronic notebook?
   - Example: photodiode used to measure a series of measurements. Does the metadata system record whether or not a lens was used to focus the laser onto the diode, or if an ND filter was used? Or is this information saved somewhere else, if at all?
5. Digital Twin tied to Metadata system would be nice to have
   - Something to show current digital representation of the experiment to see if something is missing
   - Nice to have: moving parts refresh as data is taken
6. Extent of modular metadata definitions
   - Examples
     - Electron Pointing measurement= Scintillator + Camera + Schematic
     - Gas Target = Gas regulator + Valve + Nozzle/Gas-Cell + Schematic
     - Electron Spectrometer = Collimator + Magnet + Scintillators + Cameras + Schematic
   - So, define individual parts and then have container to build the sum of their parts, or just define the sum with lots of entries for all the sub-parts?
7. Discussion on separating Laser-side and Experiment-side Metadata
   - Many Experiment-side measurements need Laser-side data to be understood properly
   - Ability to capture Laser-side data even if not “fully-amplified” is important
     - Focus measurements in Target chamber are typically not fully-amplified
     - Wavefront sensor measurements are typically not fully-amplified
8. Assumption that EVERY entry in the system is associated with a date, time, shot-number or all of the above

## Detectors

### Standard CCD/CMOS

1. **Technical Metadata**
   - Manufacturer
   - Model name/number
   - Serial number
   - Operating Software and version number
   - Interface (USB, Ethernet, etc.)
   - Sensor type
   - Sensor’s manufacturer
   - Sensor’s model number
   - Sensor size (either pixels in Horizontal/Vertical directions, or in mm)
   - Sensor’s filter (RGB, IR, etc.)
   - Pixel Size
   - Quantum Efficiency Curve
   - Technical drawing/file of device/setup

2. **Procedural Metadata**
   - Name of detector as used in experiment
   - Location of detector in experiment
   - Dynamic Range
   - Exposure time
   - Gain
   - Trigger
   - Binning
   - Background measurement
   - Region of Interest
   - Schematic of imaging/focusing setup
     - Lens, objectives, filters, etc.
     - Imaging distances
   - Other

3. **Access/Security Metadata**

4. **Data**
   - 2D array of pixel values or 3D array for RGB type camera

### Focus Diagnostic

- Combination of Camera/Optics/Motors or a separate entity in Metadata?
- Capture information on laser’s configuration during use, i.e., fully-amplified or not
- Important for more detailed simulations as well as analyzing experimental data
- (Maybe include a general point “Optical Setup”, independent on the purpose. These could be linked to the corresponding detector)
 
### Wavefront Sensor

1. **Technical Metadata**
   - Measurement principle (shearing interferometry, Shack-Hartmann, etc…?, including component information such as lens-array, pitch, focal length)
   - Manufacturer or built in-house
   - Model name/number
   - Serial number
   - Operating Software and version number
   - Interface (USB, Ethernet, etc.)
   - Sensor type
   - Sensor’s manufacturer
   - Sensor’s model number
   - Sensor size (either pixels in Horizontal/Vertical directions, or in mm)
   - Sensor’s filter (RGB, IR, etc.)
   - Pixel Size
   - Quantum Efficiency Curve
   - Technical drawing/file of device/setup

2. **Procedural Metadata**
   - Name of detector as used in experiment
   - Location of detector in experiment
   - Configuration of laser during use
   - Dynamic Range
   - Exposure time
   - Gain
   - Trigger
   - Binning
   - Background measurement
   - Region of Interest
   - Schematic of imaging/focusing setup
     - Lens, objectives, filters, etc.
     - Imaging distances

3. **Access/Security Metadata**

4. **Data**
   - 2D array of pixel values
   - Results of software analysis (if any)

### Gateable CCD

1. **Technical Metadata**
   - Manufacturer
   - Model name/number
   - Serial number
   - Operating Software and version number
   - Interface (USB, Ethernet, etc.)
   - Sensor type
   - Sensor’s manufacturer
   - Sensor’s model number
   - Sensor size (either pixels in Horizontal/Vertical directions, or in mm)
   - Sensor’s filter (RGB, IR, etc.)
   - Pixel Size
   - Quantum Efficiency Curve
   - Scintillator’s datasheet
     - Material
     - Size
   - Technical drawing/file of device/setup (camera and scintillator)

2. **Procedural Metadata**
   - Name of detector as used in experiment
   - Location of detector in experiment
   - Dynamic Range
   - Exposure time
   - Gain
   - Trigger
   - Binning
   - Background measurement
   - Region of Interest
   - Schematic of imaging/focusing setup
     - Lens, objectives, filters, etc.
     - Imaging distances
     - Calibration image of scintillator
     - Shielding on scintillator
     - Orientation of scintillator relative to target or laser forward direction
   - Other
   - GCCD Settings
     - Amplification voltage
     - Delay time
     - Gate time
     - Zero delay image
     - Date of Zero delay image

3. **Access/Security Metadata**

4. **Data**
   - 2D array of pixel values

### Streak Camera

1. **Technical Metadata**
   - Manufacturer
   - Model name/number
   - Serial number
   - Operating Software and version number
   - Interface (USB, Ethernet, etc.)
   - Sensor type
   - Sensor’s manufacturer
   - Sensor’s model number
   - Sensor size (either pixels in Horizontal/Vertical directions, or in mm)
   - Sensor’s filter (RGB, IR, etc.)
   - Pixel Size
   - Sweep ranges
   - Sweep delays
   - Sweep resolutions
   - Quantum Efficiency Curve
   - Scintillator’s datasheet
     - Material
     - Size
   - Technical drawing/file of device/setup (camera and scintillator)

2. **Procedural Metadata**
   - Name of detector as used in experiment
   - Location of detector in experiment
   - Dynamic Range
   - Exposure time of camera
   - Gain of camera
   - Sweep range
   - Slit height
   - Slit width
   - Trigger
   - Trigger delay
   - Background measurement
   - Region of Interest
   - Schematic of imaging/focusing setup
     - Lens, objectives, filters, etc.
     - Imaging distances
     - Calibration image
     - Orientation of scintillator relative to target or laser forward direction
   - MCP Settings
     - Gain of MCP
     - …
   - Other

3. **Access/Security Metadata**

4. **Data**
   - 2D Array of pixel values

### Spectrometer – Photon

1. **Technical Metadata**
   - Manufacturer or built in-house
   - Model name/number
   - Serial number
   - Operating Software and version number
   - Start wavelength (frequency)
   - End wavelength (frequency)
   - Resolution (array of wavelengths or frequencies)
   - Calibration Data
     - Light source used for calibration
     - Last Calibration Date
   - Imaging or non-imaging
   - Grating, crystal or prism
     - Manufacturer
     - Lines/mm
     - Type of grating
     - Horizontal Dimension
     - Vertical Dimension
   - Detector
     - Manufacturer
     - Model name/number
     - Serial number
     - Pixel count horizontal direction (dispersion axis)
     - Pixel count vertical direction
     - Pixel pitch
     - Quantum efficiency curve
     - Typical Noise (single value or array)

2. **Procedural Metadata**
   - Name of spectrometer as used in experiment
   - Location of spectrometer in experiment
   - Schematic of imaging/focusing setup
     - Lens, objectives, filters, etc.
     - Imaging distances
     - Entrance slit diameter
     - Fiber coupled
     - Integrating sphere
     - Spectral filter
     - Amplitude filter
     - Polarizer
     - Waveplate
     - FWHM Beam Diameter
   - Measurement Procedure
   - Number of measurements per average
   - Integration time
   - Smoothing factor
   - Dark current measurement (per shot, per run, per day, etc.)

3. **Access/Security Metadata**

4. **Data**
   - Pixel counts versus wavelength(frequency)
   - Optional: (calibrated) irradiance vs wavelength

### Spectrometer – Electron

1. **Technical Metadata**
   - Manufacturer or built in-house
   - Model name/number
   - Serial number
   - Operating Software and version number
   - Technical drawing/file of device/setup
     - Position/details of magnet
     - Position/details of cameras
     - Position/details of scintillating screens
     - Position/details of collimator/slit
   - 2D/3D map of magnetic field
   - Calibration data of spectrometer – position on scintillator screen vs. energy
     - Relative energy resolution of each energy
     - Charge calibration of scintillator(s)/camera(s) – charge per pixel count
   - Scintillation Screen
     - Manufacturer
     - Model name/number
     - Charge calibration (photons/sr*pC)
   - All cameras used to record data – tied to their relevant metadata
     - Dynamic range, exposure time, gain, trigger, background measurement, binning
     - Sketch/data for absolute camera calibration
     - Objectives, aperture settings, ND filters, spectral filters
     - Imaging scale (mm on scintillator screen/pix)
   - Tracing file of electron deflection angle vs. energy

2. **Procedural Metadata**
   - Name of spectrometer as used in experiment
   - Location of spectrometer in experiment
   - Measurement procedure

3. **Access/Security Metadata**

4. **Data**
   - Pixel counts over 2D array of camera pixels

### Spectrometer – Proton/Ion

1. **Technical Metadata**

2. **Procedural Metadata**

3. **Access/Security Metadata**

4. **Data**

### Thomson Parabola Spectrometer

1. **Technical Metadata**
   - Manufacturer or in-house design
   - Model name/number
   - Serial number
   - Operating Software and version number
   - Technical drawing/file of device/setup
   - Entrance aperture
     - Dimensions
     - Position
     - Height of particle beam after aperture
     - Distance of aperture to electric field (start)
     - Distance of aperture to magnetic field (start)
   - Magnetic field/magnet yoke
     - Strength
     - Height
     - Start above ground
     - Horizontal dimension
     - Vertical dimension
     - Distance of magnetic field (end) to detector
     - Calibration data (magnetic field strength)
     - Last calibration date
   - Electric field/Capacitor
     - Length
     - Height
     - Start above ground
     - Distance of electric field (end) to detector
   - Detector
     - Type (MCP, CR-39, image plate, …)
     - Manufacturer
     - Model name/number
     - Serial Number
     - Size
     - Characteristics (online or offline measurement, data sheet)
   - Camera (if detector is MCP)
     - Manufacturer
     - Model name/number
     - Pixel size
     - Camera objective
   - Other readout device (if detector is different)
     - Manufacturer
     - Model name/number (microscope, scanner, …)
   - Position zero deflection point on detector/camera
   - Low energy cutoff

2. **Procedural Metadata**
   - Name of Thomson Parabola as used in experiment
   - Location of Thomson Parabola in experiment
   - Name of detector used in Thomson parabola (MCP, CR-39, …)
   - Schematic of measurement setup
     - Distance target to entrance aperture
     - Angle observed with respect to target normal direction/laser direction
   - MCP settings (voltages)
   - Capacitor voltage
   - Schematic of imaging/focusing setup if camera used
     - Lens, objectives, filters, etc.
     - Imaging distances
     - Calibration image (for µm/pixel)
     - Camera settings (gain, exposure, …)
   - Proton energy at pixel position
   - (Heavier-) ion energy at pixel position
   - Energy resolution at pixel position
   - Particle per signal calibration for camera
   - Dark current measurement (per shot, per run, per day, etc.)

3. **Access/Security Metadata**

4. **Data**
   - Images of ion/proton traces (if camera is used, raw data)
   - Or detectors with ion/proton traces (CR-39, image plates, …)
   - Maximum ion/proton energy
   - Signal/particle number per solid angle and energy interval

### Radiochromic-film stack

1. **Technical Metadata**
   - Manufacturer
   - RCF type / name
   - LOT number
   - Scanner name / model used
   - Ion response calibration for a given scanner

2. **Procedural Metadata**
   - Stack composition
     - Position of each layer within the stack
     - Orientation of each RCF within the stack
     - Material / RCF type of each layer within the stack
     - Thickness of each layer
   - Location of RCF stack in the experiment
   - Energy loss files for each layer

3. **Access/Security Metadata**

4. **Data**
   - Set of RGB/IR images with 16-Bit for each channel

### Wizzler

1. **Technical Metadata**
   - Manufacturer
   - Model name/number
   - Serial number
   - Operating Software and version number

2. **Procedural Metadata**
   - Input Energy
   - Input FWHM Beam Diameter
   - Input Polarization
   - Input Spectrum: Center and FWHM
     - Full Spectrum as .txt/.csv if available
   - Name of device as used in experiment
   - Location of device in experiment
   - Schematic of measurement setup
     - optics, filters, etc.
     - distances
     - On air, behind window, etc.
       - Dispersion compensated in Wizzler software?
   - Number of shots per average
   - Corresponding settings of stretcher/compressor/dazzler and laser configuration
     - Best case, linked via a shot number

3. **Access/Security Metadata**

4. **Data**
   - Wizzler file types
     - \*SRSI_nums.txt
     - \*SRSI_raw.msr
     - \*SRSI_Raw_spectral.txt
     - \*SRSI_spectral.txt
     - \*SRSI_time.txt

### Dazzler

1. **Technical Metadata**
   - Manufacturer
   - Model name/number
   - Serial number
   - Operating Software and version number

2. **Procedural Metadata**
   - Input Energy
   - Input FWHM Beam Diameter
   - Input Polarization
   - Input Spectrum: Center and FWHM
     - Full Spectrum as .txt/.csv if available
   - Name of device as used in experiment
   - Location of device in experiment
   - Schematic of setup
     - optics, filters, etc.
     - distances
   - Corresponding settings of stretcher/compressor/dazzler and laser configuration
     - Best case, linked via a shot number

3. **Access/Security Metadata**

4. **Data**
   - Data files for Wizzler/Dazzler loop come from Wizzler
   - Any extra information from the GUI would have to be saved manually (or a script developed)

### SPIDER

1. **Technical Metadata**
   - Manufacturer or built in-house
   - Model name/number
   - Serial number
   - Operating Software and version number
   - Technical drawing/file of device/setup

2. **Procedural Metadata**
   - Input Energy
   - Input FWHM Beam Diameter
   - Input Polarization
   - Input Spectrum: Center and FWHM (if not measured/saved by device)
     - Full Spectrum as .txt/.csv if available
   - Name as used in experiment
   - Location in experiment
   - Schematic of setup
     - optics, filters, etc.
     - distances
   - Dispersive elements that are compensated for in software
   - Corresponding settings of stretcher/compressor/dazzler and laser configuration
     - Best case, linked via a shot number

3. **Access/Security Metadata**

4. **Data**
   - Fundamental spectrum
   - Spectral phase
   - Reconstructed pulse duration (normalized intensity vs. time)
   - FWHM pulse duration, GDD, TOD, FOD, etc. if calculated by the software

### FROG

1. **Technical Metadata**
   - Manufacturer or built in-house
   - Model name/number
   - Serial number
   - Operating Software and version number
   - Technical drawing/file of device/setup
   - Nonlinear crystal type and cut
   - Nonlinear crystal thickness
     - Minimum pulse duration measurable

2. **Procedural Metadata**
   - Input Energy
   - Input FWHM Beam Diameter
   - Input Polarization
   - Input Spectrum: Center and FWHM (if not measured/saved by device)
     - Full Spectrum as .txt/.csv if available
   - Name as used in experiment
   - Location in experiment
   - Schematic of setup
     - optics, filters, etc.
     - distances
   - Dispersive elements that are compensated for in software
   - Corresponding settings of stretcher/compressor/dazzler and laser configuration
     - Best case, linked via a shot number
   - retrieval algorithm

3. **Access/Security Metadata**

4. **Data**
   - Fundamental spectrum
   - Spectral phase
   - Reconstructed pulse duration (normalized intensity vs. time)
   - FWHM pulse duration, GDD, TOD, FOD, etc. if calculated by the software
   - Wigner plot

### 2nd Order Autocorrelator

1. **Technical Metadata**
   - Manufacturer or built in-house
   - Model name/number
   - Serial number
   - Operating Software and version number
   - Technical drawing/file of device/setup
   - Nonlinear crystal type and cut
   - Nonlinear crystal thickness
     - Minimum pulse duration measurable

2. **Procedural Metadata**
   - Input Energy
   - Input FWHM Beam Diameter
   - Input Polarization
   - Name as used in experiment
   - Location in experiment
   - Assumed pulse shape (for deconvolution factor)
   - Schematic of measurement setup
     - optics, filters, etc.
     - distances
   - Corresponding settings of stretcher/compressor/dazzler and laser configuration
     - Best case, linked via a shot number

3. **Access/Security Metadata**

4. **Data**
   - Autocorrelation trace: 2D array of pixel values, or lineout of pixel values
   - FWHM Deconvolved pulse duration

### 2nd Order Autocorrelator for Measurement of Pulse Front Tilt, e.g., TiPa from Light Conversion

1. **Technical Metadata**
   - Manufacturer or built in-house
   - Model name/number
   - Serial number
   - Operating Software and version number
   - Technical drawing/file of device/setup
   - Nonlinear crystal type and cut
   - Nonlinear crystal thickness
     - Minimum pulse duration measurable

2. **Procedural Metadata**
   - Input Energy
   - Input FWHM Beam Diameter
   - Input Polarization
   - Name as used in experiment
   - Location in experiment
   - Assumed pulse shape (for deconvolution factor)
   - Schematic of measurement setup
     - optics, filters, etc.
     - distances
   - Corresponding settings of stretcher/compressor/dazzler and laser configuration
     - Best case, linked via a shot number

3. **Access/Security Metadata**

4. **Data**
   - Autocorrelation trace: 2D array of pixel values, or lineout of pixel values
   - FWHM Deconvolved pulse duration
   - Measured pulse front tilt

### 3rd Order Autocorrelator (Sequoia, Tundra)

1. **Technical Metadata**
   - Manufacturer or built in-house
   - Model name/number
   - Serial number
   - Operating Software and version number
   - Technical drawing/file of device/setup
   - Nonlinear crystal types and cuts
   - Nonlinear crystal thicknesses
   - Known artefacts due to design of device

2. **Procedural Metadata**
   - Input Energy
   - Input FWHM Beam Diameter
   - Input Polarization
   - Name as used in experiment
   - Location in experiment
   - Schematic of measurement setup
     - optics, filters, etc.
     - distances
   - Corresponding settings of stretcher/compressor/dazzler and laser configuration
     - Best case, linked via a shot number
   - Noise floor measurement
     - Date of measurement
   - Measurement details
     - Number of shots per average
     - Start, stop, step size of temporal scan
     - Normalized or raw data
     - Peak shifted to t=0 or no shift

3. **Access/Security Metadata**

4. **Data**
   - Measured temporal intensity contrast

### Scintillator Screen (electron pointing diagnostic)

1. **Technical Metadata**

2. **Procedural Metadata**

3. **Access/Security Metadata**

4. **Data**

### Temperature Sensor

1. **Technical Metadata**

2. **Procedural Metadata**

3. **Access/Security Metadata**

4. **Data**

### Vibration Sensor

1. **Technical Metadata**

2. **Procedural Metadata**

3. **Access/Security Metadata**

4. **Data**

### Humidity Sensor

1. **Technical Metadata**

2. **Procedural Metadata**

3. **Access/Security Metadata**

4. **Data**

### Photodiode

1. **Technical Metadata**
   - Manufacturer
   - Model name/number
   - Serial number
   - Detector Type
   - Active Area
   - Rise Time
   - Calibration data: Responsivity Curve or calibration value/curve
   - Last calibration date
   - Power Supply
   - Technical drawing/file of device/setup

2. **Procedural Metadata**
   - Name of photodiode as used in experiment
   - Location of photodiode as used in experiment
   - Used Oscilloscope or readout device
     - Manufacturer
     - Model name/number (link)
     - Readout settings
   - Impedance/Termination
   - Schematic of imaging/focusing setup
     - Lens, objectives, filters, etc.
     - Imaging distances
   - Beam Size on detector
   - Cabling
     - Type
     - Length
     - Details

3. **Access/Security Metadata**

4. **Data**
   - Measured Voltage vs. time

### Quadrant Detector

1. **Technical Metadata**
   - Manufacturer
   - Model name/number
   - Serial number
   - Detector Type
   - Active Area
   - Rise Time
   - Calibration data: Responsivity Curve or calibration value/curve
   - Last calibration date
   - Power Supply
   - Technical drawing/file of device/setup

2. **Procedural Metadata**
   - Name of detector as used in experiment
   - Location of detector as used in experiment
   - Calibration of µm/volt or µrad/volt if used as position or pointing diagnostic
   - Used Oscilloscope or readout device
     - Manufacturer
     - Model name/number (link)
     - Readout settings
   - Impedance/Termination
   - Schematic of imaging/focusing setup
     - Lens, objectives, filters, etc.
     - Imaging distances
   - Beam Size on detector
   - Cabling
     - Type
     - Length
     - Details

3. **Access/Security Metadata**

4. **Data**
   - Measured Voltage vs. time per channel

### Vacuum Sensor

1. **Technical Metadata**

2. **Procedural Metadata**

3. **Access/Security Metadata**

4. **Data**

## Devices

### Linear Motor Stage (stepper, piezo, etc.)

1. **Technical Metadata**
   - Manufacturer
   - Model name/number
   - Serial number
   - Calibration data (µm/step)
   - Last Calibration date
   - Special Gearing
   - Type (Stepper, DC, piezo)
   - Feedback system (yes/no/type)
   - Current/Frequency/Ramp Settings or similar for non-stepper motors
   - Technical drawing/file of device/setup

2. **Procedural Metadata**
   - Name of motor stage as used in experiment
   - Location of motor stage as used in experiment
   - Description of direction of travel
   - Zero Position
   - Soft limits
   - Run mode (microstepping/full steps)

3. **Access/Security Metadata**

4. **Data**
   - Motor position

### Rotation Stage

1. **Technical Metadata**
   - Manufacturer
   - Model name/number
   - Serial number
   - Calibration data (rad/step)
   - Last Calibration date
   - Special Gearing
   - Type (Stepper, DC, piezo)
   - Feedback system (yes/no/type)
   - Current/Frequency/Ramp Settings or similar for non-stepper motors
   - Technical drawing/file of device/setup

2. **Procedural Metadata**
   - Name of rotation stage as used in experiment
   - Location of rotation stage as used in experiment
   - Description of direction of travel
   - Zero Position
   - Soft limits
   - Run mode (microstepping/full steps)

3. **Access/Security Metadata**

4. **Data**
   - Rotational position

### Mechanical Shutter (only template)

1. **Technical Metadata**
   - Manufacturer
   - Model name/number
   - Serial number
   - Calibration data
   - Last Calibration date
   - Technical drawing/file of device/setup

2. **Procedural Metadata**
   - Name of shutter as used in experiment
   - Location of shutter as used in experiment

3. **Access/Security Metadata**

4. **Data**
   - Shutter open or closed

### Electro-Optical Shutter (only template)

1. **Technical Metadata**
   - Manufacturer
   - Model name/number
   - Serial number
   - Calibration data
   - Last Calibration date
   - Technical drawing/file of device/setup

2. **Procedural Metadata**
   - Name of shutter as used in experiment
   - Location of shutter as used in experiment

3. **Access/Security Metadata**

4. **Data**
   - Shutter open or closed

### Spatial Filter

1. **Technical Metadata**
   - Manufacturer
   - Model name/number
   - Serial number
   - Operating Software and Version Number
   - Aperture shape
   - Aperture size
   - Technical drawing/file of device/setup

2. **Procedural Metadata**
   - Name of spatial filter as used in experiment
   - Location of spatial filter as used in experiment
   - Motion Control for XYZ position of spatial filter
     - Manufacturer
     - Model Name/Number
     - Serial Number
     - Channel 1
       - Step size / resolution
       - Motor Position
       - Current / Voltage
       - Frequency
     - Channel 2
       - Step size / resolution
       - Motor Position
       - Current / Voltage
       - Frequency
     - Channel 3
       - Step size / resolution
       - Motor Position
       - Current / Voltage
       - Frequency
   - Optical Setup and Focusing
     - F-number
     - Setup
     - Optic Specification
   - Vacuum Conditions
     - Setup
     - Pressure
     - Windows

3. **Access/Security Metadata** (changed based on experiment)

4. **Data**
   - Maybe link to NF/FF images before and after spatial filter

### Spectral Filter (only template)

1. **Technical Metadata**
   - Manufacturer
   - Model name/number
   - Serial number
   - Calibration data
   - Last Calibration date
   - Technical drawing/file of device/setup

2. **Procedural Metadata**
   - Location of filter as used in experiment

3. **Access/Security Metadata**

4. **Data**

### Amplitude Filter (only template)

1. **Technical Metadata**
   - Manufacturer
   - Model name/number
   - Serial number
   - Calibration data
   - Last Calibration date
   - Technical drawing/file of device/setup

2. **Procedural Metadata**
   - Location of filter as used in experiment

3. **Access/Security Metadata**

4. **Data**

### Polarizer Filter

1. **Technical Metadata**
   - Type: Linear polarizer, Half-waveplate, Quarter-waveplate, other
   - Manufacturer
   - Model name/number
   - Serial number
   - Material type
   - Spectral bandwidth
   - Extinction ratio (for linear polarizers)
   - Technical drawing/file of device/setup

2. **Procedural Metadata**
   - Location of filter as used in experiment
   - Orientation in experiment
   - FWHM Beam size into filter
   - Beam collimated, diverging, converging

3. **Access/Security Metadata**

4. **Data**

### Beam Splitter (only template)

1. **Technical Metadata**
   - Manufacturer
   - Model name/number
   - Serial number
   - Calibration data (e.g., transmission and reflection curves per polarization)
   - Last Calibration date
   - Coating specifications
     - Front surface
     - Rear surface
   - Technical drawing/file of device/setup
     - Diameter, thickness, substrate material

2. **Procedural Metadata**
   - Location of beam splitter as used in experiment

3. **Access/Security Metadata**

4. **Data**

### Generic Optic (only template)

Maybe needed if someone wants to put a glass wedge or window into a beamline for some purpose

(Does it also include generic elements like apodizers / apertures?)

1. **Technical Metadata**
   - Manufacturer
   - Model name/number
   - Serial number
   - Calibration data
   - Last Calibration date
   - Coating specifications per surface
   - Technical drawing/file of device/setup
     - Diameter, thickness, substrate material

2. **Procedural Metadata**
   - Location of generic optic as used in experiment

3. **Access/Security Metadata**

4. **Data**

## Targets

### Nozzle Target (Gas/Liquid/Cryogenic and Sheet/Filament/Droplet/Capillary)

1. **Technical Metadata**
   - Technical drawing of Nozzle/Cell/etc.
   - Nozzle’s Cone Angle
   - Nozzle’s Cone Length
   - Gas cell’s Exit Diameter
   - Gas cell’s Entrance Diameter
   - Surface Treatment
   - Valve’s Specifications
     - Manufacturer
     - Model Name
     - Serial Number
     - Gas mass flow calibration
     - Date of calibration
   - Valve + Nozzle Calibration data (neutral density map)
     - Method of calibration
     - Date of last calibration
   - Gas Controllers
     - Manufacturer
     - Model name/number
     - Serial number
     - Operating Software and Version number

2. **Procedural Metadata**
   - Name of target as used in experiment
   - Location of target used in experiment
   - Valve Timing values
     - Trigger time (relative to laser trigger)
     - Opening time
   - Position of Laser focus relative to a reference on the Nozzle Target
   - Material Used (gas type, liquid type)
   - Backing pressure

3. **Access/Security Metadata**

4. **Data**
   - Probably something from the Procedural Metadata like backing pressure and timings mapped to target density
   - Gas type

### Foil (Metal, Plastic, etc.)

1. **Technical Metadata**

2. **Procedural Metadata**

3. **Access/Security Metadata**

4. **Data**

### Wire (Metal, Plastic, etc.)

1. **Technical Metadata**

2. **Procedural Metadata**

3. **Access/Security Metadata**

4. **Data**

## Laser

### Laser Oscillator

1. **Technical Metadata**
   - Manufacturer
   - Model name/number
   - Serial number
   - Calibration data
   - Last Calibration date
   - Pump energy/current vs. time
   - Continuous Wave power
   - Mode-locked power
   - Manual or similar documentation
   - Technical drawing/file of device/setup

2. **Procedural Metadata**

3. **Access/Security Metadata**

4. **Data**
   - Output Power vs. time
   - Measured Spectrum (.txt, .csv)
     - FWHM spectrum
     - Central wavelength
   - Transverse Near-field profile (output)
     - Location measured
     - FWHM in horizontal and vertical directions
     - 2D array of pixel values
     - Calibration of µm/pixel

### Regenerative Amplifier

1. **Technical Metadata**
   - Manufacturer
   - Model name/number
   - Serial number
   - Calibration data
   - Last Calibration date
   - Active Medium
     - Manufacturer
     - Date of installation
     - Surface coating specifications
     - Material Type
     - Length
     - Parallel or wedged entrance/exit surfaces
   - Description of cooling system
   - Pump laser or Flashlamp Information
     - Manufacturer
     - Model name/number
     - Wavelength
     - Pulse duration
   - Pump energy/current vs. time
   - Pump timings
   - Pockels cell timings for seeded operation and Q-switch operation
   - Roundtrip time of cavity
   - Number of roundtrips
   - Manual or similar documentation
   - Technical drawing/file of device/setup

2. **Procedural Metadata**
   - Name of regenerative amplifier as used in laser
   - Location of regenerative amplifier as used in laser
   - Input parameters
     - Polarization
     - Pulse energy
     - Pulse duration
     - Transverse Near-field profile
       - Location measured
       - FWHM in horizontal and vertical directions
       - 2D array of pixel values
       - Calibration of µm/pixel
     - Far-field profile (if not in separate pointing diagnostic)
     - Measured spectrum
       - FWHM Spectrum
       - Central Wavelength

3. **Access/Security Metadata**

4. **Data**
   - Output parameters
     - Polarization
     - Pulse energy
     - Pulse duration
     - Transverse Near-field profile
       - Location measured
       - FWHM in horizontal and vertical directions
       - 2D array of pixel values
       - Calibration of µm/pixel
     - Far-field profile (if not in separate pointing diagnostic)
     - Measured Spectrum (.txt, .csv)
       - FWHM spectrum
       - Central wavelength

### Multi-pass Amplifier (pretty much same as regenerative amplifier)

1. **Technical Metadata**
   - Manufacturer
   - Model name/number
   - Serial number
   - Calibration data
   - Last Calibration date
   - Active Medium
     - Manufacturer
     - Date of installation
     - Surface coating specifications
     - Material Type
     - Length
     - Parallel or wedged entrance/exit surfaces
   - Description of cooling system
   - Pump laser or Flashlamp Information
     - Manufacturer
     - Model name/number
     - Wavelength
     - Pulse duration
   - Pump energy/current vs. time
   - Pump timings
   - Pockels cell timings for seeded operation and Q-switch operation
   - Traversal time of cavity
   - Number of passes through active medium
   - Manual or similar documentation
   - Technical drawing/file of device/setup

2. **Procedural Metadata**
   - Name of multi-pass amplifier as used in laser
   - Location of multi-pass amplifier as used in laser
   - Input parameters
     - Polarization
     - Pulse energy
     - Pulse duration
     - Transverse Near-field profile
       - Location measured
       - FWHM in horizontal and vertical directions
       - 2D array of pixel values
       - Calibration of µm/pixel
     - Far-field profile (if not in separate pointing diagnostic)
     - Measured spectrum
       - FWHM Spectrum
       - Central Wavelength

3. **Access/Security Metadata**

4. **Data**
   - Output parameters
     - Polarization
     - Pulse energy
     - Pulse duration
     - Transverse Near-field profile
       - Location measured
       - FWHM in horizontal and vertical directions
       - 2D array of pixel values
       - Calibration of µm/pixel
     - Far-field profile (if not in separate pointing diagnostic)
     - Measured Spectrum (.txt, .csv)
       - FWHM spectrum
       - Central wavelength

### OPA (OP-CPA) – sub-sume in MPA? Timings are highly critical, often single-pass

### Stretcher

1. **Technical Metadata**
   - Manufacturer
   - Model name/number
   - Serial number
   - Operating Software and version number
   - Center Wavelength
   - Start Wavelength of spectral transmission
   - End wavelength of spectral transmission
   - Angle of Incidence
   - Grating Separation distance from Center of Curvature (on optical axis for central wavelength)
   - Stretching ratio
   - Grating line density (type of grating, manufacturer, model number, etc.)
   - Clear Aperture Size
   - Clear Aperture Shape
   - Manual or similar documentation
   - Technical drawing/file of device/setup
   - Characterization/Measurements
   - Simulations

2. **Procedural Metadata**
   - Name of stretcher as used in laser
   - Location of stretcher as used in laser
   - Schematic of device’s setup
     - Geometrical Description
     - Optics Specification
   - Motion Control
     - Manufacturer
     - Model Name/Number
     - Serial Number
     - Channel 1…N
       - Description
       - Step size / resolution
       - Motor Position
       - Current / Voltage
       - Frequency

3. **Access/Security Metadata**

4. **Data**

### Compressor

1. **Technical Metadata**
   - Manufacturer
   - Model name/number
   - Serial number
   - Operating Software and version number
   - Center Wavelength
   - Start Wavelength of spectral transmission
   - End wavelength of spectral transmission
   - Grating Separation distance for central wavelength
   - Compression ratio
   - Grating line density
   - Clear Aperture Size
   - Clear Aperture Shape
   - Manual or similar documentation
   - Technical drawing/file of device/setup
   - Characterization/Measurements
   - Simulations

2. **Procedural Metadata**
   - Name of stretcher as used in laser
   - Location of stretcher as used in laser
   - Schematic of device’s setup
     - Geometrical Description
     - Optics Specification
   - Motion Control
     - Manufacturer
     - Model Name/Number
     - Serial Number
     - Channel 1…N
       - Description
       - Step size / resolution
       - Motor Position
       - Current / Voltage
       - Frequency

3. **Access/Security Metadata**

4. **Data**

### XPW System

1. **Technical Metadata**
   - Manufacturer
   - Model name/number
   - Serial number
   - Calibration data
   - Last Calibration date
   - Nonlinear Crystal
     - Manufacturer
     - Date of installation
     - Surface coating specifications
     - Material Type
     - Length
     - Parallel or wedged entrance/exit surfaces
   - Focusing optic
   - Location of nonlinear crystal relative to focus of focusing optic
   - Collimating optic
   - Vacuum pressure
   - Manual or similar documentation
   - Technical drawing/file of device/setup

2. **Procedural Metadata**
   - Name of the XPW stage as used in laser
   - Location of the XPW stage as used in laser
   - Input parameters
     - Polarization
     - Pulse energy
     - Pulse duration
     - Transverse Near-field profile
       - Location measured
       - FWHM in horizontal and vertical directions
       - 2D array of pixel values
       - Calibration of µm/pixel
     - Far-field profile (if not in separate pointing diagnostic)
     - Measured spectrum
       - FWHM Spectrum
       - Central Wavelength

3. **Access/Security Metadata**

4. **Data**
   - Output parameters
     - Polarization
     - Pulse energy
     - Pulse duration
     - Transverse Near-field profile
       - Location measured
       - FWHM in horizontal and vertical directions
       - 2D array of pixel values
       - Calibration of µm/pixel
     - Far-field profile (if not in separate pointing diagnostic)
     - Measured Spectrum (.txt, .csv)
       - FWHM spectrum
       - Central wavelength

## Probe

### Optical Probe Beam

1. **Technical Metadata**
   - Manufacturer or in-house design
   - Model name/number
   - Serial number
   - Operating software and version number
   - Calibration data
   - Last calibration date
   - Technical drawing/file of device/setup
   - Example of a Hollow-Core Fiber (HCF) system
     - Collimated FWHM Beam size before HCF
     - Focusing Length into HCF
     - Energy input into HCF
     - Energy output from HCF
     - Gas type in HCF
     - Gas pressure in HCF
     - Collimated FWHM beam size after HCF
     - Spectrum input to HCF
     - Spectrum output from HCF
     - HCF length
     - HCF inner diameter
     - HCF outer diameter
     - HCF material
     - Chirped Mirror Specifications

2. **Procedural Metadata**
   - Name of probe beam system as used in experiment
   - Location of probe beam system as used in experiment
   - Polarization at Target
   - FWHM pulse duration at Target
   - Pulse energy at Target
   - FWHM beam size at Target
   - Collimated, diverging or converging at Target
   - Spectrum at Target (if different than output from probe system)
   - Fourier Transformed or temporally chirped at target

3. **Access/Security Metadata**

4. **Data**
   - Depends on use of probe system in experiment
     - Camera image
     - Measured spectrum

### Particle Probe Beam

1. **Technical Metadata**
   - Manufacturer or in-house design
   - Model name/number
   - Serial number
   - Operating software and version number
   - Calibration data
   - Last calibration date
   - Type of particles
   - Energy spectrum of particles
   - FWHM pulse duration of particle beam

2. **Procedural Metadata**
   - Name of particle probe beam as used in experiment
   - Location of particle probe beam as used in experiment
   - Schematic of particle probe beam’s setup in experiment
   - Mediator target used?
     - Material
     - Thickness
     - Parameters of secondary beam

3. **Access/Security Metadata**

4. **Data**
   - Probably linked to a detector entity with an output image
