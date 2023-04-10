# SOLVING BAKING DILEMMA USING LINEAR PROGRAMMING ON R SOFTWARE
SM4290 RESEARCH PROJECT

## First month R code
### Control group code
```
library(lpSolve)

# This is the control code for the first month where the restriction is
# At least a batch of x1, x2 and x3 and other product less than 15 batches

## Define the yj and zj values when Budget is $51.45 ---------------------------
y1.agar_51.45 = 0
y2.apfl_51.45 = 1
y3.baso_51.45 = 0
y4.brsu_51.45 = 1
y5.choc_51.45 = 2
y6.coco_51.45 = 1
y7.eggs_51.45 = 1
y8.grsu_51.45 = 1
y9.milk_51.45 = 0
y10.ore_51.45 = 1
y11.sbu_51.45 = 1
y12.vae_51.45 = 1
y13.wat_51.45 = 1
y14.whc_51.45 = 1
y15.yog_51.45 = 1

z01_51.45 = 0
z02_51.45 = 0
z03_51.45 = 0
z04_51.45 = 0
z05_51.45 = 0
z06_51.45 = 0
z07_51.45 = 0
z08_51.45 = 0
z09_51.45 = 0
z10_51.45 = 0
z11_51.45 = 0
z12_51.45 = 0
z13_51.45 = 0
z14_51.45 = 0
z15_51.45 = 0
  
## Define the objective function -----------------------------------------------
OBJ <- c(1, 1, 1, 1, 1, 1, 1, 1, 1, 1)

## Define the LHS coefficients -------------------------------------------------
LHS <- matrix(c(
  0.3, 2.5, 3.5, 1, 1.7, 1.7, 2, 0.7, 1, 0.3,
  010, 000, 000, 000, 000,   000, 000, 000, 000, 000,
  000, 025, 120, 190, 090,   045, 000, 250, 000, 040,
  000, 000, 000, 005, 003,   000, 000, 005, 000, 000,
  000, 060, 000, 000, 150,   000, 000, 000, 000, 000,
  150, 200, 100, 000, 225,   100, 200, 050, 400, 000,
  
  000, 025, 000, 100, 000,   000, 000, 005, 000, 005,
  000, 003, 004, 001, 002,   002, 000, 001, 000, 000,
  100, 125, 000, 000, 000,   020, 000, 012, 000, 075,
  500, 000, 000, 000, 000,   000, 000, 175, 000, 150,
  000, 000, 000, 000, 000,   000, 013, 000, 013, 000,
  
  000, 115, 110, 100, 060,   050, 030, 110, 000, 000,
  000, 005, 000, 000, 010,   000, 000, 010, 000, 005,
  000, 000, 200, 150, 000,   000, 000, 000, 000, 000,
  000, 000, 200, 000, 000,   000, 300, 000, 000, 000,
  000, 000, 000, 000, 000,   000, 000, 245, 300, 000,
  
  1, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 1, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 1, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 1, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 1, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 1, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 1, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 1, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 1, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 1), nrow = 26, byrow = TRUE)

## Inequalities direction ------------------------------------------------------
DIR <- c("<=",
         "<=", "<=", "<=", "<=", "<=", "<=", "<=", "<=", "<=", "<=",
         "<=", "<=", "<=", "<=", "<=",
         "<=", ">=", ">=", "<=", "<=", "<=", "<=", "<=", ">=", "<=")

## Define the RHS coefficients when time available is 7 hours ------------------

# $51.45
RHS7.51.45 <-c(
  7,
  10*y1.agar_51.45+z01_51.45, 1000*y2.apfl_51.45+z02_51.45, 
  100*y3.baso_51.45+z03_51.45, 100*y4.brsu_51.45+z04_51.45, 
  500*y5.choc_51.45+z05_51.45, 200*y6.coco_51.45+z06_51.45, 
  51.45*y7.eggs_51.45+z07_51.45, 2000*y8.grsu_51.45+z08_51.45, 
  1000*y9.milk_51.45+z09_51.45, 13*y10.ore_51.45+z10_51.45, 
  250*y11.sbu_51.45+z11_51.45, 115*y12.vae_51.45+z12_51.45, 
  1500*y13.wat_51.45+z13_51.45, 1000*y14.whc_51.45+z14_51.45, 
  1000*y15.yog_51.45+z15_51.45,
  15, 1, 1, 15, 15, 15, 15, 15, 1, 15)

################################################################################
# RESULTS when the time is 7 hours ## -----------------------------------------
# $51.45
lp(direction = "max", OBJ, LHS, DIR, RHS7.51.45, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS7.51.45, all.int = TRUE)$solution
```

### Control group result
```
> # RESULTS when the time is 7 hours ## -----------------------------------------
> # $51.45
> lp(direction = "max", OBJ, LHS, DIR, RHS7.51.45, all.int = TRUE)
Success: the objective function is 3 
> lp(direction = "max", OBJ, LHS, DIR, RHS7.51.45, all.int = TRUE)$solution
 [1] 0 1 1 0 0 0 0 0 1 0
 ```

