# UN SDG May 2026
This CTF was hosted by "Hack for a Change" team. It seemed to aim to train than test participatns in cybersecurity. None of the challenges were categorized (although the descriptions and artifacts made them explicit). It wasn't really capture the flag, but capture the logic to extract useful information. The flag was just given once the user typed in the required information and clicked on the "extract flag" button. Most of the challenges also "auto-extracted" the required info (e.g. authentication token, hash, etc.) once the user reached it, so there really wasn't much work to be done on that side.

One feature I would want them to add is theme toggles: light mode. The text was so hard for me to read that I had to print the website and read the light mode ver pdf to see certain placeholders or instructions.

## Slum Survey Photo
> A community mapping NGO published an aerial photograph of an informal settlement as part of an SDG 1 housing survey. The image was released publicly without a thorough review. Standard image viewers show nothing unusual. Not every tool that reads a file is an image viewer.

### Solution
* The artifact was a photo: Slum_Survey_Photo.png
<br>`exiftool Slum_Survey_Photo.png`<br>
`...`<br>
`Warning   : [minor] Trailer data after PNG IEND chunk`
* I know the IEND signature is: 00 00 00 00 49 45 4E 44 AE 42 60 82
    * A similar challenge existed in 0xV01D CTF.
* Created extract.py where I opened the png in 'rb' mode and located the beginning index of the trailer data (= the end of the IEND chunk) to write it out to a file.
* The trailer data was the flag.
### Flag
<details>
  <summary>Answer</summary>
  <b>SDG{6402be9d23bd6997ba5abbd00428cc19}</b>
</details>

___

## Microfinance IDOR
> A microfinance platform lets donors retrieve receipts for their contributions. Receipts are accessed through a public endpoint that takes a numeric ID. One hundred receipts were issued last cycle. One of them belongs to an internal audit account and contains a token it was never meant to expose. Track it down.

**Objective** <br> 
Find the receipt whose note carries the ADMIN_AUDIT_TOKEN. There are 100 receipts. Only one is interesting.

**Description** <br> 
KivaConnect's donor portal lets a logged-in donor pull receipts by ID. The ID column is sequential; nothing in the API checks who issued which receipt. A naive enumeration finds the audit token.

### Solution
* For this, I checked each id until I hit the one that showed me the token. I'm not really sure if there was a way I could have done it faster.
* I think it worked because the id = 18 when the site auto loaded the token, not too long before I started typing in all the ids.
### Flag
<details>
  <summary>Answer</summary>
  <b>SDG{c2c012f506d451318ff1cf2eefe4af0e}</b>
</details>

___

## WelfareNet Admin
> The national welfare portal lets field caseworkers log in and access disbursement records. After a pentest last quarter flagged the authentication layer, management signed off on the report and closed the ticket without making changes. The portal is back online. The admin dashboard holds a disbursement integrity token that is not meant to leave the system. Your job is to get in.

**Objective** <br> 
Authenticate as the admin and read the disbursement integrity token from the dashboard.

**Description** <br> 
WelfareNet routes every login through a query the team wrote by hand against an in-memory roster. A penetration-test report flagged the login form last quarter — it has not been fixed.

### Solution
> <img width="829" height="438" src="https://github.com/user-attachments/assets/cf4c40bc-28cb-4f6d-8c9e-82c10fc2f287" />
* After seeing that the username and password was concatenated 
### Flag
<details>
  <summary>Answer</summary>
  <b>SDG{c2c012f506d451318ff1cf2eefe4af0e}</b>

</details>

___

## Welfare Payments PCAP
> A whistleblower forwarded a packet capture taken from inside a national welfare payments gateway. The message broker handling disbursement traffic was running without encryption. Most of the traffic is routine operational chatter. One message published to the administrative channel carries something it should not. You will receive a .pcap file. A packet analyser such as Wireshark is a good place to start.

### Solution
* The pcap artifact contained transactions (welfare payments) and 3 audits that were different from all other packets.
* I used CyberChef to decode all three from hex and then base 64, and it turned out that the flag was hidden in the middle one.
### Flag
<details>
  <summary>Answer</summary>
  <b>SDG{06fe3b28c20af240faffa3f976ee7a97}</b>
  
  <br><img width="478" height="277" src="https://github.com/user-attachments/assets/ea47496e-f6cb-4b3d-9057-40cd8964fa55" /></details>

