# Engineering Technical Journal: Turbofan Pylon Mount

## Project Overview & Phase Status
* [x] **Phase 1: Boundary Conditions & Vector Statics**
* [ ] **Phase 2: Parametric SolidWorks CAD & DFM Optimization**
* [ ] **Phase 3: Material Selection & Python Trade Study**
* [ ] **Phase 4: Structural Mass Optimization & Iteration**
* [ ] **Phase 5: ASME Y14.5 Manufacturing Drawings & GD&T**

## Phase 1: Boundary Conditions & Vector Statics
  Status: Completed

### 1. Objective
  * Define the 3D coordinate frame at the pylon-to-wing interface, resolve multi-axis engine forces into a single 3D resultant vector, and size the primary clevis pin under double-shear loading to meet the Factor of Safety constraint (FoS ≥ 2.0).

### 2. Applied Load Profile
  * Origin: Center of the primary wing attachment interface.

    +X (Longitudinal): Aircraft forward flight direction (Engine thrust axis).

    +Y (Vertical): Upward toward wing spar (Opposite gravity).

    +Z (Lateral): Outward along starboard wing.

  $$\vec{F}_{\text{thrust}} = 25\hat{i} + 0\hat{j} + 0\hat{k} \text{ kN}$$

  $$\vec{F}_{\text{weight}} = 0\hat{i} - 15\hat{j} + 0\hat{k} \text{ kN}$$
  
  $$\vec{F}_{\text{drag}} = 0\hat{i} + 0\hat{j} + 5\hat{k} \text{ kN}$$

  $$\vec{F}_{\text{total}} = 25\hat{i} - 15\hat{j} + 5\hat{k} \text{ kN}$$

### 3. Vector Analysis & Math Breakdown
* Applying the 3D Euclidean norm:

  $$F_{\text{resultant}} = \sqrt{(25)^2 + (-15)^2 + (5)^2} = \sqrt{625 + 225 + 25} = \sqrt{875} \approx 29.5804 \text{ kN}$$

### 4. Double-Shear Pin Sizing
* Material Basis: Al 7075-T6 Alloy ($\sigma_y = 503 \text{ MPa}$, $\tau_y \approx 290 \text{ MPa}$)

  * Allowable Shear Stress ($\text{FoS} = 2.0$):
  
  $$\tau_{\text{allow}} = \frac{\tau_y}{\text{FoS}} = \frac{290 \text{ MPa}}{2.0} = 145.0 \text{ MPa}$$
  
  * Minimum Required Pin Diameter:
  
  $$d_{\text{min}} = \sqrt{\frac{2 \cdot F_{\text{resultant}}}{\pi \cdot \tau_{\text{allow}}}} = \sqrt{\frac{2 \cdot 29580.4}{\pi \cdot 145.0}} \approx 11.3961 \text{ mm}$$

 ### 5. Hardware Selection & Operating Safety Margin

  * Nominal Pin Selected: $12.0 \text{ mm}$ off-the-shelf metric pin.
  * Pin Cross-Sectional Area: $A = \frac{\pi}{4}(12)^2 \approx 113.10 \text{ mm}^2$

  * Operating Shear Stress: 

  $$\tau_{\text{actual}} = \frac{29580.4}{2 \cdot 113.10} \approx 130.77 \text{ MPa}$$

  * Actual Operating FoS: 

  $$\text{FoS}_{\text{actual}} = \frac{290}{130.77} = 2.22 \quad (\ge 2.0 \text{ verified})$$

## Phase 2 Log: Parametric CAD Modeling & DFM
  Status: In Progress

  Entry pending feature tree creation and pocket geometry layout.
