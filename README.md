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

![Screenshot from 2024-05-04 15-02-30](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/fbe7be4c-0788-41a1-8182-de3064551797)

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

![Screenshot (1348)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/558011e1-fbd3-4a84-a4b8-dc68ba14b76b)

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

Checking DRC errors :

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

![Screenshot from 2024-05-05 19-22-33](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/371dd58b-0c2e-42c2-abf1-90c5aae18ba9)

From above pics the spacing is 220um which doesn't fulfill the min requirements.

Lets Fix this DRC error by changing the ```sky130A.tech``` file. :

From tech file min spacing is defined only between poly resistors and diffusion and N-tap.
No spacing between poly resistors and poly.

![Screenshot (1408)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/688efa8d-77cb-48d0-b3b1-2b646122eec8)

![Screenshot (1409)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/fb838e93-7d99-471a-8693-d01a857a7da8)

FIX :

![Screenshot (1410)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/096cac5d-772a-410b-a746-9e03cce45606)

![Screenshot (1411)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/3bbafae5-a898-4052-b837-08122d9ba541)

Load the changed tech file by command ```  tech load sky130A.tech ```

![Screenshot (1412)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/c3d8b78b-e130-40db-9797-414dc80b65b8)

Check the DRC again by command ``` drc check ```

![Screenshot (1413)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/6660026c-20ba-424c-becd-daa94d4a35ec)

![Screenshot (1414)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/fa7c7b99-1349-4493-83cf-faeff4db1134)

Exercise to describe DRC error as geometrical construct :

![Screenshot from 2024-05-05 22-13-29](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/324a4fd5-7b5c-440c-a412-95d7bf464790)

Above layout we have some violations, Open tech file and make changes as shown :

![Screenshot (1416)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/f11fa0a1-84ed-4899-8765-2b1c5af55e9f)

![Screenshot (1417)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/54b0cdb2-3b2b-4eae-9abd-36ebef09e9de)

Lab challenge to find missing or Incorrect rules and fix them:

After updating the tech file load it again and check for errors:

![Screenshot (1419)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/f77b95ae-753b-435c-b4c4-063d3053020a)


# Day 4. Pre-layout timing analysis and importance of good clock tree

LABs:

Steps to convert grid info to track info:

Track Info:

![Screenshot from 2024-05-04 23-34-32](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/21fd79fb-b7bd-4562-be0d-41ed754eaac0)

Coverting to grid info :

By using command ```grid [xSpacing [ySpacing [xOrigin yOrigin]]] ```

![Screenshot from 2024-05-01 14-42-32](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/211db10b-1970-4de3-a53c-76565d6108fb)

![Screenshot from 2024-05-01 14-42-22](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/c4367393-414c-4cb4-846e-d98ce94412a5)

Steps to convert magic layout to std cell LEF :

Chnage the name of the mag file by using command ``` save [name of the cell] ``` .

![Screenshot (615)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/dc041137-73e1-4a27-9fe3-0a2d6e504675)

Open the mag file in magic with changed name.

Write the lef file by using command : ``` lef write ``` .

![Screenshot (620)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/879c7b86-8898-4d32-b3d9-a7d6315a791e)

Content of the New lef file:

![Screenshot from 2024-05-05 00-09-32](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/b485df8b-5256-4fca-af01-a07c774f58cb)

Steps to configure synthesis settings to fix slack and include vsdinv :

Copy these ```.lib``` and ```.lef``` file  ``` sky130_fd_sc_hd__slow.lib sky130_fd_sc_hd__typical.lib sky130_vsdinv.lef ``` to src of the picorv32a .

Change the ```config.tcl``` file of the design picorv32a :

![Screenshot from 2024-05-05 00-29-59](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/524f106c-f36a-408b-8c91-893238ffa0e8)

Run the Flow from starting 

After the design prep Step run this commands:

```
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs
```

![Screenshot (1329)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/90297cfd-4072-4df1-9f32-e89222494278)

After running the commands ``` run_synthesis ``` check that your custom cell in present in the design.

![Screenshot (1336)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/560467de-5ac4-4484-a6d6-744d71e7e636)

Run the floorplan by command ```run_floorplan```

Run the Placement by command ```run_placement```

![Screenshot (1335)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/1111613b-d253-4ce6-b403-83c5a8c50506)

Open the magic Tool.

![Screenshot from 2024-04-28 14-55-27](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/505a4e65-6a96-4b0a-89b8-3e1818474900)

Select the vsdinv cell

![Screenshot from 2024-05-01 22-59-35](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/aa19af73-a936-4a5e-90f4-6feaccd0d481)

Expand and check it perpectly allign :

![Screenshot from 2024-05-01 23-00-06](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/4686ad0a-57e9-4dac-a8d9-4c4a344f7887)

Steps to configure OpenSTA for post-synth timing analysis :

Create a file ``` pre_sta.conf ```

![Screenshot (1337)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/03ea5e91-2561-43bb-97ea-54aad4924d7a)

Create another file ```my_base.sdc``` to invoke the varibale of openlane to OpenSta.

![Screenshot (1338)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/9fb6f1a2-54e2-4e98-a206-9f07011eee6b)