### Code for the time range of 8, 16, 32 and 48 hours when the budget is $30, $60, $100, $300 and $500
```

library(lpSolve)

# This is a control group code for the first month where the restriction is
# At least a batch of x1, x2 and x3 and other product less than 15 batches

## Define the yj and zj values when Budget is $30 ------------------------------
y1.agar_30 = 0
y2.apfl_30 = 1
y3.baso_30 = 0
y4.brsu_30 = 1
y5.choc_30 = 2
y6.coco_30 = 1
y7.eggs_30 = 1
y8.grsu_30 = 1
y9.milk_30 = 0
y10.ore_30 = 0
y11.sbu_30 = 0
y12.vae_30 = 0
y13.wat_30 = 0
y14.whc_30 = 0
y15.yog_30 = 0

z01_30 = 0
z02_30 = 0
z03_30 = 0
z04_30 = 0
z05_30 = 0
z06_30 = 0
z07_30 = 0
z08_30 = 0
z09_30 = 0
z10_30 = 0
z11_30 = 0
z12_30 = 0
z13_30 = 0
z14_30 = 0
z15_30 = 0

## Define the yj and zj values when Budget is $60 ------------------------------
y1.agar_60 = 1
y2.apfl_60 = 1
y3.baso_60 = 1
y4.brsu_60 = 1
y5.choc_60 = 2
y6.coco_60 = 1
y7.eggs_60 = 1
y8.grsu_60 = 1
y9.milk_60 = 1
y10.ore_60 = 1
y11.sbu_60 = 1
y12.vae_60 = 1
y13.wat_60 = 1
y14.whc_60 = 1
y15.yog_60 = 1

z01_60 = 0
z02_60 = 0
z03_60 = 0
z04_60 = 0
z05_60 = 0
z06_60 = 0
z07_60 = 0
z08_60 = 0
z09_60 = 0
z10_60 = 0
z11_60 = 0
z12_60 = 0
z13_60 = 0
z14_60 = 0
z15_60 = 0

## Define the yj and zj values when Budget is $100 -----------------------------
y1.agar_100 = 2
y2.apfl_100 = 2
y3.baso_100 = 1
y4.brsu_100 = 2
y5.choc_100 = 4
y6.coco_100 = 2
y7.eggs_100 = 2
y8.grsu_100 = 2
y9.milk_100 = 1
y10.ore_100 = 2
y11.sbu_100 = 2
y12.vae_100 = 2
y13.wat_100 = 2
y14.whc_100 = 1
y15.yog_100 = 2

z01_100 = 0
z02_100 = 0
z03_100 = 0
z04_100 = 0
z05_100 = 0
z06_100 = 0
z07_100 = 0
z08_100 = 0
z09_100 = 0
z10_100 = 0
z11_100 = 0
z12_100 = 0
z13_100 = 0
z14_100 = 0
z15_100 = 0

## Define the yj and zj values when Budget is $300 -----------------------------
y1.agar_300 = 5
y2.apfl_300 = 6
y3.baso_300 = 5
y4.brsu_300 = 6
y5.choc_300 = 12
y6.coco_300 = 6
y7.eggs_300 = 5
y8.grsu_300 = 5
y9.milk_300 = 5
y10.ore_300 = 5
y11.sbu_300 = 5
y12.vae_300 = 5
y13.wat_300 = 5
y14.whc_300 = 5
y15.yog_300 = 5

z01_300 = 0
z02_300 = 0
z03_300 = 0
z04_300 = 0
z05_300 = 0
z06_300 = 0
z07_300 = 0
z08_300 = 0
z09_300 = 0
z10_300 = 0
z11_300 = 0
z12_300 = 0
z13_300 = 0
z14_300 = 0
z15_300 = 0

## Define the yj and zj values when Budget is $500 -----------------------------
y1.agar_500 = 9
y2.apfl_500 = 9
y3.baso_500 = 9
y4.brsu_500 = 9
y5.choc_500 = 18
y6.coco_500 = 9
y7.eggs_500 = 9
y8.grsu_500 = 9
y9.milk_500 = 9
y10.ore_500 = 9
y11.sbu_500 = 9
y12.vae_500 = 9
y13.wat_500 = 9
y14.whc_500 = 9
y15.yog_500 = 9

z01_500 = 0
z02_500 = 0
z03_500 = 0
z04_500 = 0
z05_500 = 0
z06_500 = 0
z07_500 = 0
z08_500 = 0
z09_500 = 0
z10_500 = 0
z11_500 = 0
z12_500 = 0
z13_500 = 0
z14_500 = 0
z15_500 = 0

## Define the objective function -----------------------------------------------
OBJ <- c(1, 1, 1, 1, 1, 1, 1, 1, 1, 1)

## Define the LHS coefficients -------------------------------------------------
LHS <- matrix(c(
  0.3, 2.5, 3.5, 1, 1.7, 1.7, 2, 0.7, 1, 0.3,
  010, 000, 000, 000, 000,   000, 000, 000, 000, 000,
  000, 025, 120, 190, 090,   045, 000, 250, 000, 040,
  000, 000, 000, 005, 003,   000, 000, 005, 000, 000,
  000, 060, 000, 000, 150,   000, 000, 000, 000, 000,
  150, 200, 100, 000, 225,   100, 200, 050, 400, 000,
  
  000, 025, 000, 100, 000,   000, 000, 005, 000, 005,
  000, 003, 004, 001, 002,   002, 000, 001, 000, 000,
  100, 125, 000, 000, 000,   020, 000, 012, 000, 075,
  500, 000, 000, 000, 000,   000, 000, 175, 000, 150,
  000, 000, 000, 000, 000,   000, 013, 000, 013, 000,
  
  000, 115, 110, 100, 060,   050, 030, 110, 000, 000,
  000, 005, 000, 000, 010,   000, 000, 010, 000, 005,
  000, 000, 200, 150, 000,   000, 000, 000, 000, 000,
  000, 000, 200, 000, 000,   000, 300, 000, 000, 000,
  000, 000, 000, 000, 000,   000, 000, 245, 300, 000,
  
  1, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 1, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 1, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 1, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 1, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 1, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 1, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 1, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 1, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 1), nrow = 26, byrow = TRUE)

## Inequalities direction ------------------------------------------------------
DIR <- c("<=",
         "<=", "<=", "<=", "<=", "<=", "<=", "<=", "<=", "<=", "<=",
         "<=", "<=", "<=", "<=", "<=",
         "<=", ">=", ">=", "<=", "<=", "<=", "<=", "<=", ">=", "<=")

## Define the RHS coefficients when time available is 8 hours ------------------

# $30
RHS8.30 <-c(
  8,
  10*y1.agar_30+z01_30, 1000*y2.apfl_30+z02_30, 100*y3.baso_30+z03_30, 
  100*y4.brsu_30+z04_30, 500*y5.choc_30+z05_30, 200*y6.coco_30+z06_30, 
  30*y7.eggs_30+z07_30, 2000*y8.grsu_30+z08_30, 1000*y9.milk_30+z09_30, 
  13*y10.ore_30+z10_30, 250*y11.sbu_30+z11_30, 115*y12.vae_30+z12_30, 
  1500*y13.wat_30+z13_30, 1000*y14.whc_30+z14_30, 1000*y15.yog_30+z15_30,
  15, 1, 1, 15, 15, 15, 15, 15, 1, 15)

# 60
RHS8.60 <- c(
  8,
  10*y1.agar_60+z01_60, 1000*y2.apfl_60+z02_60, 100*y3.baso_60+z03_60, 
  100*y4.brsu_60+z04_60, 500*y5.choc_60+z05_60, 200*y6.coco_60+z06_60, 
  30*y7.eggs_60+z07_60, 2000*y8.grsu_60+z08_60, 1000*y9.milk_60+z09_60, 
  13*y10.ore_60+z10_60, 250*y11.sbu_60+z11_60, 115*y12.vae_60+z12_60, 
  1500*y13.wat_60+z13_60, 1000*y14.whc_60+z14_60, 1000*y15.yog_60+z15_60,
  15, 1, 1, 15, 15, 15, 15, 15, 1, 15)  

# $100
RHS8.100 <- c(
  8,
  10*y1.agar_100+z01_100, 1000*y2.apfl_100+z02_100, 100*y3.baso_100+z03_100, 
  100*y4.brsu_100+z04_100, 500*y5.choc_100+z05_100, 200*y6.coco_100+z06_100, 
  30*y7.eggs_100+z07_100, 2000*y8.grsu_100+z08_100, 1000*y9.milk_100+z09_100, 
  13*y10.ore_100+z10_100, 250*y11.sbu_100+z11_100, 115*y12.vae_100+z12_100, 
  1500*y13.wat_100+z13_100, 1000*y14.whc_100+z14_100, 1000*y15.yog_100+z15_100,
  15, 1, 1, 15, 15, 15, 15, 15, 1, 15)

# $300
RHS8.300 <- c(
  8,
  10*y1.agar_300+z01_300, 1000*y2.apfl_300+z02_300, 100*y3.baso_300+z03_300, 
  100*y4.brsu_300+z04_300, 500*y5.choc_300+z05_300, 200*y6.coco_300+z06_300, 
  30*y7.eggs_300+z07_300, 2000*y8.grsu_300+z08_300, 1000*y9.milk_300+z09_300, 
  13*y10.ore_300+z10_300, 250*y11.sbu_300+z11_300, 115*y12.vae_300+z12_300, 
  1500*y13.wat_300+z13_300, 1000*y14.whc_300+z14_300, 1000*y15.yog_300+z15_300,
  15, 1, 1, 15, 15, 15, 15, 15, 1, 15)

# $500
RHS8.500 <- c(
  8,
  10*y1.agar_500+z01_500, 1000*y2.apfl_500+z02_500, 100*y3.baso_500+z03_500, 
  100*y4.brsu_500+z04_500, 500*y5.choc_500+z05_500, 200*y6.coco_500+z06_500, 
  30*y7.eggs_500+z07_500, 2000*y8.grsu_500+z08_500, 1000*y9.milk_500+z09_500, 
  13*y10.ore_500+z10_500, 250*y11.sbu_500+z11_500, 115*y12.vae_500+z12_500, 
  1500*y13.wat_500+z13_500, 1000*y14.whc_500+z14_500, 1000*y15.yog_500+z15_500,
  15, 1, 1, 15, 15, 15, 15, 15, 1, 15)
## Define the RHS coefficients when time available is 16 hours -----------------

# $30
RHS16.30 <-c(
  16,
  10*y1.agar_30+z01_30, 1000*y2.apfl_30+z02_30, 100*y3.baso_30+z03_30, 
  100*y4.brsu_30+z04_30, 500*y5.choc_30+z05_30, 200*y6.coco_30+z06_30, 
  30*y7.eggs_30+z07_30, 2000*y8.grsu_30+z08_30, 1000*y9.milk_30+z09_30, 
  13*y10.ore_30+z10_30, 250*y11.sbu_30+z11_30, 115*y12.vae_30+z12_30, 
  1500*y13.wat_30+z13_30, 1000*y14.whc_30+z14_30, 1000*y15.yog_30+z15_30,
  15, 1, 1, 15, 15, 15, 15, 15, 1, 15)

# 60
RHS16.60 <- c(
  16,
  10*y1.agar_60+z01_60, 1000*y2.apfl_60+z02_60, 100*y3.baso_60+z03_60, 
  100*y4.brsu_60+z04_60, 500*y5.choc_60+z05_60, 200*y6.coco_60+z06_60, 
  30*y7.eggs_60+z07_60, 2000*y8.grsu_60+z08_60, 1000*y9.milk_60+z09_60, 
  13*y10.ore_60+z10_60, 250*y11.sbu_60+z11_60, 115*y12.vae_60+z12_60, 
  1500*y13.wat_60+z13_60, 1000*y14.whc_60+z14_60, 1000*y15.yog_60+z15_60,
  15, 1, 1, 15, 15, 15, 15, 15, 1, 15)  

# $100
RHS16.100 <- c(
  16,
  10*y1.agar_100+z01_100, 1000*y2.apfl_100+z02_100, 100*y3.baso_100+z03_100, 
  100*y4.brsu_100+z04_100, 500*y5.choc_100+z05_100, 200*y6.coco_100+z06_100, 
  30*y7.eggs_100+z07_100, 2000*y8.grsu_100+z08_100, 1000*y9.milk_100+z09_100, 
  13*y10.ore_100+z10_100, 250*y11.sbu_100+z11_100, 115*y12.vae_100+z12_100, 
  1500*y13.wat_100+z13_100, 1000*y14.whc_100+z14_100, 1000*y15.yog_100+z15_100,
  15, 1, 1, 15, 15, 15, 15, 15, 1, 15)

# $300
RHS16.300 <- c(
  16,
  10*y1.agar_300+z01_300, 1000*y2.apfl_300+z02_300, 100*y3.baso_300+z03_300, 
  100*y4.brsu_300+z04_300, 500*y5.choc_300+z05_300, 200*y6.coco_300+z06_300, 
  30*y7.eggs_300+z07_300, 2000*y8.grsu_300+z08_300, 1000*y9.milk_300+z09_300, 
  13*y10.ore_300+z10_300, 250*y11.sbu_300+z11_300, 115*y12.vae_300+z12_300, 
  1500*y13.wat_300+z13_300, 1000*y14.whc_300+z14_300, 1000*y15.yog_300+z15_300,
  15, 1, 1, 15, 15, 15, 15, 15, 1, 15)

# $500
RHS16.500 <- c(
  16,
  10*y1.agar_500+z01_500, 1000*y2.apfl_500+z02_500, 100*y3.baso_500+z03_500, 
  100*y4.brsu_500+z04_500, 500*y5.choc_500+z05_500, 200*y6.coco_500+z06_500, 
  30*y7.eggs_500+z07_500, 2000*y8.grsu_500+z08_500, 1000*y9.milk_500+z09_500, 
  13*y10.ore_500+z10_500, 250*y11.sbu_500+z11_500, 115*y12.vae_500+z12_500, 
  1500*y13.wat_500+z13_500, 1000*y14.whc_500+z14_500, 1000*y15.yog_500+z15_500,
  15, 1, 1, 15, 15, 15, 15, 15, 1, 15)

## Define the RHS coefficients when time available is 32 hours -----------------

# $30
RHS32.30 <-c(
  32,
  10*y1.agar_30+z01_30, 1000*y2.apfl_30+z02_30, 100*y3.baso_30+z03_30, 
  100*y4.brsu_30+z04_30, 500*y5.choc_30+z05_30, 200*y6.coco_30+z06_30, 
  30*y7.eggs_30+z07_30, 2000*y8.grsu_30+z08_30, 1000*y9.milk_30+z09_30, 
  13*y10.ore_30+z10_30, 250*y11.sbu_30+z11_30, 115*y12.vae_30+z12_30, 
  1500*y13.wat_30+z13_30, 1000*y14.whc_30+z14_30, 1000*y15.yog_30+z15_30,
  15, 1, 1, 15, 15, 15, 15, 15, 1, 15)

# 60
RHS32.60 <- c(
  32,
  10*y1.agar_60+z01_60, 1000*y2.apfl_60+z02_60, 100*y3.baso_60+z03_60, 
  100*y4.brsu_60+z04_60, 500*y5.choc_60+z05_60, 200*y6.coco_60+z06_60, 
  30*y7.eggs_60+z07_60, 2000*y8.grsu_60+z08_60, 1000*y9.milk_60+z09_60, 
  13*y10.ore_60+z10_60, 250*y11.sbu_60+z11_60, 115*y12.vae_60+z12_60, 
  1500*y13.wat_60+z13_60, 1000*y14.whc_60+z14_60, 1000*y15.yog_60+z15_60,
  15, 1, 1, 15, 15, 15, 15, 15, 1, 15)  

# $100
RHS32.100 <- c(
  32,
  10*y1.agar_100+z01_100, 1000*y2.apfl_100+z02_100, 100*y3.baso_100+z03_100, 
  100*y4.brsu_100+z04_100, 500*y5.choc_100+z05_100, 200*y6.coco_100+z06_100, 
  30*y7.eggs_100+z07_100, 2000*y8.grsu_100+z08_100, 1000*y9.milk_100+z09_100, 
  13*y10.ore_100+z10_100, 250*y11.sbu_100+z11_100, 115*y12.vae_100+z12_100, 
  1500*y13.wat_100+z13_100, 1000*y14.whc_100+z14_100, 1000*y15.yog_100+z15_100,
  15, 1, 1, 15, 15, 15, 15, 15, 1, 15)

# $300
RHS32.300 <- c(
  32,
  10*y1.agar_300+z01_300, 1000*y2.apfl_300+z02_300, 100*y3.baso_300+z03_300, 
  100*y4.brsu_300+z04_300, 500*y5.choc_300+z05_300, 200*y6.coco_300+z06_300, 
  30*y7.eggs_300+z07_300, 2000*y8.grsu_300+z08_300, 1000*y9.milk_300+z09_300, 
  13*y10.ore_300+z10_300, 250*y11.sbu_300+z11_300, 115*y12.vae_300+z12_300, 
  1500*y13.wat_300+z13_300, 1000*y14.whc_300+z14_300, 1000*y15.yog_300+z15_300,
  15, 1, 1, 15, 15, 15, 15, 15, 1, 15)

# $500
RHS32.500 <- c(
  32,
  10*y1.agar_500+z01_500, 1000*y2.apfl_500+z02_500, 100*y3.baso_500+z03_500, 
  100*y4.brsu_500+z04_500, 500*y5.choc_500+z05_500, 200*y6.coco_500+z06_500, 
  30*y7.eggs_500+z07_500, 2000*y8.grsu_500+z08_500, 1000*y9.milk_500+z09_500, 
  13*y10.ore_500+z10_500, 250*y11.sbu_500+z11_500, 115*y12.vae_500+z12_500, 
  1500*y13.wat_500+z13_500, 1000*y14.whc_500+z14_500, 1000*y15.yog_500+z15_500,
  15, 1, 1, 15, 15, 15, 15, 15, 1, 15)

## Define the RHS coefficients when time available is 48 hours -----------------

# $30
RHS48.30 <-c(
  48,
  10*y1.agar_30+z01_30, 1000*y2.apfl_30+z02_30, 100*y3.baso_30+z03_30, 
  100*y4.brsu_30+z04_30, 500*y5.choc_30+z05_30, 200*y6.coco_30+z06_30, 
  30*y7.eggs_30+z07_30, 2000*y8.grsu_30+z08_30, 1000*y9.milk_30+z09_30, 
  13*y10.ore_30+z10_30, 250*y11.sbu_30+z11_30, 115*y12.vae_30+z12_30, 
  1500*y13.wat_30+z13_30, 1000*y14.whc_30+z14_30, 1000*y15.yog_30+z15_30,
  15, 1, 1, 15, 15, 15, 15, 15, 1, 15)

# 60
RHS48.60 <- c(
  48,
  10*y1.agar_60+z01_60, 1000*y2.apfl_60+z02_60, 100*y3.baso_60+z03_60, 
  100*y4.brsu_60+z04_60, 500*y5.choc_60+z05_60, 200*y6.coco_60+z06_60, 
  30*y7.eggs_60+z07_60, 2000*y8.grsu_60+z08_60, 1000*y9.milk_60+z09_60, 
  13*y10.ore_60+z10_60, 250*y11.sbu_60+z11_60, 115*y12.vae_60+z12_60, 
  1500*y13.wat_60+z13_60, 1000*y14.whc_60+z14_60, 1000*y15.yog_60+z15_60,
  15, 1, 1, 15, 15, 15, 15, 15, 1, 15)  

# $100
RHS48.100 <- c(
  48,
  10*y1.agar_100+z01_100, 1000*y2.apfl_100+z02_100, 100*y3.baso_100+z03_100, 
  100*y4.brsu_100+z04_100, 500*y5.choc_100+z05_100, 200*y6.coco_100+z06_100, 
  30*y7.eggs_100+z07_100, 2000*y8.grsu_100+z08_100, 1000*y9.milk_100+z09_100, 
  13*y10.ore_100+z10_100, 250*y11.sbu_100+z11_100, 115*y12.vae_100+z12_100, 
  1500*y13.wat_100+z13_100, 1000*y14.whc_100+z14_100, 1000*y15.yog_100+z15_100,
  15, 1, 1, 15, 15, 15, 15, 15, 1, 15)

# $300
RHS48.300 <- c(
  48,
  10*y1.agar_300+z01_300, 1000*y2.apfl_300+z02_300, 100*y3.baso_300+z03_300, 
  100*y4.brsu_300+z04_300, 500*y5.choc_300+z05_300, 200*y6.coco_300+z06_300, 
  30*y7.eggs_300+z07_300, 2000*y8.grsu_300+z08_300, 1000*y9.milk_300+z09_300, 
  13*y10.ore_300+z10_300, 250*y11.sbu_300+z11_300, 115*y12.vae_300+z12_300, 
  1500*y13.wat_300+z13_300, 1000*y14.whc_300+z14_300, 1000*y15.yog_300+z15_300,
  15, 1, 1, 15, 15, 15, 15, 15, 1, 15)

# $500
RHS48.500 <- c(
  48,
  10*y1.agar_500+z01_500, 1000*y2.apfl_500+z02_500, 100*y3.baso_500+z03_500, 
  100*y4.brsu_500+z04_500, 500*y5.choc_500+z05_500, 200*y6.coco_500+z06_500, 
  30*y7.eggs_500+z07_500, 2000*y8.grsu_500+z08_500, 1000*y9.milk_500+z09_500, 
  13*y10.ore_500+z10_500, 250*y11.sbu_500+z11_500, 115*y12.vae_500+z12_500, 
  1500*y13.wat_500+z13_500, 1000*y14.whc_500+z14_500, 1000*y15.yog_500+z15_500,
  15, 1, 1, 15, 15, 15, 15, 15, 1, 15)

################################################################################
# RESULTS when the time is 8 hours ## -----------------------------------------
# $30
lp(direction = "max", OBJ, LHS, DIR, RHS8.30, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS8.30, all.int = TRUE)$solution

# $60
lp(direction = "max", OBJ, LHS, DIR, RHS8.60, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS8.60, all.int = TRUE)$solution

# $100
lp(direction = "max", OBJ, LHS, DIR, RHS8.100, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS8.100, all.int = TRUE)$solution

# $300
lp(direction = "max", OBJ, LHS, DIR, RHS8.300, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS8.300, all.int = TRUE)$solution

# $500
lp(direction = "max", OBJ, LHS, DIR, RHS8.500, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS8.500, all.int = TRUE)$solution



## RESULTS when the time is 16 hours ## ----------------------------------------
# $30
lp(direction = "max", OBJ, LHS, DIR, RHS16.30, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS16.30, all.int = TRUE)$solution

# $60
lp(direction = "max", OBJ, LHS, DIR, RHS16.60, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS16.60, all.int = TRUE)$solution

# $100
lp(direction = "max", OBJ, LHS, DIR, RHS16.100, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS16.100, all.int = TRUE)$solution

# $300
lp(direction = "max", OBJ, LHS, DIR, RHS16.300, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS16.300, all.int = TRUE)$solution

# $500
lp(direction = "max", OBJ, LHS, DIR, RHS16.500, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS16.500, all.int = TRUE)$solution



## RESULTS when the time is 32 hours ## ----------------------------------------
# $30
lp(direction = "max", OBJ, LHS, DIR, RHS32.30, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS32.30, all.int = TRUE)$solution

# $60
lp(direction = "max", OBJ, LHS, DIR, RHS32.60, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS32.60, all.int = TRUE)$solution

# $100
lp(direction = "max", OBJ, LHS, DIR, RHS32.100, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS32.100, all.int = TRUE)$solution

# $300
lp(direction = "max", OBJ, LHS, DIR, RHS32.300, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS32.300, all.int = TRUE)$solution

# $500
lp(direction = "max", OBJ, LHS, DIR, RHS32.500, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS32.500, all.int = TRUE)$solution



## RESULTS when the time is 48 hours ## ----------------------------------------
# $30
lp(direction = "max", OBJ, LHS, DIR, RHS48.30, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS48.30, all.int = TRUE)$solution

# $60
lp(direction = "max", OBJ, LHS, DIR, RHS48.60, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS48.60, all.int = TRUE)$solution

# $100
lp(direction = "max", OBJ, LHS, DIR, RHS48.100, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS48.100, all.int = TRUE)$solution

# $300
lp(direction = "max", OBJ, LHS, DIR, RHS48.300, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS48.300, all.int = TRUE)$solution

# $500
lp(direction = "max", OBJ, LHS, DIR, RHS48.500, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS48.500, all.int = TRUE)$solution
```

