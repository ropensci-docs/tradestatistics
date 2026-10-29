# String matching of official commodity/section names and Harmonized System (HS) codes according to the United Nations nomenclature

Takes a text string and searches within the package data for all
matching commodity codes in the context of valid API commodity codes.

## Usage

``` r
ots_commodity_code(commodity = NULL, section = NULL)
```

## Arguments

- commodity:

  A text string such as "Animals", "COPPER" or "fruits".

- section:

  A text string such as "meat", "FISH" or "Dairy".

## Value

A tibble with all possible matches (no uppercase distinction) showing
the commodity name and commodity code

## Examples

``` r
ots_commodity_code(commodity = "ANIMALS ")
#>     commodity_code
#>             <char>
#>  1:         010121
#>  2:         010129
#>  3:         010221
#>  4:         010229
#>  5:         010231
#>  6:         010239
#>  7:         010290
#>  8:         010310
#>  9:         010391
#> 10:         010392
#> 11:         010690
#> 12:         020110
#> 13:         020120
#> 14:         020130
#> 15:         020210
#> 16:         020220
#> 17:         020230
#> 18:         020610
#> 19:         020621
#> 20:         020622
#> 21:         020629
#> 22:         021020
#> 23:         050400
#> 24:         051191
#> 25:         150290
#> 26:         160250
#> 27:         410120
#> 28:         410150
#> 29:         410190
#> 30:         410229
#> 31:         410390
#> 32:         410691
#> 33:         410692
#> 34:         410711
#> 35:         410712
#> 36:         410719
#> 37:         410791
#> 38:         410792
#> 39:         410799
#> 40:         411390
#> 41:         430180
#> 42:             01
#>     commodity_code
#>             <char>
#>                                                                                                                                                                                                                                       commodity_fullname_english
#>                                                                                                                                                                                                                                                           <char>
#>  1:                                                                                                                                                                                                                     Horses; live, pure-bred breeding animals
#>  2:                                                                                                                                                                                                          Horses; live, other than pure-bred breeding animals
#>  3:                                                                                                                                                                                                                     Cattle; live, pure-bred breeding animals
#>  4:                                                                                                                                                                                                          Cattle; live, other than pure-bred breeding animals
#>  5:                                                                                                                                                                                                                    Buffalo; live, pure-bred breeding animals
#>  6:                                                                                                                                                                                                         Buffalo; live, other than pure-bred breeding animals
#>  7:                                                                                                                                                                                                          Bovine animals; live, other than cattle and buffalo
#>  8:                                                                                                                                                                                                                      Swine; live, pure-bred breeding animals
#>  9:                                                                                                                                                                                  Swine; live, other than pure-bred breeding animals, weighing less than 50kg
#> 10:                                                                                                                                                                                    Swine; live, other than pure-bred breeding animals, weighing 50kg or more
#> 11:                                                                                                                                                                         Animals; live, n.e.c. in chapter 01, other than mammals, reptiles, birds and insects
#> 12:                                                                                                                                                                                      Meat; of bovine animals, carcasses and half-carcasses, fresh or chilled
#> 13:                                                                                                                                                        Meat; of bovine animals, cuts with bone in (excluding carcasses and half-carcasses), fresh or chilled
#> 14:                                                                                                                                                                                                     Meat; of bovine animals, boneless cuts, fresh or chilled
#> 15:                                                                                                                                                                                                Meat; of bovine animals, carcasses and half-carcasses, frozen
#> 16:                                                                                                                                                                  Meat; of bovine animals, cuts with bone in (excluding carcasses and half-carcasses), frozen
#> 17:                                                                                                                                                                                                               Meat; of bovine animals, boneless cuts, frozen
#> 18:                                                                                                                                                                                                           Offal, edible; of bovine animals, fresh or chilled
#> 19:                                                                                                                                                                                                            Offal, edible; of bovine animals, tongues, frozen
#> 20:                                                                                                                                                                                                             Offal, edible; of bovine animals, livers, frozen
#> 21:                                                                                                                                                                                    Offal, edible; of bovine animals, (other than tongues and livers), frozen
#> 22:                                                                                                                                                                                                   Meat; salted, in brine, dried or smoked, of bovine animals
#> 23:                                                                                               Animal products; guts, bladders and stomachs of animals (other than fish), whole and pieces thereof, fresh, chilled, frozen, salted, in brine, dried or smoked
#> 24:                                                                                                                    Animal products; of fish or crustaceans, molluscs or other aquatic invertebrates; dead animals of chapter 03, unfit for human consumption
#> 25:                                                                                                                                                               Fats of bovine animals, sheep or goats; excluding tallow, and other than those of heading 1503
#> 26:                                                                                                                              Meat preparations; of bovine animals, meat or meat offal, prepared or preserved (excluding livers and homogenised preparations)
#> 27:                                                       Raw hides and skins; whole, unsplit, of bovine or equine animals, of a weight per skin not exceeding 8kg when simply dried, 10kg when dry-salted or 16kg when fresh, wet-salted or otherwise preserved
#> 28:                                                                                                                                                               Hides and skins; raw, whole, of bovine or equine animals, of a weight per skin exceeding 16 kg
#> 29:            Hides and skins; other than whole, but including butts, bends and bellies, of bovine (including. buffalo) and equine animals, fresh, salted or preserved, but not tanned, parchment dressed or further prepared, whether or not dehaired or split
#> 30:                                              Hides and skins; raw, of animals n.e.c. in this chapter, fresh, salted, dried, limed, pickled or otherwise preserved, (but not tanned, parchment-dressed or further prepared), whether or not dehaired or split
#> 31:                                              Hides and skins; raw, of animals n.e.c. in this chapter, fresh, salted, dried, limed, pickled or otherwise preserved, (but not tanned, parchment-dressed or further prepared), whether or not dehaired or split
#> 32:                              Tanned or crust hides and skins; of animals other than equine, ovine, bovine, goats or kids, swine and reptiles, without wool or hair on, whether or not split, but not further prepared, in the wet state (including wet blue)
#> 33:                                           Tanned or crust hides and skins; of animals other than equine, ovine, bovine, goats or kids, swine and reptiles, without wool or hair on, whether or not split, but not further prepared, in the dry state (crust)
#> 34:                  Leather; further prepared after tanning or crusting, including parchment-dressed leather, of bovine (including buffalo) or equine animals, without hair on, other than leather of heading 41.14, whole hides and skins, full grain, unsplit
#> 35:                         Leather; further prepared after tanning or crusting, including parchment-dressed leather, of bovine (including buffalo) or equine animals, without hair on, other than leather of heading 41.14, whole hides and skins, grain splits
#> 36:    Leather; further prepared after tanning or crusting, including parchment-dressed, of bovine (including buffalo) or equine animals, without hair on, split or not, other than leather of heading 41.14, (other than grain splits and full grains, unsplit)
#> 37: Leather; further prepared after tanning or crusting, including parchment-dressed, of bovine (including buffalo) or equine animals, without hair on, other than leather of heading 41.14, not whole hides and skins, but including sides, full grain, unsplit
#> 38:        Leather; further prepared after tanning or crusting, including parchment-dressed, of bovine (including buffalo) or equine animals, without hair on, other than leather of heading 41.14, not whole hides and skins, but including sides, grain splits
#> 39:    Leather; further prepared after tanning or crusting, incl. parchment-dressed, of bovine (including buffalo) or equine animals, no hair, excluding leather of heading 41.14, and whole hides and skins, and sides, (full grains, unsplit and grain splits)
#> 40:    Leather; further prepared after tanning or crusting, including parchment-dressed leather, of animals (other than sheep and lambs, goats and kids, swine and reptiles), without wool or hair on, whether or not split, other than leather of heading 41.14
#> 41:                                                                                                         Furskins; raw, of animals n.e.c. in heading no. 4301, whole, with or without head, tail or paws (excluding goods of heading no. 4101, 4102 and 4103)
#> 42:                                                                                                                                                                                                               Alias for all codes in the group Animals; live
#>                                                                                                                                                                                                                                       commodity_fullname_english
#>                                                                                                                                                                                                                                                           <char>
ots_commodity_code(section = "  fish")
#> Empty data.table (0 rows and 2 cols): section_code,section_fullname_english
ots_commodity_code(commodity = "Milk", section = "Dairy")
#> Empty data.table (0 rows and 5 cols): section_code,commodity_code,commodity_code_short,commodity_fullname_english,section_fullname_english
```
