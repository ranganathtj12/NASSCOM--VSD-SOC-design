# NASSCOM-VSD-SoC-Design-Program
Explore the ASIC design process using tools like Openlane and the 130nm process design kit (PDK) from the Google-Sky Water collaboration. Under the guidance of industry expert Kunal Ghosh, this course equips participants with the skills to craft standard cells, navigate the Physical Design domain, and generate GDSII files.                                                                                        

Hello everyone! I'll be sharing what I've learned from a 2-weeks workshop on VLSI-SOC and design.
## TABLE OF THE CONTENT
1-Inception of open-source EDA, OpenLANE and Sky130 PDK.                                                                                                                                                
2-Good floorplan vs bad floorplan and introduction to library cells.                                                                                                                                            
3-Design library cell using magic layout and ngspice characterization.                                                                                                                                          
4-Pre-layout timing analysis and importance of good clock tree.                                                                                                                                                 
5-Final steps for RTL2GDS using tritonRoute and openSTA.                                                                                                                                                        
## Inception of open-source EDA, OpenLANE and Sky130 PDK.   
#### *Blockdiagram of processor/SOC.
A System on a Chip (SoC) integrates processor cores, memory, GPU, connectivity, and peripherals onto a single chip, optimizing size, power efficiency, and cost for various devices. The processor within an SoC executes instructions, performs calculations, and coordinates the functions of integrated components to enable efficient computing in a compact form factor.                                                 ![WhatsApp Image 2024-05-14 at 09 17 54_1b743ae5](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/b123acf2-929d-47c4-80de-4e6e6101e695)
#### *Components of open-source digital asic design                                                                                                                                                             
Process Design Kit is PDK data which contains information about the manufacturing process. In 2020, Google collaborated with SkyWater Technology to release an open-source FOSS 130nm Production PDK.           
                                                                                                                                                                                                          ![WhatsApp Image 2024-05-14 at 09 17 55_67d082b0](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/f8557a12-8579-4f45-9d15-7329d8f155af)
#### *RTL2GDS Flow                                                                                                                                                                                               ![Screenshot (103)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/341c9dd4-6c04-46a3-9402-22aaf55a8ffa)
#### *OpenLANE ASIC design flow
OpenLane is an open-source digital ASIC implementation flow that encompasses stages like synthesis, floorplan, placement, clock tree synthesis, routing, and GDSII generation. It offers a command-line interface for seamless execution of these steps, enabling efficient design implementation and optimization for custom integrated circuits. OpenLane streamlines the process of converting RTL designs into physical layouts, ensuring robustness and performance in ASIC development.                                                                                                                                     ![Screenshot (31)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/1d2920f2-7724-4da4-bcc5-4f10cd3c840d)
#### *TOOL INVOCATION & OPERATION:
We're using the Sky130_fd_sc_hd PDK variant.

"Sky130" refers to the process or node name.

"fd" indicates the foundry name, which is SkyWater foundry.

"sc" denotes standard cell library files.

"hd" represents high density, a specific variant.

The Sky130_fd_sc_hd variant includes various technology files such as Verilog, Spice, Techlef, Meglef, Mag, GDS, CDL, LIB, LEF, etc.

The techlef file provides layer information essential for the design process.
## Good floorplan vs bad floorplan and introduction to library cells.
#### *Directory order to invoke the tool OPENLAN.
![Screenshot (104)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/9c820b68-5669-4caf-ab0c-cbe261ccc034)
![Screenshot (105)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/e615535a-78da-4bec-9639-ccd7a21e2e8e)
#### *To check the files after design is prepared.
![Screenshot (106)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/5cbbde0d-a9bc-49d1-9582-599f0e9cf47b)
![Screenshot (107)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/760ab1b1-3b68-4b37-aafe-db7b047cfddf)
![Screenshot (108)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/792b28ec-bed1-4e50-a49a-27fd4efbdfa2)
![Screenshot (109)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/123d2d3b-f6ea-4db8-b9f1-abf9557acd6f)
![Screenshot (110)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/2c3eea2b-1085-4284-a607-18b4d05b52cf)
![Screenshot (111)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/1190bcb7-6032-4aba-bf50-6d26dd73bc12)
There will be total 1613 flip flops. flip flop ratio=((no of flip flops)/(total no of cells))*100=(1613/14876)*100=10.84%
Before Performing Synthesis the reports directory was null. After Synthesis completed the reports that are generated during synthesis will be in the reports directory.
![Screenshot (112)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/589e340f-f30b-4206-8c3d-b75741879f7f)
![Screenshot (113)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/34ac3f6d-6442-4e08-a52e-bede1001376d)
To ensure the floorplan runs smoothly, designers must carefully manage certain parameters, known as switches, that influence the floorplan. For instance, the utilization factor and aspect ratio are crucial switches. Designers should verify these switches before initializing the floorplan to ensure they align with the project requirements. The image below illustrates the various types of switches used during the floorplan stage.
![Screenshot (114)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/1bf6663f-c70e-4fa1-933e-c0129c98383c)
![Screenshot (115)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/e0cc680e-76b5-446e-b5f6-36c00f6432e8)
![Screenshot (116)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/ef4afec7-dcd5-40bd-9d20-0851801d7e60)
![Screenshot (117)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/3d938beb-a12d-4437-a6d7-d8e47f577b6b)
![Screenshot (118)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/9b84c020-df37-4ef7-b73e-4e9749e1a531)
To see the actual layout after the floorplan ,go the folders as shown below:
![Screenshot (124)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/8700a38a-01ff-450e-86e8-a8da3f56b10d)
![Screenshot (125)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/11b30331-f815-4402-9556-cd28cc91a7f2)
In order to know the details of any cell in the layout , just move the cursor to that cell and press S to select the cell and then in the window of tkcon enter the command "what". then it will displey the details of the selected cell. lets see the detail of horizontal and vertical pins , in tkcon window it shows that the pin is in the metal 3 for horizontal pins ,similarly for the vertical pins, we see that thepin is at metal 2. image is shown below.
![Screenshot (126)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/6c02c1e8-d475-417c-beda-7a79ecd57e40)
![Screenshot (127)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/a85c7488-4766-4efa-a24a-723ecb10e96e)
![Screenshot (129)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/4842983c-d8ef-4d84-995b-4a3ac790f043)
## STEPS TO RUN PLACEMENT
![Screenshot (130)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/eff790ec-4198-4452-b118-316e5ed476a8)
![Screenshot (131)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/9956426d-1cc7-4870-b7fa-33e59f3ac167)
![Screenshot (132)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/41f537fa-b6f2-407d-93e0-51d521ccc3fc)
![Screenshot (133)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/6a63c1ab-024c-4507-9ab7-0c4ecd2483cd)
![Screenshot (134)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/62bae994-8a4e-458b-9a76-c2620251f202)




