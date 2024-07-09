# Shader-Graphs-Part-1

I'm excited to share the process behind creating a dynamic texture effect using Unity's Shader Graph. This README outlines each step I took to achieve the animation similar to the script-based shader I developed in the Custom Shader assignment:

#### Script-Based Shader
![OriginalShader](https://github.com/hamidakhatri/Shader-Graphs-Part-1/assets/43552885/e5c33dff-3402-48aa-a1d1-7486297721ff)

#### Inpector Values
![ShaderInspector](https://github.com/hamidakhatri/Shader-Graphs-Part-1/assets/43552885/11b5f470-018f-464c-843f-c59b549ba4bb)

#### Script of Script-Based Shader
![OriginalShaderScript](https://github.com/hamidakhatri/Shader-Graphs-Part-1/assets/43552885/d416479e-a177-4da5-985e-6e2d6b1f09b6)

#### Shader Graph of the Script-Based Shader
![FinalShaderGraph](https://github.com/hamidakhatri/Shader-Graphs-Part-1/assets/43552885/2723bbd0-48b9-4a8f-b652-1787f814846c)

#### Full Shader Graph
![FullFinalShaderGraph](https://github.com/hamidakhatri/Shader-Graphs-Part-1/assets/43552885/41a31b96-ff3f-4367-a641-079ec9b2da07)

#### Magnified Parts of the Shader Graph
![Part1FinalShaderGraph](https://github.com/hamidakhatri/Shader-Graphs-Part-1/assets/43552885/0ebf17c3-fb6e-4330-957e-b4024dc1d619)
![Part2FinalShaderGraph](https://github.com/hamidakhatri/Shader-Graphs-Part-1/assets/43552885/318738c6-e3c0-47f0-922e-fa182fe17452)

### Step-by-Step Shader Graph Setup

#### 1. Starting with UV Coordinates
I began with a **UV node** to get the default UV coordinates from the geometry. This is essential as the basis for all subsequent texture manipulations.

#### 2. Splitting UVs
To manipulate the U and V coordinates independently, I used a **Split node**. This allowed me to apply effects separately to each component, enhancing control over the distortion effects.

#### 3. Applying Time-Based Distortion
The dynamic aspect of the shader comes from applying time-based changes:
- **Time Node**: I utilized the Time node to access Unity's continuously updating time value.
- **Sine and Cosine Functions**: I applied these functions to the time values to create naturalistic, oscillatory distortions across the UV map.

#### 4. Controlling Frequency and Amplitude
To fine-tune the distortion:
- **Multiply Nodes**: I controlled the frequency and amplitude by multiplying the time values before applying the sine and cosine functions. This step was crucial for matching the visual style and behavior seen in the original shader.

#### 5. Adding Distortion to UVs
After obtaining the modified wave outputs, I added them back to the original UV coordinates using **Add nodes**. This effectively combined the base texture placement with dynamic distortions.

#### 6. Combining Modified UVs
I then recombined the adjusted U and V components using a **Combine node**. This reassembled UV vector was crucial for the subsequent texture sampling, ensuring the distortions affected the final output.

#### 7. Texture Sampling
Using the **Sample Texture 2D Node**, I sampled the texture with the dynamically modified UVs. This is where the modified UVs were used to fetch the texture colors based on the dynamic distortions.

#### 8. Output to PBR Master
Finally, I directed the sampled texture color to the **PBR Master Node**. This step integrated the shader's visual effects into Unity's physically-based rendering pipeline, affecting how the material interacts with scene lighting and environmental factors.

### Conclusion
This shader graph setup exemplifies how to leverage Unity Shader Graph’s capabilities to create visually dynamic textures. By manipulating UV coordinates with time-based functions and adjusting parameters like frequency and amplitude, I achieved a visually appealing effect that enhances the realism and artistic flair of 3D objects in Unity.