### Results obtained
```
> # RESULTS when the time is 8 hours ## -----------------------------------------
> # $30
> lp(direction = "max", OBJ, LHS, DIR, RHS8.30, all.int = TRUE)
Error: no feasible solution found> lp(direction = "max", OBJ, LHS, DIR, RHS8.30, all.int = TRUE)$solution
 [1] 0 0 0 0 0 0 0 0 0 0
> 
> # $60
> lp(direction = "max", OBJ, LHS, DIR, RHS8.60, all.int = TRUE)
Success: the objective function is 6 
> lp(direction = "max", OBJ, LHS, DIR, RHS8.60, all.int = TRUE)$solution
 [1] 1 1 1 0 0 0 0 0 1 2
> 
> # $100
> lp(direction = "max", OBJ, LHS, DIR, RHS8.100, all.int = TRUE)
Success: the objective function is 6 
> lp(direction = "max", OBJ, LHS, DIR, RHS8.100, all.int = TRUE)$solution
 [1] 1 1 1 0 0 0 0 0 1 2
> 
> # $300
> lp(direction = "max", OBJ, LHS, DIR, RHS8.300, all.int = TRUE)
Success: the objective function is 6 
> lp(direction = "max", OBJ, LHS, DIR, RHS8.300, all.int = TRUE)$solution
 [1] 3 1 1 0 0 0 0 0 1 0
> 
> # $500
> lp(direction = "max", OBJ, LHS, DIR, RHS8.500, all.int = TRUE)
Success: the objective function is 6 
> lp(direction = "max", OBJ, LHS, DIR, RHS8.500, all.int = TRUE)$solution
 [1] 3 1 1 0 0 0 0 0 1 0
> 
> 
>
> ## RESULTS when the time is 16 hours ## ----------------------------------------
> # $30
> lp(direction = "max", OBJ, LHS, DIR, RHS16.30, all.int = TRUE)
Error: no feasible solution found> lp(direction = "max", OBJ, LHS, DIR, RHS16.30, all.int = TRUE)$solution
 [1] 0 0 0 0 0 0 0 0 0 0
> 
> # $60
> lp(direction = "max", OBJ, LHS, DIR, RHS16.60, all.int = TRUE)
Success: the objective function is 9 
> lp(direction = "max", OBJ, LHS, DIR, RHS16.60, all.int = TRUE)$solution
 [1] 0 1 1 0 0 0 0 0 1 6
> 
> # $100
> lp(direction = "max", OBJ, LHS, DIR, RHS16.100, all.int = TRUE)
Success: the objective function is 14 
> lp(direction = "max", OBJ, LHS, DIR, RHS16.100, all.int = TRUE)$solution
 [1] 0 1 1 1 0 3 0 0 2 6
> 
> # $300
> lp(direction = "max", OBJ, LHS, DIR, RHS16.300, all.int = TRUE)
Success: the objective function is 26 
> lp(direction = "max", OBJ, LHS, DIR, RHS16.300, all.int = TRUE)$solution
 [1]  4  1  1  0  0  0  0  5  1 14
> 
> # $500
> lp(direction = "max", OBJ, LHS, DIR, RHS16.500, all.int = TRUE)
Success: the objective function is 29 
> lp(direction = "max", OBJ, LHS, DIR, RHS16.500, all.int = TRUE)$solution
 [1]  9  1  1  0  0  0  0  3  1 14
> 
> 
> 
> ## RESULTS when the time is 32 hours ## ----------------------------------------
> # $30
> lp(direction = "max", OBJ, LHS, DIR, RHS32.30, all.int = TRUE)
Error: no feasible solution found> lp(direction = "max", OBJ, LHS, DIR, RHS32.30, all.int = TRUE)$solution
 [1] 0 0 0 0 0 0 0 0 0 0
> 
> # $60
> lp(direction = "max", OBJ, LHS, DIR, RHS32.60, all.int = TRUE)
Success: the objective function is 9 
> lp(direction = "max", OBJ, LHS, DIR, RHS32.60, all.int = TRUE)$solution
 [1] 0 1 1 0 0 0 0 0 1 6
> 
> # $100
> lp(direction = "max", OBJ, LHS, DIR, RHS32.100, all.int = TRUE)
Success: the objective function is 15 
> lp(direction = "max", OBJ, LHS, DIR, RHS32.100, all.int = TRUE)$solution
 [1] 0 1 1 0 0 5 0 0 2 6
> 
> # $300
> lp(direction = "max", OBJ, LHS, DIR, RHS32.300, all.int = TRUE)
Success: the objective function is 39 
> lp(direction = "max", OBJ, LHS, DIR, RHS32.300, all.int = TRUE)$solution
 [1]  5  1  1  7  1  3  0  1  5 15
> 
> # $500
> lp(direction = "max", OBJ, LHS, DIR, RHS32.500, all.int = TRUE)
Success: the objective function is 48 
> lp(direction = "max", OBJ, LHS, DIR, RHS32.500, all.int = TRUE)$solution
 [1]  9  1  1  1  0  0  0 13  9 14
> 
> 
> 
> ## RESULTS when the time is 48 hours ## ----------------------------------------
> # $30
> lp(direction = "max", OBJ, LHS, DIR, RHS48.30, all.int = TRUE)
Error: no feasible solution found> lp(direction = "max", OBJ, LHS, DIR, RHS48.30, all.int = TRUE)$solution
 [1] 0 0 0 0 0 0 0 0 0 0
> 
> # $60
> lp(direction = "max", OBJ, LHS, DIR, RHS48.60, all.int = TRUE)
Success: the objective function is 9 
> lp(direction = "max", OBJ, LHS, DIR, RHS48.60, all.int = TRUE)$solution
 [1] 0 1 1 0 0 0 0 0 1 6
> 
> # $100
> lp(direction = "max", OBJ, LHS, DIR, RHS48.100, all.int = TRUE)
Success: the objective function is 15 
> lp(direction = "max", OBJ, LHS, DIR, RHS48.100, all.int = TRUE)$solution
 [1] 0 1 1 0 0 5 0 0 2 6
> 
> # $300
> lp(direction = "max", OBJ, LHS, DIR, RHS48.300, all.int = TRUE)
Success: the objective function is 45 
> lp(direction = "max", OBJ, LHS, DIR, RHS48.300, all.int = TRUE)$solution
 [1]  5  1  1  0  3 15  0  0  5 15
> 
> # $500
> lp(direction = "max", OBJ, LHS, DIR, RHS48.500, all.int = TRUE)
Success: the objective function is 58 
> lp(direction = "max", OBJ, LHS, DIR, RHS48.500, all.int = TRUE)$solution
 [1]  9  1  1  2  0  9  0 12  9 15
 ```
## Second month R code
### Control group code
```
library(lpSolve)

# This is a control group code for the second month where the restriction is
# At least a batch of each product

## Define the yj and zj values when Budget is $73.13 ---------------------------
y1.agar_73.13 = 1
y2.apfl_73.13 = 1
y3.baso_73.13 = 1
y4.brsu_73.13 = 3
y5.choc_73.13 = 3
y6.coco_73.13 = 1
y7.eggs_73.13 = 1
y8.grsu_73.13 = 1
y9.milk_73.13 = 1
y10.ore_73.13 = 2
y11.sbu_73.13 = 3
y12.vae_73.13 = 1
y13.wat_73.13 = 1
y14.whc_73.13 = 1
y15.yog_73.13 = 1

z01_73.13 = 0
z02_73.13 = 855
z03_73.13 = 0
z04_73.13 = 40
z05_73.13 = 300
z06_73.13 = 175
z07_73.13 = 23
z08_73.13 = 1875
z09_73.13 = 0
z10_73.13 = 0
z11_73.13 = 34
z12_73.13 = 110
z13_73.13 = 1300
z14_73.13 = 800
z15_73.13 = 700

## Define the objective function -----------------------------------------------
OBJ <- c(1, 1, 1, 1, 1, 1, 1, 1, 1, 1)

## Define the LHS coefficients -------------------------------------------------
LHS <- matrix(c(
  0.3, 2.5, 3.5, 1, 1.7, 1.7, 2, 0.7, 1, 0.3,
  010, 000, 000, 000, 000,   000, 000, 000, 000, 000,
  000, 025, 120, 190, 090,   045, 000, 250, 000, 040,
  000, 000, 000, 005, 003,   000, 000, 005, 000, 000,
  000, 060, 000, 000, 150,   000, 000, 000, 000, 000,
  150, 200, 100, 000, 225,   100, 200, 050, 400, 000,
  
  000, 025, 000, 100, 000,   000, 000, 005, 000, 005,
  000, 003, 004, 001, 002,   002, 000, 001, 000, 000,
  100, 125, 000, 000, 000,   020, 000, 012, 000, 075,
  500, 000, 000, 000, 000,   000, 000, 175, 000, 150,
  000, 000, 000, 000, 000,   000, 013, 000, 013, 000,
  
  000, 115, 110, 100, 060,   050, 030, 110, 000, 000,
  000, 005, 000, 000, 010,   000, 000, 010, 000, 005,
  000, 000, 200, 150, 000,   000, 000, 000, 000, 000,
  000, 000, 200, 000, 000,   000, 300, 000, 000, 000,
  000, 000, 000, 000, 000,   000, 000, 245, 300, 000,
  
  1, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 1, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 1, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 1, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 1, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 1, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 1, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 1, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 1, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 1), nrow = 26, byrow = TRUE)

## Inequalities direction ------------------------------------------------------
DIR <- c("<=",
         "<=", "<=", "<=", "<=", "<=", "<=", "<=", "<=", "<=", "<=",
         "<=", "<=", "<=", "<=", "<=",
         ">=", ">=", ">=", ">=", ">=", ">=", ">=", ">=", ">=", ">=")
## Define the RHS coefficients when time available is 14.7 hours ---------------

# $73.13
RHS8.73.13 <-c(
  14.7,
  10*y1.agar_73.13+z01_73.13, 1000*y2.apfl_73.13+z02_73.13, 
  100*y3.baso_73.13+z03_73.13, 100*y4.brsu_73.13+z04_73.13, 
  500*y5.choc_73.13+z05_73.13, 200*y6.coco_73.13+z06_73.13, 
  30*y7.eggs_73.13+z07_73.13, 2000*y8.grsu_73.13+z08_73.13, 
  1000*y9.milk_73.13+z09_73.13, 13*y10.ore_73.13+z10_73.13, 
  250*y11.sbu_73.13+z11_73.13, 115*y12.vae_73.13+z12_73.13, 
  1500*y13.wat_73.13+z13_73.13, 1000*y14.whc_73.13+z14_73.13, 
  1000*y15.yog_73.13+z15_73.13, 
  1, 1, 1, 1, 1, 1, 1, 1, 1, 1)

################################################################################
# RESULTS when the time is 14.7 hours ## ---------------------------------------
# $30
lp(direction = "max", OBJ, LHS, DIR, RHS8.73.13, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS8.73.13, all.int = TRUE)$solution
```

### Control group result
```
> # RESULTS when the time is 14.7 hours ## ---------------------------------------
> # $30
> lp(direction = "max", OBJ, LHS, DIR, RHS8.73.13, all.int = TRUE)
Success: the objective function is 10 
> lp(direction = "max", OBJ, LHS, DIR, RHS8.73.13, all.int = TRUE)$solution
 [1] 1 1 1 1 1 1 1 1 1 1
 ```

