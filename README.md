# NASSCOM-SOC-VLSI-DESIGN-AND_PLANNING workshop

Day 1. Inception of open-source EDA, OpenLane and Sky 130 PDK

Introduction:

Openlane :
 An open-source ASIC development flow reference. It consists of multiple open-source tools needed for the whole RTL to GDSII flow. 
 This is tuned epecially for Sky130 PDK. It also works for OSU 130nm.

 Openlane Flow:

 ![Screenshot (2)](https://github.com/Birendar-kumar-singh/NASSCOM-SOC-VLSI-DESIGN-AND_FLOW/assets/134377293/a3ab464a-ceca-4ff6-8960-ca0015585b0d)

 LABs:

 Design Preparation Step:

 step 1. Invok the docker 
 
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

day 2. Good floorplan vs bad floorplan and introduction to library cells















 

 





