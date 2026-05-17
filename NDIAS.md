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

## Joby First Flight (easy)
## Joby 2025 Last Flight (med)
