# Building QuickSignt visuals


### Example 1
To build a visual that shows the different user registration channels, drag the connection field onto the visual. Then choose the Pie chart icon from the Visual types section.

![Building an analysis](https://raw.githubusercontent.com/bls20AWS/Auth0EventBridge/master/images/analysis1.png "S3 Permissions Dashboard")

Once there are registrations from multiple channels, your chart looks like this:
![Pie Chart visual with multiple data points](https://raw.githubusercontent.com/bls20AWS/Auth0EventBridge/master/images/piechart.png "S3 Permissions Dashboard")

### Calculated Fields
You can create additional calculated fields that use functions and operators to analyze or transform field data.  
Do this to create a separate field for each Auth0 event, e.g.,  successful signup and successful login.


1.	Choose Add, in the top left-hand menu, then choose Add calculated field
2.	Choose countIf from the Function list column, enter Registrations in the Calculated field name field.
3.	Enter countIf(type,type='ss')  in the Formula field.
This formula calculates the number of values in the type dimension, where type is equal to ss (a successful sign-up).
 
![Creating calculated fields](https://raw.githubusercontent.com/bls20AWS/Auth0EventBridge/master/images/alculatedFields.png "S3 Permissions Dashboard")

You can repeat this process for each of the event types that an EventBridge rule was created for:

| EventRType           | Formla                                                 |
| -------------------- |:-------------------------------------------------------|
| Successful sign-in   | countIf(type,type = 's')                               |
| Successful sign-out  | countIf(type,type = 'slo')                             |
| Unsuccessful sign-out| countIf(type,type = 'f' OR type = 'fp' OR type = 'fu') |


To create additional calculated fields, refer to this list for the full Function index.

### Example 2
Now to add a new visual with these calculated fields, choose the Add button in the top menu, then choose Add visual. Drag the new Registrations field onto the new visual.  This automatically shows the Registration trend.  

Add further clarity to this visual by applying some conditional formatting.  Choose the drop-down arrow in the top right of the visual, then choose conditional formatting and set the following:


1.	Format field based on: Difference
2.	Condition: Less than
3.	Value: 0
4.	Color: Red

### Example 3 – comparisons over time 
This third example shows registrations versus sign-ins over time:
![Time based comparrisons](https://raw.githubusercontent.com/bls20AWS/Auth0EventBridge/master/images/timebasedComparisons.png "Time based comparrisons")

To build this, add a new visual and drag the date, Successful sign in and Registrations fields onto it.

A complete analysis could look something like this, with multiple visuals, custom fields, conditional formatting, and events. This gives a snapshot of user interaction with the front-end application at any given time.