---
tags:
  - source/video
time: 2026-02-12 15:34
status: done
---
# References
- [[@csZiXueSheQu24CachesI_BiLiBiLi_bilibili]]

# Binary Prefix and calculation with them
The binary prefixes are usually used to describe some kind of amount, like "kilo-byte". But the standard might be confusing since some hardware manufacturers uses the *SI* factors which holds less than user might expect. The following table contains the corresponding amount attached to each prefix.


| Name  | Abbr | Factor   | SI Size   | IEC standard prefix |
| ----- | ---- | -------- | --------- | ------------------- |
| Kilo  | K    | $2^{10}$ | $10^{3}$  | kibi                |
| Mega  | M    | $2^{20}$ | $10^{6}$  | mebi                |
| Giga  | G    | $2^{30}$ | $10^{9}$  | gibi                |
| Tera  | T    | $2^{40}$ | $10^{12}$ | tebi                |
| Peta  | P    | $2^{50}$ | $10^{15}$ | pebi                |
| Exa   | E    | $2^{60}$ | $10^{18}$ | exbi                |
| Zetta | Z    | $2^{70}$ | $10^{21}$ | zebi                |
| Yotta | Y    | $2^{80}$ | $10^{24}$ | yobi                |

Given a random 2's power number, we can predict the binary prefix representation like this. Take $2^{\text{XY}}$ for instance, we treat $2^{Y}$ as the factor, and replace the $2^{X 0}$ with the IEC standard prefix.