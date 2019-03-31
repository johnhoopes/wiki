<!-- TITLE: Angr -->
<!-- SUBTITLE: A quick summary of Angr -->

# Loading
'''
import angr
proj = angr.Project('/bin/true')

proj.loader.all_objects - shows all the parts that were loaded
'''
# Hooking Functions
'''
proj.hook(0x10000, stub_func())
@proj.hook(0x10000, length=5) - skip 5 bytes when return.... used to replace portions of a basic block
proj.hook_symbol(name, hook)

'''

# Blocks
'''
block = proj.factory.block(proj.entry)
block.pp() - pretty print a disassembly
block.instructions - number of instructions
block.instruction_addrs - addrs of all instructions


not sure how to enumerate all blocks yet

'''

# States
Note that symbolic execution isn't real.  State is available but may not match real world.

state.regs.rip - instruction pointer
state.mem[addr].type = x

simgr = proj.factory.simulation_manager(state)
simgr.step() - steps an entire basic block

# Analyses

Tons of these notes when I use them.

cfg = proj.analyses.CFGFast()  - control flow graph
len(cfg.graph.nodes()) - number of nodes
entry_node = cfg.get_any_node(proj.entry) - might be able to enumerate basic block here.
len(list(cfg.graph.successors(entry_node)))



