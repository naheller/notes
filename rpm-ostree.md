# rpm ostree

Layer package with `rpm-ostree install <package>`

I initially layered `tlp` but then removed it. I hear that updates take longer if any layered packages are present.

View all installed packages on ostree image (and optionally filter):
`rpm -qa | grep <my-term>`

TODO: Set up automatic rpm-ostree update checks (and a notification?)
