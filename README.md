# Tiller Zillow (Simple) Automation
The tiller-zillow-simple script is a simple Google Apps Script to scrape Zillow Zestimates® and insert them into the Balance History sheet of Tiller-enabled spreadsheets. This workflow is especially useful for tracking net worth. 

Visit [Tiller HQ](https://tillerhq.com) to learn more about Tiller.

## Adivsory
*This simple script is designed for intermediate users and includes only lightweight error checking. We hope it meets your needs out of the box, but further tweaks may be required to get it working in your environment. As a one-off Tiller-Labs release, Tiller offers no warranties or support for this solution.*

## Setting Up Your Project

To configure your project, implement the following steps in Google Sheets:
1. Visit [Zillow](https://zillow.com) and browse to the property you'd like to link.
2. Click on the `Public View` link.
3. Find the Zillow Property ID number in the URL— it will have a format similar to: `...homes/for_sale/48000000_zpid/47.63...`. (In this example, the Property ID is `48000000`.) 
4. Create a Zillow Web Services ID by visiting [Zillow's API Overview page](https://www.zillow.com/howto/api/APIOverview.htm).
5. Follow the link to `Get a Zillow Web Services ID (ZWSID)` and follow the steps.
6. Open the Tiller Google-Sheets spreadsheet you'd like to integrate with Zillow.
7. Click on Tools -> Script editor to open the spreadsheet's bound scripts.
8. Copy the contents of [zillow.js](https://raw.githubusercontent.com/TillerHQ/tiller-zillow-simple/master/zillow.js) from this repo into the Google Sheets script editor.
9. Set the `zwsid` variable (at the start of the code) equal to your new Zillow Web Services ID.
10. Set the `zpid` variable (at the start of the code) equal to your new Zillow Property ID.
11. Save the script file.
12. Click on the Set Function dropdown in the control bar and select the `zestimateInsert` function.
13. Click the run/play button.
14. In the 'Authorization required' window that appears, click 'Review Permissions', then authenticate and allow the script to run.

If you've completed all the steps successfully, you should have a new entry in your Balance History reflecting the Zestimate® of the linked property.

## Reporting on Multiple Properties
Most users will configure only a single Zillow Property ID like this:

`var zpid = '11111111';`

If you'd like to run the script against multiple properties, the `zpid` can be configured as an array:

`var zpid = '[11111111, 22222222, 33333333]'`

## Taking This Solution Further...

Consider adding:
* An [onOpen()](https://developers.google.com/apps-script/guides/triggers/#onopene) function to create a menu item to execute an update
* [Triggers](https://developers.google.com/apps-script/guides/triggers/) to automate script execution
