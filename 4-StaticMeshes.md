
<a name="4"></a>
<a name="Static Meshes"></a>
<a name="s"></a>
## 4. Статичные меши (Static Meshes) 

### Sections

> 4.1 [UVs](#s-uvs)

> 4.2 [LODs](#s-lods)

> 4.3 [Modular Socketless Snapping](#s-modular-snapping)

> 4.4 [Должна быть коллизия](#s-collision)

> 4.5 [Корректное масштабирование (Scale)](#s-scaled)

<a name="4.1"></a>
<a name="s-uvs"></a>
### 4.1 Static Mesh UVs

<a name="4.1.1"></a>
<a name="s-uvs-no-missing"></a>
#### 4.1.1 Все меши должны иметь UVs

<a name="4.1.2"></a>
<a name="s-uvs-no-overlapping"></a>
#### 4.1.2 Все меши должны иметь непересекающиеся UVs для карт освещения (Lightmaps) 

<a name="4.2"></a>
<a name="s-lods"></a>
### 4.2 LODs Should Be Set Up Correctly 

This is a subjective check on a per-project basis, but as a general rule any mesh that can be seen at varying distances should have proper LODs.

<a name="4.3"></a>
<a name="s-modular-snapping"></a>
### 4.3 Modular Socketless Assets Should Snap To The Grid Cleanly 

This is a subjective check on a per-asset basis, however any modular socketless assets should snap together cleanly based on the project's grid settings.

It is up to the project whether to snap based on a power of 2 grid or on a base 10 grid. However if you are authoring modular socketless assets for the marketplace, Epic's requirement is that they snap cleanly when the grid is set to 10 units or bigger.

<a name="4.4"></a>
<a name="s-collision"></a>
### 4.4 All Meshes Must Have Collision 

Regardless of whether an asset is going to be used for collision in a level, all meshes should have proper collision defined. This helps the engine with things such as bounds calculations, occlusion, and lighting. Collision should also be well-formed to the asset.

<a name="4.5"></a>
<a name="s-scaled"></a>
### 4.5 All Meshes Should Be Scaled Correctly 

This is a subjective check on a per-project basis, however all assets should be scaled correctly to their project. Level designers or blueprint authors should not have to tweak the scale of meshes to get them to confirm in the editor. Scaling meshes in the engine should be treated as a scale override, not a scale correction.

**[⬆ Back to Top](#s)**
