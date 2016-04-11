# Contributing 

Everyone is welcome to contribute to this specification.

Any simple editorial contribution can simply be done with a GitHub Pull Request.
You can even do an inline edit of the file on GitHub.

For more substantial contributions that, please first start a thread in the
[webappsec mailing list](http://lists.w3.org/Archives/Public/public-webappsec/)  at
the W3C.

Note: Contributions to this repository are intended to become part of Recommendation-track documents governed by the
[W3C Patent Policy](http://www.w3.org/Consortium/Patent-Policy-20040205/) and
[Software and Document License](http://www.w3.org/Consortium/Legal/copyright-software). To make substantive contributions to specifications, you must either participate
in the relevant W3C Working Group or make a non-member patent licensing commitment.

If you are not the sole contributor to a contribution (pull request), please identify all 
contributors in the pull request comment.

To add a contributor (other than yourself, that's automatic), mark them one per line as follows:

```
+@github_username
```

If you added a contributor by mistake, you can remove them in a comment with:

```
-@github_username
```

If you are making a pull request on behalf of someone else but you had no part in designing the 
feature, you can remove yourself with the above syntax.


# Style guide to contributors 

- the spec uses [Bikeshed](https://github.com/tabatkins/bikeshed).
  Please update `index.html` before sending a pull request.
- Wrap lines at 80 columns.
- put comments in front of sections, for better readability with
  syntax coloring   editors

# Running Bikeshed

If you're going to be making a lot of changes to the spec, you should
[install Bikeshed](https://github.com/tabatkins/bikeshed/blob/master/docs/install.md)
and run `bikeshed watch` while you're editing, so that you can save
and reload easily.

If you're just making one change, you can update `index.html` by
running `index.bs` through https://api.csswg.org/bikeshed/.
