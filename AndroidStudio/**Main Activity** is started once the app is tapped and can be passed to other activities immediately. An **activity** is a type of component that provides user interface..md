**Main Activity** is started once the app is tapped and can be passed to other activities immediately. An **activity** is a type of component that provides user interface. 

App composed of hierarchy of **layouts**(ViewGroup objects) and **widgets**(View objects)
* Layouts are containers that control child view positioning 
  * Views are the leaves
* Widgets are UI components: buttons and text boxes

*Set default margins in dpp*, recommended is 8 or 16. Can create constraints between components by using the circle handles of view objects and dragging to each other or the layout borders. This wil automatically adjust to default margins.

Use the baseline property so elements are aligned horizontally.

Can chain horizontally for responsiveness by selecting all objects in row and right-click --> create horizontal chain. Allowing layout in unison. 

**Match Constaints** means that the width expands to meet the definition of the horizontal constraints and margins. 

An **intent** is an object that provides runtime binding between separate components. *An apps intent to do something*
* an intent can carry data types as key-value pairs called "extras"