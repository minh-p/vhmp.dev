+++
title = "Replit.py (WIP)"
draft = false
+++

## Replit.py {#replit-dot-py}

Recent Replit projects use nix to handle the development environment (installing packages for a development environment).

An example setup for newly created REPL which has nix support uses changes the `replit.nix` file in order to install the necessary packages

```nix { filename="replit.nix" }
{ pkgs }: {
  deps = [
    (pkgs.python3.withPackages (ps: with ps; [
      pytest
    ]))
  ];
}
```

Search packages at <https://search.nixos.org>. Replit uses different nix channels so I would advise sticking with packages names that do not have versions in it. An example would be `python311` as that would mean it has to be a nixpkgs channel version that has this package.

Further configuration options can be found on this page: <https://docs.replit.com/features/project-setup/configuration>.
