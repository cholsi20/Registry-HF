# Registry-HF

*General Layout*
- Text based email body
-	Footer

*Template Purpose*<br>
This template was used as part of our Deprecated Programs emails.  It helped to inform our customers that we were no longer going to be offering this program.  

*AMPscript Usage*
-	Used to supply unsubscribe link
-	date/ time of send 
-	used to compile links w/ google analytics (tracking)  
-	Add name functionality 
-	Convert dollar totals into US dollar denominations. 
-	Used to populate individual coupon code

*Template Features*
-	Responsive Design 
-	Dynamic content
-	Personalization

*Template Logic*<br>
The template uses some very basic AMPscript calls, such as the first name which makes a call simply to the data within that column of the Data Extension.  What’s potentially less obvious is the call for when the first name is not in our database.  In this case, I asked specifically for Data Analytics to do a search and replace in the file on their end, such that when the information was either not there, or came in a format we knew to be incorrect (such as, has a ‘.com’ in the name), to replace that name with the literal @ symbol.  This explains the presence of the fairly crude regular expression search, without a whole lot of safety precautions around it.  As of the writing of this documentation, it was unclear how to perform a breakdown of strings to do a character search in the string.  Additionally, error handling can only be performed with if/ then conditionals.  Given that AMPscript is somewhat limited in this way, much of the error handling happened before the file was even handed off to ETO.   Moving forward using this template, a similar procedure would be necessary to ensure the desired effect as there are no checks in place, otherwise.  
<br>
To break down the solution I was able to write using AMPscript, I set the variable for the first name, and then set the variables for the alternate desired greetings, according the business logic.  I then performed a string search to determine if the literal ‘@’ symbol was found more than zero times, and to populate an array, were a match to be found.  From there, I set a conditional statement to determine if the array was populated, to only give the greeting “Hello”, and if it was not, to concatenate the desired greeting of “Dear ‘Customer Name Here’”.  
<br>
This template also utilized another column, which is the coupon code.  Coupons of varying dollar amounts were given to customers who fell into certain categories.  This was determined by their DRX score, and the dollar amount they currently had available in credit.  In this instance, we compartmentalized this group into High Future, or those customers who had not yet spent any money with us, but would have a higher probability to do so.  



