Lab 4 Report
================
Haider Ali
‘r format(sys.Date())’

``` r
# load packages -----------------------------------------------------------
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.0 ──

    ## ✓ ggplot2 3.3.3     ✓ purrr   0.3.4
    ## ✓ tibble  3.0.6     ✓ dplyr   1.0.4
    ## ✓ tidyr   1.1.2     ✓ stringr 1.4.0
    ## ✓ readr   1.4.0     ✓ forcats 0.5.1

    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

``` r
library(auk)
```

    ## auk 0.4.2 is designed for EBD files downloaded after 2019-08-15. 
    ## No EBD data directory set, see ?auk_set_ebd_path to set EBD_PATH 
    ## eBird taxonomy version:  2019

``` r
# birds -------------------------------------------------------------------

birds <-                              # create a new table named birds
  ebird_taxonomy %>%                  # start with the ebird_taxonomy data
  as_tibble() %>%                     # tibbles print better in the console
  filter(category == "species")       # remove non-species taxa
birds
```

    ## # A tibble: 10,721 x 9
    ##    species_code scientific_name common_name order family family_common category
    ##    <chr>        <chr>           <chr>       <chr> <chr>  <chr>         <chr>   
    ##  1 ostric2      Struthio camel… Common Ost… Stru… Strut… Ostriches     species 
    ##  2 ostric3      Struthio molyb… Somali Ost… Stru… Strut… Ostriches     species 
    ##  3 grerhe1      Rhea americana  Greater Rh… Rhei… Rheid… Rheas         species 
    ##  4 lesrhe2      Rhea pennata    Lesser Rhea Rhei… Rheid… Rheas         species 
    ##  5 tabtin1      Nothocercus ju… Tawny-brea… Tina… Tinam… Tinamous      species 
    ##  6 higtin1      Nothocercus bo… Highland T… Tina… Tinam… Tinamous      species 
    ##  7 hootin1      Nothocercus ni… Hooded Tin… Tina… Tinam… Tinamous      species 
    ##  8 grytin1      Tinamus tao     Gray Tinam… Tina… Tinam… Tinamous      species 
    ##  9 soltin1      Tinamus solita… Solitary T… Tina… Tinam… Tinamous      species 
    ## 10 blatin1      Tinamus osgoodi Black Tina… Tina… Tinam… Tinamous      species 
    ## # … with 10,711 more rows, and 2 more variables: taxon_order <dbl>,
    ## #   report_as <chr>

# 1.Print a table containing only species NOT in the Order Passeriformes. Include all columns.

``` r
filter(birds, !(order == "Passeriformes")) 
```

    ## # A tibble: 4,335 x 9
    ##    species_code scientific_name common_name order family family_common category
    ##    <chr>        <chr>           <chr>       <chr> <chr>  <chr>         <chr>   
    ##  1 ostric2      Struthio camel… Common Ost… Stru… Strut… Ostriches     species 
    ##  2 ostric3      Struthio molyb… Somali Ost… Stru… Strut… Ostriches     species 
    ##  3 grerhe1      Rhea americana  Greater Rh… Rhei… Rheid… Rheas         species 
    ##  4 lesrhe2      Rhea pennata    Lesser Rhea Rhei… Rheid… Rheas         species 
    ##  5 tabtin1      Nothocercus ju… Tawny-brea… Tina… Tinam… Tinamous      species 
    ##  6 higtin1      Nothocercus bo… Highland T… Tina… Tinam… Tinamous      species 
    ##  7 hootin1      Nothocercus ni… Hooded Tin… Tina… Tinam… Tinamous      species 
    ##  8 grytin1      Tinamus tao     Gray Tinam… Tina… Tinam… Tinamous      species 
    ##  9 soltin1      Tinamus solita… Solitary T… Tina… Tinam… Tinamous      species 
    ## 10 blatin1      Tinamus osgoodi Black Tina… Tina… Tinam… Tinamous      species 
    ## # … with 4,325 more rows, and 2 more variables: taxon_order <dbl>,
    ## #   report_as <chr>

# 2.Print a table containing only species in the Order Passeriformes. Include all columns.

``` r
filter(birds, (order == "Passeriformes")) 
```

    ## # A tibble: 6,386 x 9
    ##    species_code scientific_name common_name order family family_common category
    ##    <chr>        <chr>           <chr>       <chr> <chr>  <chr>         <chr>   
    ##  1 stiwre1      Traversia lyal… Stephens I… Pass… Acant… New Zealand … species 
    ##  2 riflem1      Acanthisitta c… Rifleman    Pass… Acant… New Zealand … species 
    ##  3 buswre1      Xenicus longip… Bush Wren   Pass… Acant… New Zealand … species 
    ##  4 soiwre1      Xenicus gilviv… South Isla… Pass… Acant… New Zealand … species 
    ##  5 afrbro1      Smithornis cap… African Br… Pass… Calyp… African and … species 
    ##  6 gyhbro1      Smithornis sha… Gray-heade… Pass… Calyp… African and … species 
    ##  7 rusbro1      Smithornis ruf… Rufous-sid… Pass… Calyp… African and … species 
    ##  8 grebro1      Calyptomena vi… Green Broa… Pass… Calyp… African and … species 
    ##  9 hosbro1      Calyptomena ho… Hose's Bro… Pass… Calyp… African and … species 
    ## 10 whibro1      Calyptomena wh… Whitehead'… Pass… Calyp… African and … species 
    ## # … with 6,376 more rows, and 2 more variables: taxon_order <dbl>,
    ## #   report_as <chr>

# 3.Print a table containing all species. Only the variables Species Code, Scientific Name, and Common Name should be in the final table.

``` r
select(birds,species_code , scientific_name, common_name) 
```

    ## # A tibble: 10,721 x 3
    ##    species_code scientific_name           common_name           
    ##    <chr>        <chr>                     <chr>                 
    ##  1 ostric2      Struthio camelus          Common Ostrich        
    ##  2 ostric3      Struthio molybdophanes    Somali Ostrich        
    ##  3 grerhe1      Rhea americana            Greater Rhea          
    ##  4 lesrhe2      Rhea pennata              Lesser Rhea           
    ##  5 tabtin1      Nothocercus julius        Tawny-breasted Tinamou
    ##  6 higtin1      Nothocercus bonapartei    Highland Tinamou      
    ##  7 hootin1      Nothocercus nigrocapillus Hooded Tinamou        
    ##  8 grytin1      Tinamus tao               Gray Tinamou          
    ##  9 soltin1      Tinamus solitarius        Solitary Tinamou      
    ## 10 blatin1      Tinamus osgoodi           Black Tinamou         
    ## # … with 10,711 more rows

# 4.Print a table with all species in the Order Passeriformes whose common name starts with the word “Common”. Species should be in reverse taxonomic order (taxon\_order variable). Only the variables Species Code, Scientific Name, and Common Name should be in the final table.

``` r
big_birds <- filter(birds, (order == "Passeriformes")) 
hello <- filter(big_birds, str_detect(common_name, "Common"))
reverse <- arrange(hello,desc(taxon_order))
select(reverse,species_code:common_name)
```

    ## # A tibble: 32 x 3
    ##    species_code scientific_name           common_name         
    ##    <chr>        <chr>                     <chr>               
    ##  1 cocfin3      Geospiza scandens         Common Cactus-Finch 
    ##  2 codfin1      Diuca diuca               Common Diuca-Finch  
    ##  3 comyel       Geothlypis trichas        Common Yellowthroat 
    ##  4 comgra       Quiscalus quiscula        Common Grackle      
    ##  5 cobtan1      Chlorospingus flavopectus Common Chlorospingus
    ##  6 comred       Acanthis flammea          Common Redpoll      
    ##  7 comros       Carpodacus erythrinus     Common Rosefinch    
    ##  8 comcha       Fringilla coelebs         Common Chaffinch    
    ##  9 comwax       Estrilda astrild          Common Waxbill      
    ## 10 comred2      Phoenicurus phoenicurus   Common Redstart     
    ## # … with 22 more rows

# 5.Print a table containing species with “Warbler” in the common name. Include all columns.

``` r
warbler <- filter(birds, str_detect(common_name, "Warbler"))
warbler
```

    ## # A tibble: 334 x 9
    ##    species_code scientific_name common_name order family family_common category
    ##    <chr>        <chr>           <chr>       <chr> <chr>  <chr>         <chr>   
    ##  1 rumwar1      Crateroscelis … Rusty Mous… Pass… Acant… Thornbills a… species 
    ##  2 bimwar1      Crateroscelis … Bicolored … Pass… Acant… Thornbills a… species 
    ##  3 momwar1      Crateroscelis … Mountain M… Pass… Acant… Thornbills a… species 
    ##  4 spewar3      Pyrrholaemus s… Speckled W… Pass… Acant… Thornbills a… species 
    ##  5 mogwar1      Melocichla men… Moustached… Pass… Macro… African Warb… species 
    ##  6 viswar1      Cryptillas vic… Victorin's… Pass… Macro… African Warb… species 
    ##  7 grawar1      Graueria vitta… Grauer's W… Pass… Macro… African Warb… species 
    ##  8 mitbab1      Micromacronus … Leyte Plum… Pass… Cisti… Cisticolas a… species 
    ##  9 minmib1      Micromacronus … Mindanao P… Pass… Cisti… Cisticolas a… species 
    ## 10 rwgwar2      Drymocichla in… Red-winged… Pass… Cisti… Cisticolas a… species 
    ## # … with 324 more rows, and 2 more variables: taxon_order <dbl>,
    ## #   report_as <chr>

# 6.Using the species found in the previous step (with “Warbler” in their name), print a frequency table for the family variable. You should end up with a table with two columns: family and n.

``` r
count(warbler, family)
```

    ## # A tibble: 15 x 2
    ##    family                                                    n
    ##  * <chr>                                                 <int>
    ##  1 Acanthizidae (Thornbills and Allies)                      4
    ##  2 Acrocephalidae (Reed Warblers and Allies)                60
    ##  3 Aegithalidae (Long-tailed Tits)                           2
    ##  4 Bernieridae (Malagasy Warblers)                           2
    ##  5 Cisticolidae (Cisticolas and Allies)                     19
    ##  6 Locustellidae (Grassbirds and Allies)                    38
    ##  7 Macrosphenidae (African Warblers)                         3
    ##  8 Parulidae (New World Warblers)                           83
    ##  9 Peucedramidae (Olive Warbler)                             1
    ## 10 Phaenicophilidae (Hispaniolan Tanagers)                   2
    ## 11 Phylloscopidae (Leaf Warblers)                           73
    ## 12 Scotocercidae (Bush Warblers and Allies)                 22
    ## 13 Sylviidae (Sylviid Warblers, Parrotbills, and Allies)    21
    ## 14 Teretistridae (Cuban Warblers)                            2
    ## 15 Thraupidae (Tanagers and Allies)                          2

# 7.print a table with all species whose common name contains a color.

``` r
filter(birds, str_detect(common_name, "White|Black|Pink|Yellow|Blue|Green|Red|Orange|Brown|Golden"))
```

    ## # A tibble: 2,722 x 9
    ##    species_code scientific_name common_name order family family_common category
    ##    <chr>        <chr>           <chr>       <chr> <chr>  <chr>         <chr>   
    ##  1 blatin1      Tinamus osgoodi Black Tina… Tina… Tinam… Tinamous      species 
    ##  2 whttin1      Tinamus guttat… White-thro… Tina… Tinam… Tinamous      species 
    ##  3 brotin1      Crypturellus o… Brown Tina… Tina… Tinam… Tinamous      species 
    ##  4 reltin1      Crypturellus e… Red-legged… Tina… Tinam… Tinamous      species 
    ##  5 yeltin1      Crypturellus n… Yellow-leg… Tina… Tinam… Tinamous      species 
    ##  6 blctin1      Crypturellus a… Black-capp… Tina… Tinam… Tinamous      species 
    ##  7 rewtin1      Rhynchotus ruf… Red-winged… Tina… Tinam… Tinamous      species 
    ##  8 whbnot1      Nothura boraqu… White-bell… Tina… Tinam… Tinamous      species 
    ##  9 sobkiw1      Apteryx austra… Southern B… Apte… Apter… Kiwis         species 
    ## 10 okbkiw1      Apteryx rowi    Okarito Br… Apte… Apter… Kiwis         species 
    ## # … with 2,712 more rows, and 2 more variables: taxon_order <dbl>,
    ## #   report_as <chr>

sessioninfo::session\_info()
