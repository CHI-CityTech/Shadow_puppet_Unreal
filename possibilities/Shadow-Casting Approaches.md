# **Unreal Engine Shadow Projection for Virtual Shadow Puppetry**

## **Overview**
In Unreal Engine, shadows interact with materials in specific ways, particularly when dealing with transparency. By default, transparent materials do not receive or cast proper shadows due to depth buffer limitations. This presents a challenge when simulating traditional shadow puppetry, where a light source projects shadows onto a semi-transparent screen.

This document explores two separate approaches to overcoming this issue:
1. **Fake Shadow Mesh Parent Approach** – Duplicating the puppet as a separate shadow entity with manual scaling.
2. **Decal-Based Shadow Projection Approach** – Using Unreal’s decal system to project shadows onto surfaces dynamically.

Each approach has strengths and trade-offs, which are discussed in detail below.

---

## **Why Standard Unreal Shadows Don't Work Well for This Case**

### **Challenges with Unreal's Default Shadow System**
1. **Specularity Issues on Partly Transparent Materials**
   - Unreal does not allow specularity on translucent objects, making it difficult to simulate the way light interacts with a semi-transparent shadow screen.

2. **Transparency and Shadows Don't Mix Well**
   - Transparent materials do not write to the depth buffer, meaning they do not properly receive or cast dynamic shadows.
   
3. **No Native Soft Shadows for Translucency**
   - Even with ray tracing, Unreal struggles to produce soft, realistic shadows on translucent objects.

### **Alternative Approaches**
Given these limitations, two practical workarounds are proposed:
- **Approach 1: Fake Shadow Mesh Parent**
  - Uses a duplicate mesh with an alpha-masked material to manually control shadow projection.
- **Approach 2: Decal-Based Shadow Projection**
  - Uses Unreal’s decal system to project a shadow-like texture onto the shadow-catching surface.

Each approach is detailed in the next sections.

---

# **Approach 1: Fake Shadow Mesh Parent**
## **Overview**
This method involves creating a **duplicate of the puppet** that acts as the shadow. The shadow object remains **locked to a fixed plane** (the projection surface) and scales dynamically based on the puppet's position relative to the light source.

### **Implementation Steps**
#### **Step 1: Create the Shadow Object**
1. Duplicate the puppet’s mesh.
2. Apply an **alpha-masked material** (not translucent) to allow soft edges.
3. Adjust the color to a dark gray/black to simulate a shadow.

#### **Step 2: Parent the Shadow to the Puppet**
1. Attach the shadow mesh as a **child** of the puppet in the **Outliner**.
2. Ensure that when the puppet moves, the shadow follows.
3. Disable shadow casting on the shadow mesh to prevent rendering issues.

#### **Step 3: Lock Z Position**
- Prevent the shadow from moving on the Z-axis by **locking its world location**.
- The shadow should always stay on the surface where shadows should be cast.

#### **Step 4: Scale the Shadow Based on Distance**
1. **Calculate Distance from Light Source**:
   - Use `Vector Length` between the puppet and the light.
2. **Apply a Scale Factor**:
   - The closer the puppet is to the light, the larger the shadow should be.
3. **Update Scale Dynamically** in **Blueprints** or **C++**.

#### **Step 5: Handle Rigging (If Needed)**
- If the puppet is rigged, create **separate shadow meshes** for each rigged part.
- Ensure that each shadow piece follows the corresponding bone.

---

# **Approach 2: Decal-Based Shadow Projection**
## **Overview**
Instead of using a separate shadow mesh, this approach projects a **decal** onto the surface below the puppet. The decal mimics the shape of the puppet’s shadow and dynamically adjusts based on movement.

### **Implementation Steps**
#### **Step 1: Enable Decals in Unreal**
1. Open **Project Settings** (`Edit → Project Settings`).
2. Search for **Decals**.
3. Enable **DBuffer Decals** (required for proper rendering).
4. Restart Unreal Engine if changes were made.

#### **Step 2: Create a Shadow Decal Material**
1. **Create a New Material** (`M_ShadowDecal`).
2. In the **Material Details Panel**:
   - Set **Material Domain** to `Deferred Decal`.
   - Set **Blend Mode** to `Translucent`.
   - Set **Decal Blend Mode** to `DBuffer Translucent Color, Normal, Roughness`.
3. **Import or create a shadow texture** (black silhouette of the puppet).
4. Connect the texture to **Base Color**.
5. Multiply the texture by an adjustable **Opacity Parameter** and connect it to **Opacity**.
6. Save the material.

#### **Step 3: Create a Decal Component**
1. Select the puppet in the **Outliner**.
2. Add a **Decal Component**.
3. Assign `"M_ShadowDecal"` as the material.
4. Adjust **Decal Size**:
   - Increase X/Y to match puppet dimensions.
   - Keep Z very small (`e.g., 10`) to limit projection depth.

#### **Step 4: Lock Decal to the Surface Below**
1. **Use a Line Trace to Find the Floor**:
   - In **Blueprints**, use `Line Trace by Channel` to find the ground below the puppet.
   - Set the **ShadowDecal’s position** to the **Impact Point**.
2. **Prevent Rotation Issues**:
   - Set **World Rotation** of the decal to match the floor normal.

#### **Step 5: Scale the Decal Based on Distance to Light**
1. **Detect Puppet-to-Light Distance**:
   - Use `Vector Length (Light Position - Puppet Position)`.
2. **Scale the Decal Dynamically**:
   - Multiply distance by a **scaling factor**.
   - Apply the result to the **Decal Component’s scale**.

#### **Step 6: Adjust Shadow Softness & Opacity**
1. Modify `"Shadow Opacity"` dynamically.
2. Add a **Multiply** node with `"Shadow Softness"` in the material to create **blurred edges**.

---

# **Comparison of Both Approaches**

| Approach                | Pros | Cons |
|-------------------------|------|------|
| **Fake Shadow Mesh**    | Full control, better for non-flat surfaces | Requires per-rigged part duplication |
| **Decal-Based Shadows** | Soft edges, auto-wraps to surfaces | Harder to blend with moving objects |

---

# **Final Thoughts**
Both approaches provide viable alternatives to Unreal’s default shadow system, which struggles with transparency. The choice depends on the project’s specific needs:
- Use **Fake Shadow Mesh** if you need **precise control over shadow behavior** and don’t mind extra geometry.
- Use **Decal-Based Shadows** if you want a **softer, more natural look** and can work with decal projection limitations.

For real-time performances, testing both approaches may be necessary to find the best balance of **visual fidelity and performance**.
