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
