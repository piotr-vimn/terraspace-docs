---
title: "Tfvars: Additional Lookup Locations"
---

It is generally encouraged to create tfvars files in the `app/stacks/MOD/tfvars` folder. Terraspace considers additional lookup paths though.  It's similar to how `LOAD_PATH` works. The lookup paths are:

    seed/tfvars/stacks/MOD
    seed/tfvars/modules/MOD
    app/stacks/MOD/tfvars

## Additional Seed Structure

Here's an example folder structure. The tfvars files should mainly be in `app/stacks/MOD/tfvars` folders.  However, you can create one-off `seed/tfvars` folders that mirror the modules and stack structure.

    ├── app
    │   ├── modules
    │   │   ├── instance
    │   │   └── vpc
    │   └── stacks
    │       └── core
    │           └── tfvars
    │               └── dev.tfvars
    └── seed
        └── tfvars
            └── modules
                └── instance
                    └── dev.tfvars

## One-Off Purposes

Terraspace offers this flexibility for one-off purposes.  For example:

* You may also want to try out an app/modules/MOD quickly without having to define a stack.
* You may need to temporarily override the tfvars files embedded within the `app/stacks/MOD/tfvars`.

Note, `app/modules/*/tfvars` are **not** considered in the lookup paths at all. This is because modules should be reusable.

Remember modules and like "functions" and tfvars are like "parameters" passed to them. Putting the tfvars files within the same module directory would be akin to hard coding parameters.

## Why tfvars in Stacks?

To understand why terraspace encourages creating your tfvars within the `app/stack/MOD/tfvars` folder, it is key to understand the difference between `app/modules` and `app/stacks`. The difference is how you use them.

* Stacks are meant to be used to group together modules. It makes sense to include business-specific logic here.
* Whereas modules are smaller pieces that are meant to be reused. It does not make sense to include business-specific logic in here.