---
title: "How to use JabRef LSP with Emacs"
author: Abilashini
date: 2025-12-20
tags: [emacs, lsp, jabref]
---

This post explains how to use the **JabRef Language Server (LSP)** with **Emacs**.
It is intended for users who want IDE-like features such as autocompletion,
navigation, and diagnostics while editing **BibTeX** files in Emacs.

---

## What is Emacs?

Emacs is a powerful and highly customizable text editor.
It is popular among developers and researchers because it can be extended
using Emacs Lisp and supports advanced workflows.

---

## What is LSP?

The **Language Server Protocol (LSP)** allows editors to provide features like:

- Code completion
- Error checking
- Navigation
- Documentation lookup

These features are provided by a *language server*, not the editor itself.

---

## How JabRef LSP works with Emacs

JabRef includes a **built-in LSP server** for BibTeX files.

- Emacs acts as the **LSP client**
- JabRef acts as the **LSP server**
- Communication happens via standard input/output

This allows Emacs to understand BibTeX files using JabRef’s logic.

---

## Prerequisites

- JabRef installed (with LSP support)
- Emacs installed
- Basic familiarity with Emacs

---

## Install lsp-mode in Emacs

Emacs uses an LSP client called **lsp-mode**.

Install it using the Emacs package manager:

```elisp
M-x package-install RET lsp-mode RET
---

## Configure JabRef LSP in Emacs

JabRef provides a built-in language server that can be started from the JabRef application.
To use it with Emacs, JabRef must be running.

Open JabRef and enable the language server:

1. Start JabRef
2. Go to **Options → Preferences → Advanced**
3. Enable **Language Server**
4. Note the port number shown
---

## Configure Emacs to use JabRef LSP

Add the following configuration to your Emacs init file (`~/.emacs` or `init.el`):

```elisp
(require 'lsp-mode)

(add-hook 'bibtex-mode-hook #'lsp)

(setq lsp-log-io nil)
---

## Configure Emacs to use JabRef LSP

Add the following configuration to your Emacs init file (`~/.emacs` or `init.el`):

```elisp
(require 'lsp-mode)

(add-hook 'bibtex-mode-hook #'lsp)

(setq lsp-log-io nil)
---

## Configure Emacs to use JabRef LSP

Add the following configuration to your Emacs init file (`~/.emacs` or `init.el`):

```elisp
(require 'lsp-mode)

(add-hook 'bibtex-mode-hook #'lsp)

(setq lsp-log-io nil)
---

## Start JabRef LSP and test in Emacs

1. Make sure JabRef is installed and available in your system PATH.
2. Open Emacs.
3. Open any `.bib` file.
4. Emacs will automatically start the JabRef LSP server via `lsp-mode`.

If everything is set up correctly, you should see:
- Autocompletion for BibTeX fields
- Validation warnings for invalid entries
- Navigation support for references