### Code for the time range of 8, 16, 32 and 48 hours when the budget is $30, $60, $100, $300 and $500
```
library(lpSolve)

# This is code for the second month where the restriction is
# At least a batch of each product

## Define yj values for all budgets --------------------------------------------
y1.agar_30 = 0
y2.apfl_30 = 0
y3.baso_30 = 0
y4.brsu_30 = 3
y5.choc_30 = 3
y6.coco_30 = 0
y7.eggs_30 = 0
y8.grsu_30 = 0
y9.milk_30 = 0
y10.ore_30 = 0
y11.sbu_30 = 3
y12.vae_30 = 0
y13.wat_30 = 0
y14.whc_30 = 0
y15.yog_30 = 0 # $30

y1.agar_60 = 0
y2.apfl_60 = 1
y3.baso_60 = 0
y4.brsu_60 = 3
y5.choc_60 = 3
y6.coco_60 = 1
y7.eggs_60 = 1
y8.grsu_60 = 1
y9.milk_60 = 0
y10.ore_60 = 2
y11.sbu_60 = 3
y12.vae_60 = 1
y13.wat_60 = 1
y14.whc_60 = 0
y15.yog_60 = 0 # $60

y1.agar_100 = 1
y2.apfl_100 = 1
y3.baso_100 = 1
y4.brsu_100 = 6
y5.choc_100 = 6
y6.coco_100 = 1
y7.eggs_100 = 1
y8.grsu_100 = 1
y9.milk_100 = 1
y10.ore_100 = 2
y11.sbu_100 = 3
y12.vae_100 = 1
y13.wat_100 = 1
y14.whc_100 = 1
y15.yog_100 = 1 # $100

y1.agar_300 = 4
y2.apfl_300 = 4
y3.baso_300 = 4
y4.brsu_300 = 15
y5.choc_300 = 12
y6.coco_300 = 4
y7.eggs_300 = 4
y8.grsu_300 = 4
y9.milk_300 = 4
y10.ore_300 = 8
y11.sbu_300 = 12
y12.vae_300 = 4
y13.wat_300 = 4
y14.whc_300 = 4
y15.yog_300 = 4 # $300

y1.agar_500 = 6
y2.apfl_500 = 7
y3.baso_500 = 6
y4.brsu_500 = 21
y5.choc_500 = 21
y6.coco_500 = 7
y7.eggs_500 = 7
y8.grsu_500 = 7
y9.milk_500 = 6
y10.ore_500 = 14
y11.sbu_500 = 21
y12.vae_500 = 7
y13.wat_500 = 7
y14.whc_500 = 6
y15.yog_500 = 7 # $500

## Define the zj values when Budget is $30 -------------------------------------
# Leftover from 1st month at 8 hours, 16 hours, 32 hours and 48 hours for $30 
z01_30 = 0
z02_30 = 1000
z03_30 = 0
z04_30 = 100
z05_30 = 500
z06_30 = 200
z07_30 = 30
z08_30 = 0
z09_30 = 0
z10_30 = 0
z11_30 = 0
z12_30 = 0
z13_30 = 0
z14_30 = 0
z15_30 = 0

## Define the zj value when Budget is $60 --------------------------------------
z01_60_8 = 0
z02_60_8 = 775
z03_60_8 = 100
z04_60_8 = 40
z05_60_8 = 150
z06_60_8 = 165
z07_60_8 = 23
z08_60_8 = 1625
z09_60_8 = 200
z10_60_8 = 0
z11_60_8 = 34
z12_60_8 = 100
z13_60_8 = 1300
z14_60_8 = 800
z15_60_8 = 1700 # 8 hours

z01_60_16_32_48 = 10
z02_60_16_32_48 = 615
z03_60_16_32_48 = 100
z04_60_16_32_48 = 40
z05_60_16_32_48 = 300
z06_60_16_32_48 = 145
z07_60_16_32_48 = 23
z08_60_16_32_48 = 1425
z09_60_16_32_48 = 100
z10_60_16_32_48 = 0
z11_60_16_32_48 = 34
z12_60_16_32_48 = 80
z13_60_16_32_48 = 1300
z14_60_16_32_48 = 800
z15_60_16_32_48 = 700 # 16 hours, 32 hours and 48 hours

## Define the zj value when Budget is $100 -------------------------------------
z01_100_8 = 10
z02_100_8 = 1775
z03_100_8 = 100
z04_100_8 = 140
z05_100_8 = 1150
z06_100_8 = 365
z07_100_8 = 53
z08_100_8 = 3625
z09_100_8 = 200
z10_100_8 = 13
z11_100_8 = 293
z12_100_8 = 215
z13_100_8 = 2800
z14_100_8 = 800
z15_100_8 = 1700 # 8 hours

z01_100_16 = 20
z02_100_16 = 1290
z03_100_16 = 95
z04_100_16 = 140
z05_100_16 = 600
z06_100_16 = 245
z07_100_16 = 46
z08_100_16 = 3365
z09_100_16 = 100
z10_100_16 = 0
z11_100_16 = 43
z12_100_16 = 195
z13_100_16 = 2650
z14_100_16 = 800
z15_100_16 = 1400 # 16 hours

z01_100_32_48 = 20
z02_100_32_48 = 1390
z03_100_32_48 = 100
z04_100_32_48 = 140
z05_100_32_48 = 400
z06_100_32_48 = 345
z07_100_32_48 = 43
z08_100_32_48 = 3325
z09_100_32_48 = 100
z10_100_32_48 = 0
z11_100_32_48 = 43
z12_100_32_48 = 195
z13_100_32_48 = 2800
z14_100_32_48 = 800
z15_100_32_48 = 1400 # 32 hours and 48 hours



## Define the zj value when Budget is $300 -------------------------------------
z01_300_8 = 20
z02_300_8 = 5855
z03_300_8 = 500
z04_300_8 = 540
z05_300_8 = 4850
z06_300_8 = 1175
z07_300_8 = 143
z08_300_8 = 9575
z09_300_8 = 3500
z10_300_8 = 53
z11_300_8 = 1070
z12_300_8 = 570
z13_300_8 = 7300
z14_300_8 = 4800
z15_300_8 = 4705 # 8 hours

z01_300_16 = 10
z02_300_16 = 4045
z03_300_16 = 475
z04_300_16 = 540
z05_300_16 = 4450
z06_300_16 = 1080
z07_300_16 = 138
z08_300_16 = 8365
z09_300_16 = 25
z10_300_16 = 52
z11_300_16 = 520
z12_300_16 = 450
z13_300_16 = 7300
z14_300_16 = 4800
z15_300_16 = 3475 # 16 hours

z01_300_32 = 0
z02_300_32 = 3450
z03_300_32 = 457
z04_300_32 = 390
z05_300_32 = 2375
z06_300_32 = 395
z07_300_32 = 127
z08_300_32 = 8178
z09_300_32 = 75
z10_300_32 = 0
z11_300_32 = 50
z12_300_32 = 475
z13_300_32 = 6250
z14_300_32 = 4800
z15_300_32 = 3255 # 32 hours

z01_300_48 = 0
z02_300_48 = 4310
z03_300_48 = 491
z04_300_48 = 90
z05_300_48 = 775
z06_300_48 = 110
z07_300_48 = 107
z08_300_48 = 7950
z09_300_48 = 250
z10_300_48 = 0
z11_300_48 = 140
z12_300_48 = 465
z13_300_48 = 7300
z14_300_48 = 4800
z15_300_48 = 3500 # 48 hours

## Define the zj value when Budget is $500 -------------------------------------
z01_500_8 = 60
z02_500_8 = 8855
z03_500_8 = 900
z04_500_8 = 840
z05_500_8 = 7850
z06_500_8 = 1175
z07_500_8 = 263
z08_500_8 = 17575
z09_500_8 = 7500
z10_500_8 = 104
z11_500_8 = 2106
z12_500_8 = 1030
z13_500_8 = 13300
z14_500_8 = 8800
z15_500_8 = 8700 # 8 hours

z01_500_16 = 0
z02_500_16 = 7545
z03_500_16 = 885
z04_500_16 = 840
z05_500_16 = 6800
z06_500_16 = 1690
z07_500_16 = 260
z08_500_16 = 15889
z09_500_16 = 1875
z10_500_16 = 104
z11_500_16 = 1776
z12_500_16 = 930
z13_500_16 = 13300
z14_500_16 = 8800
z15_500_16 = 7965 # 16 hours

z01_500_32 = 0
z02_500_32 = 4855
z03_500_32 = 830
z04_500_32 = 840
z05_500_32 = 3100
z06_500_32 = 1540
z07_500_32 = 249
z08_500_32 = 15769
z09_500_32 = 125
z10_500_32 = 0
z11_500_32 = 576
z12_500_32 = 830
z13_500_32 = 13150
z14_500_32 = 8800
z15_500_32 = 3115 # 32 hours

z01_500_48 = 0
z02_500_48 = 4470
z03_500_48 = 830
z04_500_48 = 840
z05_500_48 = 2250
z06_500_48 = 1440
z07_500_48 = 231
z08_500_48 = 15526
z09_500_48 = 150
z10_500_48 = 0
z11_500_48 = 136
z12_500_48 = 835
z13_500_48 = 13000
z14_500_48 = 8800
z15_500_48 = 3360 # 48 hours

################################################################################
## Define the objective function -----------------------------------------------
OBJ <- c(1, 1, 1, 1, 1, 1, 1, 1, 1, 1)

## Define the LHS coefficients -------------------------------------------------
LHS <- matrix(c(
  0.3, 2.5, 3.5, 1, 1.7, 1.7, 2, 0.7, 1, 0.3,
  010, 000, 000, 000, 000,   000, 000, 000, 000, 000,
  000, 025, 120, 190, 090,   045, 000, 250, 000, 040,
  000, 000, 000, 005, 003,   000, 000, 005, 000, 000,
  000, 060, 000, 000, 150,   000, 000, 000, 000, 000,
  150, 200, 100, 000, 225,   100, 200, 050, 400, 000,
  
  000, 025, 000, 100, 000,   000, 000, 005, 000, 005,
  000, 003, 004, 001, 002,   002, 000, 001, 000, 000,
  100, 125, 000, 000, 000,   020, 000, 012, 000, 075,
  500, 000, 000, 000, 000,   000, 000, 175, 000, 150,
  000, 000, 000, 000, 000,   000, 013, 000, 013, 000,
  
  000, 115, 110, 100, 060,   050, 030, 110, 000, 000,
  000, 005, 000, 000, 010,   000, 000, 010, 000, 005,
  000, 000, 200, 150, 000,   000, 000, 000, 000, 000,
  000, 000, 200, 000, 000,   000, 300, 000, 000, 000,
  000, 000, 000, 000, 000,   000, 000, 245, 300, 000,
  
  1, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 1, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 1, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 1, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 1, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 1, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 1, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 1, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 1, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 1), nrow = 26, byrow = TRUE)

## Inequalities direction ------------------------------------------------------
DIR <- c("<=",
         "<=", "<=", "<=", "<=", "<=", "<=", "<=", "<=", "<=", "<=",
         "<=", "<=", "<=", "<=", "<=",
         ">=", ">=", ">=", ">=", ">=", ">=", ">=", ">=", ">=", ">=")

## Define the RHS coefficients when time available is 8 hours ------------------

# $30
RHS8.30 <-c(
  8,
  10*y1.agar_30+z01_30, 1000*y2.apfl_30+z02_30, 100*y3.baso_30+z03_30, 
  100*y4.brsu_30+z04_30, 500*y5.choc_30+z05_30, 200*y6.coco_30+z06_30, 
  30*y7.eggs_30+z07_30, 2000*y8.grsu_30+z08_30, 1000*y9.milk_30+z09_30, 
  13*y10.ore_30+z10_30, 250*y11.sbu_30+z11_30, 115*y12.vae_30+z12_30, 
  1500*y13.wat_30+z13_30, 1000*y14.whc_30+z14_30, 1000*y15.yog_30+z15_30, 
  1, 1, 1, 1, 1, 1, 1, 1, 1, 1)

# $60
RHS8.60 <- c(
  8,
  10*y1.agar_60+z01_60_8, 1000*y2.apfl_60+z02_60_8, 100*y3.baso_60+z03_60_8, 
  100*y4.brsu_60+z04_60_8, 500*y5.choc_60+z05_60_8, 200*y6.coco_60+z06_60_8, 
  30*y7.eggs_60+z07_60_8, 2000*y8.grsu_60+z08_60_8, 1000*y9.milk_60+z09_60_8, 
  13*y10.ore_60+z10_60_8, 250*y11.sbu_60+z11_60_8, 115*y12.vae_60+z12_60_8, 
  1500*y13.wat_60+z13_60_8, 1000*y14.whc_60+z14_60_8, 1000*y15.yog_60+z15_60_8,
  1, 1, 1, 1, 1, 1, 1, 1, 1, 1)

# $100
RHS8.100 <- c(
  8,
  10*y1.agar_100+z01_100_8, 1000*y2.apfl_100+z02_100_8, 
  100*y3.baso_100+z03_100_8, 100*y4.brsu_100+z04_100_8, 
  500*y5.choc_100+z05_100_8, 200*y6.coco_100+z06_100_8, 
  30*y7.eggs_100+z07_100_8, 2000*y8.grsu_100+z08_100_8, 
  1000*y9.milk_100+z09_100_8, 13*y10.ore_100+z10_100_8, 
  250*y11.sbu_100+z11_100_8, 115*y12.vae_100+z12_100_8, 
  1500*y13.wat_100+z13_100_8, 1000*y14.whc_100+z14_100_8, 
  1000*y15.yog_100+z15_100_8,
  1, 1, 1, 1, 1, 1, 1, 1, 1, 1)

# $300
RHS8.300 <- c(
  8,
  10*y1.agar_300+z01_300_8, 1000*y2.apfl_300+z02_300_8, 
  100*y3.baso_300+z03_300_8, 100*y4.brsu_300+z04_300_8, 
  500*y5.choc_300+z05_300_8, 200*y6.coco_300+z06_300_8, 
  30*y7.eggs_300+z07_300_8, 2000*y8.grsu_300+z08_300_8, 
  1000*y9.milk_300+z09_300_8, 13*y10.ore_300+z10_300_8, 
  250*y11.sbu_300+z11_300_8, 115*y12.vae_300+z12_300_8, 
  1500*y13.wat_300+z13_300_8, 1000*y14.whc_300+z14_300_8, 
  1000*y15.yog_300+z15_300_8,
  1, 1, 1, 1, 1, 1, 1, 1, 1, 1)

# $500
RHS8.500 <- c(
  8,
  10*y1.agar_500+z01_500_8, 1000*y2.apfl_500+z02_500_8, 
  100*y3.baso_500+z03_500_8, 100*y4.brsu_500+z04_500_8, 
  500*y5.choc_500+z05_500_8, 200*y6.coco_500+z06_500_8, 
  30*y7.eggs_500+z07_500_8, 2000*y8.grsu_500+z08_500_8, 
  1000*y9.milk_500+z09_500_8, 13*y10.ore_500+z10_500_8, 
  250*y11.sbu_500+z11_500_8, 115*y12.vae_500+z12_500_8, 
  1500*y13.wat_500+z13_500_8, 1000*y14.whc_500+z14_500_8, 
  1000*y15.yog_500+z15_500_8,
  1, 1, 1, 1, 1, 1, 1, 1, 1, 1)

## Define the RHS coefficients when time available is 16 hours -----------------

# $30
RHS16.30 <-c(
  16,
  10*y1.agar_30+z01_30, 1000*y2.apfl_30+z02_30, 100*y3.baso_30+z03_30, 
  100*y4.brsu_30+z04_30, 500*y5.choc_30+z05_30, 200*y6.coco_30+z06_30, 
  30*y7.eggs_30+z07_30, 2000*y8.grsu_30+z08_30, 1000*y9.milk_30+z09_30, 
  13*y10.ore_30+z10_30, 250*y11.sbu_30+z11_30, 115*y12.vae_30+z12_30, 
  1500*y13.wat_30+z13_30, 1000*y14.whc_30+z14_30, 1000*y15.yog_30+z15_30,
  1, 1, 1, 1, 1, 1, 1, 1, 1, 1)

# $60
RHS16.60 <- c(
  16,
  10*y1.agar_60+z01_60_16_32_48, 1000*y2.apfl_60+z02_60_16_32_48, 
  100*y3.baso_60+z03_60_16_32_48, 100*y4.brsu_60+z04_60_16_32_48, 
  500*y5.choc_60+z05_60_16_32_48, 200*y6.coco_60+z06_60_16_32_48, 
  30*y7.eggs_60+z07_60_16_32_48, 2000*y8.grsu_60+z08_60_16_32_48, 
  1000*y9.milk_60+z09_60_16_32_48, 13*y10.ore_60+z10_60_16_32_48, 
  250*y11.sbu_60+z11_60_16_32_48, 115*y12.vae_60+z12_60_16_32_48, 
  1500*y13.wat_60+z13_60_16_32_48, 1000*y14.whc_60+z14_60_16_32_48, 
  1000*y15.yog_60+z15_60_16_32_48,
  1, 1, 1, 1, 1, 1, 1, 1, 1, 1)  

# $100
RHS16.100 <- c(
  16,
  10*y1.agar_100+z01_100_16, 1000*y2.apfl_100+z02_100_16, 
  100*y3.baso_100+z03_100_16, 100*y4.brsu_100+z04_100_16, 
  500*y5.choc_100+z05_100_16, 200*y6.coco_100+z06_100_16, 
  30*y7.eggs_100+z07_100_16, 2000*y8.grsu_100+z08_100_16, 
  1000*y9.milk_100+z09_100_16, 13*y10.ore_100+z10_100_16, 
  250*y11.sbu_100+z11_100_16, 115*y12.vae_100+z12_100_16, 
  1500*y13.wat_100+z13_100_16, 1000*y14.whc_100+z14_100_16, 
  1000*y15.yog_100+z15_100_16,
  1, 1, 1, 1, 1, 1, 1, 1, 1, 1)

# $300
RHS16.300 <- c(
  16,
  10*y1.agar_300+z01_300_16, 1000*y2.apfl_300+z02_300_16, 
  100*y3.baso_300+z03_300_16, 100*y4.brsu_300+z04_300_16, 
  500*y5.choc_300+z05_300_16, 200*y6.coco_300+z06_300_16, 
  30*y7.eggs_300+z07_300_16, 2000*y8.grsu_300+z08_300_16, 
  1000*y9.milk_300+z09_300_16, 13*y10.ore_300+z10_300_16, 
  250*y11.sbu_300+z11_300_16, 115*y12.vae_300+z12_300_16, 
  1500*y13.wat_300+z13_300_16, 1000*y14.whc_300+z14_300_16, 
  1000*y15.yog_300+z15_300_16,
  1, 1, 1, 1, 1, 1, 1, 1, 1, 1)

# $500
RHS16.500 <- c(
  16,
  10*y1.agar_500+z01_500_16, 1000*y2.apfl_500+z02_500_16, 
  100*y3.baso_500+z03_500_16, 100*y4.brsu_500+z04_500_16, 
  500*y5.choc_500+z05_500_16, 200*y6.coco_500+z06_500_16, 
  30*y7.eggs_500+z07_500_16, 2000*y8.grsu_500+z08_500_16, 
  1000*y9.milk_500+z09_500_16, 13*y10.ore_500+z10_500_16, 
  250*y11.sbu_500+z11_500_16, 115*y12.vae_500+z12_500_16, 
  1500*y13.wat_500+z13_500_16, 1000*y14.whc_500+z14_500_16, 
  1000*y15.yog_500+z15_500_16,
  1, 1, 1, 1, 1, 1, 1, 1, 1, 1)

## Define the RHS coefficients when time available is 32 hours -----------------

# $30
RHS32.30 <-c(
  32,
  10*y1.agar_30+z01_30, 1000*y2.apfl_30+z02_30, 100*y3.baso_30+z03_30, 
  100*y4.brsu_30+z04_30, 500*y5.choc_30+z05_30, 200*y6.coco_30+z06_30, 
  30*y7.eggs_30+z07_30, 2000*y8.grsu_30+z08_30, 1000*y9.milk_30+z09_30, 
  13*y10.ore_30+z10_30, 250*y11.sbu_30+z11_30, 115*y12.vae_30+z12_30, 
  1500*y13.wat_30+z13_30, 1000*y14.whc_30+z14_30, 1000*y15.yog_30+z15_30,
  1, 1, 1, 1, 1, 1, 1, 1, 1, 1)

# $60
RHS32.60 <- c(
  32,
  10*y1.agar_60+z01_60_16_32_48, 1000*y2.apfl_60+z02_60_16_32_48, 
  100*y3.baso_60+z03_60_16_32_48, 100*y4.brsu_60+z04_60_16_32_48, 
  500*y5.choc_60+z05_60_16_32_48, 200*y6.coco_60+z06_60_16_32_48, 
  30*y7.eggs_60+z07_60_16_32_48, 2000*y8.grsu_60+z08_60_16_32_48, 
  1000*y9.milk_60+z09_60_16_32_48, 13*y10.ore_60+z10_60_16_32_48, 
  250*y11.sbu_60+z11_60_16_32_48, 115*y12.vae_60+z12_60_16_32_48, 
  1500*y13.wat_60+z13_60_16_32_48, 1000*y14.whc_60+z14_60_16_32_48, 
  1000*y15.yog_60+z15_60_16_32_48,
  1, 1, 1, 1, 1, 1, 1, 1, 1, 1)  

# $100
RHS32.100 <- c(
  32,
  10*y1.agar_100+z01_100_32_48, 1000*y2.apfl_100+z02_100_32_48, 
  100*y3.baso_100+z03_100_32_48, 100*y4.brsu_100+z04_100_32_48, 
  500*y5.choc_100+z05_100_32_48, 200*y6.coco_100+z06_100_32_48, 
  30*y7.eggs_100+z07_100_32_48, 2000*y8.grsu_100+z08_100_32_48, 
  1000*y9.milk_100+z09_100_32_48, 13*y10.ore_100+z10_100_32_48, 
  250*y11.sbu_100+z11_100_32_48, 115*y12.vae_100+z12_100_32_48, 
  1500*y13.wat_100+z13_100_32_48, 1000*y14.whc_100+z14_100_32_48, 
  1000*y15.yog_100+z15_100_32_48,
  1, 1, 1, 1, 1, 1, 1, 1, 1, 1)

# $300
RHS32.300 <- c(
  32,
  10*y1.agar_300+z01_300_32, 1000*y2.apfl_300+z02_300_32, 
  100*y3.baso_300+z03_300_32, 100*y4.brsu_300+z04_300_32, 
  500*y5.choc_300+z05_300_32, 200*y6.coco_300+z06_300_32, 
  30*y7.eggs_300+z07_300_32, 2000*y8.grsu_300+z08_300_32, 
  1000*y9.milk_300+z09_300_32, 13*y10.ore_300+z10_300_32, 
  250*y11.sbu_300+z11_300_32, 115*y12.vae_300+z12_300_32, 
  1500*y13.wat_300+z13_300_32, 1000*y14.whc_300+z14_300_32, 
  1000*y15.yog_300+z15_300_32,
  1, 1, 1, 1, 1, 1, 1, 1, 1, 1)

# $500
RHS32.500 <- c(
  32,
  10*y1.agar_500+z01_500_32, 1000*y2.apfl_500+z02_500_32, 
  100*y3.baso_500+z03_500_32, 100*y4.brsu_500+z04_500_32, 
  500*y5.choc_500+z05_500_32, 200*y6.coco_500+z06_500_32, 
  30*y7.eggs_500+z07_500_32, 2000*y8.grsu_500+z08_500_32, 
  1000*y9.milk_500+z09_500_32, 13*y10.ore_500+z10_500_32, 
  250*y11.sbu_500+z11_500_32, 115*y12.vae_500+z12_500_32, 
  1500*y13.wat_500+z13_500_32, 1000*y14.whc_500+z14_500_32, 
  1000*y15.yog_500+z15_500_32,
  1, 1, 1, 1, 1, 1, 1, 1, 1, 1)

## Define the RHS coefficients when time available is 48 hours -----------------

# $30
RHS48.30 <-c(
  48,
  10*y1.agar_30+z01_30, 1000*y2.apfl_30+z02_30, 100*y3.baso_30+z03_30, 
  100*y4.brsu_30+z04_30, 500*y5.choc_30+z05_30, 200*y6.coco_30+z06_30, 
  30*y7.eggs_30+z07_30, 2000*y8.grsu_30+z08_30, 1000*y9.milk_30+z09_30, 
  13*y10.ore_30+z10_30, 250*y11.sbu_30+z11_30, 115*y12.vae_30+z12_30, 
  1500*y13.wat_30+z13_30, 1000*y14.whc_30+z14_30, 1000*y15.yog_30+z15_30,
  1, 1, 1, 1, 1, 1, 1, 1, 1, 1)

# $60
RHS48.60 <- c(
  48,
  10*y1.agar_60+z01_60_16_32_48, 1000*y2.apfl_60+z02_60_16_32_48, 
  100*y3.baso_60+z03_60_16_32_48, 100*y4.brsu_60+z04_60_16_32_48, 
  500*y5.choc_60+z05_60_16_32_48, 200*y6.coco_60+z06_60_16_32_48, 
  30*y7.eggs_60+z07_60_16_32_48, 2000*y8.grsu_60+z08_60_16_32_48, 
  1000*y9.milk_60+z09_60_16_32_48, 13*y10.ore_60+z10_60_16_32_48, 
  250*y11.sbu_60+z11_60_16_32_48, 115*y12.vae_60+z12_60_16_32_48, 
  1500*y13.wat_60+z13_60_16_32_48, 1000*y14.whc_60+z14_60_16_32_48, 
  1000*y15.yog_60+z15_60_16_32_48,
  1, 1, 1, 1, 1, 1, 1, 1, 1, 1)  

# $100
RHS48.100 <- c(
  48,
  10*y1.agar_100+z01_100_32_48, 1000*y2.apfl_100+z02_100_32_48, 
  100*y3.baso_100+z03_100_32_48, 100*y4.brsu_100+z04_100_32_48, 
  500*y5.choc_100+z05_100_32_48, 200*y6.coco_100+z06_100_32_48, 
  30*y7.eggs_100+z07_100_32_48, 2000*y8.grsu_100+z08_100_32_48, 
  1000*y9.milk_100+z09_100_32_48, 13*y10.ore_100+z10_100_32_48, 
  250*y11.sbu_100+z11_100_32_48, 115*y12.vae_100+z12_100_32_48, 
  1500*y13.wat_100+z13_100_32_48, 1000*y14.whc_100+z14_100_32_48, 
  1000*y15.yog_100+z15_100_32_48,
  1, 1, 1, 1, 1, 1, 1, 1, 1, 1)

# $300
RHS48.300 <- c(
  48,
  10*y1.agar_300+z01_300_48, 1000*y2.apfl_300+z02_300_48, 
  100*y3.baso_300+z03_300_48, 100*y4.brsu_300+z04_300_48, 
  500*y5.choc_300+z05_300_48, 200*y6.coco_300+z06_300_48, 
  30*y7.eggs_300+z07_300_48, 2000*y8.grsu_300+z08_300_48, 
  1000*y9.milk_300+z09_300_48, 13*y10.ore_300+z10_300_48, 
  250*y11.sbu_300+z11_300_48, 115*y12.vae_300+z12_300_48, 
  1500*y13.wat_300+z13_300_48, 1000*y14.whc_300+z14_300_48, 
  1000*y15.yog_300+z15_300_48,
  1, 1, 1, 1, 1, 1, 1, 1, 1, 1)

# $500
RHS48.500 <- c(
  48,
  10*y1.agar_500+z01_500_48, 1000*y2.apfl_500+z02_500_48, 
  100*y3.baso_500+z03_500_48, 100*y4.brsu_500+z04_500_48, 
  500*y5.choc_500+z05_500_48, 200*y6.coco_500+z06_500_48, 
  30*y7.eggs_500+z07_500_48, 2000*y8.grsu_500+z08_500_48, 
  1000*y9.milk_500+z09_500_48, 13*y10.ore_500+z10_500_48, 
  250*y11.sbu_500+z11_500_48, 115*y12.vae_500+z12_500_48, 
  1500*y13.wat_500+z13_500_48, 1000*y14.whc_500+z14_500_48, 
  1000*y15.yog_500+z15_500_48,
  1, 1, 1, 1, 1, 1, 1, 1, 1, 1)

################################################################################
# RESULTS when the time is 8 hours ## -----------------------------------------
# $30
lp(direction = "max", OBJ, LHS, DIR, RHS8.30, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS8.30, all.int = TRUE)$solution

# $60
lp(direction = "max", OBJ, LHS, DIR, RHS8.60, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS8.60, all.int = TRUE)$solution

# $100
lp(direction = "max", OBJ, LHS, DIR, RHS8.100, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS8.100, all.int = TRUE)$solution

# $300
lp(direction = "max", OBJ, LHS, DIR, RHS8.300, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS8.300, all.int = TRUE)$solution

# $500
lp(direction = "max", OBJ, LHS, DIR, RHS8.500, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS8.500, all.int = TRUE)$solution



## RESULTS when the time is 16 hours ## ----------------------------------------
# $30
lp(direction = "max", OBJ, LHS, DIR, RHS16.30, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS16.30, all.int = TRUE)$solution

# $60
lp(direction = "max", OBJ, LHS, DIR, RHS16.60, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS16.60, all.int = TRUE)$solution

# $100
lp(direction = "max", OBJ, LHS, DIR, RHS16.100, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS16.100, all.int = TRUE)$solution

# $300
lp(direction = "max", OBJ, LHS, DIR, RHS16.300, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS16.300, all.int = TRUE)$solution

# $500
lp(direction = "max", OBJ, LHS, DIR, RHS16.500, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS16.500, all.int = TRUE)$solution



## RESULTS when the time is 32 hours ## ----------------------------------------
# $30
lp(direction = "max", OBJ, LHS, DIR, RHS32.30, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS32.30, all.int = TRUE)$solution

# $60
lp(direction = "max", OBJ, LHS, DIR, RHS32.60, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS32.60, all.int = TRUE)$solution

# $100
lp(direction = "max", OBJ, LHS, DIR, RHS32.100, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS32.100, all.int = TRUE)$solution

# $300
lp(direction = "max", OBJ, LHS, DIR, RHS32.300, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS32.300, all.int = TRUE)$solution

# $500
lp(direction = "max", OBJ, LHS, DIR, RHS32.500, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS32.500, all.int = TRUE)$solution



## RESULTS when the time is 48 hours ## ----------------------------------------
# $30
lp(direction = "max", OBJ, LHS, DIR, RHS48.30, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS48.30, all.int = TRUE)$solution

# $60
lp(direction = "max", OBJ, LHS, DIR, RHS48.60, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS48.60, all.int = TRUE)$solution

# $100
lp(direction = "max", OBJ, LHS, DIR, RHS48.100, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS48.100, all.int = TRUE)$solution

# $300
lp(direction = "max", OBJ, LHS, DIR, RHS48.300, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS48.300, all.int = TRUE)$solution

# $500
lp(direction = "max", OBJ, LHS, DIR, RHS48.500, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS48.500, all.int = TRUE)$solution
```

