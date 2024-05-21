# NASSCOM-VSD-SoC-Design-Program
Explore the ASIC design process using tools like Openlane and the 130nm process design kit (PDK) from the Google-Sky Water collaboration. Under the guidance of industry expert Kunal Ghosh, this course equips participants with the skills to craft standard cells, navigate the Physical Design domain, and generate GDSII files.                                                                                        

Hello everyone! I'll be sharing what I've learned from a 2-weeks workshop on VLSI-SOC and design.
## TABLE OF THE CONTENT
1-Inception of open-source EDA, OpenLANE and Sky130 PDK.                                                                                                                                                
2-Good floorplan vs bad floorplan and introduction to library cells.                                                                                                                                            
3-Design library cell using magic layout and ngspice characterization.                                                                                                                                          
4-Pre-layout timing analysis and importance of good clock tree.                                                                                                                                                 
5-Final steps for RTL2GDS using tritonRoute and openSTA.                                                                                                                                                        
## 1. Inception of open-source EDA, OpenLANE and Sky130 PDK.   
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
## 2. Good floorplan vs bad floorplan and introduction to library cells.
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
### STEPS TO RUN PLACEMENT
![Screenshot (130)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/eff790ec-4198-4452-b118-316e5ed476a8)
![Screenshot (131)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/9956426d-1cc7-4870-b7fa-33e59f3ac167)
![Screenshot (132)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/41f537fa-b6f2-407d-93e0-51d521ccc3fc)
![Screenshot (133)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/6a63c1ab-024c-4507-9ab7-0c4ecd2483cd)
![Screenshot (134)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/62bae994-8a4e-458b-9a76-c2620251f202)
## 3. Design library cell using Magic Layout and ngspice characterization
### Labs for CMOS inverter ngspice simulations.
To gitclone the given inverter files from github to your area use this command                                                                                                                            
         ```
         git clone https://github.com/nickson-jose/vsdstdcelldesign.git
         ```
![VirtualBox_vsdworkshop_20_05_2024_11_52_26](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/fd05c246-337c-432e-a3b6-3a80ddc0753a)

Inside the vsdstdcelldesign folder , all the files realted to inverter are present In order to open the std cell in Magic .tech file is needed , copy the sky130A.tech file to the current folder.
![VirtualBox_vsdworkshop_20_05_2024_11_54_26](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/3fa2b342-b908-4867-b272-842fdfca3c04)

Open the inverter design in the Magic tool.
![VirtualBox_vsdworkshop_20_05_2024_11_55_10](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/e6f068a9-8a8e-4214-b4b2-c6858b76db7a)

To select the pmos and nmos device select the poly and diffusion layer intersection using by entering s and enter what in tkon console window to check if its proper or not.
![VirtualBox_vsdworkshop_20_05_2024_12_19_51](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/6683c732-1381-479f-9184-47e149f8c7e6)
![VirtualBox_vsdworkshop_20_05_2024_12_28_07](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/bc86cba0-433b-40b8-b6a3-c39f026db5d4)

### Lab steps to extract spice netlist from std cell layout.
For characterizing this inverter in Ngspice we need the SPICE file , to ectract SPICE from the layout use these commands.                                                                              
    ``` extract all
       
       ext2spice cthresh0 rthresh0
       
       ext2spice
    ```
![VirtualBox_vsdworkshop_20_05_2024_12_28_07](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/163608a4-2db3-4409-bc0e-b8296aef3cd6)

The SPICE file is extracted to the current directory.
![VirtualBox_vsdworkshop_20_05_2024_12_34_21](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/f444a0c4-d8e3-4115-8e8d-2f84a9f95f7e)

Edit the spice file to include the the power supply and the input to the cmos inverter. 
![VirtualBox_vsdworkshop_20_05_2024_12_36_35](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/782fcc8c-b0d8-464e-84a7-11b18d41a44f)

Now to run the simulation using ngpcie use this command.                                                                                                                                                     
    ```
    ngspice sky130_inv.spice
    ```
![VirtualBox_vsdworkshop_20_05_2024_13_06_33](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/978dc60d-d029-445c-93cc-ecd6ecfe35e1)

### Lab Steps to characterize the Inverter using sky130 model files.                                                                                                                                     
To plot the graph between Voltage and time using this command.                                                                                                                                                 plot y vs time a
![VirtualBox_vsdworkshop_20_05_2024_13_34_09](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/043c6021-7ae3-4b1b-af4c-0e53a51d07df)

