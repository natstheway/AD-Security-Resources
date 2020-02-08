# AD-Security-Resources

<p><h2>Setting up active directory lab :</h2>
<p>https://github.com/outflanknl/Invoke-ADLabDeployer 
<p> AutomatedLab - Works good for small labs based on HyperV
 
<p><h2>Local Computer Enumeration and Privesc : </h2>

<p>1. Bypass Execution Policy : 

<p>One of the 15 methods mentioned in the blog usually works.. </p>
<p>https://blog.netspi.com/15-ways-to-bypass-the-powershell-execution-policy/

<u>Notes :</u> Bypassing Powershell execution policy issues : </H2>


<p>2. AMSI Bypass for loading malicious scripts:
<p>  https://github.com/S3cur3Th1sSh1t/Amsi-Bypass-Powershell </p>
<u>Few scripts that usually works quickly </u>
<p>sETItEM ( 'V'+'aR' + 'IA' + 'blE:1q2' + 'uZx' ) ( [TYpE]( "{1}{0}"-F'F','rE') ) ; ( GeT-VariaBle ( "1Q2U" +"zX" ) -VaL)."A`ss`Embly"."GET`TY`Pe"(( "{6}{3}{1}{4}{2}{0}{5}" -f'Util','A','Amsi','.Management.','utomation.','s','System' ))."g`etf`iElD"( ( "{0}{2}{1}" -f'amsi','d','InitFaile' ),("{2}{4}{0}{1}{3}" -f 'Stat','i','NonPubli','c','c,' ))."sE`T`VaLUE"(${n`ULl},${t`RuE} ) </p>

<p>[Ref].Assembly.GetType('System.Management.Automation.Ams'+'iUtils').GetField('am'+'siInitFailed','NonPu'+'blic,Static').SetValue($null,$true)</p>

<u>Detailed Article on this subject : </u>
https://blog.f-secure.com/hunting-for-amsi-bypasses/
https://burmat.gitbook.io/security/hacking/domain-exploitation#user-and-computers-with-unconstrained-delegation

<p>3. Constrained Language Mode :</p> 
Constrained Language consists of a number of restrictions that limit unconstrained code execution on a locked-down system.  (https://devblogs.microsoft.com/powershell/powershell-constrained-language-mode/)

AD Module usually goes undetected and can be used for enumerating from the system with CLM enabled.
https://www.labofapenetrationtester.com/2018/10/domain-enumeration-from-PowerShell-CLM.html

Few other interesting methods to bypass CLM 
https://www.secjuice.com/powershell-constrainted-language-mode-bypass-using-runspaces/

Other references : 
https://github.com/padovah4ck/PSByPassCLM
https://chickenpwny.github.io/concepts/bypass/

<p>4. Turning of Windows Defender - Real Time Monitoring (for not letting exploits to be deleted):</p>
Set-MpPreference -DisableRealtimeMonitoring $true

<p>5. Privesc on Local Computer </p>
Run Invoke-AllChecks 
<p>PowerView / Powersploit: https://github.com/PowerShellMafia/PowerSploit</p>


<H2>Domain Enumeration</h2>

<p><h3>1. ACL Enumeration and escalation :</h3></p>
<p>Some of the Active Directory object permissions and types that we as attackers are interested in:</p>
<p><b>GenericAll</b> - full rights to the object (add users to a group or reset user's password)
<p><b>GenericWrite</b> - update object's attributes (i.e logon script)
<p><b>WriteOwner</b> - change object owner to attacker controlled user take over the object
<p><b>WriteDACL</b> - modify object's ACEs and give attacker full control right over the object
<p><b>AllExtendedRights</b> - ability to add user to a group or reset password
<p><b>ForceChangePassword</b> - ability to change user's password
<p><b>Self (Self-Membership)</b> - ability to add yourself to a group
https://ired.team/offensive-security-experiments/active-directory-kerberos-abuse/abusing-active-directory-acls-aces

AD Module :
  https://github.com/samratashok/ADModule

<p>2. Bloodhound - Visualizing the attack patch and AD Objects
  https://github.com/BloodHoundAD/SharpHound
  https://github.com/BloodHoundAD/BloodHound

Lateral Movement Automation using Bloodhound data :
  https://github.com/GoFetchAD/GoFetch

<p>3. Tools for Credential Dumping for all attacks (PTH, Kerberoasting, Golden Ticket Attack, Silver Ticket Attack, Skeleton Key Attack:
Mimikatz : https://github.com/gentilkiwi/mimikatz

Spraykatz - Credentials gathering tool automating remote procdump and parse of lsass process
  https://github.com/aas-n/spraykatz

Mimikittenz - Reading credentians from process :
  https://github.com/putterpanda/mimikittenz

Benjamin Delpy's Kekeo 
  https://github.com/gentilkiwi/kekeo/

Vincent LE TOUX's MakeMeEnterpriseAdmin
  https://github.com/vletoux/MakeMeEnterpriseAdmin

Rubeus :
  https://github.com/GhostPack/Rubeus

<p>4. Generate HTML report of AD Security Posture - Pingcastle :
  https://github.com/vletoux/pingcastle

<p>5 Delegation attacks 

<p>5.1 Unconstrained Delegation
When a user authenticates to a computer that has unresitricted kerberos delegation privilege turned on, authenticated user's TGT ticket gets saved to that computer's memory. It will be possible to extract the same once the system is compromised.
 
<p>5.2 Constrained Delegation
If you have compromised a user account or a computer (machine account) that has kerberos constrained delegation enabled, it's possible to impersonate any domain user (including administrator) and authenticate to a service that the user account is trusted to delegate to.

<p>5.3 Resource Based Constrained Delegation
It's possible to gain code execution with elevated privileges on a computer if you have WRITE privilege on that computer's AD object.
 
<p><h2> References : </h2>
Huge list of AD security resources available below :
  https://adsecurity.org/
  https://www.harmj0y.net/
  https://m0chan.github.io/2019/07/31/How-To-Attack-Kerberos-101.html
  https://beta.hackndo.com/