### Results obtained
```
> # RESULTS when the time is 8 hours ## -----------------------------------------
> # $30
> lp(direction = "max", OBJ, LHS, DIR, RHS8.30, all.int = TRUE)
Error: no feasible solution found> lp(direction = "max", OBJ, LHS, DIR, RHS8.30, all.int = TRUE)$solution
 [1] 0 0 0 0 0 0 0 0 0 0
> 
> # $60
> lp(direction = "max", OBJ, LHS, DIR, RHS8.60, all.int = TRUE)
Error: no feasible solution found> lp(direction = "max", OBJ, LHS, DIR, RHS8.60, all.int = TRUE)$solution
 [1] 0 0 0 0 0 0 0 0 0 0
> 
> # $100
> lp(direction = "max", OBJ, LHS, DIR, RHS8.100, all.int = TRUE)
Error: no feasible solution found> lp(direction = "max", OBJ, LHS, DIR, RHS8.100, all.int = TRUE)$solution
 [1] 0 0 0 0 0 0 0 0 0 0
> 
> # $300
> lp(direction = "max", OBJ, LHS, DIR, RHS8.300, all.int = TRUE)
Error: no feasible solution found> lp(direction = "max", OBJ, LHS, DIR, RHS8.300, all.int = TRUE)$solution
 [1] 0 0 0 0 0 0 0 0 0 0
> 
> # $500
> lp(direction = "max", OBJ, LHS, DIR, RHS8.500, all.int = TRUE)
Error: no feasible solution found> lp(direction = "max", OBJ, LHS, DIR, RHS8.500, all.int = TRUE)$solution
 [1] 0 0 0 0 0 0 0 0 0 0
> 
> 
> 
> ## RESULTS when the time is 16 hours ## ----------------------------------------
> # $30
> lp(direction = "max", OBJ, LHS, DIR, RHS16.30, all.int = TRUE)
Error: no feasible solution found> lp(direction = "max", OBJ, LHS, DIR, RHS16.30, all.int = TRUE)$solution
 [1] 0 0 0 0 0 0 0 0 0 0
> 
> # $60
> lp(direction = "max", OBJ, LHS, DIR, RHS16.60, all.int = TRUE)
Error: no feasible solution found> lp(direction = "max", OBJ, LHS, DIR, RHS16.60, all.int = TRUE)$solution
 [1] 0 0 0 0 0 0 0 0 0 0
> 
> # $100
> lp(direction = "max", OBJ, LHS, DIR, RHS16.100, all.int = TRUE)
Success: the objective function is 12 
> lp(direction = "max", OBJ, LHS, DIR, RHS16.100, all.int = TRUE)$solution
 [1] 1 1 1 2 1 1 1 1 1 2
> 
> # $300
> lp(direction = "max", OBJ, LHS, DIR, RHS16.300, all.int = TRUE)
Success: the objective function is 14 
> lp(direction = "max", OBJ, LHS, DIR, RHS16.300, all.int = TRUE)$solution
 [1] 5 1 1 1 1 1 1 1 1 1
> 
> # $500
> lp(direction = "max", OBJ, LHS, DIR, RHS16.500, all.int = TRUE)
Success: the objective function is 14 
> lp(direction = "max", OBJ, LHS, DIR, RHS16.500, all.int = TRUE)$solution
 [1] 5 1 1 1 1 1 1 1 1 1
> 
> 
> 
> ## RESULTS when the time is 32 hours ## ----------------------------------------
> # $30
> lp(direction = "max", OBJ, LHS, DIR, RHS32.30, all.int = TRUE)
Error: no feasible solution found> lp(direction = "max", OBJ, LHS, DIR, RHS32.30, all.int = TRUE)$solution
 [1] 0 0 0 0 0 0 0 0 0 0
> 
> # $60
> lp(direction = "max", OBJ, LHS, DIR, RHS32.60, all.int = TRUE)
Error: no feasible solution found> lp(direction = "max", OBJ, LHS, DIR, RHS32.60, all.int = TRUE)$solution
 [1] 0 0 0 0 0 0 0 0 0 0
> 
> # $100
> lp(direction = "max", OBJ, LHS, DIR, RHS32.100, all.int = TRUE)
Success: the objective function is 15 
> lp(direction = "max", OBJ, LHS, DIR, RHS32.100, all.int = TRUE)$solution
 [1] 1 1 1 1 2 4 1 1 1 2
> 
> # $300
> lp(direction = "max", OBJ, LHS, DIR, RHS32.300, all.int = TRUE)
Success: the objective function is 42 
> lp(direction = "max", OBJ, LHS, DIR, RHS32.300, all.int = TRUE)$solution
 [1]  1  1  1  6  1  1  1  1  7 22
> 
> # $500
> lp(direction = "max", OBJ, LHS, DIR, RHS32.500, all.int = TRUE)
Success: the objective function is 51 
> lp(direction = "max", OBJ, LHS, DIR, RHS32.500, all.int = TRUE)$solution
 [1]  1  1  1  1  1  1  1  1  8 35
> 
> 
> 
> ## RESULTS when the time is 48 hours ## ----------------------------------------
> # $30
> lp(direction = "max", OBJ, LHS, DIR, RHS48.30, all.int = TRUE)
Error: no feasible solution found> lp(direction = "max", OBJ, LHS, DIR, RHS48.30, all.int = TRUE)$solution
 [1] 0 0 0 0 0 0 0 0 0 0
> 
> # $60
> lp(direction = "max", OBJ, LHS, DIR, RHS48.60, all.int = TRUE)
Error: no feasible solution found> lp(direction = "max", OBJ, LHS, DIR, RHS48.60, all.int = TRUE)$solution
 [1] 0 0 0 0 0 0 0 0 0 0
> 
> # $100
> lp(direction = "max", OBJ, LHS, DIR, RHS48.100, all.int = TRUE)
Success: the objective function is 15 
> lp(direction = "max", OBJ, LHS, DIR, RHS48.100, all.int = TRUE)$solution
 [1] 1 1 1 1 2 4 1 1 1 2
> 
> # $300
> lp(direction = "max", OBJ, LHS, DIR, RHS48.300, all.int = TRUE)
Success: the objective function is 52 
> lp(direction = "max", OBJ, LHS, DIR, RHS48.300, all.int = TRUE)$solution
 [1]  1  1  1  7  9  1  1  3  7 21
> 
> # $500
> lp(direction = "max", OBJ, LHS, DIR, RHS48.500, all.int = TRUE)
Success: the objective function is 67 
> lp(direction = "max", OBJ, LHS, DIR, RHS48.500, all.int = TRUE)$solution
 [1]  1  1  1 12  1  1  1  1 13 35
 ```
 
