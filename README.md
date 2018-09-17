# `gwsystems` Repositories

- `composite` - the main Composite source directory including the Speck kernel, and the foundational user-space components/libraries.  Includes:
    + Scheduling work by @phanikishoreg
    + Multicore work by @yzcode and @phanikishoreg
    + Some initial rust work by @Others
    + ...
- `cFE` & `OpenSatKit` - cool research by @Others, @base0x10, and @zacharied to get the Core Flight System running on Composite for more reliable, more secure satellite systems.
- `rumprun` - a [Rumpkernel](http://rumpkernel.org/) port to Composite by @RobertGiff, @lab176, and @phanikishoreg including full networking support.
- `dpdk` - The Data-Plane Development Kit support for 10Gbe/40Gbe support in Composite by @rskennedy and @ryuxin.
- `ps` - Parsec, quescence-based data-structure coordination by @ryuxin.
- `click` - Click modular router support in Composite by @vnitu02, paired with the DPDK support to support efficient middlebox execution.
- `silverfish` - Web assembly (`wasm`) for all devices!  Work done almost exclusively by @Others to explore the co-design between software fault isolation through `wasm`, and hardware support across various hardware platforms.  This serves as an interesting comparison between software and hardware isolation facilities, and the middle-ground in-between.

# Github organization conventions

All researchers part of this organization have the ability to transfer repos in, and make modifications to the different repos.
To avoid ambient authority for everything, we're using `github` "protected branches" to ensure that specific branches of different repos can be modified (`push`ed to) *only* by those who are running the project.
Please read the [details](https://github.com/gwsystems/documentation/blob/master/github_conventions.md) of this convention.

# Overview of building and using the repos in this org

## Composite standalone
[VM recommendation and installation](https://github.com/gwsystems/composite/blob/ppos/doc/README.md)
## Composite + Rumpkernel
[Rumpkernel installation on composite](https://github.com/gwsystems/composite/blob/rumpkernel/doc/rumpkernel_with_composite.md)  
This project entails running [rumpkernels](http://rumpkernel.org/) on the composite system.  
## Composite + CFE
[cFE2cos setup](https://github.com/gw-shc/cFE2cos)
Note that these steps create an independent installation of composite in the project's `composite` submodule.
## Composite Coding Style
For the Composite style guide see [here](https://github.com/gwsystems/composite/blob/ppos/doc/style_guide/composite_coding_style.pdf)
