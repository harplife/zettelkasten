
## Interaction of Light and Material

## Properties of Light

Main properties :
- Reflection
- Absorption
- Transmission
- Scattering

Special properties :
- Emission


### Reflection

Light bounces off the surface.

- Happens at the boundary between two materials (air --> solid)
- Can be :
	- Specular (mirror-like)
	- Diffuse (scattered)
- What controls it :
	- Surface smoothness
	- Electron mobility
	- Refractive index

#### Specular Reflection

- Light reflects almost immedicately
- Direction preserved

This gives highlights and mirrors


#### Diffuse Reflection

- Light enters slightly
- Bounces between molecules
- Exits randomly

This is why matte surfaces look matte.

> [!note] So is this direct result of texture? How can metals have matte finish?


### Absorption

Light energy is taken in by the material.

- Energy goes into :
	- Electron excitation
	- Molecular vibration (heat)
- Results :
	- Material appears colored (mix of reflection and absorption)
	- Material heats up


### Transmission

Light passes through the material.

- Happens in :
	- Glass
	- Water
	- Plastic
	- Skin (partially)
- Can be :
	- Clear (straight through)
	- Tinted (some wavelengths absorbed or scattered)

> [!warning] Light does *not* pass through without interacting at all.
> Even transparent materials interact, but just weakly.


#### Refraction

- Light bends as it enters or exits a material
- Caused by speed change inside the material

Important for :
- Lenses
- Glass
- Water
- Eyes


### Scattering

Light changes direction inside the material.

> [!note] How does it relate to refraction?
> Or is scattering specifically collision with electrons?

- Can be :
	- Forward
	- Backward
	- Sideways
- Results :
	- Milk looks white
	- Skin looks soft
	- Marble glows at edges


#### Subsurface Scattering (SSS)

SSS occurs because :
- Light enters
- Scatters internally (bounces between molecules)
- Exits somewhere else

This happens because :
- Molecules are semi-transparent
- Bonds vibrate and redirect photons

In chemistry terms :
- Partial absorption
- Molecular vibration
- Non-uniform scattering

Critical for :
- Skin
- Wax
- Leaves
- Food


### Emission

The material produces light itself.

Examples :
- LEDs
- Fire
- Hot metal (incandescence) & blackbody radiation

Chemically :
- Excited electrons drop energy levels
- Emit photons


## Properties of Material

Light interacts with electrons in atoms and molecules.

These electrons can :
- Oscillate
- Jump between energy levels
- Dissipate energy as heat

> [!important] Different materials = different electron structures = different visual responses.


### Metals

- Electrons are **delocalized** (free-ish electrons)
- Incoming light makes electrons oscillate collectively
- Results :
	- Strong reflection
	- Color mostly comes from the light source (color in the reflection, not the base)
	- Sharp highlights
	- High specular & low diffuse

> [!important] Metallic bonds + electron sea --> mirror-like behavior


### Non-metals

- Examples
	- Wood
	- Plastic
	- Skin
- Electrons are **bound** in molecules
- Light penetrates a bit, scatters, then exits
- Some wavelengths are absorbed --> color

This leads to :
- Diffuse reflection
- Softer highlights
- Subsurface scattering (for skin, wax, milk)

Chemistry decides :
- Which wavelengths are absorbed
- How deep light penetrates
- How random the scattering is

### Why "Color" is a Chemical Property

When you see red paint :
- The molecules absorb blue & green light
- Red wavelengths are reflected

That absorption depends on :
- Molecular structure
- Electron energy gaps
- Bonding patterns

Physically Based Rendering (PBR) works because it respects chemical reality.

Key assumptions :
- Energy conservation
- Microfacet theory
- Fresnel effects

> [!important] All of these trace back to how electrons in matter respond to electromagnetic waves.


Chemistry topics that affect light :
- Atomic orbitals --> light absorption
- Energy levels --> color
- Bonding --> transparency vs. opacity
- Vibrational modes --> scattering & heat
- States of matter --> surface roughness


## Hierarchy of Particles

Smallest --> Largest

1. Subatomic particles
	- Electrons
	- Protons
	- Neutrons
2. Atoms
	- One nucleus (protons + neutrons)
	- Surrounded by electrons
3. Molecules
	- Two or more atoms bonded together

An "element" is not a physical object. It describes the type of an atom, which is defined by the number of protons in the atom.

Examples :
- Hydrogen = atoms with 1 proton
- Carbon = atoms with 6 protons
- Oxygen = atoms with 8 protons

A molecule is a structured combination of atoms.
- A single atom can be called a molecule (e.g. noble gases)
- A solid may not have discrete molecules (e.g. metals, crystals)


## Molecular Structure

Molecules (and atoms) have preferred ways of bonding. These preferences lead to specific structures.
- This preference is due to energy minimization.

Bonding is constraint-based optimization. Atoms and molecules arrange themselves to :
- Lower total energy
- Satisfy electron constraints
- Balance attractive and repulsive forces

There are two levels of structure :
- Atomic bonding --> molecules
- Molecule-to-molecule interactions --> Materials

---
Level 1 : Atomic boding --> molecules

Atoms bond to form molecules (e.g. $H_{2}O$, $CO_{2}$).

These bonds are :
- Directional
- Quantized
- Geometry-specific

For example, water ($H_{2}O$) forms a bent shape.

![[Pasted image 20260111115024.png | center | 500]]

Carbon forms tetrahedral or planar structures.


Electron geometries + molecular geometries
![[Pasted image 20260111115425.png]]

