# pcdos71-patch
This is a batch file for applying the IBM PC-DOS 7.1 files found in the ServerGuide Scripting Toolkit to an existing PC-DOS 7.01 (also known as PC-DOS 2000) installation.  PC-DOS 7.1 adds FAT32 support, but it does have certain compatibility issues, such as no known version of ``SETVER.EXE`` correctly loading on it.

In order to use this, you need the following:
* An existing PC-DOS 7.01 (PC-DOS 2000) installation, US English release
* A copy of the [DOS anycpu edition](ftp://ftp.software.ibm.com/systems/support/system_x/ibm_sw_sgtk_1_3_07_anyos_anycpu.zip) of the [IBM ServerGuide Scripting Toolkit](https://www.ibm.com/support/pages/ibm-serverguide-scripting-toolkit), v1.3.07.

Once you have the ServerGuide Scripting Kit, extract it and navigate to:

``sgdeploy\sgtk\DOS``

From there, copy the below files to a floppy disk or other location to be used for patching, and copy ``DOSPATCH.BAT`` to the same location.

The files this batch file copies to the installation, along with their associated SHA256 sums:

    ATTRIB.EXE    91710325176330e403be85d935d6ad21d5bb6a77b589afb84ac4739636e466cd
    BLDLEVEL.COM  d25a4e54cddc46070fd5ad7ca26ff566fe344c2ef9fac87d6b2d8956363d9133
    COMMAND.COM   4bb46e6c3228969b06c423dd181df9c6765999094d4c687772efd9ee23881e7a
    DEBUG.COM     8b0b0a27486c8ad67d60644ede2e57b5621291054baf5d3d376e216bfdb78957
    DYNALOAD.COM  458201d78b36e5a1cc03afe7a16e8f765483034c7279b7cdc74f470ec1208e28
    FDISK32.COM   e4ef889ad29b49d472cd4b30b14e47bf3e95cbcac7c60d4e9ee96cfadfbe5198
    FORMAT.COM    8de7d48bf524159cb7340067590d02cf033aafb2c8d1f77f5f63da7ba35252ff
    FORMAT32.COM  8281d9480359868740c45ab3c8f709417d83bb3461061fe5f796a2670c0041c1
    HIMEM.SYS     f758d0fce53b5879747c38aa64662109fe7d2d504cae16dc410bf227873a2fb9
    IBMBIO.COM    d1c9e34aafa2a65b8f74eeace701b273e16d6b7fae1368c1ba7a768b39eb4558
    IBMCDET.SYS   4ce81df66fd3e6674485f0f70d1413bfca17163f95b02aec68fee28673cf0b2d
    IBMDOS.COM    f426a13b1e2e5a05bc7e56a18d551608d3bdc4cb14045324468860a3725e2084
    IBMIDECD.SYS  6623d237bdfb6bd416e5de3076cd18f12119562005af8cd005b634b94afb80c8
    IPSRASPI.SYS  3b1398944b44b0f9245095bd1f72c1841f36e3967038574c02f86fbc8acc9639
    MSCDEX.EXE    8fd939a93c1153c2a1b2c8e349d438237d3a67f268a78908420447d90c518199
    NOINT25.COM   9ac9a255e9fb2248eef66b18479e19abeef04d82dd16c5aa16696db5dda1c94b

The filenames and expected SHA256 sums of the files that this batch file looks for in the existing installation are:

    COMMAND.COM   6bdab428500f5d57d099e63d63f5e4f4f0c1c4708920618aa734e239d1c0f239
    DEBUG.COM     dac2d539346a98b4d5b2b1763bcf24bd0f537cb624cf51e428c8e8ca6483ff60
    DYNALOAD.COM  081b2b977ea0a72c6a309b476ca639423eb51b8b58d342ac13f707b460a591a2
    FORMAT.COM    bc89f41fb5157e98cbaeb27b2856ff064669336867aca07ec622d5d8c1b6d68a
    HIMEM.SYS     12a45ab571e82c6e1c5ac8f05c0919a7dc9ca62ad0c39e0e8adb945cd31d8623
    IBMBIO.COM    27e9f851de09d1ec3f21dfff12675c29451fda24e6644640c965c87c622d7b6b
    IBMDOS.COM    8e1283bb4421ff003a5b6097f6c3b7aa577258e7913a525b8be70acf2930bff6
    MSCDEX.EXE    aba92c75e00b16b84c787a0ccba65a2b58fdd48288594d4392534031c6a2ab72

Finally, this batch file uses MD5 digests to check whether the patch files and the files to be patched are the expected files.  Note that MD5 isn't a secure hashing algorithm at this point.  If there are questions about the legitimacy of the files, a more secure hashing algorithm (such as SHA256) is strongly encouraged instead.  The intent of using MD5 was primarily to prevent accidental application of this patch to a system which is not suited for it while not requiring an implementation of a hashing algorithm which would likely be extremely slow on a computer of the era that runs DOS.

Because DOS does not have a native MD5 tool, ``MD5SUM.EXE`` (SHA256 sum 484e05c00662d260c95a3a11e5922b465d14ead71a8950cd54193c32bcebd4c7)from https://github.com/Kreeblah/md5sum is also required.

To use this batch file, switch to the location where it's located and run:

``dospatch [DRIVE] [DOSDIR]``

``[DRIVE]`` should indicate the drive where PC-DOS 7.01 is currently installed, and ``[DOSDIR]`` should indicate the directory it's installed in.  For example, if PC-DOS 7.01 is installed in ``C:\DOS`` then you could use the following command to apply the patch:

``dospatch c: dos``

Once the patch completes, remove any floppy disks from the drives and reboot.