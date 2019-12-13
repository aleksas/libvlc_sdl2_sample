# Making libvlccore and libvlc lib files

To generate lib files 

## x86

```batch
vcvars32.bat

lib /def:libvlccore.def /out:libvlccore.lib
lib /def:libvlccore.def /machine:x86 /out:libvlccore.lib
lib /def:libvlc.def /out:libvlc.lib
lib /def:libvlc.def /machine:x86 /out:libvlc.lib
```

## x64

```batch
vcvars64.bat

lib /def:libvlccore.def /out:libvlccore.lib
lib /def:libvlccore.def /machine:x64 /out:libvlccore.lib
lib /def:libvlc.def /out:libvlc.lib
lib /def:libvlc.def /machine:x64 /out:libvlc.lib
```

## The def file generation

The def files were generated using 

```batch
dumpbin /EXPORTS libvlccore.dll > libvlccore.def
dumpbin /EXPORTS libvlc.dll > libvlc.def
```

and cleaning them up. For convinience here is a regex for cleaning:

`\s+\d{1,3}\s+[\d\w]{1,3}\s+[\d\w]{8} ([^\s]+)$` > `\t$1\n`