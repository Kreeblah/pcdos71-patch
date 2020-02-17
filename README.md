# pcdos71-patch
This is a batch file for applying the IBM PC-DOS 7.1 files found in the ServerGuide Scripting Toolkit to an existing PC-DOS 7.01 (also known as PC-DOS 2000) installation.

In order to use this, you need the following:
* An existing PC-DOS 7.01 (PC-DOS 2000) installation
* A copy of the [DOS anycpu edition](ftp://ftp.software.ibm.com/systems/support/system_x/ibm_sw_sgtk_1_3_07_anyos_anycpu.zip) of the [IBM ServerGuide Scripting Toolkit](https://www.ibm.com/support/pages/ibm-serverguide-scripting-toolkit)

Once you have the ServerGuide Scripting Kit, extract it and navigate to:

``sgdeploy\sgtk\DOS``

From there, copy the below files to a floppy disk or other location to be used for patching, and copy ``DOSPATCH.BAT`` to the same location.

Files to copy:

    ATTRIB.EXE
    BLDLEVEL.COM
    COMMAND.COM
    DEBUG.COM
    DYNALOAD.COM
    FDISK32.COM
    FORMAT.COM
    FORMAT32.COM
    HIMEM.SYS
    IBMBIO.COM
    IBMCDET.SYS
    IBMDOS.COM
    IBMIDECD.SYS
    IPSRASPI.SYS
    MSCDEX.EXE
    NOINT25.COM

To use it, switch to the location with the batch file and run:

``dospatch [DRIVE] [DOSDIR]``

``[DRIVE]`` should indicate the drive where PC-DOS 7.01 is currently installed, and ``[DOSDIR]`` should indicate the directory it's installed in.  For example, if PC-DOS 7.01 is installed in ``C:\DOS`` then you could use the following command to apply the patch:

``dospatch c: dos``

Once the patch completes, reboot.