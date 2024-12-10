# Documentation and Reporting

<h2>Description</h2>
In this phishing analysis task, I analyzed a phishing email attempt spoofing Amazon attempting to harvest user credentials through a malicious phishing link. I documented artifacts throughout my investigation to generate a report on my findings and actions taken to resolve this phishing attempt.  
<br />


<h2>Languages and Utilities Used</h2>

- <b>python IOC script</b>
- <b>URLScan</b>
- <b>Virustotal</b>


<h2>Environments Used </h2>

- <b>Unbuntu</b> 

<br />
<br />
LEFT: phishing email spoofing Amazon Prime Support. RIGHT: artifact documentation template provided by the exercise.

![1) left phishing email right documentation template](https://github.com/user-attachments/assets/93eae545-3adf-4059-ba7f-fb6d6be991a1)

<br />
<br />
First I filled out the description of the phishing attempt. 

![2) filled out description of email first](https://github.com/user-attachments/assets/5388569a-e94c-4c0b-92eb-1f6e9bc5a86c)

<br />
<br />  
Using a python IOC script from malwarecube (https://github.com/MalwareCube/Email-IOC-Extractor), I extracted the necessary header artifacts. However, Reseolve Host was still missing. 

![3) eioc python to filter headers from email](https://github.com/user-attachments/assets/afe22158-a96a-4ca0-a8b8-64d8df3b8dac)

<br />
<br />
I performed a reverse DNS lookup on the extracted X-Sender IP address and found the Resolve Host using DomainTools. 

![4) reverse dns lookup to find resolve host](https://github.com/user-attachments/assets/7ba58f12-8552-4379-89e4-f73b04ee6481)
c
<br />
<br />
The extraction provided a lot of URLS but the only relevant one contained a link to a domain containing "cabinet" when you hover your mouse over the "Go to your account" button in the email. I reran the IOC extraction script
and piped the output to grep out "cabinet." Only one URL remained in defanged format. 

![5) grep cabinet url that is linked with the button](https://github.com/user-attachments/assets/e0a463af-05c5-48e2-84f6-1ccff85119d6)

<br />
<br />
Entering the fanged url into URLScan did not yield a result.

![6) urlscan doesn't show up](https://github.com/user-attachments/assets/7c4feead-e1f1-4d3b-8483-ee90936db513)

<br />
<br />
However, virustotal showed 14 vendor flags for phishing for the malicious URL. 

![7) but virustotal shows as phishing](https://github.com/user-attachments/assets/3337508b-a51f-4081-941b-5885ab461d14)

<br />
<br />
I completed the rest of the documentation for Artifact Analysis, Verdict (I would include investigation screenshots in a ticket system), and Defensive Actions taken against the attempt. 

![8 completing the report](https://github.com/user-attachments/assets/d7335177-a86c-48ee-b981-dd69a34a989c)
<br />
<br />
