
<h5 align="center">
  <code>
    <a href="https://www.linkedin.com/in/dheerajtechnolegends/" title="LinkedIn Profile"><img height="22" width="22" src="https://github.com/Dheerajmadhukar/Dheerajmadhukar/blob/main/img/linkedin.svg"> LinkedIn</a></code>
  <code><a href="https://twitter.com/Dheerajmadhukar/" title="Twitter Profile"><img height="22" width="22" src="https://github.com/Dheerajmadhukar/Dheerajmadhukar/blob/main/img/twitter.svg"> Twitter</a></code>
  <code><a href="https://www.instagram.com/me_dheeraj/" title="Instagram Profile"><img height="22" width="22" src="https://github.com/Dheerajmadhukar/Dheerajmadhukar/blob/main/img/instagram.svg"> Instagram</a></code>
  <code><a href="https://www.twitch.tv/techn0legends"><img alt="Twitch" title="Twitch" height="22" width="22" src="https://github.com/Dheerajmadhukar/Dheerajmadhukar/blob/main/img/twitch.svg"> Twitch</a></code>
  <code><a href="https://www.youtube.com/c/DheerajMadhukar"><img alt="YouTube" title="YouTube" height="22" width="22" src="https://github.com/Dheerajmadhukar/Dheerajmadhukar/blob/main/img/youtube.svg"> YouTube</a></code>
</h5>
<br>

<h3 align="center"> <strong>__Business Logic Attacks__</strong> </h3>

## >__ Basics 🤓
<p>“Users can only access authorized information and operations and are enforced to follow the intended workflow provided by the web application”</p>

