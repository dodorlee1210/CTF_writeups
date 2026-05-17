# OSINT
There were 5 challenges in total. I took around 3 hours on solving all of them.
I enjoyed these challenges quite a lot, because they were somehow related to each other, especially the Zoox one.

## It's not a car (easy)
> Identify the location shown in the top image at the link below.
<br> https://zoox.com/journal/resorts-world-las-vegas/
<br> Flag format: flag{latitude_longitude}
<br> Round down to the third decimal place and discard any digits after that.
<br> Example: flag{35.628_139.744}
<img width="2880" height="1620" alt="1748388387-four-people-waiting-for-a-zoox-robotaxi-at-resorts-world-las-vegas" src="https://github.com/user-attachments/assets/15c66282-c019-4d12-8b87-deeb694a4f23" />

### Observation
* The link was an article posted by Zoox on its partnership with Resorts World Las Vegas.
* The image was a picture of an entrance driveway.
### Solve
1) Searched "Resorts World Las Vegas" on Google Map; however, street view was limited to 2 entrance driveways.
<br>- I followed the street views for both driveways, but none of them had the same component as the image (a grey bar touching the pillars).

2) Searched "Resorts World Las Vegas Zoox" on Google Map.
I noticed it actually gave me a location that was right at an entrance where a street view was not provided, so right clicked for coordinates
### Flag
<details>
  <summary>Answer</summary>
  flag{36.134_-115.167}
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
* Now that I have a specific school name and region, I searched "grant elementary santa monica" on Google Map, which gave me 1 location.
* The pin was actually placed right in front of the crosswalk, so I right-cliked for coordinates.
### Flag
<details>
  <summary>Answer</summary>
  flag{34.0194_-118.462}
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
  flag{Highlander_5TDDGRFH0KS}
</details>

___

## Joby First Flight (easy)
## Joby 2025 Last Flight (med)
