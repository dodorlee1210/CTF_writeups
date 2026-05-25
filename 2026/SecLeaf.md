# OSINT
## Can _you_Find_Cafe
> A single image holds all the clues you need. Study the surroundings carefully and identify the exact location where it was taken. Accuracy matters.
Use "_" instead of spaces. <br>
Flag Format: SecLeaf{Name_of_the_place+Location_name}
### Solution
* Google image search with the picture provided.
    * The search results showed a blog with a similar picture that described the exterior of a "Good Luck Cafe."
* I searched up Good Luck Cafe in Google Maps:
    * Its official name was "Cafe Goodluck."
    * Fergusson College Rd, near Goodluck Chowk, Deccan Gymkhana, Pune, Maharashtra 411004, India
* At first I thought the "loaction name" referred to Pune (city) or Maharashtra (state), but both were incorrect flags. After trying with different combinations, I saw the Discord for the specific flag format.
    * Like me, a lot of participants were confused about the format, I'm guessing beacuse not a lot were familiar with Indian addresses. 
    * I confirmed that the flag was **case insensitive** and it needs the **+** and saw that the full address was not needed.
* I gave Gemini the address, the name of the place, and the flag formats and the failed flag formats. Gemini right away gave me the correct answer: Deccan Gymkhana (neighborhood).
    * Gemini gave me a lesson on how CTF OSINT flags refer to "specific suburbs," but in my opinion, the flag should have been more specfic.
    * Anyways... at least now I know what each part of Indian addresses represent.
        * Goodluck Chowk was a bus station, which I thought was interesting to put as a part of the address.
### Flag
<details>
  <summary>Answer</summary>
  <b>SecLeaf{Cafe_Goodluck+Deccan_Gymkhana}</b>
</details>

# WEB
## Hidden_panel
> 
### Solution
* 
### What I Learned
* Status 301 = permanently moved
### Flag
<details>
  <summary>Answer</summary>
  <b>flag</b>
</details>

___

