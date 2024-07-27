#importing pandas,numpy and matplotlib library.
!pip install pandas
!pip install numpy
!pip install matplotlib
# Importing numpy,pandas and matplotlib library
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
# Quadrant4
# Making a dataframe of quadrant 4 of marteloscope
data_marteloscope4 = pd.read_csv("Q4.csv",sep=";",decimal = ',')
data_marteloscope4
# Defining diameter growth of Species present in Quadrant 4
Diameter_Growth = data_marteloscope4["Diameter_Growth"]
Diameter_Growth
# Defining height growth of Species present in Quadrant 4
Height_Increase = data_marteloscope4["Height_Increase"]
Height_Increase
# Defining Species present in Quadrant 4
Species = data_marteloscope4["Species"].unique()
Species
# Making a dataframe where species are aranged according to their mean diameter growth
Data_Diameter_Growth4 = data_marteloscope4.groupby("Species",as_index=False)[["Diameter_Growth"]].mean()
Data_Diameter_Growth4
# Making a dataframe where species are aranged according to their mean height growth in quadrant 4
Data_Height_Increase4 = data_marteloscope4.groupby("Species", as_index=False)[["Height_Increase"]].mean()
Data_Height_Increase4
# Bar graph displaying mean diameter growth ad height growth of different species of Quadrant4
# Create a figure and axis using plt.subplots
fig, ax = plt.subplots( )
x=np.arange(len(Data_Diameter_Growth4['Species']))
width = 0.35
#Plot a bar graph and modify it
ax.bar(x-width/2, Data_Diameter_Growth4['Diameter_Growth'], width= width, color='green', alpha= 0.5,label = "Diameter Growth [cm]")
ax.bar(x+width/2, Data_Height_Increase4['Height_Increase'],width= width, color='red', alpha=0.5,label = "Height Growth[m]")
# Put the limits on y axis
ax.set_ylim((0,8))
# Set the label on x and y axis
ax.set_ylabel('Mean Values',fontsize=14)
ax.set_xlabel('Species',fontsize=13)
# Add legends,adjust x ticks and give them labels.
plt.legend(loc='upper right', numpoints=1, ncol=3, fontsize=9, bbox_to_anchor=(1,1))
ax.set_xticks(x, Data_Diameter_Growth4['Species'])
ax.set_xticklabels( Data_Diameter_Growth4['Species'], fontsize=12, rotation=90, ha='center' )
#Give the  suptitle to the bargraph
fig.suptitle( 'Diameter and Height Growth in Plot 4', fontsize=16 )
# Save the bargraph and show it
save_results_to ="C:/Users/Rhythem Kaushal/Python_Images/"
plt.savefig(save_results_to + 'DBH4.jpg',bbox_inches='tight')
plt.show(fig)
# Quadrant 3
# Making a dataframe of quadrant 3 of marteloscope
data_marteloscope3 = pd.read_csv("Q3.csv",sep=";",decimal = ',')
data_marteloscope3
# Defining species of quadrant 3
Species = data_marteloscope3["Species"].unique()
Species
# Making a dataframe where species are aranged according to their mean height growth in quadrant 3
Data_Height_Increase3 = data_marteloscope3.groupby("Species",as_index=False)[["Height_Increase"]].mean()
Data_Height_Increase3
# Making a dataframe where species are aranged according to their mean diameter growth in quadrant 3
Data_Diameter_Growth3 = data_marteloscope3.groupby("Species",as_index=False)[["Diameter_Growth"]].mean()
Data_Diameter_Growth3
# Bar graph displaying mean diameter growth and height growth of different species of Quadrant3
# Create a figure and axis using plt.subplots
fig, ax = plt.subplots( )
x=np.arange(len(Data_Diameter_Growth3['Species']))
width = 0.35
# Plot a bar graph and modify it.
ax.bar(x-width/2, Data_Diameter_Growth3['Diameter_Growth'], width= width, color='green', alpha= 0.5,label = "Diameter Growth[cm]")
ax.bar(x+width/2, Data_Height_Increase3['Height_Increase'],width= width, color='red', alpha=0.5,label = "Height Growth[m]")
ax.set_ylim((0,8))
# Specify the label on x axis and y axis
ax.set_ylabel('Mean Values',fontsize=14)
ax.set_xlabel('Species',fontsize=13)
# Add legend,adjust x ticks and provide labels to them
plt.legend(loc='upper right', numpoints=1, ncol=3, fontsize=9, bbox_to_anchor=(1,1))
ax.set_xticks(x, Data_Diameter_Growth3['Species'])
ax.set_xticklabels( Data_Diameter_Growth3['Species'], fontsize=12, rotation=90, ha='center' )
# Giving the suptitle to the bargraph
fig.suptitle( 'Diameter and Height Growth in Plot 3', fontsize=16 )
# Save the figure and show it
save_results_to ="C:/Users/Rhythem Kaushal/Python_Images/"
plt.savefig(save_results_to + 'DBH3.jpg',bbox_inches='tight')
plt.show(fig)
# Quadrant 1
# Making a dataframe of quadrant 1 of marteloscope
data_marteloscope1 = pd.read_csv("Q1.csv",sep=";",decimal = ',')
data_marteloscope1
# Making a dataframe where species are aranged according to their mean height growth in quadrant 1
Data_Height_Increase1 = data_marteloscope1.groupby("Species", as_index=False)[["Height_Increase"]].mean()
Data_Height_Increase1
# Making a dataframe where species are arranged according to their mean diameter growth in quadrant 1
Data_Diameter_Growth1 = data_marteloscope1.groupby("Species", as_index=False)[["Diameter_Growth"]].mean()
Data_Diameter_Growth1
# Bar graph displaying mean diameter growth and height growth of different species of Quadrant1
# Create a figure and axis using plt.subplots
fig, ax = plt.subplots( )
x=np.arange(len(Data_Diameter_Growth1))
# Creating new variables and replacing the missing values with zero
growth = Data_Diameter_Growth1['Diameter_Growth'].fillna(0)
height = Data_Height_Increase1['Height_Increase'].fillna(0)
# Creating a new variable that contains all values of the first column of Data_Diameter_Growth1 dataset.
y = Data_Diameter_Growth1.iloc[:, 0]
# Setting the limits on y axis, Plotting the bar graph and modifying it.
width = 0.35
ax.set_ylim((0,8))
ax.bar(x-width/2, growth, width= width, color='green', alpha= 0.5,label = "Diameter Growth[cm]")
ax.bar(x+width/2, height,width= width, color='red', alpha=0.5,label = "Height Growth[m]")
# Putting labels on y and x axis
ax.set_ylabel('Mean Values',fontsize=14)
ax.set_xlabel('Species',fontsize=13)
# Adding legend,adjusting x ticks and giving them labels
plt.legend(loc='upper right', numpoints=1, ncol=3, fontsize=9, bbox_to_anchor=(1,1))
ax.set_xticks(x, y)
ax.set_xticklabels( y, fontsize=12, rotation=90, ha='center' )
# Giving suptitle, save the figure and show it
fig.suptitle( 'Diameter and Height Growth in Plot 1', fontsize=16 )
save_results_to ="C:/Users/Rhythem Kaushal/Python_Images/"
plt.savefig(save_results_to + 'DBH1.jpg',bbox_inches='tight')
plt.show(fig)
# Quadrant 2
# Making a dataframe of quadrant 2 of marteloscope
data_marteloscope2 = pd.read_csv("Q2.csv",sep=";",decimal = ',')
data_marteloscope2
# Defining species of quadrant 2
Species = data_marteloscope2["Species"].unique()
Species
#  Making a dataframe where species are arranged according to their mean diameter growth in quadrant 2
Data_DBH_Growth = data_marteloscope2.groupby("Species", as_index=False)[["Diameter_Growth"]].mean()
Data_DBH_Growth
#  Making a dataframe where species are arranged according to their mean height growth in quadrant 2
Data_Height_Increase = data_marteloscope2.groupby("Species",as_index=False)[["Height_Increase"]].mean()
Data_Height_Increase
# Bar graph displaying mean diameter growth and height growth of different species of Quadrant2
#Create a figure and axis using plt.subplots
fig, ax = plt.subplots( )
x=np.arange(len(Data_DBH_Growth['Species']))
width = 0.35
#Plot bar graph, modify it
ax.bar(x-width/2, Data_DBH_Growth['Diameter_Growth'], width= width, color='green', alpha= 0.5,label = "Daimeter Growth[cm]")
ax.bar(x+width/2, Data_Height_Increase['Height_Increase'],width= width, color='red', alpha=0.5,label = "Height Growth[m]")
# Specify the limits on y axis
ax.set_ylim((0,8))
# Putting the labels on x and y axis
ax.set_ylabel('Mean Values',fontsize=14)
ax.set_xlabel('Species',fontsize=13)
# Adding legends,adjusting x ticks and giving labels to it
plt.legend(loc='upper right', numpoints=1, ncol=3, fontsize=9, bbox_to_anchor=(1,1))
ax.set_xticks(x, Data_DBH_Growth['Species'])
ax.set_xticklabels( Data_DBH_Growth['Species'], fontsize=12, rotation=90, ha='center' )
# Adding suptitle, save the figure and show it.
fig.suptitle( 'Diameter and Height Growth in Plot 2', fontsize=16 )
save_results_to ="C:/Users/Rhythem Kaushal/Python_Images/"
plt.savefig(save_results_to + 'DBH2.jpg',bbox_inches='tight')
plt.show(fig)
# Defining Diameter Growth of quadrant 1 as x1
x1=Data_Diameter_Growth1
x1
# Defining Diameter Growth of quadrant 2 as x2
x2=Data_DBH_Growth
x2
# Defining Diameter Growth of quadrant 3 as x3
x3=Data_Diameter_Growth3
x3
# Defining Diameter Growth of quadrant 4 as x4
x4=Data_Diameter_Growth4
x4
# Scatterplot displaying the plot wise comparison of mean diameter growth of diffferent species
# Create a figure and axis using plt.subplot
fig, ax = plt.subplots()
#Specifying the respective variables to species of diameter growth dataframes of all quadrants
x1=Data_Diameter_Growth1['Species']
x2=Data_DBH_Growth['Species']
x3=Data_Diameter_Growth3['Species']
x4=Data_Diameter_Growth4['Species']
# Making scatterplot and modifying it
ax.scatter( x1,Data_Diameter_Growth1['Diameter_Growth'], color='green', label = "plot1" )
ax.scatter( x2,Data_DBH_Growth['Diameter_Growth'],color='red', label = "plot2")
ax.scatter( x3,Data_Diameter_Growth3['Diameter_Growth'], color='blue',label = "plot3" )
ax.scatter( x4, Data_Diameter_Growth4['Diameter_Growth'], color='yellow', label = "plot4" )
#P Putting labels on x axis and y axis
ax.set_ylabel('Mean Diameter Growth[cm]',fontsize=14)
ax.set_xlabel('Species',fontsize=13)
#Adding legend and suptitle
plt.legend(loc='upper right', numpoints=1, ncol=3, fontsize=9, bbox_to_anchor=(1,1))
fig.suptitle( 'Plot wise comparison of Mean Diameter Growth ', fontsize=14 )
#Specifying the y axis limit
ax.set_ylim((0,5))
#Save the figure, show and close it
save_results_to ="C:/Users/Rhythem Kaushal/Python_Images/"
plt.savefig(save_results_to + 'sactterdia.jpg',bbox_inches='tight')
plt.show(fig)
plt.show( fig ) 
plt.close( fig )
# Scatterplot displaying the plot wise comparison of mean height growth of diffferent species
# Create a figure and axis using plt.subplots
fig, ax = plt.subplots()
# Specifying the variables to species of  Height Increase dataframes of all quadrants 
x1=Data_Height_Increase1['Species']
x2=Data_Height_Increase['Species']
x3=Data_Height_Increase3['Species']
x4=Data_Height_Increase4['Species']
# Making scatterplot and modifying it
ax.scatter( x1,Data_Height_Increase1['Height_Increase'], color='green', label = "plot1" )
ax.scatter( x2,Data_Height_Increase['Height_Increase'],color='red', label = "plot2")
ax.scatter( x3,Data_Height_Increase3['Height_Increase'], color='blue',label = "plot3" )
ax.scatter( x4, Data_Height_Increase4['Height_Increase'], color='yellow', label = "plot4" )
# Putting labels on x and y axis
ax.set_ylabel('Mean Height Increase[m]',fontsize=14)
ax.set_xlabel('Species',fontsize=13)
#Adding legend and suptitle
plt.legend(loc='upper right', numpoints=1, ncol=3, fontsize=9, bbox_to_anchor=(1,1))
fig.suptitle( 'Plot wise comparison of Mean Height Growth', fontsize=14 )
# Specifying the y axis limit
ax.set_ylim((0,5))
# Save the figure,show and close it
save_results_to ="C:/Users/Rhythem Kaushal/Python_Images/"
plt.savefig(save_results_to + 'sactterheight.jpg',bbox_inches='tight')
plt.show( fig ) 
plt.close( fig )
