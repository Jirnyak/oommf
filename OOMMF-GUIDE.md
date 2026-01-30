# OOMMF Installation and Usage Guide for macOS

## What is OOMMF?

**OOMMF** (Object Oriented MicroMagnetic Framework) is the best alternative to mumax3 for macOS. It solves the **Landau-Lifshitz-Gilbert equation** for micromagnetic simulations on CPU (no NVIDIA GPU required).

## Installation Status

✅ **OOMMF is now installed and working on your Mac!**

Location: `~/oommf/`

## Quick Start

### Run a simulation:
```bash
cd ~/oommf
./oommf.tcl boxsi +fg your-file.mif -exitondone 1
```

### Example simulation file created:
`~/oommf-example.mif` - A simple 100nm x 100nm x 10nm permalloy square

### Run the example:
```bash
cd ~
~/oommf/oommf.tcl boxsi +fg oommf-example.mif -exitondone 1
```

### View results:
```bash
# Output data table
cat ~/oommf-example.odt

# Or use OOMMF's data viewer
~/oommf/oommf.tcl mmDataTable oommf-example.odt
```

## Key Differences from mumax3

| Feature | mumax3 | OOMMF |
|---------|--------|-------|
| **Platform** | NVIDIA GPU (CUDA) | CPU (any Mac) |
| **Speed** | Very fast (GPU) | Slower (CPU) |
| **Input Format** | .mx3 scripts | .mif files |
| **Language** | Go-like syntax | Tcl-based |
| **LLG Equation** | ✅ Yes | ✅ Yes |

## MIF File Structure

OOMMF uses MIF (Micromagnetic Input Format) files:

```tcl
# Define geometry
Specify Oxs_BoxAtlas:atlas {
  xrange {0 100e-9}
  yrange {0 100e-9}
  zrange {0 10e-9}
}

# Define mesh
Specify Oxs_RectangularMesh:mesh {
  cellsize {5e-9 5e-9 5e-9}
  atlas :atlas
}

# Exchange interaction
Specify Oxs_UniformExchange {
  A 1.3e-11  # Exchange constant (J/m)
}

# Demagnetization
Specify Oxs_Demag {}

# LLG Dynamics
Specify Oxs_RungeKuttaEvolve:evolve {
  alpha 0.5        # Damping parameter
  gamma_G 2.211e5  # Gyromagnetic ratio
}

# Initial magnetization
Specify Oxs_UniformScalarField:Ms {
  value 8e5  # Saturation magnetization (A/m)
}

Specify Oxs_UniformVectorField:start {
  norm 1
  vector {1 0 0}  # Initial direction
}

# Time driver
Specify Oxs_TimeDriver {
  evolver :evolve
  stopping_time 1e-9
  mesh :mesh
  Ms :Ms
  m0 :start
  basename output-name
}
```

## Common OOMMF Commands

```bash
# Launch OOMMF GUI
~/oommf/oommf.tcl

# Run simulation (batch mode)
~/oommf/oommf.tcl boxsi +fg file.mif -exitondone 1

# View data tables
~/oommf/oommf.tcl mmDataTable output.odt

# View vector fields (magnetization)
~/oommf/oommf.tcl mmDisp output.omf

# Convert mumax3 to OOMMF (you'll need to adapt manually)
# mumax3 uses .mx3, OOMMF uses .mif - syntax is different
```

## Documentation

- **Official OOMMF Manual**: [https://math.nist.gov/oommf/doc/](https://math.nist.gov/oommf/doc/)
- **Standard Problems**: `~/oommf/app/oxs/examples/`
- **More examples**: `~/oommf/app/oxs/local/`

## Performance Tips

1. **Use more threads**: Set `OOMMF threads` in platform config
2. **Optimize cell size**: Smaller cells = more accurate but slower
3. **Use appropriate solvers**: RK4 vs. Euler for different problems
4. **Profile your code**: OOMMF has built-in timing

## Alternative: Ubermag (Python Interface)

If you prefer Python, consider **Ubermag** which uses OOMMF as a backend:

```bash
pip install ubermag
```

Then write simulations in Python:
```python
import ubermag as um
# Much easier syntax than MIF files!
```

## Summary

✅ **OOMMF successfully installed and tested**
✅ **Solves Landau-Lifshitz-Gilbert equation**
✅ **Works natively on macOS (M2 Pro)**
✅ **Example simulation runs successfully**

Your example simulation output is in: `~/oommf-example.odt`
