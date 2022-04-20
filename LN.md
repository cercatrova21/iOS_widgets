# Lightning Network.

Firts number: Number of Nodes.
Middle number: Number of Channels.
Last number: Network Capacity.

## Tutorial

1. Install the app "Scriptable" -> [Apple Appstore - Scriptable](https://apps.apple.com/ch/app/scriptable/id1405459188?l=en)
2. Open the app and click the "+" sign on the top right corner
3. Paste the following script created by [SN](https://twitter.com/__B__T__C__):

```js
let req = new Request('https://1ml.com/statistics?json=true');
let json = await req.loadJSON();

nodes = json.numberofnodes.toString();
channels = json.numberofchannels.toString();
capacity = json.networkcapacity.toString();

let widget = await createWidget();

// Check where the script is running
if (config.runsInWidget) {
  // Runs inside a widget so add it to the homescreen widget
  Script.setWidget(widget);
} else {
  // Show the medium widget inside the app
  widget.presentMedium();
}
Script.complete();



async function createWidget() {
  // Create new empty ListWidget instance
  let listwidget = new ListWidget();

  
  // Set new background color
  listwidget.backgroundColor = new Color("#000000");


  // Add widget heading  
   let heading = listwidget.addText(nodes + "    ");    
   let heading = listwidget.addText(channels + "    "); 
   let heading = listwidget.addText(capacity + "    "); 
   

  heading.centerAlignText();
  
  if(capacity < 1,000.00)
    heading.font = Font.lightSystemFont(60);
  else if(capacity < 10,000.00)
     heading.font = Font.lightSystemFont(50);
  else
    heading.font = Font.lightSystemFont(35);
    
  heading.textColor = new Color("#eeeeee")
  
    

  // Return the created widget
  return listwidget;
}
```

4. Click on the bottom left corner the "sliders" to name your script. For example: Lightning Network
5. Click close and done
6. Go to the homescreen, press and hold for a few seconds to make the icons move. Tab on the top left corner the "+" symbol

<img src="./images/2.PNG" style="zoom: 50%;" />

7. Scroll down untill you find the "Scriptable" App. Select it and scroll to the right for the full sized version.

<img src="./images/3.PNG" style="zoom: 30%;" />

8. Click "Add Widget" and tab the new created widget to edit it. Select the created script and you're done :)