## Third month R code
### Control group code
```
library(lpSolve)

# This is code for the second month where the restriction is
# Only producing Agar-agar (x1), Brownies (x2) and Muffins (x3)

## Define the yj and zj values when Budget is $40.63 ---------------------------
y1.agar_40.63 = 1
y2.apfl_40.63 = 1
y3.baso_40.63 = 1
y4.brsu_40.63 = 1
y5.choc_40.63 = 1
y6.coco_40.63 = 1
y7.eggs_40.63 = 1
y8.grsu_40.63 = 1
y9.milk_40.63 = 1
y10.ore_40.63 = 0
y11.sbu_40.63 = 1
y12.vae_40.63 = 1
y13.wat_40.63 = 0
y14.whc_40.63 = 0
y15.yog_40.63 = 1

z01_40.63 = 0
z02_40.63 = 0
z03_40.63 = 0
z04_40.63 = 0
z05_40.63 = 0
z06_40.63 = 0
z07_40.63 = 0
z08_40.63 = 0
z09_40.63 = 0
z10_40.63 = 0
z11_40.63 = 0
z12_40.63 = 0
z13_40.63 = 0
z14_40.63 = 0
z15_40.63 = 0

################################################################################
## Define the objective function -----------------------------------------------
OBJ <- c(1, 1, 1, 1, 1, 1, 1, 1, 1, 1)

## Define the LHS coefficients -------------------------------------------------
LHS <- matrix(c(
  0.3, 2.5, 3.5, 1, 1.7, 1.7, 2, 0.7, 1, 0.3,
  010, 000, 000, 000, 000,   000, 000, 000, 000, 000,
  000, 025, 120, 190, 090,   045, 000, 250, 000, 040,
  000, 000, 000, 005, 003,   000, 000, 005, 000, 000,
  000, 060, 000, 000, 150,   000, 000, 000, 000, 000,
  150, 200, 100, 000, 225,   100, 200, 050, 400, 000,
  
  000, 025, 000, 100, 000,   000, 000, 005, 000, 005,
  000, 003, 004, 001, 002,   002, 000, 001, 000, 000,
  100, 125, 000, 000, 000,   020, 000, 012, 000, 075,
  500, 000, 000, 000, 000,   000, 000, 175, 000, 150,
  000, 000, 000, 000, 000,   000, 013, 000, 013, 000,
  
  000, 115, 110, 100, 060,   050, 030, 110, 000, 000,
  000, 005, 000, 000, 010,   000, 000, 010, 000, 005,
  000, 000, 200, 150, 000,   000, 000, 000, 000, 000,
  000, 000, 200, 000, 000,   000, 300, 000, 000, 000,
  000, 000, 000, 000, 000,   000, 000, 245, 300, 000,
  
  1, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 1, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 1, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 1, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 1, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 1, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 1, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 1, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 1, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 1), nrow = 26, byrow = TRUE)

## Inequalities direction ------------------------------------------------------
DIR <- c("<=",
         "<=", "<=", "<=", "<=", "<=", "<=", "<=", "<=", "<=", "<=",
         "<=", "<=", "<=", "<=", "<=",
         ">=", ">=", "=", "=", "=", "=", "=", ">=", "=", "=")

## Define the RHS coefficients when time available is 3.5 hours ----------------
# $40.63
RHS3.5.40.63 <-c(
  3.5,
  10*y1.agar_40.63+z01_40.63, 1000*y2.apfl_40.63+z02_40.63, 
  100*y3.baso_40.63+z03_40.63, 100*y4.brsu_40.63+z04_40.63, 
  500*y5.choc_40.63+z05_40.63, 200*y6.coco_40.63+z06_40.63, 
  30*y7.eggs_40.63+z07_40.63, 2000*y8.grsu_40.63+z08_40.63, 
  1000*y9.milk_40.63+z09_40.63, 13*y10.ore_40.63+z10_40.63,
  250*y11.sbu_40.63+z11_40.63, 115*y12.vae_40.63+z12_40.63, 
  1500*y13.wat_40.63+z13_40.63, 1000*y14.whc_40.63+z14_40.63, 
  1000*y15.yog_40.63+z15_40.63, 
  1, 1, 0, 0, 0, 0, 0, 1, 0, 0)

################################################################################
# RESULTS when the time is 8 hours ## -----------------------------------------
# $30
lp(direction = "max", OBJ, LHS, DIR, RHS3.5.40.63, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS3.5.40.63, all.int = TRUE)$solution
```

### Control group result
```
> # RESULTS when the time is 8 hours ## -----------------------------------------
> # $30
> lp(direction = "max", OBJ, LHS, DIR, RHS3.5.40.63, all.int = TRUE)
Success: the objective function is 3 
> lp(direction = "max", OBJ, LHS, DIR, RHS3.5.40.63, all.int = TRUE)$solution
 [1] 1 1 0 0 0 0 0 1 0 0
 ```

