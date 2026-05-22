## Slum Survey Photo
> A community mapping NGO published an aerial photograph of an informal settlement as part of an SDG 1 housing survey. The image was released publicly without a thorough review. Standard image viewers show nothing unusual. Not every tool that reads a file is an image viewer.

### Solution
*
### Flag
<details>
  <summary>Answer</summary>
  <b>flag</b>
</details>

___

## Microfinance IDOR
> A microfinance platform lets donors retrieve receipts for their contributions. Receipts are accessed through a public endpoint that takes a numeric ID. One hundred receipts were issued last cycle. One of them belongs to an internal audit account and contains a token it was never meant to expose. Track it down.

**Objective** <br> 
Find the receipt whose note carries the ADMIN_AUDIT_TOKEN. There are 100 receipts. Only one is interesting.

**Description** <br> 
KivaConnect's donor portal lets a logged-in donor pull receipts by ID. The ID column is sequential; nothing in the API checks who issued which receipt. A naive enumeration finds the audit token.

### Solution
*
### Flag
<details>
  <summary>Answer</summary>
  <b>flag</b>
</details>

___

## WelfareNet Admin
> The national welfare portal lets field caseworkers log in and access disbursement records. After a pentest last quarter flagged the authentication layer, management signed off on the report and closed the ticket without making changes. The portal is back online. The admin dashboard holds a disbursement integrity token that is not meant to leave the system. Your job is to get in.

**Objective** <br> 
Authenticate as the admin and read the disbursement integrity token from the dashboard.

**Description** <br> 
WelfareNet routes every login through a query the team wrote by hand against an in-memory roster. A penetration-test report flagged the login form last quarter — it has not been fixed.

### Solution
*
### Flag
<details>
  <summary>Answer</summary>
  <b>flag</b>
</details>

___

## Welfare Payments PCAP
> A whistleblower forwarded a packet capture taken from inside a national welfare payments gateway. The message broker handling disbursement traffic was running without encryption. Most of the traffic is routine operational chatter. One message published to the administrative channel carries something it should not. You will receive a .pcap file. A packet analyser such as Wireshark is a good place to start.

### Solution
*
### Flag
<details>
  <summary>Answer</summary>
  <b>flag</b>
</details>

___

## Cash Aid Routing
> A field logistics team needs to deliver emergency cash aid to twenty-five villages and return to the depot. Fuel is expensive and the operational budget has a hard ceiling. The platform accepts a proposed delivery order and measures the total route distance against a published threshold. Orders that exceed the threshold are rejected. Submit a route that fits within the budget.

**Objective** <br> 
Submit a tour of all 25 villages (returning to the depot) whose total distance is under the published threshold.

**Description** <br> 
The depot disburses cash to 25 villages each cycle. Edge costs are Euclidean over the published coordinates. The threshold is pegged about 10% above the nearest-neighbour heuristic; a single pass clears it.

### Solution
*
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

### Solution
*
### Flag
<details>
  <summary>Answer</summary>
  <b>flag</b>
</details>

___

## Slum Pinpoint
> A humanitarian mapping project released three photographs of informal urban settlements as part of an SDG 1 field study. Metadata was stripped before publication. Each image contains enough context to identify its location — signage, terrain, transit infrastructure, vegetation, and architectural patterns all leave traces. All three sites must be placed within five kilometres of their reference centroids to claim the flag.

**Objective** <br> 
Geolocate three EXIF-stripped photos to within 5 km of the reference point.

**Description** <br> 
A community mapping NGO published three aerial photos of informal settlements. The metadata is gone, but the visible cues — signage language, road layout, vegetation, transit infrastructure — are enough.

### Solution
*
### Flag
<details>
  <summary>Answer</summary>
  <b>flag</b>
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
