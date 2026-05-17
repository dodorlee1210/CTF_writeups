# OSINT
There were 5 challenges in total. I took around 3 hours on solving all of them.
I enjoyed these challenges quite a lot, because they were somehow related to each other, especially the Zoox one.

## It's not a car (easy)
> Identify the location shown in the top image at the link below.
<br> https://zoox.com/journal/resorts-world-las-vegas/
<br> Flag format: flag{latitude_longitude}
<br> Round down to the third decimal place and discard any digits after that.
<br> Example: flag{35.628_139.744}
<img width="341" height="201" alt="1748388387-four-people-waiting-for-a-zoox-robotaxi-at-resorts-world-las-vegas" src="https://github.com/user-attachments/assets/15c66282-c019-4d12-8b87-deeb694a4f23" />

### Observation
* The link was an article posted by Zoox on its partnership with Resorts World Las Vegas.
* The image was a picture of an entrance driveway.
### Solve
1) Searched "Resorts World Las Vegas" on Google Maps; however, street view was limited to 2 entrance driveways.
<br>- I followed the street views for both driveways, but none of them had the same component as the image (a grey bar touching the pillars).

2) Searched "Resorts World Las Vegas Zoox" on Google Maps.
I noticed it actually gave me a location that was right at an entrance where a street view was not provided, so right clicked for coordinates
### Flag
<details>
  <summary>Answer</summary>
  <b>flag{36.134_-115.167}</b>
</details>

___

## AV Striking (med)
> Identify the location where the incident described in the document occurred.
<br> Document: https://static.nhtsa.gov/odi/inv/2026/INOA-PE26001-10005.pdf
<br> Flag format: flag{latitude_longitude}
<br> Round down to the third decimal place and discard any digits after that.
<br> Example: flag{35.628_139.744}
### Observation
* US Department of Transportation, Investigation PE26001
* Subject: Waymo AV striking a child in the area of a school
* Summary: ... within 2 blocks of a Santa Monica, CA elementary school
### Solve
* I Google searched "waymo av santa monica elementary" based on the observed data. Resulting AI overview said it was "reported as Grant Elementary."
* Now that I have a specific school name and region, I searched "grant elementary santa monica" on Google Maps, which gave me 1 location.
* The pin was actually placed right in front of the crosswalk, so I right-cliked for coordinates.
### Flag
<details>
  <summary>Answer</summary>
  <b>flag{34.0194_-118.462}</b>
</details>

___

## Unexpected Braking (hard)
> In 2024, an automated driving system drew public attention because unnecessarily harsh braking was found to increase the risk of collisions. Investigate the publicly available documents related to this case and identify the vehicle model and the first 11 characters of the VIN No. If there is more than one applicable vehicle, any of them may be used as the flag.
<br> Flag format: flag{Model_VIN11digits}
<br> The VIN must be written in uppercase.
<br> Example: flag{Corolla_ABCDEFG0123}
### Observation
* 2024, automated driving system, harsh braking increases risk of collisions
### Solve
* I searched "2024 automated driving system unnecessarily harsh braking collision incident investigation" on Google. This prompt showed very recent incidents or investigations (2025-2026).
* I prompted Gemini with the challenge description. The response gave me useful info:
  * Zoox Automated Driving System (ADS)
  * PE24015
  * https://www.vitallaw.com/news/nhtsa-news-odi-investigation-odi-to-probe-zoox-vehicles-for-risk-of-unexpected-braking/
    * In this link I found the link to the PE24015 pdf file: https://business.cch.com/plsd/PE24015open.pdf
        * In this file, I saw that 2 cases happened in 2024, both involving Toyota Highlanders with Zoox ADS causing rear-end collisions.
        * I read the SGO files listed in the PE24015 file. I also looked into Toyota Highlander recalls in 2024 in the official NHSTA website. No VIN numbers were to be found. **Dead-End**