## >__ Table of Contents
1. [Abusing Workflows](#Abusing-Workflows)
2. [Exploit Policies and Practices](#Exploit-Policies-and-Practices)
3. [Induction](#Induction)
    - [Authentication parameters and privilege escalation](#Authentication-parameters-and-privilege-escalation)
    - [Critical Parameter Manipulation and Access to Unauthorized Information/Content](#Critical-Parameter-Manipulation-and-Access-to-Unauthorized-Information/Content)
    - [Developer’s cookie tampering and business process/logic bypass](#Developer’s-cookie-tampering-and-business-process/logic-bypass)
    - [File or Unauthorized URL Access and Business Information Extraction](#File-or-Unauthorized-URL-Access-and-Business-Information-Extraction)
4. [Repetitive Attacks](#Repetitive-Attacks)
5. [Insecure design patterns and implementation of business logic](#Insecure-design-patterns-and-implementation-of-business-logic)
    - [Lack of Authorization Checks](#Lack-of-Authorization-Checks)
    - [Improper data sanitization](#Improper-data-sanitization)
    - [Unverified state mechanism](#Unverified-state-mechanism)
    - [Vulnerability by association](#Vulnerability-by-association)
    - [Process timing attack](#Process-timing-attack)
    - [Identity or Profile Extraction](#Identity-or-Profile-Extraction)
7. [Methodology for Attacking Business Logic Vulnerabilities In Web Application](#Methodology-for-Attacking-Business-Logic-Vulnerabilities-In-Web-Application)
    - [Profiling phase](#Profiling-phase)
    - [Analysis phase](#Analysis-phase)
    - [Test/Attack phase](#Test/Attack-phase)
    - [Evaluation phase](#Evaluation-phase)
 
8. [Web Server Basics](#Web-Server-Basics)
9. [Computing Fundamentals](#Computing-Fundamentals)
10. [Hacking Basics](#Hacking-Basics)

##

## 1. <u>Abusing Workflows</u> :
[For example, in the normal workflow of an application from A to B to C, an attacker to skip the straight line from A to C or go back to A from C]

>•&emsp;Changing requests in a code path from HTTP POST to GET or vice versa

>•&emsp;Going through steps out of order or skipping steps that will normally verify or validate an action or information

>•&emsp;Repeating a step or series of steps

>•&emsp;Performing an unexpected action

## 2. <u>Exploit policies and practices</u> :

e.g , the attackers exploited a business policy of “one vote equals one person” because the website had no rate limit, authentication nor validation mechanism.

## 3. <u>Induction</u> : 

Information provided within the code and behavior of the web application

>•&emsp;It is possible for an attacker to carry out some form of induction from suspicious easily guessable/predictable parameter 	names and predict, forge or manipulate legitimate requests

>•&emsp;Parameter names in most HTTP GET and POST requests in the form of name/value pairs, XML, JSON or Cookies are guessable, predictable and can be tampered with, as a result.

>•&emsp;Sometimes, this may require a combination of logical guessing, brute-forcing and creative tampering to decipher the logic

  #### a) <u>Authentication parameters and privilege escalation</u>:
   
>•&emsp;Applications can manage access control lists and privileges, any authenticated user has access to some internal parts of the application
	
>•&emsp;if authorization implementation is weak, it could likely include problems such as accessing another user’s account or acquiring greater permissions than what was originally assigned at login
   	
>•&emsp;if an application passes ACLs as cookies at time of authentication, this information can be tampered and exploited, A certain parameter becomes a target if the parameter name suggests ACL or permissions
   	
>•&emsp;The target value is now evaluated, predicted and tampered
   	
>•&emsp;The value to be tampered may be hex, binary, string, etc and tampering can involve changing bit patterns (1 to 0) or permission flags (Y to N, R to W)

  #### b) <u>Critical Parameter Manipulation and Access to Unauthorized Information/Content</u>:

>•&emsp;When the business logic of an application is processing parameters such as name-value pairs (which are guessable and can be tampered with), without proper validation, this allows a malicious user to perform unauthorized functions
	
>•&emsp;e.g : An application, after authentication, allows the user to request authorized functions and while making these requests, some parameters are being supplied to the application such as the “accountid” parameter. If this parameter is easily guessable, then an attacker can successfully inject another user’s accountid
	
>•&emsp;If the application does not do a validity check to map the existing session to the original logged in account, then another user’s information gets disclosed e.g : A similar example is the "domain.tld" privilege escalation case where the "PIN" parameter was visible in an `<iframe>` tag. Guessing another user’s PIN was enough to get into that user’s account without proper validation.
	
#### c) <u>Developer’s cookie tampering and business process/logic bypass: [ Response Manipulation ]</u>:

>•&emsp;This is an easy way to create a logical bypass to perform functions ordinarily not open to the malicious user

>•&emsp;When authentication occurs, to maintain the state over HTTP the developer may decide to set cookies in the browser. This way, the cookies can be tampered while it is being passed to, for example, upgrade membership from silver to platinum

#### d) <u>File or Unauthorized URL Access and Business Information Extraction</u>:

>•&emsp;If export functionalities are not implemented carefully, it can enable asset leakage from features in the business application

>•&emsp; Files could either be fetched directly from URL or by using internal parameters

>•&emsp;For example, if a transaction document requested is made available by a temporary link, an attacker could learn the naming convention and guess possible other documents if there are no proper authorization checks


## 4. <u>Repetitive Attacks</u>: 

>•&emsp;Many features if not implemented correctly can lead to a condition where an attacker can identify and exploit a loophole leading to infinite loops in the application layer

>•&emsp;BLBs [Business Logic Bots] have been commonly used in brute forcing an application to obtain login credentials and DOS [denial of service] to lock resources or web spam through forum posting

## 5. <u>Insecure design patterns and implementation of business logic</u>: 
#### &emsp;a) <u>Lack of Authorization Checks</u>:
		
>•&emsp;When there are not enough or no user action validation against a privilege table to make sure the user is allowed to perform any function, (for example, if checks are performed only at the beginning/login), this poses a huge vulnerability that can be easily exploited

>•&emsp;A similar authorization problem has to do with incorrect privilege assignments where a user may have conflicting access levels or obtain a higher access level only by manipulating parameter values.

#### &emsp;b. <u>Improper data sanitization</u>:

>•&emsp;In order to combat against syntax attacks, a developer might decide to implement a blacklist filter that strips SQL related words or other typical attack words

>•&emsp;Another is a nonrecursive application of blacklisted parameters. Most times the check is done once and an attacker can outsmart this by embedding the blacklisted word in a duplicate blacklisted word [As multiple parameters OR parameter pollution]
	
#### &emsp;c. <u>Unverified state mechanism</u>:

>•&emsp;The client must be treated as an adversary and the server must not stick to the assumption that the client browser will enforce the sequential steps or prevent repetition of steps as business logic attacks are very similar to legitimate traffic

>•&emsp;Thus if all incoming requests are not verified by the server, an attacker will take advantage of this to perform a wide variety of logical attacks

#### &emsp;d. <u>Vulnerability by association</u>:

>•&emsp;With the growing complexity of web applications tailored to meet business needs, there may arise the need to incorporate new tools, third party components or interact with other complex web applications

>•&emsp;All these interactions expose the application to logical vulnerabilities as integrated components or web applications may contain vulnerabilities in it

#### &emsp;e. <u>Process timing attack</u>: 
	
>•&emsp;This type of attack can be carried out by being able to guess or predict the web applications behavior based on input or output timing	

>•&emsp;This can be exploited to circumvent business logic by not completing transactions in a timely manner or carry out RACE CONDITIONS typical in applications dealing with money or credits

>•&emsp;The Starbucks race condition hack was used to process a transfer of $500 twice and at the same time to receive $1000 at the other end
	
#### f. <u>Identity or Profile Extraction</u>:

>•&emsp;Poorly designed applications may allow an attacker to identify token parameters that relate directly to a particular user providing an opportunity for abuse and exploitation through harvesting of this information

>•&emsp;This is critical in applications holding sensitive information such as user’s name and account information embedded in parameter values


## * METHODOLOGY FOR ATTACKING BUSINESS LOGIC VULNERABILITIES IN WEB APPLICATIONS *

### The methodology is divided into 4 phases:
&emsp;&emsp;**1. Profiling phase** <br>
&emsp;&emsp;**2. Analysis phase** <br>
&emsp;&emsp;**3. Test/Attack phase** <br>
&emsp;&emsp;**4. Evaluation phase** <br>

***MIND MAP: [METHODOLOGY FOR ATTACKING BUSINESS LOGIC VULNERABILITIES IN WEB APPLICATIONS]***

• [mindmap tweet](https://twitter.com/Dheerajmadhukar/status/1453298893052121115/photo/)

• [raw image](https://pbs.twimg.com/media/FCsnobrXMAsYsV0?format=jpg&name=4096x4096)


### &emsp;1. <u>Profiling Phase</u>:

>•&emsp;The purpose of profiling is to attempt to create a complete picture of the content, components, function, tools, policies and flow of the web application in order to gain information for further analysis

>•&emsp;This will involve proper inspection which will reveal more about the site without documentations provided from the organization

#### &emsp;&emsp;a. <u>Web crawling</u>:
	
>•&emsp;Web crawling is an absolute necessity to create a knowledge-baseline for attacks and this spares a ton of labor

>•&emsp;Web crawling also provides a locally cached copy of the web application components including static pages, executables, forms, and so on...

>•&emsp;While also providing a snapshot of the web application (snapshots easily reveal naming conventions for directories parameters and files).
	
#### &emsp;&emsp;b. <u>Manual inspection</u>:
	
>•&emsp;This can be done by simply clicking through the application to become familiar with the website and its available source code

>•&emsp;This can be done to augment the shortcomings of automatic crawling activity which include forms requiring human interaction, complex flows, source code inspection and broken links assessment

>•&emsp;Information from FAQs, policies, terms and conditions of use, and other information given on the website are helpful to forging an attack
	
#### &emsp;&emsp;c. <u>Search tools</u>: [eg: wayback, paraminer etc.]

>•&emsp;At least one internet search engine has indexed the target web application at least once in the past

>•&emsp;The use of google search hacks such as `site:www.example.com`, `related:www.example.com` and `site:example.com` to tailor search results are most helpful

>•&emsp;Third party application flaws and web services running on the application [shodan.io](https://shodan.io)

>•&emsp;`robots.txt` is another interesting search file containing a list of directories that search engines such as Google are supposed to index or ignore but this provides information concerning directory structure
	
#### &emsp;&emsp;d. <u>Web application scanning</u>:

>•&emsp;This is done to gather more information concerning the backend of the web application

>•&emsp;Information concerning services running, operating systems and versions and possible devices such as firewalls, can be gathered amongst others

### &emsp;2. <u>Analysis Phase</u>:
&emsp; The purpose of this phase is to critically analyze the interesting aspects of information gathered from the profiling phase.

>•&emsp;Analyze what kind of site it is. Development sites are prone to many attacks, business logic attacks inclusive.

>•&emsp;Identify and analyze flows concerning critical business functionalities like check-out, wire transfer, login etc.

>•&emsp;Identify and analyze possible restrictions based on the critical flows (sessions, access controls).

>•&emsp;Analyze HTTP GET/POST requests of all interesting pages.

>•&emsp;Analyze directory, file, and URL naming conventions including file call functionalities based on parameter names.

>•&emsp;Identify all application entry points, possible error creators, possible file inclusions (dig deeper into JavaScript)

>•&emsp;Analyze visible policies such as password recovery options. Look for loopholes in the policies

>•&emsp;Analyze client-side applications (for example, Adobe Flash, Java, Silverlight etc) for possible information disclosure or induction

>•&emsp;Analyze parameter names in interesting HTTP GET and POST requests in the form of name/value pairs, XML, JSON or Cookies.

>•&emsp;Especially analyze all cookies delivered during the profiling, look for incrementing easily guessable values across all cookies.

>•&emsp;Analyze whether a parameter's value in the traffic is easily guessable and can be changed in order to gain unauthorized access.

>•&emsp;Especially analyze parameters that are controlling user profiles.

### &emsp;2. <u>Test/Attack phase</u>:
&emsp; With the information gathered from the discovery and analysis phase, test cases can be derived to test and in essence attempt to attack possible and most common business logic flaws that may exist. Test cases are modeled with the studied attack vectors in mind and each test case may reveal the need to perform more analysis in order to improve a test case or test scenario.

#### &emsp;&emsp;a. <u>Workflow abuse</u>:
&emsp; It works around lack of constraints and data validation at critical points where the application believes that the data/information can be trusted.

>•&emsp; Does the application allow users to insert "un-validated" data into the system/application?

>•&emsp; Does the application perform validation before performing critical requests?

>•&emsp; Does the application allow users to perform actions outside of the “approved/required” business process flow?

#### &emsp;&emsp;b. <u>Policy and practices exploit</u>:
&emsp; Policies and practices that have been gathered should be assessed to verify if there exists, loopholes that can be exploited.

>•&emsp; Password recovery options. Does the password recovery option contain a weak link?

>•&emsp; File upload options. Does the application verify upload file types to prevent uploads of malicious files and files the system is not expecting or wanted per the business logic requirements?

>•&emsp; Return/Refund policy options

#### &emsp;&emsp;c. <u>Induction</u>:
>•&emsp; Does the application allow code validation on the client side? Allowing client side validation allows data to be accessible to an attacker no matter how obfuscated it may be.

>•&emsp; Do parameters have guessable or predictable values (including cookies) that can be tampered with either by increments or by other means (such as changing from False to False)?

>•&emsp; Does the application's file, directory and URL have naming conventions that are guessable enough to access others like it via URL?

>•&emsp; Does the client perform validation before performing critical requests?

#### &emsp;&emsp;d. <u>Repetitive Attacks</u>:
&emsp; its basis on performing requests repetitively.

>•&emsp; Does the application allow users to exercise its functions more times than required by the business logic workflow?

>•&emsp; Do certain features of the web application allow for the possibility of infinite loop formation without constraints?

#### &emsp;&emsp;e. <u>Insecure design patterns</u>:

>•&emsp; Can the application's timing be predictable or guessable?

>•&emsp; Are there third party application integration, new functionality implementation or reported bugs that can cause an associative vulnerability to the web application?

>•&emsp; Does the application contain token parameters that relate directly to a particular user or group?

>•&emsp; Does the application perform validation before performing requests?

>•&emsp; Does the application allow for unauthorized actions (like privilege escalation)?

>•&emsp; Does the application implement proper data sanitization and normalization of input data?

>•&emsp; Are there certain parameters that are added by the application (through JavaScript)?


### &emsp;2. <u>Evaluation phase</u>:
&emsp; This phase works around the test cases after they have been applied to the web application and to assess the vulnerability of the web application and the risk this imposes on the business process and organization as a whole. Also, the evaluation phase considers possible iteration of the methodology for the purpose of regression testing (in the light of controls implemented or changes made).











## <u>Extra Stuff</u>:

**>_ The other problem(s) with business logic flaws is:**

>•&emsp;Scanners can’t identify them

>•&emsp;IDS can’t detect them

>•&emsp;Web application firewalls can’t defend them
