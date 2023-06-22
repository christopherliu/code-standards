# What is the purpose of a CODE-STANDARDS.md?
Codebases frequently develop "lava layers" where
1. part of the codebase is written in one standard,
2. a new better way of doing things comes out, and then
3. part of the codebase is written in another standard.

These layers are a frequent source of problems that are common among old codebases:
1. We write new code by copying old code, and if we happen to copy code written with the old standard, we unwittingly propagate that old standard.
2. If we need to fix a bug across the code base, we may need to fix it in 2 (or more) ways, depending on the number of standards currently in play.

CODE-STANDARDS.md is a way of combatting the lava layers problem by adding explicit metadata that identifies where these layers are, and by giving developers an escape hatch when deadlines prevent them from 100% updating a piece of legacy code to the current best practice.

# How to use CODE-STANDARDS.md
1. Include a CODE-STANDARDS.md at the root of your repository or project.
2. Using the [example](CODE-STANDARDS.example.md), document the standards (style, data access patterns, libraries, etc.) your code is expected to follow in CODE-STANDARDS.md.
3. At the top of CODE-STANDARDS.md, include the last day the standards were updated and a link to this project, as follows:

```
* Last updated: 2023/06/22
* Code standards, based on https://github.com/christopherliu/code-standards
```

# Whenever you create a new source file
1. If you're developing a new piece of code, any page that has `// standards-accept [CODE-STANDARDS.md's last updated date]` is a reasonable starting point.
2. Whenever you create a new source file, follow all of the standards in the current version of CODE-STANDARDS.md. (Skim CODE-STANDARDS.md before every commit.)
3. Treat any (knowing) violation of these standards as a build/lint error.
4. (Better: Integrate the current standards into your linter wherever possible. Written standards can be unwittingly and wittingly ignored.)
5. To document that you are up to date, include the following comment near the top of your source file:
```
// standards-accept 2023/06/22 (replace with the last updated date of CODE-STANDARDS.md)
```

# When you can't follow CODE-STANDARDS.md
Deadlines happen, here's what to do.
1. To exclude a file from a specific standard, use the ignore pattern:

```
// standards-accept 2023/06/22
// standards-ignore RSQUO
```

2. To exclude a file from all standards, use the ignore-all pattern:

```
// standards-ignore-all
```

3. Any file that has no comment at the header is implicitly assumed to be `standards-ignore-all`!

By using the ignore pattern, it is not necessary to update 100% every file you touch. Future developers will know (if properly trained by your organization) that old files use old patterns.

# Recommendations
* Try not to have more than 2 standards in flight at any time.
