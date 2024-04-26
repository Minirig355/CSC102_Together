# CSC102 - BRING IT ALL TOGETHER

For the Bring It All Together project, despite already having those practices incorporated into my webpage (game.js), I felt it would be innapropriate to reupload my design with no changes so I added a login page to the front. Since this isn't supposed to actually be secure I'll include the valid logins right here in the README, I'll do this going forward too.
## VALID LOGINS:
    
| First Name  | Last Name  | Badge Number | Misc |
|:---------------:|:---------------:|:---------------:|:---------------:|
| Jordan | Kelly | 123 ||
| Jael | Battana | 123 ||
| Chris | Javier | 123 ||
| Chris | Javier | 1234 | (length debug) |
| Christian | Javier | 123 ||
| 1 | 1 | 1 | (quick bypass) |
_________________________________________________________________________


I incorporated this by using a HTML form and some Javascript for input validation. The data itself is sent via POST and the badge number field is set to type="password" to treat it as though it is sensitive. What used to be index.html is now main.html and located with the other pages in ./config/pages/main.html

On the Javascript side of things (./config/js/logincode.js) you'll see a variable with the hashes loaded, this was not my preferred method of comparing the hashes, originally I was using a JSON file, but I was running into cross origin request issues. The CORS policies are there for a good reason and since we're not running a Node.js instance I cannot process JSON files, or at least that's my understanding. After that you'll find the function I use to hash the user input using SHA256. There is also a function for updating the user's concatenated name above the input fields, this is just a nice touch. After that is the actual validation, this function is called when the user presses submit.

The validation grabs the user input in the three fields, it outputs the concatenated name and length of the badge number in the console (in this fake scenario all badge numbers are 3 numbers long). It then gathers together what will be hashed, which is first, last and badge number all together with no spaces, sends it off to be hashed and then compares it to the list. If the hash matches it continues to the main page, if it doesn't then it will alert the user and not progress. This is insecure in its current implementation and is a proof of concept, you can simply open main.html directly if you wish.
___________

Accreditations				Page		Purpose
https://pqina.nl/flip/?ref=pqina	Game		Flip-counter plugin
