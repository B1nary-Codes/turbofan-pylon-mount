# Turbofan Engine Pylon Mount Design & Structural Analysis

Parametric 3D CAD design, static vector load resolution, and Design for Assembly (DFA) optimization for a 7075-T6 aluminum aircraft turbofan engine pylon mount using SolidWorks.

## Benchmark & Structural Specifications

Evaluated against 3D static load vectors (Fx = 18.5 kN, Fy = 8.2 kN, Fz = 21.5 kN) under double-shear pin loading and under-wing bolt mounting constraints:

| Parameter | Specification | Engineering Rationale |
| :--- | :--- | :--- |
| **Material** | Al 7075-T6 (density = 2.81 g/cm³) | High yield strength (σy = 503 MPa, τ_allow = 145 MPa) for aerospace primary structures |
| **Resultant Load** | F_resultant = 29.58 kN | Derived via 3D Euclidean vector norm from multi-axis engine thrust and aerodynamic forces |
| **Clevis Pin Hardware** | Ø 12.0 mm (Al alloy) | Double-shear installation yields Factor of Safety FoS = 2.22 against yield shear |
| **Fastener Array** | 8x M10 Socket Head Counterbores | Positioned on underside overhang (10 mm edge offset, 80 mm pitch) for bottom-up assembly |
| **Fillet Geometry** | 6 mm Internal / 2 mm Outer | Variable radius allocation balances channel stress relief with flat bolt seating lands |
| **Final Component Mass** | 3.78 kg (3,779.97 g) | Verified via SolidWorks mass properties and analytical volumetric breakdown |

## Key Design Decisions

- **3D Euclidean Load Resolution:** Aggregated multi-axis engine loads into a resultant force vector F_resultant = 29.58 kN to establish exact stress baselines for double-shear clevis hardware.
- **Bottom-Up Fastener Orientation:** Positioned fastener counterbores on the underside face of the flange overhang, enabling technicians to install and torque M10 bolts directly beneath the aircraft wing spar.
- **Clearance Offset Optimization:** Shifted hole centers to a 10 mm edge offset (65 mm centerline offset), placing the 18 mm counterbores cleanly in open air while providing 11 mm clearance from outer leg walls.
- **Asymmetric Fillet Allocation:** Applied 6 mm internal fillets within the 80 mm clevis channel to minimize stress concentrations under dynamic bending, while reducing outer junction fillets to 2 mm to prevent counterbore interference.
- **Neutral Format Export:** Generated a standard .STEP artifact alongside native .SLDPRT files to allow zero-dependency 3D browser viewing directly within GitHub.

## Project Structure

```text
turbofan-engine-pylon-mount/
├── assets/
│   ├── bottom_counterbores.png
│   ├── isometric_view.png
│   └── side_profile.png
├── models/
│   ├── pylon_mount.SLDPRT   # Native SolidWorks 2026 part file
│   └── pylon_mount.STEP     # Neutral 3D CAD exchange format
├── .gitignore               # Excludes SW lock files & Python cache
├── Engineering_Report.md    # Formal structural & manufacturing report
├── LICENSE                  # MIT License
├── PROJECT_LOG.md           # Engineering decision tracking & change log
├── README.md                # Main portfolio showcase & landing page
└── requirements.txt         # Dependencies for analytical verification
```
##Quickstart
```bash
# Clone repository
git clone [https://github.com/B1nary-Codes/turbofan-engine-pylon-mount.git](https://github.com/B1nary-Codes/turbofan-engine-pylon-mount.git)
cd turbofan-engine-pylon-mount

# Setup Python environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt

# Run analytical load & mass verification scripts
python src/vector_math.py
python src/pin_sizing.py
python src/mass_calculator.py
