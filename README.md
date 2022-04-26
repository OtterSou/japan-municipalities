# japan-administrative-divisions

[日本語版](README-ja.md)

This repository contains a list of all administrative divisions with [standard area codes](http://data.e-stat.go.jp/lodw/en/provdata/lodRegion/)in Japan as of April 26, 2022.

## Levels and Types

Administrative divisions are classified into "types" based on what suffixes are used. Types are assigned 2-digit codes, where the first digit shows the level of the administrative divisions.

code | description | count
--- | --- | --:
**1** | **Prefectures** | **47**
11 | metropolis/to | 1
12 | prefecture/do | 1
13 | prefecture/fu | 2
14 | prefecture/ken | 43
**2** | **Prefecture subdivisions** | **462**
21 | designated city | 20
22 | special ward area (Tokyo) | 1
23 | city area | 47
24 | county | 376
25 | general subprefectural bureau (Hokkaido) | 9
26 | subprefectural bureau (Hokkaido) | 5
27 | branch office (Tokyo islands) | 4
**3** | **Municipalities** | **1747**
31 | designated city | 20
32 | city | 772
33 | special ward (Tokyo) | 23
34 | town/machi | 277
35 | town/cho | 466
36 | village/mura | 161
37 | village/son | 28
**4** | **Wards** | **175**
41 | ward | 175

## Files and Fields

All tables are in tab-separated values (TSV) format.

### 0-all.tsv, 1-pref.tsv, 2-psub.tsv, 3-muni.tsv, 4-ward.tsv

[0-all.tsv](0-all.tsv) contains all administrative divisions, whereas each of other 4 files contain only one level with irrelevant fields omitted.

Field | Description
--- | ---
level | Level of the entity as described above (level 0 only)
code | 5-digit standard area code
pref | 2-digit prefecture code
psub | Prefecture subdivision which the municipality belongs to (level 3 only)
muni | Municipality which the ward belongs to (level 4 only)
full-ja | Name in kanji with suffix
full-ja-hira | Name in hiragana with suffix
full-en | Name in romaji with suffix
base-ja | Name in kanji without suffix
base-ja-hira | Name in hiragana without suffix
base-en | Name in romaji without suffix
type | Type of the entity as described above
county | County (type 24) which the municipality belongs to (level 3 only)
subpref | Subprefecture (types 25, 26, and 27) which the municipality belongs to (level 3 only)

### suffix.tsv

Field | Description
--- | ---
type | 2-digit Type code
ja | suffix in kanji
ja-hira | suffix in hiragana
en | suffix in English

### spelling-variants.tsv

See notes on English/Romaji names below.

Field | Description
--- | ---
code | 5-digit standard area code
GSI-rules | Name based on [Notation Rules of Geographic Names, etc. in English](https://www.gsi.go.jp/common/000138865.pdf) by [Geospatial Information Authority of Japan](https://www.gsi.go.jp/) (GSI)
GSI-map | Name on English basemap in [GSI map](https://maps.gsi.go.jp/)
MLIT | Name from [webland API](https://www.land.mlit.go.jp/webland/api.html#todofukenlist) by [Ministry of Land, Infrastructure, Transport and Tourism](https://www.mlit.go.jp/) (MLIT)
official | Name used by the municipality's official website
url | URL of municipality's official website

## Notes

### Entities with identical names

Some entities in Hokkaido have identical names.

* Tomari Village
  * `01403` Shiribeshi General Subprefectural Bureau, Furuu County
  * `01696` Nemuro Subprefectural Bureau, Kunashiri County, part of disputed Northern Territories
* Kamikawa County
  * `01826` former Ishikari Province
  * `01828` former Teshio Province
  * `01851` former Tokachi Province
* Nakagawa County
  * `01829` former Teshio Province
  * `01854` former Tokachi Province

2 towns named Esashi Town (`01361` and `01514`) can be distinguished by their names in kanji. (江差町 and 枝幸町 respectively)

### Designated cities

Each designated city constitutes a prefecture subdivision by itself. To make the hierarchical structure consistent, each designated city has an entry duplicated in levels 2 and 3 with types 21 and 31.

### Hokkaido counties

Hokkaido uses subprefectures instead of counties to assign codes to towns and villages, even though there are counties in Hokkaido. Because the counties do not have official 5-digit standard area codes, I assigned them codes between 01801 and 01869.
These county codes are by no means official, and only exists to provide information about which town/village belongs to which county.

### English/Romaji names

Romaji spelling of administrative divisions follows [Notation Rules of Geographic Names, etc. in English](https://www.gsi.go.jp/common/000138865.pdf) by [Geospatial Information Authority of Japan](https://www.gsi.go.jp/) (GSI) in the tables. However, There are several instances where an entity's name has more than one romanized spelling. For example, `27220` 箕面市(みのおし), Osaka Prefecture is romanized Minoo City based on the GSI rules, but the city officially prefers Minoh City.  
Such variations are summarized in [spelling-variants.tsv](spelling-variants.tsv). This list may be expanded as more of such inconsistencies are found.

English names of suffixes follow the GSI rules as much as possible. When a term is not specified, one from English Wikipedia is used.
