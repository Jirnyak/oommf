# OOMMF - How It Works (Simple Explanation)

## ✅ Your First Simulation Just Ran!

**What happened:** A 10nm × 10nm × 10nm magnetic cube was simulated for 0.1 nanoseconds.

## The 3 Most Important Things

### 1. **INPUT FILE** (.mif)
The `.mif` file tells OOMMF what to simulate:
- **Geometry**: Size of material (10nm × 10nm × 10nm)
- **Material**: Magnetic properties (permalloy)
- **Physics**: What forces act on magnetization

### 2. **SIMULATION** (boxsi command)
```bash
./oommf.tcl boxsi +fg minimal.mif -exitondone 1
```
- `boxsi` = the simulator program
- `+fg` = run in foreground (see output)
- `-exitondone 1` = quit when finished

### 3. **OUTPUT FILES** (.omf)
Results saved as `minimal-*.omf` files:
- Each file = magnetization at one time step
- Contains: magnetic field direction at each point
- You got ~40 files = 40 time steps

---

## Step-by-Step: What Each Part Does

### Step 1: Define Geometry
```tcl
Specify Oxs_BoxAtlas:atlas {
  xrange {0 10e-9}    # 10 nanometers in X
  yrange {0 10e-9}    # 10 nanometers in Y
  zrange {0 10e-9}    # 10 nanometers in Z
}
```
**What it does:** Creates a 10×10×10 nm box of magnetic material.

### Step 2: Define Mesh (Grid)
```tcl
Specify Oxs_RectangularMesh:mesh {
  cellsize {5e-9 5e-9 5e-9}  # Divide into 5nm cells
}
```
**What it does:** Splits the box into 2×2×2 = 8 smaller cubes.
- Each cube is 5nm × 5nm × 5nm
- Simulation calculates magnetization in each cube

### Step 3: Material Properties

#### Exchange Energy
```tcl
Specify Oxs_UniformExchange {
  A 1.3e-11  # Exchange constant
}
```
**What it does:** Neighboring magnetic moments want to point the same direction.

#### Demagnetization
```tcl
Specify Oxs_Demag {}
```
**What it does:** Material creates its own magnetic field (shape matters).

### Step 4: Dynamics (How Magnetization Moves)
```tcl
Specify Oxs_RungeKuttaEvolve:evolve {
  alpha 0.5  # Damping (how fast it settles down)
}
```
**What it does:** Solves the **Landau-Lifshitz-Gilbert (LLG) equation**:
$$\frac{d\mathbf{m}}{dt} = -\gamma \mathbf{m} \times \mathbf{H} + \alpha \mathbf{m} \times \frac{d\mathbf{m}}{dt}$$

Where:
- $\mathbf{m}$ = magnetization direction
- $\mathbf{H}$ = effective magnetic field
- $\alpha$ = damping parameter (0.5 = high damping)
- $\gamma$ = gyromagnetic ratio

### Step 5: Initial State
```tcl
Specify Oxs_UniformScalarField:Ms {
  value 8e5  # Saturation magnetization (A/m)
}

Specify Oxs_UniformVectorField:start {
  vector {1 0 0}  # Start pointing in X direction
}
```
**What it does:** At time = 0, all magnetization points to the right (+X).

### Step 6: Run Simulation
```tcl
Specify Oxs_TimeDriver {
  stopping_time 1e-10  # 0.1 nanoseconds
  basename minimal
}
```
**What it does:** Runs the simulation for 0.1 ns, saves results.

---

## What the Simulation Did

1. **Started**: All magnetic moments pointing right (→)
2. **Evolved**: Magnetization changed over time due to:
   - Exchange energy (neighbors want to align)
   - Demagnetization (shape creates internal field)
   - Damping (energy dissipates)
3. **Saved**: Magnetization at each time step to `.omf` files

---

## View Your Results

### Check the data:
```bash
cd ~/oommf

# View first magnetization file
head -50 minimal-Oxs_TimeDriver-Magnetization-00-0000001.omf

# Count how many time steps
ls minimal-*.omf | wc -l
```

### Visualize (optional):
```bash
# Launch OOMMF GUI viewer
./oommf.tcl mmDisp minimal-Oxs_TimeDriver-Magnetization-00-0000010.omf
```

---

## Key Concepts

### Mesh = Grid
- Material divided into cells
- Each cell has uniform magnetization
- Smaller cells = more accurate (but slower)

### Time Evolution
- LLG equation tells magnetization how to move
- OOMMF calculates this step by step
- Each step saved to file

### Energy Minimization
- System tries to minimize total energy
- Competing energies:
  - Exchange: wants uniform alignment
  - Demagnetization: wants to close flux
  - External field: wants alignment with field (if applied)

---

## Most Common Modifications

### Make it bigger:
```tcl
xrange {0 100e-9}  # 100nm instead of 10nm
```

### Run longer:
```tcl
stopping_time 1e-9  # 1 nanosecond instead of 0.1 ns
```

### Add external field:
```tcl
Specify Oxs_FixedZeeman {
  field {0.01 0 0}  # 0.01 Tesla in X direction
}
```

### Change material:
```tcl
# Iron instead of permalloy
Specify Oxs_UniformScalarField:Ms {
  value 1.7e6  # Iron saturation magnetization
}
```

---

## Summary

**You just simulated:**
- 10nm × 10nm × 10nm magnetic cube
- Starting magnetization: pointing right
- Physics: Exchange + demagnetization + damping
- Duration: 0.1 nanoseconds
- Result: ~40 snapshots of magnetization evolution

**The simulation solved the LLG equation** to show how magnetization changes over time! 🎉
