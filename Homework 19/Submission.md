## Unit 19 Homework: Protecting VSI from Future Attacks

### Scenario

In the previous class,  you set up your SOC and monitored attacks from JobeCorp. Now, you will need to design mitigation strategies to protect VSI from future attacks. 

You are tasked with using your findings from the Master of SOC activity to answer questions about mitigation strategies.

### Part 1: Windows Server Attack

Note: This is a public-facing windows server that VSI employees access.
 
#### Question 1
- Several users were impacted during the attack on March 25th.
- Based on the attack signatures, what mitigations would you recommend to protect each user account? Provide global mitigations that the whole company can use and individual mitigations that are specific to each user.

Answers:
- An attempt was made to reset an account password
   295 events were normal
   2218 events were attack.

Thi can be overcome by setting a minium time for password attempt, user account should be locked out after five faile attemps and making sure only admin has the rights to interevent. Allowing 24hrs to reset the password makes more
A global migitation strategy can be implemented to enable MFA (Multi Factor Authentication) for logins and password reset.
  
#### Question 2
- VSI has insider information that JobeCorp attempted to target users by sending "Bad Logins" to lock out every user.
- What sort of mitigation could you use to protect against this?

- Answer:
 As described above implementing password policiy like MFA can prevent form DDOS attacking and locking the account.
  

### Part 2: Apache Webserver Attack:

#### Question 1
- Based on the geographic map, recommend a firewall rule that the networking team should implement.
- Provide a "plain english" description of the rule.
  - For example: "Block all incoming HTTP traffic where the source IP comes from the city of Los Angeles."
- Provide a screen shot of the geographic map that justifies why you created this rule. 

Firewall Rule: This will block all the incoming HTTP traffic coming from Source IP from the city of Los Angeles.
  
#### Question 2

- VSI has insider information that JobeCorp will launch the same webserver attack but use a different IP each time in order to avoid being stopped by the rule you just created.

- What other rules can you create to protect VSI from attacks against your webserver?
  - Conceive of two more rules in "plain english". 
  - Hint: Look for other fields that indicate the attacker.

Forewall Rules:
 Block all the incoming HTTP traffic from dource HTTP Method is POSTVSI_Account_logon.php HTTP/1.1
 Block all the incoming HTTP traffic where the source User-Agent is Mozilla/4.0 (compatible; MSIE 6.0; Window NT 5.2; SV1; .NET CLR 2.0.50727987787; InfoPath.1)
  


---

© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.
