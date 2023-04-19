## Recreating Reported road casualty statistics in Great Britain From 2017

This dataset gives more insights into the casuality statistics within the the Great Britain from year 2017-2021.

🚗[Click to download the the dataset](https://www.gov.uk/government/collections/road-accidents-and-safety-statistics)

🚗 [Click here to view as reported](https://maps.dft.gov.uk/road-casualties/index.html)


## Creating my report table for my visualization

```
Create or Alter View rpt.UkTraffic
As

Select c.accident_index
	  ,c.accident_reference
	  ,c.age_of_casualty
	  ,ag.age_barrack
	  ,cal.Year
	  ,cal.Month
	  ,cal.MonthName
	  ,c.casualty_class
	  ,cl.class_label
	  ,c.sex_of_casualty
	  ,g.gender
	  ,a.local_authority_highway
	  ,la.LA_highway_label
	  ,a.police_force
	  ,p.district_name
	  ,a.calc_road_type
	  ,r.RoadType
	  ,c.casualty_type as 'Cas_Road_User'
	  ,ro.[Road Type User]
	  ,a.accident_severity
	  ,s.severity_level
	  ,a.weather_conditions
	  ,w.Weather_label as 'Weather'
	  ,a.speed_limit
	  ,c.Count
From [vw].[fCasualities] c
inner join [vw].[fAccidents] a
on a.[accident_index] = c.[accident_index]
inner join [vw].[Age] ag
on ag.age_of_casualty = c.age_of_casualty
inner join [vw].[Calendar] cal
on cal.Date = a.acc_date
inner join [vw].[Class] cl
on cl.casualty_class = c.casualty_class
inner join [vw].[Gender] g
on g.sex_of_casualty = c.sex_of_casualty
inner join [vw].[police_force_district] p
on p.police_force = a.police_force
inner join [vw].[CasualityRoad_type] r
on r.calc_road_type = a.calc_road_type
inner join [vw].[Severity_level] s
on s.accident_severity = a.accident_severity
inner join [vw].[Weather_conditions] w
on w.weather_conditions = a.weather_conditions
inner join [vw].[Road_User_Type] ro
on ro.Road_Type = c.casualty_type
inner join [vw].[LAHighway] la
on la.local_authority_highway = a.local_authority_highway

```

## A Video of my Dashboard