___

## Cash Aid Routing
> A field logistics team needs to deliver emergency cash aid to twenty-five villages and return to the depot. Fuel is expensive and the operational budget has a hard ceiling. The platform accepts a proposed delivery order and measures the total route distance against a published threshold. Orders that exceed the threshold are rejected. Submit a route that fits within the budget.

**Objective** <br> 
Submit a tour of all 25 villages (returning to the depot) whose total distance is under the published threshold.

**Description** <br> 
The depot disburses cash to 25 villages each cycle. Edge costs are Euclidean over the published coordinates. The threshold is pegged about 10% above the nearest-neighbour heuristic; a single pass clears it.

### Solution
* This
### Flag
<details>
  <summary>Answer</summary>
  <b>flag</b>
</details>

___

## Poverty Action Cipher
> Before retiring, a UN archivist encoded a 2030 poverty-reduction commitment three times and filed only the final output. The original document no longer exists. The encoding passes and their order are part of the public record. The keyword used in the second pass comes from SDG 1 terminology. The final pass uses a single-byte key derived from a well-known action verb. Recover the original commitment text.

**Objective** <br> 
Peel back three classical-crypto layers over an SDG 1 pledge. The innermost line carries the proof.

**Description** <br> 
A 2030-Agenda commitment file was encoded three times by an over-eager archivist who insisted on belt-and-braces "for posterity". The structure is well-documented; the decryption is left as an exercise.

1. Stage 1: a single classical substitution cipher over plain text. The cleartext is an excerpt of the SDG 2030 Agenda preamble.
2. Stage 2: hidden inside the stage-1 plaintext after "STAGE2: ". Polyalphabetic over the same alphabet; the crib word "DIGNITY" features prominently in the cleartext.
3. Stage 3: hidden inside the stage-2 plaintext after "STAGE3HEX: ", encoded as hex. Repeating-byte XOR with an 8-byte key. The plaintext is a declaration about the SDG 1 mandate.
4. The stage-3 plaintext contains "PROOF: <32 hex characters>". That value is the proof.

> RAQVAT CBIREGL VA NYY VGF SBEZF RIRELJURER ERZNVAF GUR TERNGRFG TYBONY PUNYYRATR SNPVAT GUR JBEYQ GBQNL NAQ NA VAQVFCRAFNOYR ERDHVERZRAG SBE FHFGNVANOYR QRIRYBCZRAG. FGNTR2: TDZNDZJ EA TLG NFCVG BZOYWN BS AUFDYTTDUYQG. PE KRPTBX TCGE DJ HNZ CTBG UE GKQJ WXHDTO. IOTGZ3NPN: 1v295y35bxgqr4aw1a5w5h29l1rzu0e41v5h4p3uv3t9a7aj065m583uv7vcw4k5135m4u34wtbxh9ps7a3x4834a7w5g2p11q295w51u7b5y5lo08343u25wwa3v0ll1u355v51t1a4wiqr0w223051t5bzhlu619413z44v08f91xl69497m47s3y9vc9y391k2p1493t4x49y3918781491dv90iq3q187x
### Solution
**STAGE 1**
* I used a frequency analysis website, since it said "substitution cipher."
* Instructions for stage 2 gives a massive hint, "stage-1 plaintext after STAGE2:"
   * I should have known this was ROT13 as soon as I saw that R = E, but I didn't realize this until the end...
* Result: ENDING POVERTY IN ALL ITS FORMS EVERYWHERE REMAINS THE GREATEST GLOBAL CHALLENGE FACING THE WORLD TODAY AND AN INDISPENSABLE REQUIREMENT FOR SUSTAINABLE DEVELOPMENT. STAGE2:

**STAGE 2**
* I used dcode.fr/vigenere-cipher, since instructions for stage 2 states it was polyalphabetic.
* For the decryption method, I selected knowing a plaintext word and input "DIGNITY," also given in the instructions.
* Result: DIGNITY OF ALL HUMAN BEINGS IS FOUNDATIONAL. WE PLEDGE THAT NO ONE WILL BE LEFT BEHIND. STAGE3HEX: 1a295f35bcafb4fd1a5b5b29a1beb0e41a5b4e3ea3a9a7fd065b583ea7ccb4e5135b4e34babcb9ec7f3e4834a7b5a2e11a295b51b7b5d5fd08343e25bda3a0fa1e355a51a1a4bcfb0b223051a5bebae619413e44c08f91cf69497b47c3d9cc9d391e2e1493d4c49f3918781491da90cf3a187c

