**Overview of the DrivAerNet++ Dataset**

DrivAerNet++ is a large-scale, multimodal car dataset designed to advance research in aerodynamic car design, computational fluid dynamics (CFD) simulations, and deep learning applications. It consists of **8,000 diverse car designs** that have been modeled using high-fidelity CFD simulations. The dataset includes various car configurations such as fastback, notchback, and estateback, along with different underbody and wheel designs to represent both internal combustion engine (ICE) and electric vehicles (EV).

**Purpose and Significance**

The primary goal of DrivAerNet++ is to provide a comprehensive resource that enables:

- **Data-Driven Design Optimization**: Facilitating the optimization of car designs based on aerodynamic performance metrics.
- **Generative AI Applications**: Training generative models to create new car designs that balance performance and aesthetics.
- **Surrogate Modeling**: Predicting aerodynamic performance without the need for full CFD simulations, thus saving computational resources.
- **CFD Simulation Acceleration**: Speeding up simulations using machine learning and multi-GPU techniques.
- **Reduced Order Modeling**: Creating data-driven reduced-order models for efficient aerodynamic simulations.
- **Large-Scale Data Handling**: Managing and storing large datasets derived from high-fidelity simulations.
- **Part and Shape Classification**: Enhancing design analysis by classifying car categories or components.
- **Automated CFD Meshing**: Streamlining simulations by automating the meshing process based on car components.

---

**Explanation of the Dataset Features**

Each car design in DrivAerNet++ is parametrized with **26 geometric design parameters** that fully describe the vehicle's geometry. These parameters were carefully selected for their significant impact on aerodynamics and were varied within specific ranges to avoid impractical or aesthetically unappealing designs. The features were collected through a combination of **morphing boxes** and **direct morphing** methods.

Below is a detailed explanation of some key features from the dataset snippet you provided:

1. **Experiment**: A unique identifier for each car design or simulation case.

2. **B_Ramp_Angle**: The angle of the ramp at the rear underbody of the car, influencing airflow separation and rear-end lift.

3. **B_Diffusor_Angle**: The angle of the diffuser located at the car's underbody rear, affecting underbody airflow and downforce.

4. **B_Trunklid_Angle**: The inclination angle of the trunk lid, impacting the wake region and aerodynamic drag.

5. **C_Side_Mirrors_Rotation**: The rotational angle of the side mirrors, which can affect airflow around the side of the vehicle.

6. **D_Rear_Window_Inclination**: The angle of the rear window relative to the horizontal plane, influencing airflow separation over the rear of the car.

7. **D_Windscreen_Inclination**: The angle of the front windscreen, affecting frontal airflow and pressure distribution.

8. **C_Side_Mirrors_Translate_X**: The horizontal (longitudinal) position of the side mirrors along the X-axis, altering their interaction with the airflow.

9. **C_Side_Mirrors_Translate_Z**: The vertical position of the side mirrors along the Z-axis.

10. **D_Windscreen_Length**: The length of the front windscreen, which can affect the curvature and flow attachment.

11. **D_Rear_Window_Length**: The length of the rear window, influencing the slope and flow behavior over the rear.

12. **E_A_B_C_Pillar_Thickness**: The thickness of the car's structural pillars (A, B, and C pillars), which can impact side airflow and structural integrity.

13. **G_Trunklid_Curvature**: The curvature of the trunk lid, affecting the flow separation and pressure recovery at the rear.

14. **G_Trunklid_Length**: The length of the trunk lid.

15. **H_Front_Bumper_Curvature**: The curvature of the front bumper, influencing airflow attachment and pressure distribution at the front.

16. **H_Front_Bumper_Length**: The length of the front bumper.

17. **F_Door_Handles_Thickness**: The thickness of the door handles, which may have minor effects on local airflow.

18. **F_Door_Handles_Z_Position**: The vertical position of the door handles along the Z-axis.

19. **E_Fenders_Arch_Offset**: The offset of the fender arches, affecting wheel well airflow and possibly the overall drag.

20. **A_Car_Length**: The overall length of the car, a primary geometric parameter.

21. **F_Door_Handles_X_Position**: The horizontal (longitudinal) position of the door handles along the X-axis.

22. **A_Car_Width**: The overall width of the car.

23. **A_Car_Roof_Height**: The height of the car's roof from the ground.

24. **A_Car_Green_House_Angle**: The angle of the greenhouse (the upper part of the car body), affecting the aerodynamic profile and cabin space.

---

**Collection and Simulation Methodology**

- **Design Parameter Variation**: The features were collected by parametrically varying each design parameter within carefully selected ranges. These ranges were chosen to ensure that all generated designs are both manufacturable and aesthetically pleasing.

