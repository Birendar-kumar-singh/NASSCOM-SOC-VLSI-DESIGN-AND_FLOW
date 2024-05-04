# NASSCOM-SOC-VLSI-DESIGN-AND_PLANNING workshop

# Day 1. Inception of open-source EDA, OpenLane and Sky 130 PDK

Introduction:

Openlane :
 An open-source ASIC development flow reference. It consists of multiple open-source tools needed for the whole RTL to GDSII flow. 
 This is tuned epecially for Sky130 PDK. It also works for OSU 130nm.

 Openlane Flow:

 ![Screenshot (2)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/a3ab464a-ceca-4ff6-8960-ca0015585b0d)

 LABs:

 Design Preparation Step:

 step 1. Invoke the docker 
 
 ![Screenshot from 2024-05-04 14-34-15](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/e52c5d40-7f31-487a-a291-5e8d0e56b780)

step 2. Run the flow in interactive way

![Screenshot from 2024-05-04 14-34-44](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/45a67588-6555-4d62-a786-0e9ad64ea882)


step 3. run the command ```prep -design picorv32a ``` to merge the lef file

![Screenshot from 2024-05-04 14-35-55](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/bf7eede9-fb1c-43ea-8a0c-b9362f96f4bb)

step 4. Review files after design prep that all lef present are merged in one lef file.

After Design Preparation run the Synthesis command ```run_synthesis```

![Screenshot from 2024-05-04 15-01-11](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/e512e63f-c0e2-47b4-ac70-c51fb4196375)

![Screenshot from 2024-05-04 15-02-30](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/903b79a4-a2e8-4344-9ce6-e1b461ab094c)

Assignment:

CALCULATION OF FLOP RATIO : Check the statistics of picorv32a in synthesis reports

![Screenshot from 2024-05-04 15-02-54](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/0bd8b3bf-27e2-4f6a-9db4-bfaa86d03730)


```
flop ratio = no. of d flip flop/no. of cells
           = 1613/14876
           = 0.1084
           = 10.84%
```

# Day 2. Good floorplan vs bad floorplan and introduction to library cells

LABs:

followed below steps:

step 1. Invoke the docker

step 2. Run the flow in interactive way

step 3. run the command ```prep -design picorv32a ```

step 4. run the command ```run_synthesis```

step 5. run the command ```run_floorplan```

![Screenshot from 2024-05-04 15-52-07](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/a330d183-f976-4a6c-be84-a93904009bdb)

![Screenshot from 2024-04-27 17-32-35](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/f38e1822-a0d0-42f5-9adb-0d3ce0ab8cd9)

floorplan completion:

![Screenshot from 2024-05-04 16-02-39](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/1942e37a-f9f6-4efa-bc5a-552abc09ae83)

Review floorplan files and steps to view floorplan:

Goto folder : runs -> current run -> results -> floorplan

![Screenshot from 2024-04-27 17-33-25](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/a27e03e2-3403-4498-8967-ab45dff743ca)

Use the command ``` magic -T /{path_of_the_pdks}/pdks/sky130A/libs.tech/magic/sky130A.tech lef read /{path_of_the_merged_lef_file_after_run}/merged.lef def read /{path_of_the_picorv32a.floorplan.def} ``` 
to invoke the Magic tool for view of the floorplan

![Screenshot from 2024-04-27 17-34-55](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/0975220d-948a-48ba-af94-319882f993e1)

Review floorplan layout in Magic

By selecting the components and typing command ```what``` in the console of the Magic we can find what is that component

![Screenshot from 2024-04-27 17-47-36](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/167e3b9e-a4df-48ae-82b5-4be6a6ccab75)

In Floorplan all the macors , IP and Ports are placed.
All std. cells are not placed they are present in the origin.

![Screenshot from 2024-04-28 14-55-05](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/996355a5-e84e-4bb3-91fc-caf2b532a3bb)

Congestion aware placement using RePlAce:

After floorplan run the command : ```run_placement```

![Screenshot from 2024-05-04 16-38-02](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/aa988965-09d1-4382-8c37-f79a9d385bad)