* Reading over the challenge again, I realized it was pointing to a specific case.
  * I started searching for the 2 incidents mentioned the PE24015 file: "Toyota zoox rear-end collision"
  * I found a reddit post with information on where one of the cases happened (= Menlo Park) and a link to its incident report, but I found no VIN.
       * https://www.reddit.com/r/SelfDrivingCars/comments/xb6766/zoox_had_an_injury_crash_in_menlo_park_on_august/
       * https://www.dmv.ca.gov/portal/file/zoox_082322-pdf/
  * I thought if I searched with more detailed context, more information may exist: "menlo park toyota zoox rear-end crash"
      * I found an article that had a link to a document of the 2nd case.
      * The 2nd case file was redacted, but had all necessary info the challenge required.
      * I copied and pasted to VIN, but apparently, the pasted version had a 0 automatically converted to an O. Took me a few minutes to figure out why the flag was incorrect XD.
### Flag
<details>
  <summary>Answer</summary>
  <b>flag{Highlander_5TDDGRFH0KS}</b>
</details>

___

## Joby First Flight (easy)
> Where was Japan's first test flight of a "flying car" conducted? Answer with the heliport identifier.
<br> [Joby Conducts First Test Flight in Japan](https://www.youtube.com/watch?v=CPD5fH_DJmY)
<br> The heliport identifier must be the registered identifier in the following site, in the format JP-XXXX: https://ourairports.com/
<br> Flag format: flag{JP-XXXX}
### Observation
* Video posted by Toyota
* Title has "in Japan" + heliport identifier's JP
### Solve
* I searched "joby first flight location," but showed California or international locations.
* Tried specifying country by searching"joby first flight location japan" and found an article: https://www.santacruzworks.org/news/jobyfirstflightjapan
    * The link contained info on where the flight took place: "... took placce at Toyota Higashi-Fuji Technical Center at Shizuoka, Japan"
* Searched "Toyota Technical Center Higashi-Fuji" on ourairports, but yielded no results. Re-searched as "Higashi-Fuji Technical Center" which gave one heliport.
### Flag
<details>
  <summary>Answer</summary>
  <b>flag{JP-3604}</b>
</details>

___

## Joby 2025 Last Flight (med)
> Where was Joby's final international flight demonstration of 2025 held? Answer with the OpenStreetMap Way ID of the location where the aircraft took off and landed during the demonstration.
<br> Flag format: flag{123456789}
### Observation
* Joby's final international flight of 2025.
* Challenge wants the way id of where the aircraft took off and landed.
### Solve
*  I searched "joby last flight" and found an article that stated it took place on **Fuji Speedway**.
*  Hoping for a video, like the challenge above, I searched "joby's last flight," then "joby's last flight fuji speedway."
    * Found a video: [The Future of Flight is Here | Joby Flies at Mt. Fuji
](https://www.youtube.com/watch?v=7rvvvEJpPig)
        * Last 15 seconds of video shows where it landed in wideshot/fullshot
<img width="342" height="201" alt="스크린샷 2026-05-15 181433" src="https://github.com/user-attachments/assets/91d5ff2e-7868-4c2e-8d6a-f861fb707ec9" />

* **Observation**
    * A white building in distance, 2 big asphalted area, a grandstand? (wasn't sure) in distance.
* Looking at Fuji Speedway area on Google Maps in satellite mode, I figured out the structures were: a hotel and a grandstand.
* I used mobile Google Maps on satellite mode to angle it to have the same view as the screenshot above.
* While zooming out, a  unique circuit shape and two big ashphalted areas with a strip of grass in between near it caught my eye. It looked very similar to the one in the screenshot above.
<img width="180" height="330" alt="1000033918" src="https://github.com/user-attachments/assets/28a97efd-4034-4bf4-ac82-86ff63d3b20e" />
<img width="180" height="250" alt="1000033920" src="https://github.com/user-attachments/assets/f49c4d9d-4f6b-43fd-a095-db7207e825fb" />

* On OpenStreetMap, I first changed the layer to standard, then located the spot based on the landscape I saw on Google Maps labeled P1.
* To get the way id, I selected "query/?" and clicked on P1.

### Flag
<details>
  <summary>Answer</summary>
  <b>flag{593469861}</b>
  <br><br> <img width="958" height="534" alt="스크린샷 2026-05-15 183406" src="https://github.com/user-attachments/assets/6ec03794-d0aa-4e52-86bd-abe6089650ca" />
</details>