- **Morphing Techniques**:

  - **Morphing Boxes**: Adjusting predefined regions of the car's geometry to create variations.
  - **Direct Morphing**: Directly altering specific geometric features for finer control.

- **High-Fidelity CFD Simulations**: Each design underwent a detailed CFD simulation to compute aerodynamic performance metrics like drag coefficient (Cd) and lift coefficient (Cl).

- **Computational Resources**: Simulations were conducted on the MIT Supercloud, utilizing 60 nodes totaling 2,880 CPU cores. Each CFD case used 256 cores and 1,000 GB of memory, requiring approximately **3 million CPU-hours** in total.

---

**Dataset Modalities and Contents**

The DrivAerNet++ dataset is comprehensive, including multiple data modalities to support a variety of research applications:

- **Parametric Models**: Tabular data containing the 26 design parameters for each car, facilitating statistical analysis and machine learning model training.

- **Point Cloud Data**: 3D point clouds representing the car surfaces, useful for geometric deep learning methods.

- **3D Car Meshes**: Detailed mesh files (e.g., STL files) for each car design, suitable for simulations and CAD applications.

- **CFD Simulation Data**: High-fidelity simulation results, including:

  - **3D Volumetric Fields**: Detailed flow fields around the car.
  - **Surface Fields**: Pressure and shear stress distributions on the car's surface.
  - **Streamlines**: Visual representations of airflow patterns.

- **Aerodynamic Coefficients**: Key performance indicators like Cd and Cl for each design.

- **Annotations**: Detailed labels for 29 different car components, aiding tasks like semantic segmentation and object detection.

---

**Additional Valuable Information**

- **Dataset Diversity**: Emphasizes the importance of shape variation to develop robust deep learning models capable of generalizing across different car designs. By providing a wide range of car shapes and configurations with high-fidelity CFD, DrivAerNet++ enables models to generalize better, supports exploration of unconventional designs, and enhances understanding of how geometric features impact aerodynamic performance.

- **Computational Cost**: Highlights the significant computational effort invested, making the dataset particularly valuable for research that cannot afford such resources.

- **Applications in Competitions**: DrivAerNet has been utilized in the IJCAI 2024 competition, with competitors' code and results available in an open-source repository.

- **Integration with Tools**: The dataset is integrated into platforms like NVIDIA Modulus, facilitating its use in simulation workflows.

- **Dataset Size**: The full dataset requires **39 TB** of storage space, indicating its comprehensiveness.

- **License and Commercial Use**:

  - **Code**: Distributed under the MIT License.
  - **Dataset**: Distributed under the Creative Commons Attribution-NonCommercial (CC BY-NC) license.
  - **Commercial Inquiries**: Interested parties can contact the authors for commercial licensing options.

- **Maintenance and Support**: The dataset is maintained by the DeCoDE Lab at MIT, with support available via GitHub issues.

- **Citations**: Provides BibTeX entries for citing both the current and previous versions of DrivAerNet in academic work.

---

**Dataset Annotations**

- In addition to the CFD simulation data, dataset includes detailed annotations for various car components (29 labels), such as wheels, side mirrors, and doors. These annotations are instrumental for a range of machine learning tasks, including **classification, semantic segmentation, and object detection**. The comprehensive labeling can also **facilitate automated CFD meshing processes by providing precise information about different car components**. By incorporating these labels, our dataset enhances the utility for developing and testing advanced algorithms in automotive design and analysis.

---

**Accessing and Using the Dataset**

- **Data Splits**: Train, validation, and test splits are provided to facilitate benchmarking and reproducibility.

- **Replication**: Code for replicating experiments using parametric models and geometric deep learning methods is available in the repository.

- **Data Download Links**:

  - **Processed Point Clouds**: [Link](https://www.dropbox.com/scl/fo/wfx02gf00ru3dqdqngaid/AFpGKPbNHCRxsbsghcwTPg4?rlkey=2ombux69rcu1apl68x607kjrz&dl=0)
  - **STL Files**: [Link](https://www.dropbox.com/scl/fo/s4njmmkho5hhtcjcjqcea/APi6lkrYDHDzgmTLskiduXg?rlkey=9ic8g595eoc1wl3iiavmhibnl&dl=0)
  - **Drag Values**: [Link](https://www.dropbox.com/scl/fi/cfuv2zyaoxp87r7zgr0si/DrivAerNetPlusPlus_Drag_8k.csv?rlkey=3fd4c3c5a38plue3ir2r8kx7b&dl=0)

- **Previous Version**: The original DrivAerNet (version 1) with 4,000 car designs is also available for replication purposes.

---

**Conclusion**

DrivAerNet++ is a significant contribution to the fields of automotive design, aerodynamics, and machine learning. By providing a rich and diverse dataset along with detailed annotations and high-fidelity simulations, it opens up numerous possibilities for research and development in both academic and industrial settings.