### Code for the time range of 8, 16, 32 and 48 hours when the budget is $30, $60, $100, $300 and $500
```
# THIS IS IMPORTANT TO SO R SOFTWARE CAN SOLVE THE LINEAR PROGRAMMING
library(lpSolve) 



# DEFINING THE Yj/Zj VALUE FIRST WILL ALLOW THE SUBSTITUTION INTO THE INEQUALITIES
## Define yj values for all budgets
y1.agar = 0
y2.apfl = 0
y3.baso = 0
y4.brsu = 0
y5.choc = 0
y6.coco = 0
y7.eggs = 0
y8.grsu = 0
y9.milk = 0
y10.ore = 0
y11.sbu = 0
y12.vae = 0
y13.wat = 0
y14.whc = 0
y15.yog = 0 # VALUES ARE JUST SAMPLE

z01 = 0
z02 = 0
z03 = 0
z04 = 0
z05 = 0
z06 = 0
z07 = 0
z08 = 0
z09 = 0
z10 = 0
z11 = 0
z12 = 0
z13 = 0
z14 = 0
z15 = 0 # VALUES ARE JUST SAMPLE



# ONLY INPUT THE COEFFICIENTS OF THE OBEJCTIVE FUNCTION
## Define the objective function
OBJ <- c(1, 1, 1, 1, 1, 1, 1, 1, 1, 1)




# ONLY INPUT THE COEFFICIENTS OF THE LEFT HAND SIDE INEQUALITIES
## Define the LHS coefficients 
LHS <- matrix(c(
  0.3, 2.5, 3.5, 1, 1.7, 1.7, 2, 0.7, 1, 0.3,
  010, 000, 000, 000, 000,   000, 000, 000, 000, 000,
  000, 025, 120, 190, 090,   045, 000, 250, 000, 040,
  000, 000, 000, 005, 003,   000, 000, 005, 000, 000,
  000, 060, 000, 000, 150,   000, 000, 000, 000, 000,
  150, 200, 100, 000, 225,   100, 200, 050, 400, 000,
  
  000, 025, 000, 100, 000,   000, 000, 005, 000, 005,
  000, 003, 004, 001, 002,   002, 000, 001, 000, 000,
  100, 125, 000, 000, 000,   020, 000, 012, 000, 075,
  500, 000, 000, 000, 000,   000, 000, 175, 000, 150,
  000, 000, 000, 000, 000,   000, 013, 000, 013, 000,
  
  000, 115, 110, 100, 060,   050, 030, 110, 000, 000,
  000, 005, 000, 000, 010,   000, 000, 010, 000, 005,
  000, 000, 200, 150, 000,   000, 000, 000, 000, 000,
  000, 000, 200, 000, 000,   000, 300, 000, 000, 000,
  000, 000, 000, 000, 000,   000, 000, 245, 300, 000,
  
  1, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 1, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 1, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 1, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 1, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 1, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 1, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 1, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 1, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 1), nrow = 26, byrow = TRUE)



# USE ">=" FOR GREATER THAN OR EQUAL TO, 
# "<=" FOR LESS THAN OR EQUAL TO, AND
# "=" FOR EQUAL TO
## Inequalities direction
DIR <- c("<=",
         "<=", "<=", "<=", "<=", "<=", "<=", "<=", "<=", "<=", "<=",
         "<=", "<=", "<=", "<=", "<=",
         ">=", ">=", "=", "=", "=", "=", "=", ">=", "=", "=")

## Define the RHS coefficients when time available is 8 hours ------------------

# $30
RHS8.30 <-c(
  8,
  10*y1.agar_30+z01_30, 1000*y2.apfl_30+z02_30, 100*y3.baso_30+z03_30, 
  100*y4.brsu_30+z04_30, 500*y5.choc_30+z05_30, 200*y6.coco_30+z06_30, 
  30*y7.eggs_30+z07_30, 2000*y8.grsu_30+z08_30, 1000*y9.milk_30+z09_30, 
  13*y10.ore_30+z10_30, 250*y11.sbu_30+z11_30, 115*y12.vae_30+z12_30, 
  1500*y13.wat_30+z13_30, 1000*y14.whc_30+z14_30, 1000*y15.yog_30+z15_30, 
  1, 1, 0, 0, 0, 0, 0, 1, 0, 0)

# 60
RHS8.60 <- c(
  8,
  10*y1.agar_60+z01_60_8, 1000*y2.apfl_60+z02_60_8, 100*y3.baso_60+z03_60_8, 
  100*y4.brsu_60+z04_60_8, 500*y5.choc_60+z05_60_8, 200*y6.coco_60+z06_60_8, 
  30*y7.eggs_60+z07_60_8, 2000*y8.grsu_60+z08_60_8, 1000*y9.milk_60+z09_60_8, 
  13*y10.ore_60+z10_60_8, 250*y11.sbu_60+z11_60_8, 115*y12.vae_60+z12_60_8, 
  1500*y13.wat_60+z13_60_8, 1000*y14.whc_60+z14_60_8, 1000*y15.yog_60+z15_60_8,
  1, 1, 0, 0, 0, 0, 0, 1, 0, 0)

# $100
RHS8.100 <- c(
  8,
  10*y1.agar_100+z01_100_8, 1000*y2.apfl_100+z02_100_8, 
  100*y3.baso_100+z03_100_8, 100*y4.brsu_100+z04_100_8, 
  500*y5.choc_100+z05_100_8, 200*y6.coco_100+z06_100_8, 
  30*y7.eggs_100+z07_100_8, 2000*y8.grsu_100+z08_100_8, 
  1000*y9.milk_100+z09_100_8, 13*y10.ore_100+z10_100_8, 
  250*y11.sbu_100+z11_100_8, 115*y12.vae_100+z12_100_8, 
  1500*y13.wat_100+z13_100_8, 1000*y14.whc_100+z14_100_8, 
  1000*y15.yog_100+z15_100_8,
  1, 1, 0, 0, 0, 0, 0, 1, 0, 0)

# $300
RHS8.300 <- c(
  8,
  10*y1.agar_300+z01_300_8, 1000*y2.apfl_300+z02_300_8, 100*y3.baso_300+z03_300_8, 
  100*y4.brsu_300+z04_300_8, 500*y5.choc_300+z05_300_8, 200*y6.coco_300+z06_300_8, 
  30*y7.eggs_300+z07_300_8, 2000*y8.grsu_300+z08_300_8, 1000*y9.milk_300+z09_300_8, 
  13*y10.ore_300+z10_300_8, 250*y11.sbu_300+z11_300_8, 115*y12.vae_300+z12_300_8, 
  1500*y13.wat_300+z13_300_8, 1000*y14.whc_300+z14_300_8, 1000*y15.yog_300+z15_300_8,
  1, 1, 0, 0, 0, 0, 0, 1, 0, 0)

# $500
RHS8.500 <- c(
  8,
  10*y1.agar_500+z01_500_8, 1000*y2.apfl_500+z02_500_8, 100*y3.baso_500+z03_500_8, 
  100*y4.brsu_500+z04_500_8, 500*y5.choc_500+z05_500_8, 200*y6.coco_500+z06_500_8, 
  30*y7.eggs_500+z07_500_8, 2000*y8.grsu_500+z08_500_8, 1000*y9.milk_500+z09_500_8, 
  13*y10.ore_500+z10_500_8, 250*y11.sbu_500+z11_500_8, 115*y12.vae_500+z12_500_8, 
  1500*y13.wat_500+z13_500_8, 1000*y14.whc_500+z14_500_8, 1000*y15.yog_500+z15_500_8,
  1, 1, 0, 0, 0, 0, 0, 1, 0, 0)

## Define the RHS coefficients when time available is 16 hours -----------------

# $30
RHS16.30 <-c(
  16,
  10*y1.agar_30+z01_30, 1000*y2.apfl_30+z02_30, 100*y3.baso_30+z03_30, 
  100*y4.brsu_30+z04_30, 500*y5.choc_30+z05_30, 200*y6.coco_30+z06_30, 
  30*y7.eggs_30+z07_30, 2000*y8.grsu_30+z08_30, 1000*y9.milk_30+z09_30, 
  13*y10.ore_30+z10_30, 250*y11.sbu_30+z11_30, 115*y12.vae_30+z12_30, 
  1500*y13.wat_30+z13_30, 1000*y14.whc_30+z14_30, 1000*y15.yog_30+z15_30,
  1, 1, 0, 0, 0, 0, 0, 1, 0, 0)

# $60
RHS16.60 <- c(
  16,
  10*y1.agar_60+z01_60_16, 1000*y2.apfl_60+z02_60_16, 
  100*y3.baso_60+z03_60_16, 100*y4.brsu_60+z04_60_16, 
  500*y5.choc_60+z05_60_16, 200*y6.coco_60+z06_60_16, 
  30*y7.eggs_60+z07_60_16, 2000*y8.grsu_60+z08_60_16, 
  1000*y9.milk_60+z09_60_16, 13*y10.ore_60+z10_60_16, 
  250*y11.sbu_60+z11_60_16, 115*y12.vae_60+z12_60_16, 
  1500*y13.wat_60+z13_60_16, 1000*y14.whc_60+z14_60_16, 
  1000*y15.yog_60+z15_60_16,
  1, 1, 0, 0, 0, 0, 0, 1, 0, 0)  

# $100
RHS16.100 <- c(
  16,
  10*y1.agar_100+z01_100_16, 1000*y2.apfl_100+z02_100_16, 
  100*y3.baso_100+z03_100_16, 100*y4.brsu_100+z04_100_16, 
  500*y5.choc_100+z05_100_16, 200*y6.coco_100+z06_100_16, 
  30*y7.eggs_100+z07_100_16, 2000*y8.grsu_100+z08_100_16, 
  1000*y9.milk_100+z09_100_16, 13*y10.ore_100+z10_100_16, 
  250*y11.sbu_100+z11_100_16, 115*y12.vae_100+z12_100_16, 
  1500*y13.wat_100+z13_100_16, 1000*y14.whc_100+z14_100_16, 
  1000*y15.yog_100+z15_100_16,
  1, 1, 0, 0, 0, 0, 0, 1, 0, 0)

# $300
RHS16.300 <- c(
  16,
  10*y1.agar_300+z01_300_16, 1000*y2.apfl_300+z02_300_16, 
  100*y3.baso_300+z03_300_16, 100*y4.brsu_300+z04_300_16, 
  500*y5.choc_300+z05_300_16, 200*y6.coco_300+z06_300_16, 
  30*y7.eggs_300+z07_300_16, 2000*y8.grsu_300+z08_300_16, 
  1000*y9.milk_300+z09_300_16, 13*y10.ore_300+z10_300_16, 
  250*y11.sbu_300+z11_300_16, 115*y12.vae_300+z12_300_16, 
  1500*y13.wat_300+z13_300_16, 1000*y14.whc_300+z14_300_16, 
  1000*y15.yog_300+z15_300_16,
  1, 1, 0, 0, 0, 0, 0, 1, 0, 0)

# $500
RHS16.500 <- c(
  16,
  10*y1.agar_500+z01_500_16, 1000*y2.apfl_500+z02_500_16, 
  100*y3.baso_500+z03_500_16, 100*y4.brsu_500+z04_500_16, 
  500*y5.choc_500+z05_500_16, 200*y6.coco_500+z06_500_16, 
  30*y7.eggs_500+z07_500_16, 2000*y8.grsu_500+z08_500_16, 
  1000*y9.milk_500+z09_500_16, 13*y10.ore_500+z10_500_16, 
  250*y11.sbu_500+z11_500_16, 115*y12.vae_500+z12_500_16, 
  1500*y13.wat_500+z13_500_16, 1000*y14.whc_500+z14_500_16, 
  1000*y15.yog_500+z15_500_16,
  1, 1, 0, 0, 0, 0, 0, 1, 0, 0)

## Define the RHS coefficients when time available is 32 hours -----------------

# $30
RHS32.30 <-c(
  32,
  10*y1.agar_30+z01_30, 1000*y2.apfl_30+z02_30, 100*y3.baso_30+z03_30, 
  100*y4.brsu_30+z04_30, 500*y5.choc_30+z05_30, 200*y6.coco_30+z06_30, 
  30*y7.eggs_30+z07_30, 2000*y8.grsu_30+z08_30, 1000*y9.milk_30+z09_30, 
  13*y10.ore_30+z10_30, 250*y11.sbu_30+z11_30, 115*y12.vae_30+z12_30, 
  1500*y13.wat_30+z13_30, 1000*y14.whc_30+z14_30, 1000*y15.yog_30+z15_30,
  1, 1, 0, 0, 0, 0, 0, 1, 0, 0)

# $60
RHS32.60 <- c(
  32,
  10*y1.agar_60+z01_60_32_48, 1000*y2.apfl_60+z02_60_32_48, 
  100*y3.baso_60+z03_60_32_48, 100*y4.brsu_60+z04_60_32_48, 
  500*y5.choc_60+z05_60_32_48, 200*y6.coco_60+z06_60_32_48, 
  30*y7.eggs_60+z07_60_32_48, 2000*y8.grsu_60+z08_60_32_48, 
  1000*y9.milk_60+z09_60_32_48, 13*y10.ore_60+z10_60_32_48, 
  250*y11.sbu_60+z11_60_32_48, 115*y12.vae_60+z12_60_32_48, 
  1500*y13.wat_60+z13_60_32_48, 1000*y14.whc_60+z14_60_32_48, 
  1000*y15.yog_60+z15_60_32_48,
  1, 1, 0, 0, 0, 0, 0, 1, 0, 0)   

# $100
RHS32.100 <- c(
  32,
  10*y1.agar_100+z01_100_32_48, 1000*y2.apfl_100+z02_100_32_48, 
  100*y3.baso_100+z03_100_32_48, 100*y4.brsu_100+z04_100_32_48, 
  500*y5.choc_100+z05_100_32_48, 200*y6.coco_100+z06_100_32_48, 
  30*y7.eggs_100+z07_100_32_48, 2000*y8.grsu_100+z08_100_32_48, 
  1000*y9.milk_100+z09_100_32_48, 13*y10.ore_100+z10_100_32_48, 
  250*y11.sbu_100+z11_100_32_48, 115*y12.vae_100+z12_100_32_48, 
  1500*y13.wat_100+z13_100_32_48, 1000*y14.whc_100+z14_100_32_48, 
  1000*y15.yog_100+z15_100_32_48,
  1, 1, 0, 0, 0, 0, 0, 1, 0, 0)

# $300
RHS32.300 <- c(
  32,
  10*y1.agar_300+z01_300_32, 1000*y2.apfl_300+z02_300_32, 
  100*y3.baso_300+z03_300_32, 100*y4.brsu_300+z04_300_32, 
  500*y5.choc_300+z05_300_32, 200*y6.coco_300+z06_300_32, 
  30*y7.eggs_300+z07_300_32, 2000*y8.grsu_300+z08_300_32, 
  1000*y9.milk_300+z09_300_32, 13*y10.ore_300+z10_300_32, 
  250*y11.sbu_300+z11_300_32, 115*y12.vae_300+z12_300_32, 
  1500*y13.wat_300+z13_300_32, 1000*y14.whc_300+z14_300_32, 
  1000*y15.yog_300+z15_300_32,
  1, 1, 0, 0, 0, 0, 0, 1, 0, 0)

# $500
RHS32.500 <- c(
  32,
  10*y1.agar_500+z01_500_32, 1000*y2.apfl_500+z02_500_32, 
  100*y3.baso_500+z03_500_32, 100*y4.brsu_500+z04_500_32, 
  500*y5.choc_500+z05_500_32, 200*y6.coco_500+z06_500_32, 
  30*y7.eggs_500+z07_500_32, 2000*y8.grsu_500+z08_500_32, 
  1000*y9.milk_500+z09_500_32, 13*y10.ore_500+z10_500_32, 
  250*y11.sbu_500+z11_500_32, 115*y12.vae_500+z12_500_32, 
  1500*y13.wat_500+z13_500_32, 1000*y14.whc_500+z14_500_32, 
  1000*y15.yog_500+z15_500_32,
  1, 1, 0, 0, 0, 0, 0, 1, 0, 0)

## Define the RHS coefficients when time available is 48 hours -----------------

# $30
RHS48.30 <-c(
  48,
  10*y1.agar_30+z01_30, 1000*y2.apfl_30+z02_30, 100*y3.baso_30+z03_30, 
  100*y4.brsu_30+z04_30, 500*y5.choc_30+z05_30, 200*y6.coco_30+z06_30, 
  30*y7.eggs_30+z07_30, 2000*y8.grsu_30+z08_30, 1000*y9.milk_30+z09_30, 
  13*y10.ore_30+z10_30, 250*y11.sbu_30+z11_30, 115*y12.vae_30+z12_30, 
  1500*y13.wat_30+z13_30, 1000*y14.whc_30+z14_30, 1000*y15.yog_30+z15_30,
  1, 1, 0, 0, 0, 0, 0, 1, 0, 0)

# $60
RHS48.60 <- c(
  48,
  10*y1.agar_60+z01_60_32_48, 1000*y2.apfl_60+z02_60_32_48, 
  100*y3.baso_60+z03_60_32_48, 100*y4.brsu_60+z04_60_32_48, 
  500*y5.choc_60+z05_60_32_48, 200*y6.coco_60+z06_60_32_48, 
  30*y7.eggs_60+z07_60_32_48, 2000*y8.grsu_60+z08_60_32_48, 
  1000*y9.milk_60+z09_60_32_48, 13*y10.ore_60+z10_60_32_48, 
  250*y11.sbu_60+z11_60_32_48, 115*y12.vae_60+z12_60_32_48, 
  1500*y13.wat_60+z13_60_32_48, 1000*y14.whc_60+z14_60_32_48, 
  1000*y15.yog_60+z15_60_32_48,
  1, 1, 0, 0, 0, 0, 0, 1, 0, 0)  

# $100
RHS48.100 <- c(
  48,
  10*y1.agar_100+z01_100_32_48, 1000*y2.apfl_100+z02_100_32_48, 
  100*y3.baso_100+z03_100_32_48, 100*y4.brsu_100+z04_100_32_48, 
  500*y5.choc_100+z05_100_32_48, 200*y6.coco_100+z06_100_32_48, 
  30*y7.eggs_100+z07_100_32_48, 2000*y8.grsu_100+z08_100_32_48, 
  1000*y9.milk_100+z09_100_32_48, 13*y10.ore_100+z10_100_32_48, 
  250*y11.sbu_100+z11_100_32_48, 115*y12.vae_100+z12_100_32_48, 
  1500*y13.wat_100+z13_100_32_48, 1000*y14.whc_100+z14_100_32_48, 
  1000*y15.yog_100+z15_100_32_48,
  1, 1, 0, 0, 0, 0, 0, 1, 0, 0)

# $300
RHS48.300 <- c(
  48,
  10*y1.agar_300+z01_300_48, 1000*y2.apfl_300+z02_300_48, 
  100*y3.baso_300+z03_300_48, 100*y4.brsu_300+z04_300_48, 
  500*y5.choc_300+z05_300_48, 200*y6.coco_300+z06_300_48, 
  30*y7.eggs_300+z07_300_48, 2000*y8.grsu_300+z08_300_48, 
  1000*y9.milk_300+z09_300_48, 13*y10.ore_300+z10_300_48, 
  250*y11.sbu_300+z11_300_48, 115*y12.vae_300+z12_300_48, 
  1500*y13.wat_300+z13_300_48, 1000*y14.whc_300+z14_300_48, 
  1000*y15.yog_300+z15_300_48,
  1, 1, 0, 0, 0, 0, 0, 1, 0, 0)

# $500
RHS48.500 <- c(
  48,
  10*y1.agar_500+z01_500_48, 1000*y2.apfl_500+z02_500_48, 
  100*y3.baso_500+z03_500_48, 100*y4.brsu_500+z04_500_48, 
  500*y5.choc_500+z05_500_48, 200*y6.coco_500+z06_500_48, 
  30*y7.eggs_500+z07_500_48, 2000*y8.grsu_500+z08_500_48, 
  1000*y9.milk_500+z09_500_48, 13*y10.ore_500+z10_500_48, 
  250*y11.sbu_500+z11_500_48, 115*y12.vae_500+z12_500_48, 
  1500*y13.wat_500+z13_500_48, 1000*y14.whc_500+z14_500_48, 
  1000*y15.yog_500+z15_500_48,
  1, 1, 0, 0, 0, 0, 0, 1, 0, 0)

################################################################################
# RESULTS when the time is 8 hours ## -----------------------------------------
# $30
lp(direction = "max", OBJ, LHS, DIR, RHS8.30, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS8.30, all.int = TRUE)$solution

# $60
lp(direction = "max", OBJ, LHS, DIR, RHS8.60, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS8.60, all.int = TRUE)$solution

# $100
lp(direction = "max", OBJ, LHS, DIR, RHS8.100, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS8.100, all.int = TRUE)$solution

# $300
lp(direction = "max", OBJ, LHS, DIR, RHS8.300, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS8.300, all.int = TRUE)$solution

# $500
lp(direction = "max", OBJ, LHS, DIR, RHS8.500, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS8.500, all.int = TRUE)$solution



## RESULTS when the time is 16 hours ## ----------------------------------------
# $30
lp(direction = "max", OBJ, LHS, DIR, RHS16.30, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS16.30, all.int = TRUE)$solution

# $60
lp(direction = "max", OBJ, LHS, DIR, RHS16.60, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS16.60, all.int = TRUE)$solution

# $100
lp(direction = "max", OBJ, LHS, DIR, RHS16.100, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS16.100, all.int = TRUE)$solution

# $300
lp(direction = "max", OBJ, LHS, DIR, RHS16.300, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS16.300, all.int = TRUE)$solution

# $500
lp(direction = "max", OBJ, LHS, DIR, RHS16.500, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS16.500, all.int = TRUE)$solution



## RESULTS when the time is 32 hours ## ----------------------------------------
# $30
lp(direction = "max", OBJ, LHS, DIR, RHS32.30, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS32.30, all.int = TRUE)$solution

# $60
lp(direction = "max", OBJ, LHS, DIR, RHS32.60, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS32.60, all.int = TRUE)$solution

# $100
lp(direction = "max", OBJ, LHS, DIR, RHS32.100, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS32.100, all.int = TRUE)$solution

# $300
lp(direction = "max", OBJ, LHS, DIR, RHS32.300, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS32.300, all.int = TRUE)$solution

# $500
lp(direction = "max", OBJ, LHS, DIR, RHS32.500, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS32.500, all.int = TRUE)$solution



## RESULTS when the time is 48 hours ## ----------------------------------------
# $30
lp(direction = "max", OBJ, LHS, DIR, RHS48.30, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS48.30, all.int = TRUE)$solution

# $60
lp(direction = "max", OBJ, LHS, DIR, RHS48.60, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS48.60, all.int = TRUE)$solution

# $100
lp(direction = "max", OBJ, LHS, DIR, RHS48.100, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS48.100, all.int = TRUE)$solution

# $300
lp(direction = "max", OBJ, LHS, DIR, RHS48.300, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS48.300, all.int = TRUE)$solution

# $500
lp(direction = "max", OBJ, LHS, DIR, RHS48.500, all.int = TRUE)
lp(direction = "max", OBJ, LHS, DIR, RHS48.500, all.int = TRUE)$solution
```

