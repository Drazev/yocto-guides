# Recipes Guide

Yocto's official documentation while useful to experienced users is very challenging to follow for those looking to learn the system. It includes an abundance of details to help you customize your builds, but lacks a lot of basic details about the how things work together, and many of the implicit rules that come with using it.

This guide targets the specific case of recipe's in Yocto. The documentation helps you create one, but doesn't really explain anything. How it works, the flow of work, scope, and rules are all left for you to sift through documentation on an easter egg hung learning new terms and searching them in hope you can fit the pieces together eventually. Even validating what you know can be a daunting task since they way things are logged is inconsistent and where you can find those various logs and how you can identify them is not straightforward and in some cases undocumented.


# What is a Recipe

A recipe in Yocto is a configuration document that allows you to define an installable package or collection of packages (packagegroup) by modifying the configuration details of special environment variables or implicit tasks. While recipe's can define procedures by defining functions, it is not the main prupose of the document. By design functionality should be defined in classes (bbclass) files and used in recipe's to determine the value of the environment variables.

## Recipe Workflow
See [Tasks](https://docs.yoctoproject.org/dev/ref-manual/tasks.html#ref-tasks-install)
Recipe's have a basic workflow defined by the `bitbake` build system. This functionality can also be extended by bbclasses which can change the behavior of the basic workflow by redefining functions like `do_build`. It is also possible to add functions before or after functions in the workflow.

```mermaid
  flowchart LR
    do_build --> do_fetch --> do_unpack --> do_patch --> do_populate_lic --> do_configure --> do_compile --> do_install --> do_package --> do_package_qa --> do_packagedata --> do_package_write_deb --> do_prepare_recipe_sysroot
```



1. do_build 
2. do_fetch
3. do_unpack
4. do_patch
5. do_populate_lic
6. do_configure
8. do_compile
10. do_install
12. do_package
13. do_package_qa
14. do_packagedata
15. do_package_write_deb
16. do_package_write_ipk
17. do_package_write_rpm
18. do_prepare_recipe_sysroot
