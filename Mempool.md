# Mempool

Left number: Mempool suggested fee for a fast transaction

Middle number: suggested fee for a tx to get in a block the next half hour

Right number: suggested fee for a tx to get in a block the next hour

<img src="./images/6.PNG" style="zoom: 67%;" />

## Tutorial

1. Install the app "Scriptable" -> [Apple Appstore - Scriptable](https://apps.apple.com/ch/app/scriptable/id1405459188?l=en)
1. Open the app and click the "+" sign on the top right corner
1. Paste the following script created by [Janna](https://twitter.com/Janna3257):

```js
let req = new Request('https://mempool.space/api/v1/fees/recommended');
let json = await req.loadJSON();

fast = json.fastestFee.toString();
halfHour = json.halfHourFee.toString();
hour = json.hourFee.toString();

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
  
  // Add titel
  let wdgTitel = listwidget.addText("Mempool");
  let wdgDesc = listwidget.addText("High           Medium           Low");
  // Add widget heading  
   let heading = listwidget.addText(fast + "    " + halfHour + "    " + hour);    

  wdgTitel.centerAlignText();
  wdgDesc.centerAlignText();
  heading.centerAlignText();
  
  wdgTitel.font = Font.boldSystemFont(24);
  wdgDesc.font = Font.lightSystemFont(16);
  
  if(fast < 10)
    heading.font = Font.boldSystemFont(73);
  else if(fast < 100)
     heading.font = Font.boldSystemFont(54);
  else
    heading.font = Font.boldSystemFont(43);
    
  wdgTitel.textColor = new Color("#eeeeee")
  wdgDesc.textColor = new Color("#eeeeee")  
  heading.textColor = new Color("#eeeeee")
  
  // Return the created widget
  return listwidget;
}
```

4. Click on the bottom left corner the "sliders" to name your script. For example: Mempool
5. Click close and done
6. Go to the homescreen, press and hold for a few seconds to make the icons move. Tab on the top left corner the "+" symbol

<img src="./images/2.PNG" style="zoom: 50%;" />

7. Scroll down untill you find the "Scriptable" App. Select it and scroll to the right for the full sized version.

<img src="./images/3.PNG" style="zoom: 30%;" />

8. Click "Add Widget" and tab the new created widget to edit it. Select the created script and you're done :)

<img src="./images/5.PNG" style="zoom: 30%;" />