Run the command ```sta pre_sta.conf``` to invoke OpenSta.

![Screenshot (1339)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/873c1fed-29c1-4b4b-8e78-492055c5559e)

Steps to run CTS using TritonCTS :

After improving the timming write the verilog by using command ```write_verilog /{path_of_the_previous_design_verilog} ``` after synthesis.
Run floorplan and Placement with the new verilog after the improving timing.

![Screenshot (1340)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/35981d63-59ba-46cf-9c16-8ce71f64666a)

Run CTS by using command ```run_cts```

![Screenshot (1341)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/fb7ad4fb-3db8-44aa-8229-4f96f3b09fa7)

New ```_cts.v``` File will be create in the result of synthesis.

![Screenshot (1342)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/04ba8363-e675-4d88-ada9-fd0d48b5eb4b)

Steps to analyze timing with real clocks using OpenSTA :
To analyze timing in Openlane flow , need to invoke openroad by using command ```openroad``` .
Need to create database in openroad.
To create follow the below commands.
```
read_lef /openLANE_flow/designs/picorv32a/runs/04-05_21-50/tmp/merged.lef
read_def /openLANE_flow/designs/picorv32a/runs/04-05_21-50/results/cts/picorv32a.cts.def
write_db pico_cts.db
read_db pico_cts.db
read_verilog /openLANE_flow/designs/picorv32a/runs/04-05_21-50/results/synthesis/picorv32a.synthesis_cts.v
read_liberty $::env(LIB_SYNTH_COMPLETE)
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc
set_propagated_clock [all_clocks]
report_checks -path_delay min_max -format full_clock_expanded -digits 4
```


![Screenshot (1343)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/f8686158-6e99-4ee7-84dd-6caa99783341)

![Screenshot (1345)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/1380a479-858f-4195-b519-7b2517e00053)

Steps to execute OpenSTA with right timing libraries and CTS assignment :

 Remove sky130_fd_sc_hd__clkbuf_1 from the list by using command : ``` set ::env(CTS_CLK_BUFFER_LIST) [lreplace $::env(CTS_CLK_BUFFER_LIST) 0 0] ```

 Check the current value of CTS_CLK_BUFFER_LIST by using the command : ```echo $::env(CTS_CLK_BUFFER_LIST)```

 Check the current value of CURRENT_DEF by using the command :  ``` echo $::env(CURRENT_DEF) ```

 Set def as placement def by using command : ``` set ::env(CURRENT_DEF) /openLANE_flow/designs/picorv32a/runs/04-05_21-50/results/placement/picorv32a.placement.def ```

 Run cts by using the command ```run_cts```.

 Check the current value of CTS_CLK_BUFFER_LIST by using the command : ```echo $::env(CTS_CLK_BUFFER_LIST) ```

 Steps to observe impact of bigger CTS buffers on setup and hold timing :

  Follow the below steps to open the Openroad tool :
  ```
  read_lef /openLANE_flow/designs/picorv32a/runs/04-05_21-50/tmp/merged.lef
  read_def /openLANE_flow/designs/picorv32a/runs/04-05_21-50/results/cts/picorv32a.cts.def
  write_db pico_cts1.db
  read_db pico_cts1.db
  read_verilog /openLANE_flow/designs/picorv32a/runs/04-05_21-50/results/synthesis/picorv32a.synthesis_cts.v
  read_liberty $::env(LIB_SYNTH_COMPLETE)
  read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc
  set_propagated_clock [all_clocks]
  report_checks -path_delay min_max -format full_clock_expanded -digits 4
  report_clock_skew -hold
  report_clock_skew -setup

  ```

![Screenshot (1346)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/22abe49c-7c24-4120-84a8-cd3c317dcb9d)

![Screenshot (1347)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/a706514b-4430-4a03-a1fe-f9413265d2f7)

# Day 5. Final steps for RTL2GDS using tritonRoute and openSTA

LABs:

Steps to build power distribution network:

Build Power distribution by using the command ``` gen_pdn ```

![Screenshot (1421)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/c0f7120c-6762-48f5-9d45-98c214c66d15)

![Screenshot (1422)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/bc2f6caf-5f0f-4f29-8eba-63bb4785ec20)

Invoke the tool magic with reading def file after the power distribution stage:

![Screenshot (1423)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/ad57e1fb-2b9e-46ea-bb10-15b8415bb316)

Routing strategy :

Run routing by using command ```run_routing```

![Screenshot (1424)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/2b85a10a-36fb-4b54-8bdb-e268cbfce58d)

![Screenshot (1425)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/24cc9d42-e432-4a08-a80c-e3434b24640e)

![Screenshot (1426)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/73190c23-d56b-4d2c-acfe-2876f6dfd33f)

![Screenshot (1427)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/29e1fe14-07b6-4f67-bd29-32be13968308)

![Screenshot (1428)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/59deb1ad-c997-4507-b9f0-ab63a30fca60)

Post Routing :

Invoke the tool magic with reading def file after the routing stage:

![Screenshot (1429)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/f97412d2-ec7c-412d-a4cd-c08526e5dcd6)
























































 

 





