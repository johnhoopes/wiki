<!-- TITLE: Angr -->
<!-- SUBTITLE: A quick summary of Angr -->

# Loading
'''
import angr
proj = angr.Project('/bin/true')

proj.loader.shared_objects - shows all the parts that were loaded
'''
# Hooking Functions
'''
proj.hook(0x10000, stub_func())
@proj.hook(0x10000, length=5) - skip 5 bytes when return.... used to replace portions of a basic block
proj.hook_symbol(name, hook)

'''

# More