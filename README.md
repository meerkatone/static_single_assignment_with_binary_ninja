# Static-Single-Assignment-with-Binary-Ninja
Static Single Assignment (SSA) with Binary Ninja

YouTube Video:
https://youtu.be/XL0lepxA2L0

Tools:
- Binary Ninja 4.2 (Commercial) https://binary.ninja/

Get the Trivision webs binary:
- wget https://github.com/therealsaumil/emux/raw/master/files/emux/TRI227WF/rootfs.tar.bz2
- bzip2 -d ./rootfs.tar.bz2
- tar -xvf ./rootfs.tar
- mkdir ./Tenda/BNDB/
- cp ./rootfs/usr/bin/webs ./Tenda/BNDB/TRI227WF_webs
- rename the binary as needed.
- open the binary in Binary Ninja and save a bndb.

Extract SSA from Trivision webs using the API and using the Binary Ninja GUI

Within Binary Ninja we can jump to 0xB7E8, and use current_mlil to do the following:
- Check if the 3rd param to memcpy takes negative range values
    - current_mlil.ssa_form[25].params[2].possible_values.ranges[0].end<br></br>
- Check the def-use for phi nodes
    - ssa = current_mlil.ssa_form[17]
    - (current_mlil.ssa_form.get_ssa_var_definition((ssa).src[0]))
    - (current_mlil.ssa_form.get_ssa_var_uses((ssa).src[0]))

References
- Binary Ninja Python API Reference: https://api.binary.ninja/
- Static Single Assignment Basics: https://docs.binary.ninja/dev/concepts.html#static-single-assignment-basics
- Static single-assignment form: https://en.wikipedia.org/wiki/Static_single-assignment_form
- Binary Ninja Intermediate Language Overview: https://docs.binary.ninja/dev/bnil-overview.html
- SSA Explained: https://carstein.github.io/binary%20ninja/2020/10/22/ssa-explained.html
- Vulnerability Modeling with Binary Ninja: https://blog.trailofbits.com/2018/04/04/vulnerability-modeling-with-binary-ninja/
- F'ing Around with Binary Ninja: 2.0 Release Party!: https://www.youtube.com/watch?v=hQ4qxMVbLcM
- Emulating the Tenda AC15 Router: https://armx.exploitlab.net/docs/emulating-tenda-ac15.html
- EMUX: https://github.com/therealsaumil/emux/
