Homologation
============

This explain how to pass through Enedis homologation process.

This is based on SGE v22.1 (from `Enedis.SGE.REF.0465.Homologation_Catalogue
des cas de tests_Tiers_SGE22.1_v1.0.pdf`) cases.

First setup `lowatt-enedis` and then execute given commands for each services
you want homologation and report the time the command was run to fill Enedis
excel file.


Setup
-----

Set these environment variables to setup `lowatt-enedis`:

```
$ export ENEDIS_KEY_FILE=/path/to/key.pem
$ export ENEDIS_CERT_FILE=/path/to/cert.pem
$ export ENEDIS_LOGIN=XXX
$ export ENEDIS_CONTRAT=XXX
$ export ENEDIS_HOMOLOGATION=on
```


ConsultationDonneesTechniquesContractuelles v0
----------------------------------------------

| Case           | Command                                                 |
|----------------|---------------------------------------------------------|
| ADP-R1 (C1-C4) | `lowatt-enedis technical --autorisation 98800007059999` |
| ADP-R1 (C5)    | `lowatt-enedis technical --autorisation 25946599093143` |
| ADP-NR1        | `lowatt-enedis technical 99999999999999`                |


ConsultationMesures v1.1
------------------------

| Case           | Command                                                 |
|----------------|---------------------------------------------------------|
| AHC-R1 (C1-C4) | `lowatt-enedis measures --autorisation 98800005782026`  |
| AHC-R1 (C5)    | `lowatt-enedis measures --autorisation 25957452924301`  |
| AHC-NR1        | `lowatt-enedis measures 98800005782026`                 |


ConsultationMesuresDetaillees v2.0
----------------------------------

| Case            | Command                                                                                           |
|-----------------|---------------------------------------------------------------------------------------------------|
| CMD2-R1 (C1-C4) | `lowatt-enedis details 30001610071843 COURBE --from 2020-03-01 --to 2020-03-08`                   |
| CMD2-R1 (C5)    | `lowatt-enedis details 25478147557460 COURBE --from 2020-03-01 --to 2020-03-08`                   |
| CMD2-R2         | `lowatt-enedis details 30001610071843 COURBE --courbe-type PRI --from 2020-03-01 --to 2020-03-08` |
| CMD2-R3         | `lowatt-enedis details 25478147557460 ENERGIE --from 2020-03-01 --to 2020-03-08`                  |
| CMD2-R4         | `lowatt-enedis details 25478147557460 PMAX --from 2020-01-01 --to 2020-02-01`                     |
| CMD2-NR1        | `lowatt-enedis details 25478147557460 COURBE --from 2020-01-01 --to 2020-01-10`                   |
| CMD2-NR2        | `lowatt-enedis details 25478147557460 ENERGIE --from 2020-01-01 --to 2020-01-08`                  |


RecherchePoint v2.0
-------------------

| Case     | Command                                                                                           |
|----------|---------------------------------------------------------------------------------------------------|
| RP-R1    | `lowatt-enedis search --tension BTINF --categorie RES --cp 34650 --insee 34231`                   |
| RP-R2    | `lowatt-enedis search --voie "1 RUE DE LA MER" --nom=TEST --cp 84160 --insee 84042 --hp`          |
| RP-R3    | `lowatt-enedis search --voie "1 RUE DE LA MER" --nom=TES --cp 84160 --insee 84042 --hp`           |
| RP-NR1   | `lowatt-enedis search --categorie RES --cp 34650 --insee 34231`                                   |
| RP-NR2   | `lowatt-enedis search --insee 34231 --voie "1 RUE DE LA MER"`                                     |


CommandeTransmissionDonneesInfraJ v1.0
--------------------------------------

| Case      | Command                                                                                                   |
|-----------|-----------------------------------------------------------------------------------------------------------|
| F375A-R1  | *XFAIL* `lowatt-enedis cmdInfraJ 98800000000246 --cdc --injection --denomination "Raison Sociale"`        |
| F375A-NR1 | *Not implemented* (need to implement --no-autorisation for cmdInfraJ) `lowatt-enedis cmdInfraJ 98800000000246 --idx --injection --denomination "Raison Sociale"` |


CommandeTransmissionHistoriqueMesures v1.0
------------------------------------------

| Case             | Command                                                                                                   |
|------------------|-----------------------------------------------------------------------------------------------------------|
| F380-R1 (C1-C4)  | `lowatt-enedis cmdHisto 98800005144497 CDC --pas 10`                                                      |
| F380-R1 (C5)     | `lowatt-enedis cmdHisto 25957452924301 CDC --pas 30 --nom roro --civilite M`                              |
| F385B-R1         | `lowatt-enedis cmdHisto 25957452924301 IDX --nom roro --civilite M`                                       |
| F380-NR1         | `lowatt-enedis cmdHisto 25957452924301 CDC --pas 30 --nom roro --civilite M --from 2010-01-01`            |
| F385B-NR1        | `lowatt-enedis cmdHisto 25957452924301 IDX --nom roro --civilite M --from 2010-01-01`                     |