#Introdution to Trusted Computing#

###Target###
To understand how to use the embedded security subsystem(TPM) built into many computers to solve the insecure problems.
<br />

###Why Software Can't Be Made Completely Secure?###
1.Modern systems are complex, have billions of lines of code. The fact that one security-related bug per thousand lines of source code makes a software insecure.<br />
2.Compatibility.<br />
3.Hard to detect the presence of malicious code in the system without hardware support.<br />

###How Can the TPM Help?###
#####The TPM has been designed to protect security:#####
1.Private keys cannot be stolen or given away.<br />
2.The addition of malicious code is always detected.<br />
3.Malicious code is prevented from using the private keys.<br />
4.Encryption keys are not easily available to a physical thief.<br />

#####The TCG chip accomplishes these goals with three main groups of functions:#####
1.Public key authentication functions.<br />
2.Integrity measurement functions.<br />
3.Attestation functions.<br />
