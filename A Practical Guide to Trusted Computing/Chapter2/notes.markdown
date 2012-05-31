#Design Goals of the Trusted Platform Module#

###Design goals###
######Securely reporting the environment.######
1.Storing a record of the boot sequence.<br />
<lo>
    (1)TCG uses the boot sequence to determine the trusted status of a platform. control: boot a system -> BIOS -> system establishes subsystems to do basic IO and initialize cards -> transfer control to BIOS back -> boot loader -> OS kernel -> device drivers and services -> start up a program.<br />
    (2)How to know the system is secure? TCG handles it with a daisy chain design. It starts with a small root of trust that is the first thing that gets control of the system, then at every step, records the next thing being used before passing control to it. The TPM stores all this records and report on them securely.<br />
    (3)TPM stores a digest of information in Platform Configuration Registers(PCRs).<br />
    (4)Values in PCRs are stored in memory locations in the TPM and can only be changed via a extend operation: PCR_now <= SHA_1(PCR_old || input).<br />
    (5)If trust the BIOS corresponding to the recorded PCR value, then can trust the extensions to the PCR made by the BIOS, and so on.<br />
</lo>
<br />
2.Reporting the boot sequence record.<br />

######Secure storage.######
1.Storing data and symmetric keys.<br />
<br />
2.Storing asymmetric keys.<br />
<br />
3.Authorization.<br />
<br />
