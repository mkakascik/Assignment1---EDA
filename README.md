Assignment1---EDA
=================
getwd()
setwd("C:/Users/Sony/Documents/coursera")
dir()
hpc <- read.table("household_power_consumption.txt", header=T, sep = ";")

hp <- subset(hpc, hpc$Date %in% c("1/2/2007", "2/2/2007"))

hp$Date2 <- strptime(paste(hp$Date, hp$Time), "%d/%m/%Y %H:%M") 
attach(hp)
hp$Global_active_power = as.numeric(Global_active_power)
hp$Global_reactive_power = as.numeric(Global_reactive_power)
hp$Voltage = as.numeric(Voltage)
hp$Global_intensity = as.numeric(Global_intensity)
hp$Sub_metering_1 = as.numeric(Sub_metering_1)
hp$Sub_metering_2 = as.numeric(Sub_metering_2)
hp$Sub_metering_3 = as.numeric(Sub_metering_3)
str(hp)
summary(hp)

hist(hp$Global_active_power , breaks = 15, main = "Global Active Power", xlab = "Global Active Power (kilowatts)", col = "red")
Sys.setlocale(locale = "English")
plot(hp$Date2, hp$Global_active_power,xlab = NA, ylab = "Global Active Power (kilowatts)",type = "l")


plot3 <- plot(hp$Date2, Sub_metering_1,type = "l" )
lines( Sub_metering_2, type = "l", col = "red")

?lines
