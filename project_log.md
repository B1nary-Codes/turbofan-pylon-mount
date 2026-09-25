# Engineering Log: Turbofan Engine Pylon Mount Design & CAD Architecture

## System Architecture Log

### 01. Codebase & Directory Decoupling
models/ — Native SolidWorks CAD source (pylon_mount.SLDPRT) and neutral 3D CAD exchange files (pylon_mount.STEP).

assets/ — High-resolution orthographic renders, dimension layouts, and fastener clearance callouts.

Root Directory — Core engineering documentation (README.md, Engineering_Report.md, PROJECT_LOG.md), open-source license (LICENSE), and version control configuration (.gitignore).

### 02. Multi-Axis Load Vector Resolution
Primary pylon mounts experience combined thrust, aerodynamic side-slip, and vertical G-load vectors transferred through the engine core fitting:

* Thrust Force (Fx): 18.50 kN

* Side/Yaw Force (Fy): 8.20 kN

* Lift/Weight Force (Fz): 21.50 kN

Aggregating these components into a 3D Euclidean vector norm established the absolute static design load applied to the lower clevis eyelet:

* F_resultant = √(Fx² + Fy² + Fz²)

* F_resultant = √(18.50² + 8.20² + 21.50²) = 29.58 kN

### 03. Clevis Pin Double-Shear Sizing
The lower attachment uses a double-shear clevis joint across two structural legs. 
For Al 7075-T6 alloy with an allowable shear yield strength of τ_allow = 145 MPa:

* Shear force per lug wall: V = F_resultant / 2 = 14.79 kN

* Minimum shear area: A_min = V / τ_allow = 14,790 N / 145 N/mm² = 102.00 mm²

* Minimum pin diameter: d_min = √(4 * 102.00 / π) = 11.40 mm

Selecting standard hardware with Ø 12.0 mm diameter (A = 113.10 mm²) establishes the working shear stress and safety factor:

* τ_actual = 14,790 N / 113.10 mm² = 130.77 MPa

* Factor of Safety (FoS) = τ_allow / τ_actual = 145 MPa / 130.77 MPa = 2.22

### 04. Parametric Geometry & Feature Tree
Built a fully constrained 3D parametric model in SolidWorks using a top-down feature hierarchy:

* Top Flange: 300 mm x 150 mm x 14 mm base plate extruded from Mid Plane.

* Leg Profile: 141 mm vertical drop with sloped walls (48° front slope, 62° rear slope), centered at X = 50 mm offset from flange center.

* Lug Eyelet: Ø 48 mm outer boss housing the concentric Ø 12.0 mm pin hole.

* Clevis Channel Cut: 80 mm central extrusion cut across a 108 mm total outer leg span, establishing two 14 mm thick structural side legs.

### 05. Fastener Overhang & Clearance Debugging
Initial fastener layout positioned 8x M10 counterbored clearance holes at a 20 mm edge offset on the top flange face:

* Failure Mode: Top Flange half-width is 75 mm. A 20 mm edge offset placed hole centerlines at X = 55 mm from origin.

* Conflict: The inner edge of the Ø 18 mm counterbore (9 mm radius) extended inward to X = 46 mm (55 - 9 = 46 mm), intersecting the outer leg wall located at X = 54 mm. This resulted in severe material breakout along the structural legs.

### 06. DFA Optimization & Tool Clearance Resolution
Applied Design for Assembly (DFA) principles to resolve geometric interference and tool access constraints:

* Dimension Adjustment: Shifted hole edge offset from 20 mm down to 10 mm (X = 65 mm centerline offset).

* Clearance Math: Counterbore inner edge = 65 mm - 9 mm = 56 mm. With the outer leg wall at 54 mm, this leaves a clean 2.0 mm flat clearance gap (56 mm - 54 mm = 2 mm).

* Plane Reassignment: Flipped the sketch plane to the underside flange face using Edit Sketch Plane. This positions bolt heads underneath the overhang, enabling technicians to insert M10 socket head bolts and apply torque wrenches directly below the aircraft wing spar.

### 07. Asymmetric Fillet Strategy
Transition radii were allocated based on local mechanical stress states and geometric seating limits:

* Internal Channel Fillets (6 mm): Applied along internal leg-to-flange junction corners to eliminate stress risers under dynamic bending loads.

* Outer Junction Fillets (2 mm): Scaled down from 6 mm to 2 mm along outer leg transitions. A 6 mm fillet would extend outward to X = 60 mm (54 + 6 = 60 mm), encroaching 4 mm into the counterbore seating flat (X = 56 mm). The 2 mm radius meets the counterbore boundary tangentially without compromising bolt head seating.

### 08. Analytical Mass Verification Audit
Cross-verified SolidWorks Mass Properties against manual volumetric breakdowns for 7075-T6 Aluminum (density = 2.81 g/cm³):

* Net Flange Volume: 609,760 mm³ (300 x 150 x 14 mm minus 8x counterbored M10 holes) => 1,713.43 g

* Net Legs Volume: 735,220 mm³ (dual 14 mm legs with Ø 48 mm boss, sloped walls, fillets, minus Ø 12 mm hole) => 2,066.54 g

Total Calculated Mass: 1,713.43 g + 2,066.54 g = 3,779.97 g (3.78 kg)

CAD Audit Match: SolidWorks mass properties report exactly 3,779.97 g (0.00% discrepancy).

### 10. Portfolio Asset Generation & STEP Export
STEP Format Export: Generated models/pylon_mount.STEP (AP203/214 neutral CAD) to allow 3D model interaction directly inside GitHub's browser interface without needing local SolidWorks software.

Documentation Renders: Rendered isometric 3D views (assets/isometric_view.png), side profile dimension layouts (assets/side_profile.png), and underside fastener clearance details (assets/bottom_counterbores.png) for portfolio presentation.