### Results obtained
```
> # RESULTS when the time is 8 hours ## -----------------------------------------
> # $30
> lp(direction = "max", OBJ, LHS, DIR, RHS8.30, all.int = TRUE)
Error: no feasible solution found> lp(direction = "max", OBJ, LHS, DIR, RHS8.30, all.int = TRUE)$solution
 [1] 0 0 0 0 0 0 0 0 0 0
> 
> # $60
> lp(direction = "max", OBJ, LHS, DIR, RHS8.60, all.int = TRUE)
Error: no feasible solution found> lp(direction = "max", OBJ, LHS, DIR, RHS8.60, all.int = TRUE)$solution
 [1] 0 0 0 0 0 0 0 0 0 0
> 
> # $100
> lp(direction = "max", OBJ, LHS, DIR, RHS8.100, all.int = TRUE)
Success: the objective function is 6 
> lp(direction = "max", OBJ, LHS, DIR, RHS8.100, all.int = TRUE)$solution
 [1] 1 2 0 0 0 0 0 3 0 0
> 
> # $300
> lp(direction = "max", OBJ, LHS, DIR, RHS8.300, all.int = TRUE)
Success: the objective function is 12 
> lp(direction = "max", OBJ, LHS, DIR, RHS8.300, all.int = TRUE)$solution
 [1] 6 1 0 0 0 0 0 5 0 0
> 
> # $500
> lp(direction = "max", OBJ, LHS, DIR, RHS8.500, all.int = TRUE)
Success: the objective function is 15 
> lp(direction = "max", OBJ, LHS, DIR, RHS8.500, all.int = TRUE)$solution
 [1] 11  1  0  0  0  0  0  3  0  0
> 
> 
> 
> ## RESULTS when the time is 16 hours ## ----------------------------------------
> # $30
> lp(direction = "max", OBJ, LHS, DIR, RHS16.30, all.int = TRUE)
Error: no feasible solution found> lp(direction = "max", OBJ, LHS, DIR, RHS16.30, all.int = TRUE)$solution
 [1] 0 0 0 0 0 0 0 0 0 0
> 
> # $60
> lp(direction = "max", OBJ, LHS, DIR, RHS16.60, all.int = TRUE)
Success: the objective function is 8 
> lp(direction = "max", OBJ, LHS, DIR, RHS16.60, all.int = TRUE)$solution
 [1] 1 6 0 0 0 0 0 1 0 0
> 
> # $100
> lp(direction = "max", OBJ, LHS, DIR, RHS16.100, all.int = TRUE)
Success: the objective function is 8 
> lp(direction = "max", OBJ, LHS, DIR, RHS16.100, all.int = TRUE)$solution
 [1] 1 4 0 0 0 0 0 3 0 0
> 
> # $300
> lp(direction = "max", OBJ, LHS, DIR, RHS16.300, all.int = TRUE)
Success: the objective function is 20 
> lp(direction = "max", OBJ, LHS, DIR, RHS16.300, all.int = TRUE)$solution
 [1]  2  1  0  0  0  0  0 17  0  0
> 
> # $500
> lp(direction = "max", OBJ, LHS, DIR, RHS16.500, all.int = TRUE)
Success: the objective function is 23 
> lp(direction = "max", OBJ, LHS, DIR, RHS16.500, all.int = TRUE)$solution
 [1]  5  1  0  0  0  0  0 17  0  0
> 
> 
> 
> ## RESULTS when the time is 32 hours ## ----------------------------------------
> # $30
> lp(direction = "max", OBJ, LHS, DIR, RHS32.30, all.int = TRUE)
Error: no feasible solution found> lp(direction = "max", OBJ, LHS, DIR, RHS32.30, all.int = TRUE)$solution
 [1] 0 0 0 0 0 0 0 0 0 0
> 
> # $60
> lp(direction = "max", OBJ, LHS, DIR, RHS32.60, all.int = TRUE)
Error: no feasible solution found> lp(direction = "max", OBJ, LHS, DIR, RHS32.60, all.int = TRUE)$solution
 [1] 0 0 0 0 0 0 0 0 0 0
> 
> # $100
> lp(direction = "max", OBJ, LHS, DIR, RHS32.100, all.int = TRUE)
Success: the objective function is 8 
> lp(direction = "max", OBJ, LHS, DIR, RHS32.100, all.int = TRUE)$solution
 [1] 1 4 0 0 0 0 0 3 0 0
> 
> # $300
> lp(direction = "max", OBJ, LHS, DIR, RHS32.300, all.int = TRUE)
Success: the objective function is 28 
> lp(direction = "max", OBJ, LHS, DIR, RHS32.300, all.int = TRUE)$solution
 [1]  1  7  0  0  0  0  0 20  0  0
> 
> # $500
> lp(direction = "max", OBJ, LHS, DIR, RHS32.500, all.int = TRUE)
Success: the objective function is 36 
> lp(direction = "max", OBJ, LHS, DIR, RHS32.500, all.int = TRUE)$solution
 [1]  1  4  0  0  0  0  0 31  0  0
> 
> 
> 
> ## RESULTS when the time is 48 hours ## ----------------------------------------
> # $30
> lp(direction = "max", OBJ, LHS, DIR, RHS48.30, all.int = TRUE)
Error: no feasible solution found> lp(direction = "max", OBJ, LHS, DIR, RHS48.30, all.int = TRUE)$solution
 [1] 0 0 0 0 0 0 0 0 0 0
> 
> # $60
> lp(direction = "max", OBJ, LHS, DIR, RHS48.60, all.int = TRUE)
Error: no feasible solution found> lp(direction = "max", OBJ, LHS, DIR, RHS48.60, all.int = TRUE)$solution
 [1] 0 0 0 0 0 0 0 0 0 0
> 
> # $100
> lp(direction = "max", OBJ, LHS, DIR, RHS48.100, all.int = TRUE)
Success: the objective function is 8 
> lp(direction = "max", OBJ, LHS, DIR, RHS48.100, all.int = TRUE)$solution
 [1] 1 4 0 0 0 0 0 3 0 0
> 
> # $300
> lp(direction = "max", OBJ, LHS, DIR, RHS48.300, all.int = TRUE)
Success: the objective function is 31 
> lp(direction = "max", OBJ, LHS, DIR, RHS48.300, all.int = TRUE)$solution
 [1]  4 15  0  0  0  0  0 12  0  0
> 
> # $500
> lp(direction = "max", OBJ, LHS, DIR, RHS48.500, all.int = TRUE)
Success: the objective function is 43 
> lp(direction = "max", OBJ, LHS, DIR, RHS48.500, all.int = TRUE)$solution
 [1]  1 10  0  0  0  0  0 32  0  0
```
