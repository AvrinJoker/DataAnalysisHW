#PM2.5 Problems
## 0. Load the datasets
```r
NEI = readRDS("exdata_data_NEI_data/summarySCC_PM25.rds")
SCC = readRDS("exdata_data_NEI_data/Source_Classification_Code.rds")
```
## 1. Plot1
Have total emissions from PM2.5 decreased in the United States from 1999 to 2008? Using the base plotting system, make a plot showing the total PM2.5 emission from all sources for each of the years 1999, 2002, 2005, and 2008.
```r
sub1 = aggregate(NEI$Emissions,by = list(NEI$year,NEI$Pollutant),sum)
names(sub1) = c("Year","Pollutant","Total_Emission")
par(mfrow = c(1,1))
png(filename = "./plot1.png")
with(sub1,{
  plot(Year, Total_Emission, xlab = "Year", ylab = "PM2.5 Emission (ton)",main = 
         "National Total PM2.5 Emissions over Year 1999-2008", pch =19, ylim = c(0,8e+06))
  lines(Year, Total_Emission, lwd =4)
})
dev.off()
```