**STAGE 3**
* This part took a long time, because I wasn't sure how to find the key for XOR. I saw the hint which said the key was the first 8 bytes of the hash of a verb already given in the cleartext.
* I tried MD5, SHA1, SHA256 hashes of verbs such as "pledge, left, remains, ending, and facing" as keys on CyberChef. NONE worked.
* I decided do use dcode.fr/xor-cipher to bruteforce it since CyberChef was going to take an awful long time. (Next time, I'll do this first...)
* For the decryption method, I selected knowing the key size (in bytes) and input 8. As soon as I hit decrypt, the correct answer showed up.
* Result: 5f7b1e71f5ecf5a9	ERADICATE EXTREME POVERTY FOR ALL PEOPLE EVERYWHERE BY TWO THOUSAND THIRTY. PROOF: 55cdf62e66594fe0ef816fcfed6efecb
   * I really wanted to know what the verb was so I checked what it was using crackstation.net. It turned out the word was "eradicate" hashed in sha256. BUT eradicate is in the cleartext for stage 3, so... the hint was misleading.
   * Additionally, SHA256 is case-sensitive. So, if I thought the key was in all caps (like "DIGNITY" or all the other cleartexts), then it also would have not worked, too.
   * To be fair, the [SDG 1 Mandate Declaration] (https://www.un.org/sustainabledevelopment/poverty/) mentioned in the instruction for stage 3 does write "eradicate" in lowercase:
        > 1.1 By 2030, eradicate extreme poverty for all people everywhere, currently measured as people living on less than $2.15 a day
### Flag
<details>
  <summary>Answer</summary>
  <b>SDG{b718e35dccb046aacae9d2c4a251342c}</b>
</details>

___

## Slum Pinpoint
> A humanitarian mapping project released three photographs of informal urban settlements as part of an SDG 1 field study. Metadata was stripped before publication. Each image contains enough context to identify its location — signage, terrain, transit infrastructure, vegetation, and architectural patterns all leave traces. All three sites must be placed within five kilometres of their reference centroids to claim the flag.

**Objective** <br> 
Geolocate three EXIF-stripped photos to within 5 km of the reference point.

**Description** <br> 
A community mapping NGO published three aerial photos of informal settlements. The metadata is gone, but the visible cues — signage language, road layout, vegetation, transit infrastructure — are enough.

**Given Context** <br>
**A:**
* Dense low-rise rooftops crowding a peninsular landform.
* Signage in Devanagari script alongside English on a small storefront.
* A wide saltwater inlet borders the western edge; a major rail bridge runs north–south on the east.
* Monsoon-belt vegetation; tropical climate.

**B:**
* Hilly East African terrain with deep red-brown soil between corrugated-iron rooftops.
* Signage in Swahili and English. One advertisement reads Maziwa Fresh.
* A single-track railway line cuts diagonally across the settlement, fenced on both sides.
* Acacia and jacaranda trees scattered through the upper slopes.

**C:**
* Hillside favela facing the South Atlantic; rooftops stacked vertically up a steep ridgeline.
* Portuguese signage; one mural reads PAZ NA COMUNIDADE.
* A multi-lane elevated highway threads along the foot of the hill.
* Beach umbrellas visible in the distance to the east.
### Opinion
I was perplexed with the point of this challenge as I couldn't find the exact coordinates with the visible cues provided. I am guessing this was more about a region that specific places, since it accepted coordinates of sites that are within 5 km of the referene centroids?
* Was this to illustrate that informal urban settlements are hard to find...?

For Photo B, I even took the time to locate the exact coordinates (where distances_km = 0) and searched it up on Google Maps which didn't support street view. I viewed the street right beside it, but I saw no signage or advertisement that reads "Maziwa Fresh."
* The only one that I could "see" was the first cue that stated "deep red-brown soil between corrugated-iron rooftops"
* Even considering that this was supposed to locate "slums," it was weird because Google Maps showed a region with different coordinates for the actual [Kiberia Slum](https://www.google.com/maps/place/Kibera+slum,+Nairobi,+Kenya/@-1.3143716,36.7910483,14z/data=!3m1!4b1!4m6!3m5!1s0x182f107c96b535fb:0xfe6eeeb2de675724!8m2!3d-1.3122173!4d36.7913757!16s%2Fg%2F1vx70tps?entry=ttu&g_ep=EgoyMDI2MDUyMC4wIKXMDSoASAFQAw%3D%3D).
### Solution
* The visible cue sentences were not "copy-able" and a part of Photo A was cut off due to no line wrap.
* I opened the provided images in another tab and copied & pasted the texts into Gemini to find the general regions.
* For Photo A, Gemini gave me Churchgate in India.
    * The area was quite populated with dense low-rise rootftops. I tried to find a land mass with saltwater borders on the west with a major rail bridge on the east, but every coordinate I found did not get significantly closer to the centroid.
    * I continuously modified coordinates to derease distances_km, and got down to 1.81, but I was so lost by then. I looked it up on Google Maps, and it was at a foresty swamp place. I tried inputting some viable ones near the low-rise rooftops, but all of them ended up increasing the distance to the centroid.
    * Final Answer: 19.0531, 72.8599
* For Photo B, Gemini gave me Kiberia in Nairobi.
    * I took some time to find the exact coordinates the website wanted by entering numbers and checking if the distances_kim had decreased
    * Final Answer: -1.3133, 36.7891
* For Photo C, Gemini gve me Rocinha in Rio de Janeiro.
    * I checked its Google Maps coordinates, and it was within 0.26 km.
    * Final Answer: -22.9879, -43.2479
### Flag
<details>
  <summary>Answer</summary>
  <b>SDG{a416253846fac9d163ee9701f979c59c}</b>
</details>

___

## Stipend Validator
> A student stipend programme runs a self-service redemption portal. You enter a code, the page validates it, and a token is returned on success. No request is sent to the server during validation — the check runs entirely in your browser. The development team ran the bundle through an obfuscator before shipping. The logic is still present in the source. Find the code the validator accepts.

**Objective** <br> 
Reverse the obfuscated client-side validator, recover the stipend code, and POST it back to the server.

**Description** <br> 
The redemption check runs entirely in your browser. The bundle has been put through an obfuscator pass but the validator's two state arrays remain in plain literal form.

### Solution
*
### Flag
<details>
  <summary>Answer</summary>
  <b>flag</b>
</details>

___

## Cash Transfer Forge
An emergency cash-transfer programme issues personalised certificates to beneficiaries. A caseworker enters a recipient name, and the platform generates a signed document on the fly using an in-house template engine. One of the developers left a convenience helper attached to the rendering context during a late-night build sprint. It was documented internally as useful for debugging and never removed. A redeemable forge banner is waiting inside the system.

**Objective** <br> 
Exfiltrate the FORGE_BANNER from the certificate template engine and trade it at /forge for the proof.

**Description** <br> 
The recipient name field on this prototype generator runs through a micro-template engine the team prototyped in a hackathon. They left a debug helper on the rendering context "for testing", and the on-call sysadmin documented the exposed process.env for variable lookup. Nothing was hardened before deployment.

### Solution
*
### Flag
<details>
  <summary>Answer</summary>
  <b>flag</b>
</details>

___

## Aid Agency Mirror
> An international aid agency runs a supplier health-check tool that fetches status pages on behalf of procurement officers. Requests to internal infrastructure are blocked by an allowlist enforced through a custom URL parser written in-house. The fetch itself is handled by the platform's standard HTTP stack, which parses URLs by a different specification. The internal credentials vault is not on the allowlist.

**Objective** <br> 
Reach the internal credentials vault at /internal/secrets and lift the audit token.

**Description** <br> 
The supplier health checker enforces an allowlist of partner hostnames. The check uses a regex-based "host" extractor; the actual fetch uses a real URL parser. The two disagree on URLs that carry userinfo.

### Solution
*
### Flag
<details>
  <summary>Answer</summary>
  <b>flag</b>
</details>

___
