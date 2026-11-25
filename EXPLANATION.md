## File to explain what cluster_plot.py was doing, trying to achieve and how it was fixed


## Explanation of what was wrong and fixes:

File was trying to run k clustering for k = 2,3,4,5.
However it was setting 'k = min(k,3)', running k = 4 and 5 as 3 instead. Therefore repeating clustering for k = 3 (the plots produced for k=3,4,5 are identical). 
This was changed to 'k = k'.

The silhouette scores bar plot is not being created. Upon inspecting the function run_clustering() in cluster_maker/interface, in the 'metrics' dictionary inside the dictionary 'result' returned by the function, there is a key called 'silhouette'. The file cluster_plot.py was trying to access 'silhouette_score' which does not exist. 
This was changed to 'silhouette' in both the if statement and when plotting the bar chart.