%{
  title: "Direnv Makes Env Easy",
  author: "Fede Otaran",
  date: ~D[2023-02-14],
  tags: ["direnv", "environment variables", "productivity", "tools"],
  description: "How to use direnv to automatically manage environment variables per project and keep your shell clean."
}
---
Managing environment variables is a common task in development. Different projects need different tools, credentials, or configs, and manually exporting variables is error-prone.  
This is where **direnv** shines.

## What is `direnv`?

`direnv` is a command-line tool that **automatically loads and unloads environment variables based on your current directory**.  
As you move between projects, your shell environment updates itself—no manual intervention needed.

> *What environment should be active in this directory?*

## The Core Idea

When you enter a directory with a `.envrc` file, `direnv`:

1. Detects the file  
2. Asks for your permission (for security)  
3. Loads the environment variables defined in it  

When you leave, those variables are automatically unloaded.

This means:
- No global pollution  
- No forgotten `export` commands  
- No manual cleanup  

## How It Fits Into Your Shell

Once hooked into your shell (bash, zsh, fish, etc.), `direnv` works seamlessly.  
Your environment changes dynamically as you `cd` between folders.

A typical `.envrc`:

```sh
export DATABASE_URL=postgres://localhost/my_app
export NODE_ENV=development
```

After running:

```sh
direnv allow
```

those variables are available **only** while you are inside that directory (or its subdirectories).

## Why `direnv` Is Useful

The main value of `direnv` is its **automatic and contextual behavior**:

- **Project isolation**: Each project defines its own environment.  
- **Safety**: Explicit approval is required before loading any `.envrc`.  
- **Consistency**: Teams can share the same setup.  
- **Simplicity**: No custom scripts or manual sourcing needed.  

Just enter the project directory and start working.

## What `direnv` Is (and Isn’t)

`direnv` is:
- A lightweight environment loader  
- Shell-agnostic  
- Focused on developer ergonomics  

`direnv` is not:
- A secrets manager  
- A full configuration management system  
- A replacement for `.env` files in production  

Its strength is doing **one thing well**: managing local environment variables automatically.

If you want to give it a try, you can find installation instructions and download `direnv` from the [official website](https://direnv.net).

## Conclusion

`direnv` makes your directory define your environment.  
It removes friction from daily development and keeps your shell clean, predictable, and secure.

If you work with multiple projects, `direnv` quickly becomes one of those tools you forget is there—until you try working without it.