Increase the C3 value from 0.024ff to 2ff to decrease the ripples in the graphs.
![VirtualBox_vsdworkshop_20_05_2024_13_34_20](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/8f404dfa-cf87-4317-96c8-37a75d205162)

Rise Time - Rise time is typically measured from 20% to 80% of the value.                                                                                                                                
* VDD- 3.3V                                                                                                                                                                                                 
* 20% of is 3.3V 660mV                                                                                                                                                                                      * 80% of 3.3V is 2.64V

![VirtualBox_vsdworkshop_20_05_2024_13_39_16](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/59050889-1ad3-41b2-9782-c8096edb1e82)

Rise time = (2.24437 - 2.18209) e-09 = 62.28ps                                                                                                                                                                  Fall Time - It is the time take by output for transition from 80% to 20%.

![VirtualBox_vsdworkshop_20_05_2024_13_39_16](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/c97de6f9-1280-4fa2-9e6d-7f2b3633b100)

Fall time = (4.05379-4.02) e-09 = 32.64ps                                                                                                                                                                        * Propagation delay-The propagation delay of a is the difference in time (calculated at 50% of input-output transition), when output switches, after application of input.                              
    * 50% of 3.3V is 1.65
![VirtualBox_vsdworkshop_20_05_2024_13_39_16](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/0f965ef4-6a93-4cf7-82be-0ac61ca5a675)

Propagation Delay = (2.21085 - 2.15 ) e-09 =60.85 ps

Cell Fall delay -It is the time taken for the 50% of transition from high to low at the input and low to high at the output transition
![VirtualBox_vsdworkshop_20_05_2024_13_40_53](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/11478424-df0d-4f20-a126-d2a14ef80e2d)

Fall Delay = (4.07768-4.0501) e-09 = 27.58 ps
### Lab introduction to Magic and steps to load Sky130 tech-rules.
Download the lab files for DRC error fixing exercise using the command                                                                                                                                             
wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz                                                                                                                                   
      
To start magic tool,                                                                                                                                                                                  
      ```
      magic -d XR
      ```

Open met met3.mag file , different layout with different rule numbers can be seen.
![VirtualBox_vsdworkshop_20_05_2024_13_53_28](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/21635f0f-4d20-4c8d-96d5-1e484cd3efaf)
![VirtualBox_vsdworkshop_20_05_2024_14_03_34](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/cdd2fbd3-4fe9-46bb-8efe-89054855a5c9)

select an area and fill metal3 , enter command ciff see via2 so that via mask is placed on metal 3

![VirtualBox_vsdworkshop_20_05_2024_14_40_53](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/02056ee5-2884-404c-844c-fcf771a8581b)
![VirtualBox_vsdworkshop_20_05_2024_15_11_20](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/a915e55e-e519-4ce1-97e0-5bdc7620a7c4)
![VirtualBox_vsdworkshop_20_05_2024_15_11_32](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/b6d1d96d-fea9-4961-9d46-11cf55140bd8)

There are some viloations so make some changes in sky130A.tech file which are as follows:
![VirtualBox_vsdworkshop_20_05_2024_13_53_39](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/b437be93-2f3a-43db-90e5-291ce65e1ee7)
![VirtualBox_vsdworkshop_20_05_2024_15_24_38](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/251a16de-afc3-4c3c-8174-24242eccbce9)
Now execute the commands drc style drc(full) drc check.

## 4. Pre-layout timing analysis and clock tree synthesis
   The next process is to get the .lef file from the inverter and use that file in picorv32 design flow
   While designing standard cell following needs to be considered
   
   * The Input and output ports must lie on the intersection of the Vertical and Horizontal tracks.
   * The width of the standard cell should be an odd multiple of the track pitch and height should be an odd multiple of track vertical pitch.

Open the tracks.info
![VirtualBox_vsdworkshop_20_05_2024_23_01_18](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/7c1849c3-e405-4cc5-8355-78b842faab87)

From this file it can be infered that for layers li1, metal 1, and metal 2, each track is positioned at (0.23, 0.46)um in the horizontal direction and (0.17, 0.34)um in the vertical direction.

In the layout ports are on the li1 layer , translate the grid into the tracks in order to ensure that the ports are at the intersection of the tracks.

To change grid into tracks first open the tracks file and then in console window type help grid command.

![VirtualBox_vsdworkshop_20_05_2024_23_04_55](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/e955ce13-3411-4fc6-a87b-c45854b76b23)

Now the tracks can be seen on the layout.

![VirtualBox_vsdworkshop_20_05_2024_23_13_48](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/0962b29e-054c-4905-a0a7-ee68a5c7c836)

