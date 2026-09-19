+++
title = "Replit.py (WIP)"
draft = false
+++

## Replit.py {#replit-dot-py}

This page is still a work in progress (WIP). I'm planning to write how to setup Replit on here by writing into `replit.nix` and installing the necessary packages for Replit.

An example setup for newly created REPL which has nix support uses changes the `replit.nix` file in order to install the necessary packages

```nix { filename="replit.nix" }
  { pkgs }: {
  deps = [
    pkgs.python311
    pkgs.python311Packages.pip
    # pkgs.python311Packages.tkinter
    # pkgs.python311Packages.pygame
  ];
}
```
