# Engineering Report: Parametric Design and Structural Analysis of a Turbofan Engine Pylon Mount

**Author:** Christian Sultan (B1nary-Codes)  

**Domain:** Aerospace Structural Engineering & Design for Assembly (DFA)  

**Primary Material:** Aluminum 7075-T6 (density = 2.81 g/cm³, τ_allow = 145 MPa)

## 1. Executive Summary
Primary engine mounts are critical structural components that transfer multi-axis thrust, lift, and side loads from the turbofan propulsion system into the aircraft wing spar. Structural failure or improper fastener placement in these components can lead to catastrophic airframe separation or maintenance downtime.

This engineering deliverable details the parametric design, force resolution, fastener sizing, and Design for Assembly (DFA) optimization of an aerospace pylon mount executed in SolidWorks 2026. By resolving 3D Euclidean load vectors (F_resultant = 29.58 kN) and sizing double-shear clevis hardware, a design safety factor of FoS = 2.22 was achieved. Fastener counterbores were positioned on the underside flange overhang (10 mm edge offset) to allow bottom-up tool clearance and eliminate structural leg breakout. The final optimized part exhibits a total mass of 3.78 kg (3,779.97 g) with zero geometric sketch under-definitions or feature errors.

## 2. Static Load Resolution & Clevis Pin Sizing
Note: For orthographic layout views, geometric assembly relations, and load orientation diagrams, refer to assets/side_profile.png and assets/isometric_view.png.

### 2.1 3D Euclidean Load Summation
The mount experiences combined loads from engine thrust (Fx), side gust/yaw (Fy), and vertical lift/weight (Fz):

* Fx = 18.50 kN

* Fy = 8.20 kN

* Fz = 21.50 kN

The resultant 3D force vector applied to the lower clevis eyelet is calculated via vector norm:

* F_resultant = √(Fx² + Fy² + Fz²)

* F_resultant = √(18.50² + 8.20² + 21.50²) = 29.58 kN

### 2.2 Double-Shear Pin Sizing
The clevis pin operates in double shear across the dual leg structure. The minimum required pin area (A_pin) and diameter (d_pin) to prevent shear yield under allowable shear stress τ_allow = 145 MPa are:

* Shear Load per side (V) = F_resultant / 2 = 29.58 kN / 2 = 14.79 kN

* A_pin = V / τ_allow = 14,790 N / 145 N/mm² = 102.00 mm²

* d_min = √(4 * A_pin / π) = √(4 * 102.00 / π) = 11.40 mm

Selecting standard off-the-shelf hardware of d = 12.00 mm (A = 113.10 mm²) yields the following operational Factor of Safety:

* τ_actual = 14,790 N / 113.10 mm² = 130.77 MPa

* FoS = τ_allow / τ_actual = 145 MPa / 130.77 MPa = 2.22

## 3. Parametric CAD Architecture & DFA Optimization
### 3.1 Flange & Structural Leg Geometry
* Top Flange: 300 mm x 150 mm x 14 mm rectangular mounting base.

* Leg Span: 108 mm total outer width with an 80 mm central clevis channel cut, leaving two 14 mm thick structural side legs.

* Lug Eyelet: Ø 48 mm outer boss housing a concentric Ø 12.0 mm pin hole at coordinate offset X = 50 mm, Y = -141 mm.

### 3.2 Fastener Overhang & Clearance Math
Initial hole placement at 20 mm from the flange edge caused the 18 mm counterbores to intersect the outer leg walls (54 mm from center). Re-dimensioning to a 10 mm edge offset resolved all tool interference:

* Flange Outer Edge = 75.0 mm

* Hole Centerline = 75.0 mm - 10.0 mm = 65.0 mm

* Counterbore Inner Limit = 65.0 mm - 9.0 mm (radius) = 56.0 mm

* Outer Leg Boundary = 54.0 mm

* Clearance Gap = 56.0 mm - 54.0 mm = 2.0 mm (Zero Intersecting Geometry)

Note: For visual detail on fastener clearance, counterbore alignment, and bottom-up mounting orientation, refer to assets/bottom_counterbores.png.

### 3.3 Variable Fillet Strategy
Internal Clevis Channel (6 mm Radii): Positioned along primary leg-to-flange transition junctions to disperse bending stress under dynamic flight loads.

Outer Leg Junctions (2 mm Radii): Scaled down to prevent fillet material from encroaching on the 56 mm counterbore seating flat.

## 4. Mass Properties Breakdown
Final physical properties calculated in SolidWorks using Al 7075-T6 density (density = 2.81 g/cm³):

* Volume_Flange (Net) = 609,760 mm³ => Mass_Flange = 1,713.43 g

* Volume_Legs (Net) = 735,220 mm³ => Mass_Legs = 2,066.54 g

* Total Component Mass = 3,779.97 g (3.78 kg)

## 5. Conclusion & Aerospace Certification Upgrades
This project successfully proves the preliminary static viability, geometric definition, and DFA feasibility of a 3.78 kg turbofan engine pylon mount. For full commercial flight certification (FAA/EASA FAR Part 25), subsequent engineering phases require:

* Material Upgrade: Transitioning to Titanium Ti-6Al-4V for high-temperature turbine core exposure.

* Topology Optimization: Milling internal isogrid pockets into the 14 mm leg walls to reduce weight by 30%--40%.

* Fatigue & FEA Validation: Running dynamic stress intensity and spectrum fatigue life (S-N) cycles under high-frequency engine vibration.
