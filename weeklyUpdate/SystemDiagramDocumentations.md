# System Diagram Components 
## FDA recall data base
* [FDA Immediate relase](http://www.fda.gov/Food/RecallsOutbreaksEmergencies/Recalls/default.htm): 
 * [Rushabh]: Also: https://www.foodsafety.gov/recalls/alerts/index.html & http://www2c.cdc.gov/podcasts/createrss.asp?c=146
 * Pros: Updated at the moment of issue. Has pictures.  
 * Cons: Data pattern varies for each entry. Would be hard for scraping.
* [Weekly report] (http//www.accessdata.fda.gov/scripts/ires/index.cfm): Updated weekly. 
 * Well organized but need to download CSV file to see.
* [official? API](https://open.fda.gov/food/enforcement/reference/): Very well documented. The API team is still active on [twitter](https://twitter.com/openFDA).
* [FARE food allergy recall and education](https://www.foodallergy.org/stay-informed?gclid=Cj0KEQjw4MK_BRC1n6KTtezikbIBEiQA872hYReUftLmAPUvzuaPd6LODj-gS_zLHVY78dVaPzZJ3MAaAhLM8P8HAQ)
 * mainly for recalls because of undeclared ingredients that cause allergies
 * can sign up for email alers

* expected sample JSON from FDA
> {
“Company Recall Name”: “Tyson Co.”
“Item Recalled: “Chicken Nuggets”,
“Date Recalled”: “09/28/16 @ 4pm”,
“Reason for Recall”: “Didn’t declare milk as ingredient in packaging”
“Class”: I/II/III
“Product Code”:  G264A12A 
“UPC Code”: 
“Use by Date”: 10/08/16
 “Possible Distribution States”: “AL”, “FL”, “GA”, “NC”, “SC”, “TN”
“Expiration Date Range”: 11/2016 - 8/2018
“Company Contact”: 949-646-4628
}

## UPC code
NOTE: all of the following look up site may not have a complete database of UPC codes. Many of the UPC code on FDA website cannot be found.
* [a look up API called upcdatabase](http://upcdatabase.org/api):

JSON example:
> {"valid":"true","number":"0111222333446","itemname":"UPC Database Testing Code","alias":"Testing Code","description":"http:\/\/upcdatabase.org\/code\/0111222333446","avg_price":"123.45","rate_up":0,"rate_down":0}
 
 * Pros: FREE
 * Cons: have seen this webside down multiple times (usually for one minute)
* [another look up API called barcodelookup](https://www.barcodelookup.com/api)
 * Pros: more sophisticated API return
 * Cons: NOT FREE
* [index](https://info.indix.com/upc-lookup-demo?utm_campaign=Search-Product-Identifier-UPC|UPC-Code-Lookup&utm_source=ppc&gclid=Cj0KEQjwg8i_BRCT9dHt5ZSGi90BEiQAItdjpPA_yJyegmMiGFtiL_sZuIKbROWcl3pT1-6EsU6YZDwaAmzX8P8HAQ):
 * demo requested but not yet recieved
 * basic api is FREE with a 60 calls per minute rate limit. 
 
## Development Resources
* [AWS mobile hub](https://console.aws.amazon.com/mobilehub/home?region=us-east-1#/575427dd-3ce2-4393-9fd6-2db97e4c4d13/build):
 * include many features: User sign-in/NoSQL database/user data storage/cloud logic
 * well integrated with Xcode for ios development
 * much easier to manage than Ruby on Rails backend but need to experiment more on what it can do


## Database structure on [lucidchart](https://www.lucidchart.com/documents/edit/b06c6a12-68ec-409b-8459-a2c6f52556be)
 ![alt text] (https://github.com/MaxKaye/ctcornellrecall/blob/master/img/database%20stucture.png "database structure")

* how the data flows
 * user made a new purchase:
   Purchase history database updates --> check with current FDA recalls --> if UPC code match and purchase data is after the recall --> issue user alert (product name/product image/reason of recall)
 * web scraper detects FDA releases new recall:
   current FDA recalls database update --> check with purchase history --> if UPC code match --> issue user alert (product name/product image/reason of recall)
* Remaining Questions: 
 * haven't find reliable source for UPC code look up 
 * where to get itemized user purchase data
 * how to scrape FDA website and determine frequency of database updates: every few hours/every morning/everytime app is opened?
 * should we show a "safe to eat" sign if nothing is recalled
 
## Future thoughts
* B2B model integrating with POS system:
Receive customer’s items purchased by using information from receipt items from QR code on Customer Receipt. Also, we need to figure out if the purchase number that shows up on the POS system would be helpful as well in tracking and then returning the food item.
* The FDA website always says “please return the product to your retailer for a full refund or replacement” but are we going to change this? Incentivize customers by instantly returning the product? This saves them time returning the product.

