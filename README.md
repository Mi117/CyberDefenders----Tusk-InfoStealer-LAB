# Cyberdefenders.org -- TUSK INFOSTEALER LAB

INTRODUCTION
This walkthrough covers the analysis of the Tusk Infostealer malware from the CyberDefenders challenge. The scenario involves a blockchain development company that fell victim to an attack after an employee was redirected to an unfamiliar website when accessing a DAO management platform. This led to cryptocurrency wallets being drained. Our analysis will uncover the attack methods, identify indicators of compromise, and track the threat actor's infrastructure.

WALKTROUGH

Let's begin by examining the malicious file to answer the first question.

Q1) What is the size of the malicious file?

To determine the file size, we need to examine the malware sample provided in the challenge. We head to VirusTotal and check the provided hash > Details and we can see the file is 921.36 KB (943472 bytes).

![q1](https://github.com/user-attachments/assets/8b03e5e0-4a03-49c7-a779-13b276b69e01)

Q2) What word does the threat actor use in log messages to refer to victims, drawing inspiration from ancient tusk hunters?

We will need to perform a more detailed research about the malware, and we can help ourselves by leveraging some widely available OSINT tools, such as Google search. 
To make the research more efficient, we can pair the search with the already published security vendors analysis, to eventually find the Kaspersky Global Emergency Response Team (GERT) has already published a comprehensive report about the Tusk infostealer. 

Link to the report: https://securelist.com/tusk-infostealers-campaign/113367/

![q2](https://github.com/user-attachments/assets/67c28cd3-b93b-4727-b0c0-a021e213ab77)

Analyzing the report, we discover that the threat actors refer to victims as "mammoth" in their log messages, drawing inspiration from ancient tusk hunters.

Q3) The threat actor set up a malicious website to mimic a platform designed for creating and managing decentralized autonomous organizations (DAOs) on the MultiversX blockchain (peerme.io). What is the name of the malicious website the attacker created to simulate this platform?

According to the Kaspersky report, three active sub-campaigns have been identified with a specific timeline (see below).

![q3](https://github.com/user-attachments/assets/cc25ea98-7a97-4484-bec0-534899896054)

The first sub-campaign is the simulation of the of a DAO platform on the MultiversX blockchain and the the malicious website created to mimic the legitimate peerme.io platform is "tydyme.io".

![q3-3](https://github.com/user-attachments/assets/11ba101b-86aa-4029-8f85-8db331047462)

Q4) Which cloud storage service did the campaign operators use to host malware samples for both macOS and Windows OS versions?

This campaign has several malware samples for macOS and Windows, both hosted on DROPBOX. 

Q5) The malicious executable contains a configuration file that includes base64-encoded URLs and a password used for archived data decompression, enabling the download of second-stage payloads. What is the password for decompression found in this configuration file?

![q5](https://github.com/user-attachments/assets/35ab444d-3cfc-4313-8d57-6714e37e716b)

Q6) What is the name of the function responsible for retrieving the field archive from the configuration file?

The function responsible for retrieving the field archive from the configuration file is downloadAndExtractArchive.

Q7) In the third sub-campaign carried out by the operators, the attacker mimicked an AI translator project. What is the name of the legitimate translator, and what is the name of the malicious translator created by the attackers?

In this campaign, the threat actor was simulating an AI translator project named YOUS. The original website is yous.ai, while the malicious website is voico[.]io

![q7](https://github.com/user-attachments/assets/d65f9d60-718f-4381-85fa-fddf1df5b15d)

Q8) The downloader is tasked with delivering additional malware samples to the victim’s machine, primarily infostealers like StealC and Danabot. What are the IP addresses of the StealC C2 servers used in the campaign?

![q8](https://github.com/user-attachments/assets/04121d3b-57db-4101-9715-e8825ed41e84)

Q9) What is the address of the Ethereum cryptocurrency wallet used in this campaign?

By examining the malware or related intelligence, we can identify cryptocurrency wallets used by the attackers to receive stolen funds.
The Ethereum wallet address used in this campaign is 0xaf0362e215Ff4e004F30e785e822F7E20b99723A

![q9](https://github.com/user-attachments/assets/d4ab66aa-9390-483d-af2e-f5c687c19286)

CONCLUSION

The Tusk Infostealer campaign represents a highly sophisticated and targeted threat to the blockchain and cryptocurrency sectors. This campaign, orchestrated by Russian-speaking cybercriminals, employs a range of advanced techniques to deceive victims and steal sensitive information.

Sophisticated Techniques
- Typosquatting and Phishing: The attackers use typosquatting to create fake websites that closely mimic legitimate services. These sites are designed to trick users into providing sensitive information or downloading malware. The campaign exploits popular themes such as Web3, cryptocurrency, artificial intelligence, and online gaming to lure victims.
- Cloud Storage for Malware Hosting: The campaign leverages cloud services like Dropbox to host initial downloader files. Once downloaded, these files facilitate the installation of additional malware on the victim's device, often without raising suspicion due to their user-friendly interfaces.
- Multi-Stage Delivery Mechanisms: The attackers employ complex, multi-stage delivery mechanisms to evade detection. This involves injecting malicious code into legitimate programs and communicating with command and control (C2) servers to download additional malware components.

- Targeting Cryptocurrency Credentials and Wallet Information: The primary focus of the Tusk campaign is to steal cryptocurrency credentials and wallet information. This allows the attackers to access and drain funds from compromised wallets, resulting in significant financial losses for victims.
- 
- Clipper Malware: The campaign also utilizes clipper malware, which monitors clipboard data. If a user copies a cryptocurrency wallet address, the malware substitutes it with a malicious address, further facilitating unauthorized transactions.

Evidence of Careful Planning
The Tusk campaign demonstrates meticulous planning and execution. The attackers have created a network of fake websites and malware delivery systems that are both convincing and sophisticated. The use of multiple sub-campaigns targeting different sectors, such as gaming and AI, indicates a well-organized operation with specific financial motives.

This campaign highlights the evolving threat landscape in the cryptocurrency and blockchain sectors. Its sophisticated techniques and targeted approach underscore the need for heightened vigilance and robust security measures to protect against such threats. As the campaign continues to evolve, it is crucial for organizations and individuals to remain informed and proactive in defending against these advanced cyber threats.

