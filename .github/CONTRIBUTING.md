# Contributing

Everyone is welcome to contribute to this specification.

Any simple editorial contribution can simply be done with a GitHub Pull Request.
You can even do an inline edit of the file on GitHub.

Note: Contributions to this repository are intended to become part of Recommendation-track documents governed by the
[W3C Patent Policy](https://www.w3.org/Consortium/Patent-Policy-20040205/) and
[Software and Document License](https://www.w3.org/Consortium/Legal/copyright-software). To make substantive contributions to specifications, you must either participate
in the relevant W3C Working Group or make a non-member patent licensing commitment.

## Style guide to contributors

- the spec uses [ReSpec](https://www.w3.org/respec/)
- the spec is tidied using [HTML5 Tidy](https://github.com/w3c/tidy-html5). For
  instructions on running HTML5 tidy, see below.
- Running tidy is optional. We run tidy on the server after every commit.
- Put comments in front of sections, for better readability with
  syntax coloring editors.

## Commit message guidelines

  - When relevant, include `closes #` and the issue number.
  - The commit message should be short and concise.
  - Prefix the commit message with one of the following:
    - `Editorial:` -for editorial/non-normative change to the specification.
    - `Chore:` - when fixing ReSpec stuff or other non-spec related stuff (e.g., CI).
    - Normative changes should not be prefixed with anything. These go into the changelog.

## Optional - Running HTML5 Tidy

We run HTML5 tidy on the server after every commit.

But, if you are planning to make a lot of edits, please make sure you
have [HTML5 Tidy](https://github.com/w3c/tidy-html5) installed.

On MacOS:

```
brew install tidy-html5
```

Don't use the the one that ships with \*nix systems.

You can confirm check the version by running the following.

```bash
tidy --version
```

It should say "HTML Tidy for Apple macOS version 5.8.0" or something similar for your OS.

Once you have confirmed (make sure you have committed your changes before
running tidy, as the changes are destructive ... in a good way:)):

```bash
tidy -config tidyconfig.txt -o index.html index.html
```

If you are not the sole contributor to a contribution (pull request), please identify all
contributors in the pull request comment.

## Contributing for other people

To add a contributor (other than yourself, that's automatic), mark them one per line as follows:

```text
+@github_username
```

If you added a contributor by mistake, you can remove them in a comment with:

```text
-@github_username
```

If you are making a pull request on behalf of someone else but you had no part in designing the
feature, you can remove yourself with the above syntax.
