# lperin.intervalcolor.LineColor

**Version:** 1.0.0

A DAXLib function designed to dynamically color KPI values in **Bar Charts** and **Line Charts** based on the selected months.

## Behavior

The function compares the current **Bounce Rate** with the selected months:

* 🟢 **Green** → highest bounce rate
* 🔴 **Red** → lowest bounce rate
* 🔵 **Blue** → other values

This makes it easy to visually highlight the best and worst KPI values directly in Power BI **Bar Charts** and **Line Charts**.

## Usage

Use the function as a **conditional formatting / color measure** for the chart.


- create your measure 
Valeur KPI =
SUM('VENTES'[Montant])

- Create the minimum nad maximum like 
if your axis is the date the make two kpi Min KPI and max KPI
Min KPI =
MINX(
    ALLSELECTED('DATE'[Mois]),
    CALCULATE([Valeur KPI])
)
Max KPI =
MAXX(
    ALLSELECTED('DATE'[Mois]),
    CALCULATE([Valeur KPI])
)
- Call the function like that 
```dax
lperin.intervalcolor(
    [Valeur KPI],
    [Min KPI],
    [Max KPI]
)
```

The function returns a color name that can be used to dynamically format the chart:

```text
green
red
blue
```

## Dependencies

* `ValueKPI`
* `'DATE'[Année]`
* `'DATE'[mois]`
* `'DATE'[Mois_num]`

## Package

```text
Package ID: lperin.intervalcolor
Version:    1.0.0
Function:   lperin.intervalcolor.LineColor
```

## Visualization

Designed for:

* 📊 Power BI **Bar Charts**
* 📈 Power BI **Line Charts**

The color changes automatically according to the selected date context.
