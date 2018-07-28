# epics-msi-example

## Set EPICS base

##

```
$ msi -h
Usage: msi [options] [template]
  stdin is used if neither template nor substitution file is given
  options:
    -h        Print this help message
    -D        Output file dependencies, not substitutions
    -V        Undefined macros generate an error
    -g        All macros have global scope
    -o<FILE>  Send output to <FILE>
    -I<DIR>   Add <DIR> to include file search path
    -M<SUBST> Add <SUBST> to (global) macro definitions
              (<SUBST> takes the form VAR=VALUE,...)
    -S<FILE>  Expand the substitutions in FILE

$ msi -M name=mrfioc2 template1.in 
PACKAGE_NAME="mrfioc2"
PACKAGE_VERSION="2.2.0"


BUILT_MODULE_NAME[0]="mrf"
DEST_MODULE_NAME[0]="mrf"
DEST_MODULE_LOCATION[0]="/updates/dkms"

AUTOINSTALL=yes

MAKE[0]="make -C $(kernel_source_dir,undefined) M=$(dkms_tree,undefined)/$(PACKAGE_NAME,undefined)/$(PACKAGE_VERSION,undefined)/build modules"
CLEAN="make -C $(kernel_source_dir,undefined) M=$(dkms_tree,undefined)/$(PACKAGE_NAME,undefined)/$(PACKAGE_VERSION,undefined)/build clean"


$ msi -M name="mrfioc2" -M  version="2.2.0-rc2" template1.in > template1.out


PACKAGE_NAME="mrfioc2"
PACKAGE_VERSION="2.2.0-rc2"


BUILT_MODULE_NAME[0]="mrf"
DEST_MODULE_NAME[0]="mrf"
DEST_MODULE_LOCATION[0]="/updates/dkms"

AUTOINSTALL=yes

MAKE[0]="make -C $(kernel_source_dir,undefined) M=$(dkms_tree,undefined)/$(PACKAGE_NAME,undefined)/$(PACKAGE_VERSION,undefined)/build modules"
CLEAN="make -C $(kernel_source_dir,undefined) M=$(dkms_tree,undefined)/$(PACKAGE_NAME,undefined)/$(PACKAGE_VERSION,undefined)/build clean"


```