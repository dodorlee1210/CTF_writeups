# OSINT
## Questionable Trip
> Every summer, BYU student LegoClones takes a trip somewhere in the world, for absolutely zero reason at all. Can you find where he took this picture?
> Flag Format: byuctf{} Example: byuctf{Costa_Coffee}

> <img width="1250" height="500" src="https://github.com/user-attachments/assets/5b5277dd-c40b-4ea4-ba8e-bcb7cba01b99" />
### Solution
* First did image search on Google.
    * Found out the name of the building on the other side of the river: Wat Arun
* On Google Maps, found Wat Arun and angeled it so it was the view as shown in the picture.
  * There was a placed labeled "Fotospot Wat Arun," so I zoomed in and there were low level buildings along the waterbed. I streetviewed one of the place moved my cursor around and I found the roof with tables and chairs and the same housing in the background.
> <img width="415" height="190" src="https://github.com/user-attachments/assets/f56d886a-686a-4524-95ca-7a6d4f108616" />

### Flag
<details>
  <summary>Answer</summary>
  <b>byuctf{Chom_Arun}</b>
</details>

___

## Hometown_Hero_1
> Last year, famed BYU student Cameron Snider tormented you all with his OSINT challenges. He thought it was at least midly amusing, and wants to do it again. Lets start with an easy one. What is the city and state (in America) that Cameron Snider grew up in? Format: byuctf{city:state} Example: byuctf{San_Francisco:California}

### Solution
* I assumed that since he is at BYU now, he must have moved for university, so I focused on finding high schools Cameron attended.
* Searched "cameron snider byu" on Google and found a LinkedIn account.
* It said he graduated Richmond High School (2017-2021). I searched Richmond High School the results showed it's located in Richmond, Indiana. However, the flag was wrong.
* I searched again for another Cameron Snider account online and found: https://www.linkedin.com/in/cameron-snider-a61101157/
* The account's profile said: Kearney High School, 2017-2021<br>

**Alternative**: Using Cameron Snider's Quora account
* While searching for another account I found this: https://www.quora.com/profile/Cameron-Snider-5
* I assumed it was the same Cameron Snider at BYU because the profile said they studied at the same high school as the first linkedin account.
* Scrolling down the profile, the 2nd comment (8y ago) is an answer to a person who asks moving to Kearney, Nebraska from CA. Cameron's answer is as if he has experience living there or moving from there.<br>

**Confusion**: so did Cameron Snider really study at both high schools? I feel like if this were to make sense, the years attended should have been different.
### Flag
<details>
  <summary>Answer</summary>
  <b>byuctf{Kearney_Nebraska}</b>
</details>

___

## Hometown_Hero_2
> That was pretty easy, right? Lets bump it up a notch. Can you tell me what Elementary School (https://en.wikipedia.org/wiki/Primary_school for the non-Americans) Cameron went to as a child? It shouldn't be too hard to figure out. Format: byuctf{School_Name} Example: byuctf{Wasatch_Elementary}
### Solution
* I tried searching with a combination of these keywords:
    * Kearney, Nebraska, Cameron Snider, elementary, school, primary school
* No direct answer came up, so I decided to brute force. Kearney is a city, so how many elementary schools can there be in that area? I think I wouldn't have done this if there were more than 25, but thankfully there were less.
* I searched "elementary schools kearney nebraska" and looking at the list Google Map had, I started putting the names in one by one. Near the end, one name was submitted as correct.<br>

**After the CTF**: I saw byuctf's writeup and tried following their solution, still nothing... at least they wrote that a small amount of brute forcing was needed.
### Flag
<details>
  <summary>Answer</summary>
  <b>byuctf{Park_Elementary}</b>
</details>

___

## Where in the World is Scott Dourque $\color{red}{\text{(SOLVED AFTER CTF ENDED)}}$
> We've been tracking international criminal Scott Dourque for months. Hes wanted on hundreds of counts of fraud for telling single mothers that he is the father of their baby and he needs "Father Support" money. We've built out a full portfolio on Scott, but we can't get a warrant for his arrest until we know exactly where he was, and what he was doing on April 12th, 2026. Maybe you can figure out where he was?
### Solution
* 
### Flag
<details>
  <summary>Answer</summary>
  <b>byuctf{st00pid_ass1stant}</b>
</details>

___