Its clear that the ports are at the intersection of the tracks.

### Lab steps to convert magic layout to std cell LEF.
![VirtualBox_vsdworkshop_20_05_2024_23_13_48](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/0b410a31-42d3-4644-a3da-1095ba961b4d)

To extract the lef file ,enter the below command in the tckon window.
```
lef write
```
![VirtualBox_vsdworkshop_20_05_2024_23_18_50](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/b53958ab-74e8-4f2c-9819-41eb1b3952cf)

![VirtualBox_vsdworkshop_20_05_2024_23_23_12](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/9139b513-5609-4d5b-af81-06ee78c8173f)

.lef file is generated in the current directory.
![VirtualBox_vsdworkshop_20_05_2024_23_24_35](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/4b9644c8-9752-4ee3-99f8-2a3ae4522998)

### Introduction to timing libs and steps to include new cell in synthesis
.lef file has been created, the next step is to add use this file for picorv32a
For that .lef needs to be copied in src folder
![VirtualBox_vsdworkshop_20_05_2024_23_29_26](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/6dc9fa2d-1838-453c-86b0-05e041671564)

Copy the required libraries i.e .lib files to src directory
![VirtualBox_vsdworkshop_20_05_2024_23_31_46](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/b1516dbe-300a-414c-a818-e39de537df5d)
![VirtualBox_vsdworkshop_20_05_2024_23_32_25](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/f28395ae-aea4-4d02-ad68-ecedd73f6586)
![VirtualBox_vsdworkshop_20_05_2024_23_35_26](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/22b124db-a65f-4000-a11d-9403e341585a)
![VirtualBox_vsdworkshop_20_05_2024_23_37_34](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/5f78d522-aaa3-4225-bef4-a69bf0b2cb6a)
![VirtualBox_vsdworkshop_20_05_2024_23_41_43](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/0d9f78a5-4275-4398-95a7-8aefd5e17c8c)
![VirtualBox_vsdworkshop_20_05_2024_23_43_20](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/2c6b569a-35b9-429e-9c3a-2c7518ca1d1f)
![VirtualBox_vsdworkshop_21_05_2024_01_00_16](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/4377c535-423f-4d57-8fe7-607101c61603)

Next step is to edit the config.tcl of picorv32a design to include these files
![VirtualBox_vsdworkshop_21_05_2024_00_59_37](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/e6eeb698-ec7a-4b85-bd89-676264d572ff)

Go to the openLANE flow and run synthesis

for that use these commands in docker

```
./flow.tcl -interactive

package require openlane 0.9

prep -design picorv32a

set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
      
add_lefs -src $lefs

run_synthesis
```

![VirtualBox_vsdworkshop_21_05_2024_01_06_58](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/1ecda152-3be2-4a99-97d0-c0f876511b64)
![VirtualBox_vsdworkshop_21_05_2024_01_06_36](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/1502d342-062e-4a7a-af22-2088e53c1870)
![VirtualBox_vsdworkshop_21_05_2024_01_45_05](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/dd9c943b-7403-461d-9761-b53c5a0da950)

It can be seen that the inverter cell which was provided is being picked by picorv32a design during synthesis

### Lab steps to configure synthesis settings to fix slack and include vsdinv
Once the synthesis is run check the slack
![VirtualBox_vsdworkshop_21_05_2024_01_45_05](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/e469b9ed-ddb1-4a2f-bf1b-68d5152a4b4e)

wns= -23.89 tns== -711.59.

run the floorplan using command run_floorplan

if any errors are encountered run these commands one after another

```
init_floorplan

place_io

tap_decap_or
```
![VirtualBox_vsdworkshop_21_05_2024_09_58_33](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/6ae03888-7c5b-48a5-a187-25944dc91d1d)

run the placement using command run_placement

Once the placement is done open the placement in Magic tool and zoom in
The standard cell inverter can be seen in the design
![VirtualBox_vsdworkshop_21_05_2024_10_01_09](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/256d10ed-781a-4d20-be55-d9cdc79ef9a7)
![VirtualBox_vsdworkshop_21_05_2024_10_42_18](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/2171e347-25b8-4d33-8f09-1a3f1c05b011)
![VirtualBox_vsdworkshop_21_05_2024_10_42_35](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/b5937b38-dda9-4a6b-b7a1-d064025f0311)
![VirtualBox_vsdworkshop_21_05_2024_10_43_52](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/907cec14-4aa9-4caf-8c6c-a2a53500910a)
![VirtualBox_vsdworkshop_21_05_2024_10_44_30](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/349dfb54-16cf-4171-aba9-2ee148576305)
The inverter is placed and its aligned , this can be cheked using align command

