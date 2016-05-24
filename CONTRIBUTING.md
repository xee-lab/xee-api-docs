#Contributing

Please observe our contribution guidelines before creating a pull request:

* Open an issue first. 
* Expain what you want to do about the documentation, we'll discuss that with you (*Note that this documentation is intended to be a short and concise*).
* If the issue is validated, fork the repository and make a **pull request**

## Issue titles

Any issue title must follow the pattern
`[Group] root : Issue`

- `Group` is where you found the issue. For example in the *android* doc, `group` will be `Android`.
- `root` is the *file* or the *end point* where the problem is.
- And finally, `issue` is what is wrong. Or what you want.

>For example, in the `cars` api, the field `deviceId` as the wrong type. The issue should be :
>`[Cars] cars : deviceId should be a serial number`

## Commit messages and Pull requests

Before any **pull request**, please [`rebase`](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History#Changing-Multiple-Commit-Messages) your commits to make them easy to read.

- If the **PR** fixes an issue, the title must be 
`Fixes #issueNumber : Title of issue`
- Else, the title must looks like:
`[Group] Type : Description` where type is the kind of thing done (*Feat*, *Update*, *Delete*, *Style*)

#Licence

[Creative Commons Licence](LICENSE.md)

Xee Documentation by the Xee Tech team is licensed under a Creative Commons Attribution 4.0 International Licence.

Based on a work at [https://github.com/xee-lab/documentation](https://github.com/xee-lab/documentation)

> The licence must remain in all derivatives of this work.