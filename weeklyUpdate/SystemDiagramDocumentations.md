# System Diagram Components 
## FDA recall data base
* [FDA Immediate relase](http://www.fda.gov/Food/RecallsOutbreaksEmergencies/Recalls/default.htm): 
 * Pros: Updated at the moment of issue. Has pictures.  
 * Cons:Data pattern varies for each entry. Would be hard for scraping.
* [Weekly report] (http//www.accessdata.fda.gov/scripts/ires/index.cfm): Updated weekly. 
 * Well organized but need to download CSV file to see.
* [official? API](https://open.fda.gov/food/enforcement/reference/): Very well documented. The API team is still active on [twitter](https://twitter.com/openFDA).
* [FARE food allergy recall and education](https://www.foodallergy.org/stay-informed?gclid=Cj0KEQjw4MK_BRC1n6KTtezikbIBEiQA872hYReUftLmAPUvzuaPd6LODj-gS_zLHVY78dVaPzZJ3MAaAhLM8P8HAQ)
 * mainly for recalls because of undeclared ingredients that cause allergies
 * can sign up for email alers

## UPC code
NOTE: all of the following look up site may not have a complete database of UPC codes. Many of the UPC code on FDA website cannot be found.
* [a look up API called upcdatabase](http://upcdatabase.org/api):
 * JSON example: {"valid":"true","number":"0111222333446","itemname":"UPC Database Testing Code","alias":"Testing Code","description":"http:\/\/upcdatabase.org\/code\/0111222333446","avg_price":"123.45","rate_up":0,"rate_down":0}
 * Pros: FREE
 * Cons: have seen this webside down multiple times (usually for one minute)
* [another look uo API called barcodelookup](https://www.barcodelookup.com/api)
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