![Screenshot from 2024-05-04 16-41-06](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/b94e28ef-8464-4a82-baa7-634777e1f8ff)

After the placement run invoke the Magic to view the Layout with placement def file:

![Screenshot from 2024-04-28 14-55-27](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/505a4e65-6a96-4b0a-89b8-3e1818474900)

# Day 3. Design library cell using Magic Layout and ngspice characterization

Labs: 

CMOS inverter ngspice simulations

Clone the repo ```https://github.com/nickson-jose/vsdstdcelldesign.git```

Open the layout in Magic tool. Using the command ```magic -T {absolute_path_of_the_tech_file_of_the_cell} {absolute_path_of_the_mag_file_of_the_cell} ```

![Screenshot from 2024-05-01 08-57-03](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/d60df769-6d69-4ad6-a876-aa9448a99c78)

Layout Of The Cell :

![Screenshot from 2024-05-01 08-56-43](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/957afa0b-d1b7-47d5-af3c-d81c565e0c60)

Extracted the Spice Deck of the cell:

Using commands :
```
% extract all
% ext2spice cthresh 0 rthresh 0
% ext2spice
```

![Screenshot from 2024-05-01 10-22-12](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/beaf5f77-04a4-4c9d-972c-0d55bc2f61cb)

Modified the Spice deck file:

![Screenshot from 2024-05-04 18-56-26](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/3cdce39c-8e15-4a15-9f1d-bf4ca080c5a2)

Run the commnad ``` ngspice {file_name} ```

![Screenshot from 2024-05-04 00-07-15](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/48835966-2ccf-4fc9-ba5c-1d26d3b39638)

Run the command ``` plot y vs time a ```

![Screenshot from 2024-05-04 00-09-02](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/5abc07c9-f174-4db9-815e-1ce31f189b2e)

Calculating input rise time:

![Screenshot (1318)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/84f3be2f-b46f-4d97-8e17-c3f218bec9c1)

```
20% of 3.3V = 0.66V
80% of 3.3V = 2.64V
From the above data:
input rise time :
4.08-4.02 = 0.06 ns
```

Calculating output fall time:

![Screenshot (1319)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/042c10c3-530f-43c9-8606-a262a34cc3bf)

```
80% of 3.3V = 2.64v
20% of 3.3V = 0.66v
From the above data:
output fall time :
4.09-4.05 = 0.04 ns
```

Calculating Rise propagation delay:

![Screenshot (1321)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/9d34987a-de28-43ec-b5ad-2cb138483083)

![Screenshot (1320)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/e07c966f-8710-4fe7-b659-dc8edcfc1a2f)

```
50% of 3.3V = 1.65V
From the above data:
Rise propagation delay :
0.00007ns
```

Checking DRC errors

Download the file  by Using command```wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz ``` . 

By Using command : ``` magic -d XR ``` open the magic tool. :

![Screenshot from 2024-05-04 20-05-41](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/7f7cf55f-5266-4b01-8213-9bbb37943b32)

load the ``` met3.mag ``` file from the download file. :

![Screenshot from 2024-05-04 20-20-25](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/94768002-7e2e-43c5-b414-79cd286bbf2b)

To view the DRC error select the component and type the command : ```drc why ``` :

![Screenshot from 2024-05-04 20-38-51](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/1e38d341-d587-41cd-b2d4-4ca6785b3fbc)

![Screenshot from 2024-05-04 20-39-10](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/26c2a955-a230-446d-81ef-98910a081d49)

Fixing Poly.9 Error :

Load the Poly.9 mag file:

![Screenshot from 2024-05-04 20-24-05](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/98e36d79-3a39-4eff-aa10-42fb769f4eaa)

Check the compontent and the DRC error:

![Screenshot from 2024-05-04 20-46-27](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/49aa4dc9-5f58-4a8d-bd27-1d9a09809395)

![Screenshot from 2024-05-04 20-49-24](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/42d9b4cb-5575-4ce6-bc37-e0c1223b16cb)







































 

 





