<details>
  <summary><h1>OSINT</h1></summary>
  
There were 5 challenges in total. I was able to solve 4.

## Data Centre Hijack
> Gibson has attacked one of the Data Center’s of a significant company. Before their server was hijacked, the employees managed to send a drone picture of the building. Your job is to identify the location of this data server and the company that owns it. The flag is in format: RMCTF{City-Country-Company}
<img width="1000" height="416" src="https://github.com/user-attachments/assets/5dd5f30e-7b95-4a9a-99bb-4b0c17060853" />

### Observation
* Very green, numerous solar panels, curved road
### Solution
* Searched "data centres solar panels" on Google Images and found an image that looked very similar to the given one.
> <img width="300" height="200" src="https://github.com/user-attachments/assets/3b9c894e-7534-4cd3-a30d-4ac6b92be53b" />
* Visited its website: [Positive energy: Belgian site becomes first Google data center to add on-site solar](https://sustainability.google/stories/belgium-solar/) which contained information on the data centre's location and company.
### Flag
<details>
  <summary>Answer</summary>
  <b>RMCTF{Saint-Ghislain-Belgium-Google}</b>
</details>

___

## AI or Real?
> An employee of the identified company (author of the picture from challenge 1) has recently reported an impersonator account stalking them on social media – we believe it may be Gibson posting AI versions of their posts. Using their real username: starring1367 can you find the fake account and the name of the event taking place in the picture of their most recent holiday. The flag is in the format: RMCTF{username-Event Name}
### Observation
* Impersonator account stalking an employee with username starring1367
### Solution
* Found the real account under username starring1367 on Instagram. Clicked on the Tagged Photo section which showed an account with username "starr0256".
    * _You cannot view the accounts or posts without being logged into Instagram yourself._
* Three posts: hotel, data centre, and a flowery place with a building.
> <img width="270" height="151" alt="1000033924" src="https://github.com/user-attachments/assets/5f1e46d8-60ff-489f-9b97-bff25a6f3905" />

* Since the the first image's location was at Belgium, I searched "flower holiday belgium" on Google. The results showed that it's called "Flower Carpet."
* I initially put the real username in the flag, but it was incorrect. After reading the challenge again, I realized it required the fake account's username.
### Flag
<details>
  <summary>Answer</summary>
  <b>RMCTF{starr0256-Flower Carpet}</b>
</details>

___

## Gibson makes a Mistake
> Gibson has disabled the employee account and is posting fake pictures of themselves at the AI-IM global summit 2026 - but they have made mistakes in each image of their event post leaving clues to their real location. Your job is to identify the country and region they are based in. The flag is in the format: RMCTF{Region-Country}
### Observation
*
### Solution
* 
### Flag
<details>
  <summary>Answer</summary>
  <b>RMCTF{Haute-Savoie-France}</b>
</details>

___

## Office Switching
> An IT company allowed Gibson to "optimise" their office locations. Your goal is to find the flag that shows where the Infrastructure team has been moved to. https://bluepeakcyber.co.uk/
<br> The flag is in the format of RMCTF{XXXXXXXXXXXX}
### Observation
* Infrastucture team moved
### Solution
* At first, I didn't really know how to solve this. I tried:
    * Looking at the html code of the given website (F12/right click).
    * Tried to get into differente directories by guessing certain words to go after the url end (e.g. /#infra).
    * Looked all over the website for hints.
    * Tried searching for social media accounts for "bluepeakcyber"
        * Found companies with similar names doing cybersecurity work, but seemed irrelevant to challenge.
* Then, I realized I hadn't looked at the DNS records. Since the hint was "moving infrastructure," they must have had to update/change where the domain name points.
    * I input bluepeakcyber.co.uk in Viewdns.info's DNS Record Lookup. There was a TXT record that hit the two factors: "optimization" and "infrastructure team."
> <img width="806" height="253" src="https://github.com/user-attachments/assets/367b5c77-48be-420a-a1b8-c0438479d0e4" />

  * I entered conventry.r032.bluepeakcyber.co.uk as the domain, and the results showed 1 TXT record with the flag as data.
### Flag
<details>
  <summary>Answer</summary>
  <b>RMCTF{DN5_1S_PUBLIC}</b>
  <br><br>
  <img width="911" height="435" src="https://github.com/user-attachments/assets/7512b8dd-01a9-4220-ab42-1c9cf832940a" />
</details>

___

## Mission: Find the Base $\color{red}{\text{(SOLVED AFTER CTF ENDED)}}$
> The what3words of the hotel location in the previously identified country have been hidden in the photo in the language of the country they are really based in. Your job is to identify the what3words of the location and the name of the hotel. The flag is in the format: RMCTF{///word.word.word-Hotel Name}
### Observation
* 
### Solution
* 
### Flag
<details>
  <summary>Answer</summary>
  <b>RMCTF{}</b>
  <br><br>
</details>
___
</details>

<details>
  <summary><h1>Forensics</h1></summary>
</details>
