# Github and Repository Conventions

What follows describes how many of the external projects in `gwsystems` are integrated to work in *Composite*.
Currently, the external applications that we're integrating with *Composite* include:

- `rumpkernel`
- `click`
- `dpdk`
- `cFE`

In the future we should also include `lwip` (which is in-tree in a hacky way, currently).

None of these is treated as a library, as-is.
`ps` and `concurrencykit` are used by the system, and are treated most as libraries.
This might require future updates to the conventions if we want to abstract their use nicely.

## Branch management

Our high-level goals of managing each project include:

- Maintaining a link to `upstream` so that we can continue to merge each project's new code with our system.
- Enable our own development on the package in its own repo.
- Enable our own development on the package in the *Composite* repo.
- Enable a subset of team members that are able to perform PR and code reviews on the package.

Given this set of goals, we have the following conventions:

- A branch (named `upstream`) within the package's repo is devoted to merging with upstream.
    We should commit *zero* changes to this branch, and only `pull` from uptream.
    This branch's purpose is to enable other branches to `merge` with it to keep up-to-date.
    You *must* use "protected branches" and allow only the main researchers working on the project have the ability to pull from upstream.
- A branch or set of branches are used for local development.
    This branch is master.
    All PRs in this repo should be made to this branch.
    You *must* use "protected branches" and allow only the main researchers working on the project have `push` access.
- A branch in *Composite* corresponds to each external project (e.g. `dpdk`).
    This enables *Composite* development for project-specific features.
    The main researchers working on the project should be the only ones with `push` access to this branch.
    This branch merges with *Composite*'s mainline, and does PRs back into it.
    Any PR must be paired with a project repo that is in a functional state.

## Using external projects in *Composite*

We are using a number of conventions to integrate external projects and bodies of code into *Composite*.
Currently, we're focusing on projects that will

1. generate a `.o` object that contains the logic and functionality of the project, and 
2. be compiled with a *Composite* component that provides the necessary bindings to the rest of the system.

This enables the project to not need access to most of the *Composite* libraries (with the exception of libc), and instead to focus on an interface shared between the *Composite* component, and the project's `.o` object.
This interface is not a formal interface (as in `src/components/interface/*`) as it is not an inter-component interface.
Thus, the interface should be spelled out in `src/components/extern/<project>/proj_interface.h`.
Please remember that the compilation in the project will not necessarily have access to all *Composite* headers and libraries, so formulate this interface accordingly.

Each project should be represented as a `git submodule` in `src/components/extern/<project>/`.
The `<project>` directory should include the build adapters to compile and build the project.
Though the submodule will be pulled in by the *Composite* build system, it will *not* be compiled by default.
Some of the external projects are far too large to compile.
If a project is small, it is fine for the build system to compile it, but this is not the default behavior.

The `Makefile` in the `<project>` directory will receive the following build commands:

- `make build`
- `make clean`

Though you can define any additional directives for manual use within the project.
Each project should assume that the header files for the *Composite* libc (provided by `musl`) are in the `$COS_LIBC_HEADERS` makefile variable.

## TODOs and Issues

This is a generic organizing structure for a number of external projects.
As such, it doesn't well match a few features of different external projects.
For example:

- How can we support *multiple* configurations of the Rump kernel, instead of the *one* configuration the external project is built with?
- How can we support `cFE` "apps" as components as they are built in the `cFE` repo?