### Timing Analysis using openSTA
```
./flow.tcl -interactive

package require openlane 0.9
prep -design picorv32a
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs
set ::env(SYNTH_SIZING) 1
run_synthesis
```
Create a pre_sta.conf file for STA analysis in openlane directory.
![VirtualBox_vsdworkshop_21_05_2024_10_58_43](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/a3bdd60f-e42e-45d4-b491-1b5df54de298)
![VirtualBox_vsdworkshop_21_05_2024_11_27_08](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/1091ca3e-c5b1-4e51-884b-6bbdff241a9f)

create a my_base.sdc file which will have the constarints in the openlane/designs/picorv32a/src directory
![VirtualBox_vsdworkshop_21_05_2024_11_29_56](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/e63fc1ec-d802-4f26-a448-acdfa126c466)
![VirtualBox_vsdworkshop_21_05_2024_11_56_06](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/ad7e36af-f373-43f0-a37d-eed7347fcab4)

Now to run sta in this Desktop/work/tools/openlane_working_dir/openlane using the below command.
```
sta pre_sta.conf
```
![VirtualBox_vsdworkshop_21_05_2024_13_37_58](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/43a25def-85c9-4fe6-af1e-c26c72365b2e)
![VirtualBox_vsdworkshop_21_05_2024_13_38_14](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/23821864-1b10-4524-9e11-b13aaa0f9ede)
Here also the worst negative slack is -23.89. It can be reduced for that check the timing reports.

Look out for the nets having max fanout , then change the drive strength of corresponding gates

To check the connections to a net

```
report net -connenctions _10566_
```

Then replace the cell with higher drive strength using this command

```
replace_cell _13165_ sky130_fd_sc_hd__or3_4
```

to check timing

```
report_checks -fields {net cap slew input_pins} -digits 4
```

Here the or gate with drive strength 2 is has fanout as 4 ,so replace the cell with the cell having drive strength as 4

![VirtualBox_vsdworkshop_21_05_2024_13_59_22](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/6e7b1859-7cc1-4fbf-a863-53f2f9fdfabd)

Now again check STA

![VirtualBox_vsdworkshop_21_05_2024_13_59_02](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/5f24051f-553d-459a-b628-30d32250a24d)

Here it can be seen that the slack has reduced

Repeat the same thing for other cells , the wns can still be reduced

![VirtualBox_vsdworkshop_21_05_2024_13_59_02](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/90e23a94-5b26-4d4b-a4ad-ffd6dea1be6e)

### Clock tree synthesis TritonCTS and signal integrity

Lab steps to run CTS using TritonCTS

The old netlist needs to be replaced with the new netlist in which the timing is improved ,for that first copy the current synthesis.v file as old as the new file will replace the current file.

To generate the new synthesis.v file use the following commad

```
write verilog  /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/05-05_10-43/results/synthesis/picorv32a.synthesis.v
```
![VirtualBox_vsdworkshop_21_05_2024_01_06_58](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/17da4271-4ad1-4c8e-8e26-23a65844d3c8)

picorv32a.synthesis.v file is generated

Run the Synthesis , Floorplan and placemnet again
```
prep -design picorv32a -tag 05-05_10-43 -overwrite
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs
set ::env(SYNTH_STRATEGY) "DELAY 3"
set ::env(SYNTH_SIZING) 1
run_synthesis

init_floorplan
place_io
tap_decap_or

run_placement
```

For clock tree synthesis run this command

```
run_cts
```
![VirtualBox_vsdworkshop_21_05_2024_15_59_29](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/2c9ce6e4-5ef4-47bc-ba44-005061eed6bc)
![VirtualBox_vsdworkshop_21_05_2024_16_04_50](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/d9bb584c-6dd4-4b3d-8518-0c89e5609cf4)
After CTS new file is generated

### Post-CTS OpenROAD timing analysis
```
openroad

read_lef /openLANE_flow/designs/picorv32a/runs/05-05_10-43/tmp/merged.lef
read_def /openLANE_flow/designs/picorv32a/runs/05-05_10-43/results/cts/picorv32a.cts.def
write_db pico_cts.db
read_db pico_cts.db
read_verilog /openLANE_flow/designs/picorv32a/runs/05-05_10-43/results/synthesis/picorv32a.synthesis_cts.v
read_liberty $::env(LIB_SYNTH_COMPLETE)
link_design picorv32a
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc
set_propagated_clock [all_clocks]
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

exit
```
![VirtualBox_vsdworkshop_21_05_2024_16_16_45](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/75161ec7-4f0b-48c1-9d3b-0bd8bf1b246c)
![VirtualBox_vsdworkshop_21_05_2024_16_18_59](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/e3a0b0e3-db65-4ea7-a34e-52dacfcc3680)
![VirtualBox_vsdworkshop_21_05_2024_16_19_10](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/b8f04ecd-c85c-4259-9968-ec44d71bd82c)

