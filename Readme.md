# Data center model
Those names with * means:

$(\square)_{t} = (\square) \cdot \Delta t $

## Paramters with fixed model
| Parameters Names   | Symbols   |      Value      |  Unit |
|----------|---------- |:-------------:|------:|
|Time interval| $\Delta t$ |  5 | mins |
|Zone width| $I^{\text{Zone}}_{\text{width}}$ |  3 | N/A |
|Zone length| $I^{\text{Zone}}_{\text{length}}$ |  3   |   N/A |
|Zones | $I^{\text{Zone}}$ | 9 |    N/A |
|Electricity price of the local grid | $\beta^{\text{e,g}}_{t}$ | $\sim \mathcal{N}(0.989,10^{-3})$ |  $ |
|Time interval length | $\Delta t$ | 30 |    minutes |
|Battery capacity | $E^{\text{B}}$ | 150 |    kWh |
|Battery charging upper bound | $\overline{p^{\text{chr}}}$ | 60 |    kW/h |
|Battery discharging upper bound | $\overline{p^{\text{dis}}}$ | 90 |    kW/h |
|Battery initial energy| $E^{\text{B,state}}_{\text{initial}}$|$0.5\cdot E^{\text{B}}$ |kW/h|
|Battery capacity uppper bound | $\overline{\xi^{\text{B}}}$ | $0.85\cdot E^{\text{B}}$ |kWh|
|Battery capacity lower bound | $\underline{\xi^{\text{B}}}$ | $0.15\cdot E^{\text{B}}$ |kWh|
|Battery charging efficiency| $\eta^{\text{chr}}$ | 0.9 |    N/A |
|Battery discharging efficiency | $\eta^{\text{dis}}$ | $\frac{1}{0.85}$ |    N/A |
|Zone tempreture initialization |$T^{\text{Zone}}_{\text{i,init}} $|$\sim U(25,33)$|$^\circ C$|
|Zone $i$’s temperature UB |$T^{\text{Zone},+}_{i,t} $|$24$|$^\circ C$|
|Zone $i$’s temperature LB |$T^{\text{Zone},-}_{i,t} $|$15$|$^\circ C$|
|Zone $i$’s AC temperature UB |$T^{\text{AC,}+}_{i,t} $|$26$|$^\circ C$|
|Zone $i$’s AC temperature LB |$T^{\text{AC,}-}_{i,t} $|$10$|$^\circ C$|
|Outside tempreture initialization |$T^{\text{out}}_{t} $|$\sim U(27,36)$|$^\circ C$|
|Zone space | $S^{\text{Zone}}_{i}$ | $\sim U(900,1100)$ |    $\text{m}^{2}$ |
|Zone height | $h_{i}$ | $6$ |    $\text{m}$ |
|Solar energy production* | $E^{\text{S}}$ | $\sim U(40,150)$ |    kWh |
|Air thermal resistance value | $R^{\text{Zone}}_{i,i^{\prime}}$ | 0.062 |    $\text{m}K/W$ |
|Outside airflow rate* | $v^{\text{out}}_{t}$ | 0.5 |    $\text{m}^{3}$/s |
|ventilation air flow rate LB* | $\underline{v}^{\text{vent}}_{t}$* | 0.8 |    $\text{m}^{3}$/s |
|Supply airflow rate* | $v^{\text{sup}}_{t}$ | 1 |    $\text{m}^{3}$/s |
|Air specific heat capacity| $c^{\text{a,s}}$ | 0.718 | $\text{kJ} \cdot(\text{kg}\cdot\text{K})^{-1}$|
|Water specific heat capacity| $c^{\text{w,s}}$ | 4.182 |$\text{kJ}\cdot(\text{kg}\cdot\text{K})^{-1}$|
|Air density | $\rho^{\text{air}}$ | 1.2 |    kg$\cdot\text{m}^{−3}$ |
|Coefficient of mth item in chiller power| $\beta^{\text{chiller}}_{m}$ |{4,7}|$\{\text{kWh},\text{kWh}/\text{kg}\}$|
|Coefficient of mth item in chiller power| $\beta^{\text{tower}}_{m}$ |{6,5}|$\{\text{kWh},\text{kWh}/\text{kg}\}$|
|Coefficient of mth item in pump power| $\beta^{\text{pump}}_{m}$ |$\{10^{2},10\}$|$\{\text{kWh},\text{kWh}/\text{kg}\}$|
|Coefficient of mth item in vent power| $\beta^{\text{vent}}_{m}$ |$\{10^{2},10\}$|$\{\text{kWh},\text{kWh}/\text{m}^{3}\}$|
|Chiller rated water flow rate* | $m^{\text{chiller}}_{j}$ | $\sim U(12,32)$ |  kg/min |
|Condense tower rated water flow rate* | $m^{\text{tower}}_{j}$ | $\sim U(10,30)$ |  kg/min |
|Chiller water supply temperature  |$T^{\text{chws}}_{t} $|$20$|$^\circ C$|
|Chiller water return temperature  |$T^{\text{chws}}_{t} $|$30$|$^\circ C$|
|Condense tower water return temperature  |$T^{\text{chws}}_{t} $|$41$|$^\circ C$|
|Energy demands by miscellaneous  |$E^{\text{misc}} $|$0$|$\text{kWh}$|
|IT equipment and servers  |$W^{\text{server}} $|$2.5$|$\text{kW/m}^{2}$|



## Paramters that depend on others
| Parameters Names   | Symbols   |      Value      |  Unit |
|----------|---------- |:-------------:|------:|
|Condense tower water supply temperature  |$T^{\text{chws}}_{t} $|$T^{\text{out}}_{t}$|$^\circ C$|
|Server energy consumpsion** |  $E^{\text{DC}}$ | $\sum_{i\in I^{\text{Zone}}} W^{\text{server}} \cdot S_{i} \cdot\Delta t$ |    $\text{kW}/\text{m}^{2}$ |
|Weight factor for zones |  $\chi_{i}$ | $\frac{S_{i}}{\sum_{i\in I^{\text{Zone}}}{S_{i}}}$ |    N/A |
|Air mass flow into the zone |  $\dot{m}^{\text{Zone}}_{i}$ | $S^{\text{AC}} \cdot v^{\text{sup}}_t\cdot\rho^{\text{air}} \cdot \Delta t $ | $\text{kg}$ |
|Heat dissipation to zone |  $\theta_{i,t}$ | $E^{\text{DC}}_{i,t}\cdot 100\%$ |    $\text{kJ}$ |

** :$\quad E^{\text{DC}}_{t} = \sum_{i\in I^{\text{Zone}}} E^{\text{DC}}_{i,t} $