# Stealthy Roofscapes
Project from the UK Dynamo User Group Dynamo + Generative Design Hackathon 2019

#### Thomas Corrie, Wiktor Kidziak, Bogdan Davydov

Using Dynamo and Refinery to generate cuboid forms on top of an existing building and assess how visible it is from views around the surrounding streets. The initial form is a simple cuboid that could be used as a starting point for a more detailed design

#### Requirements
Dynamo Sandbox 2.0.2
Refinery

![Stealthy Roofscapes](https://github.com/thomascorrie/StealthyRoofscapes/blob/master/images/cover.PNG)

#### Process
* Export area of interest from OpenStreetMap
* Use **StealthyRoofscapes_CreateContextfromOSM.dyn** 
* Create the setup context
* Select the building of interest
* Create the assessment viewpoints
* Export the results to SAT files
* Use **StealthyRoofscapes_CreateForm.dyn**
* The graph uses parameters to create a form on top of the chosen roof. If the form overhangs the roof then it is trimmed to the roof edge
* For each viewpoint the visible sides are chosen and panelised
* Lines are drawn from the viewpoint to the centre of each panel
* Each lines is assessed against the context to see if it is blocked by an existing building or not
* The score for the view is the percentage of panels that are not visible from the viewpoint
* The score for the form is the mean of the viewpoint scores and is contrasted against the volume of the form
* Use **Refinery** to optimise the graph
* Choose Subset of views to assess (to keep computation time down for Refinery)
* Open Refinery
* Run Refinery on the graph with the Box Variables as the inputs (Rotation, Length, Width, Height, XOffset, YOffset)
* The Outputs are volume (Maximize) and mean score (Maximize)

#### Future improvements
* Generate more complex forms
* Greater number of assessment points
* More detailed panelisation to give uniform scores
* Better positioning of assessment viewpoints
* Additional assessment criteria