Lab exercise to replace bigger CTS buffers

first remove the clkbuf_1 from the list by using the below command

```
set ::env(CTS_CLK_BUFFER_LIST) [lreplace $::env(CTS_CLK_BUFFER_LIST) 0 0]
```

set the right def file and run cts

```
set ::env(CURRENT_DEF) /openLANE_flow/designs/picorv32a/runs/05-05_10-43/results/placement/picorv32a.placement.def
run_cts
```

To Enter the openROAD flow and check timing , use the following commands

```
openroad
read_lef /openLANE_flow/designs/picorv32a/runs/05-05_10-43/tmp/merged.lef
read_def /openLANE_flow/designs/picorv32a/runs/05-05_10-43/results/cts/picorv32a.cts.def
write_db pico_cts1.db
read_db pico_cts1.db
read_verilog /openLANE_flow/designs/picorv32a/runs/05-05_10-43/results/synthesis/picorv32a.synthesis_cts.v
read_liberty $::env(LIB_SYNTH_COMPLETE)
link_design picorv32a
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc
set_propagated_clock [all_clocks]
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

exit

echo $::env(CTS_CLK_BUFFER_LIST)
set ::env(CTS_CLK_BUFFER_LIST) [linsert $::env(CTS_CLK_BUFFER_LIST) 0 sky130_fd_sc_hd__clkbuf_1]
echo $::env(CTS_CLK_BUFFER_LIST)
```

![VirtualBox_vsdworkshop_21_05_2024_16_48_10](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/a0d5ab35-5369-4d7d-8502-520c7a2b8563)
![VirtualBox_vsdworkshop_21_05_2024_16_49_45](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/406304b7-b3e8-458e-b681-8ef26e17aaff)

## 5. Final step for RTL2GDS using tritinRoute and openSTA
After running CTS , to build power distribution network (PDN) use this command

```
gen_pdn
```

*To check PDN open Magic tool go to /tmp/floorplan/ inside your runs folder and run this command.

```
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read 21-pdn.def &
```
![VirtualBox_vsdworkshop_21_05_2024_17_40_38](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/ce0cbd4d-b229-4f7d-b725-ad7955a6cf3f)
![VirtualBox_vsdworkshop_21_05_2024_17_41_06](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/d92b47c5-b6ae-46d3-a447-fcffb4eb7a5b)
![VirtualBox_vsdworkshop_21_05_2024_17_41_29](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/107cc410-6719-4c0b-90ad-96d46ce72d4f)
![VirtualBox_vsdworkshop_21_05_2024_17_41_53](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/fa4ce876-ec7f-4f67-ab98-65e18b79ee77)

The power rails can be seen in this design so PDN is successful

*Now to do the final step i.e routing run this command

```
run_routing
```

*Routing is done with zero violations

To view the final design in Magic tool fo to the results/routing/ in your runs folder and then use this command

```
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.def &
```
![VirtualBox_vsdworkshop_21_05_2024_18_02_01](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/3d57a78a-879b-4f70-b8c0-3a159173d704)
![VirtualBox_vsdworkshop_21_05_2024_18_02_47](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/416c602b-6549-4e80-99d5-317f1651d733)
![VirtualBox_vsdworkshop_21_05_2024_18_04_50](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/4ed945db-4f1b-4a70-b812-e19d579202b0)
![VirtualBox_vsdworkshop_21_05_2024_18_05_27](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/01dc1866-686f-4d96-a20c-c4e4aa7a928c)
![VirtualBox_vsdworkshop_21_05_2024_18_14_39](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/8e44e975-e937-4cbf-b5d9-e2e9094c4483)

## Final GDA
![Screenshot (147)](https://github.com/ranganathtj12/NASSCOM--VSD-SOC-design/assets/144826148/d863f264-9483-482c-b0d0-2d38eb124c9a)


## References
*https://github.com/nickson-jose/vsdstdcelldesign
*https://github.com/efabless/openlane2
*https://github.com/google/skywater-pdk
*https://sourceforge.net/projects/ngspice/
*Workshop Github material
