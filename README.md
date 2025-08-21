# How to install :crab: Rust on custom location 🗺️:

Go to [official :crab: Forge](https://forge.rust-lang.org/infra/other-installation-methods.html) and download binary archive tarballs for your platform(s):  
`<platform>-<type>-<os>[<-toolchain>]`

Example: Windows on Intel / AMD CPU:
+ x86_64-pc-windows-msvc: if you want to produce MSVC compiled binaries
+ x86_64-pc-windows-gnu: if you want to produce GCC compiled binaries

Prefer `stable` release, `beta`	and `nightly` releases potentionally can have 🐛bugs.

# Windows

Create a custom directory `X:\rust-1.89.0-x86_64-pc-windows-gnu` (`X:\` is a drive letter where you prefer to put 🦀Rust files). It is up
to you to chose a good name. It is a good practice to keep original archive tarballs name (without the suffix/extension), since this will ease maintenance.

Open the downloaded binary tarball with prefered archive manager \( [7-zip](https://www.7-zip.org/) \). You will see many directories:

```
------------------- ----- ------------ ------------  ------------------------
2006-07-24 04:21:28 D....            0            0  rust-1.89.0-x86_64-pc-windows-gnu
2006-07-24 04:21:28 D....            0            0  rust-1.89.0-x86_64-pc-windows-gnu\cargo
2006-07-24 04:21:28 D....            0            0  rust-1.89.0-x86_64-pc-windows-gnu\clippy-preview
2006-07-24 04:21:28 D....            0            0  rust-1.89.0-x86_64-pc-windows-gnu\llvm-bitcode-linker-preview
2006-07-24 04:21:28 D....            0            0  rust-1.89.0-x86_64-pc-windows-gnu\llvm-tools-preview
2006-07-24 04:21:28 D....            0            0  rust-1.89.0-x86_64-pc-windows-gnu\rust-analysis-x86_64-pc-windows-gnu
2006-07-24 04:21:28 D....            0            0  rust-1.89.0-x86_64-pc-windows-gnu\rust-analyzer-preview
2006-07-24 04:21:28 D....            0            0  rust-1.89.0-x86_64-pc-windows-gnu\rust-docs
2006-07-24 04:21:28 D....            0            0  rust-1.89.0-x86_64-pc-windows-gnu\rust-docs-json-preview
2006-07-24 04:21:28 D....            0            0  rust-1.89.0-x86_64-pc-windows-gnu\rust-mingw
2006-07-24 04:21:28 D....            0            0  rust-1.89.0-x86_64-pc-windows-gnu\rust-std-x86_64-pc-windows-gnu
2006-07-24 04:21:28 D....            0            0  rust-1.89.0-x86_64-pc-windows-gnu\rustc
2006-07-24 04:21:28 D....            0            0  rust-1.89.0-x86_64-pc-windows-gnu\rustfmt-preview

```
Extract every directory in the archive to  `X:\rust-1.89.0-x86_64-pc-windows-gnu`:  
`cargo\`:
```
\cargo\bin        ----->   X:\rust-1.89.0-x86_64-pc-windows-gnu\bin
\cargo\etc        ----->   X:\rust-1.89.0-x86_64-pc-windows-gnu\etc
\cargo\share      ----->   X:\rust-1.89.0-x86_64-pc-windows-gnu\share
```
Also extract every first level directory to `X:\rust-1.89.0-x86_64-pc-windows-gnu`.
In the end you should have a single directory of `X:\rust-1.89.0-x86_64-pc-windows-gnu`:  
```
bin\
etc\
lib\
libexec\
share\
```
containing all binaries, libraries and other files.

Open a Command Prompt window (`cmd.exe`) and type:
```
C:\Users\Rustlearner> X:\rust-1.89.0-x86_64-pc-windows-gnu\bin\cargo
```
if you get:
```
Rust's package manager

Usage: cargo [OPTIONS] [COMMAND]
       cargo [OPTIONS] -Zscript <MANIFEST_RS> [ARGS]...

Options:
  -V, --version                  Print version info and exit
      --list                     List installed commands
      --explain <CODE>           Provide a detailed explanation of a rustc error message
  -v, --verbose...               Use verbose output (-vv very verbose/build.rs output)
  -q, --quiet                    Do not print cargo log messages
      --color <WHEN>             Coloring [possible values: auto, always, never]
  -C <DIRECTORY>                 Change to DIRECTORY before doing anything (nightly-only)
      --locked                   Assert that `Cargo.lock` will remain unchanged
      --offline                  Run without accessing the network
      --frozen                   Equivalent to specifying both --locked and --offline
      --config <KEY=VALUE|PATH>  Override a configuration value
  -Z <FLAG>                      Unstable (nightly-only) flags to Cargo, see 'cargo -Z help' for details
  -h, --help                     Print help

Commands:
    build, b    Compile the current package
    check, c    Analyze the current package and report errors, but don't build object files
    clean       Remove the target directory
    doc, d      Build this package's and its dependencies' documentation
    new         Create a new cargo package
    init        Create a new cargo package in an existing directory
    add         Add dependencies to a manifest file
    remove      Remove dependencies from a manifest file
    run, r      Run a binary or example of the local package
    test, t     Run the tests
    bench       Run the benchmarks
    update      Update dependencies listed in Cargo.lock
    search      Search registry for crates
    publish     Package and upload this package to the registry
    install     Install a Rust binary
    uninstall   Uninstall a Rust binary
    ...         See all commands with --list

See 'cargo help <command>' for more information on a specific command.
```
you are ready with `cargo`.  
Check `X:\rust-1.89.0-x86_64-pc-windows-gnu\bin\rustc`:
```
C:\Users\Rustlearner> X:\rust-1.89.0-x86_64-pc-windows-gnu\bin\rustc
```

If you prefer Powershell enclose paths in double quotes and prepend with ampersand symbol (`&`):
```
PS C:\Users\Rustlearner> & "X:\rust-1.89.0-x86_64-pc-windows-gnu\bin\cargo"
PS C:\Users\Rustlearner> & "X:\rust-1.89.0-x86_64-pc-windows-gnu\bin\rustc"
```

Now you are ready with custom installation.

In order to be able to run `cargo`, `rustc` from everywhere without need of typing whole executable path, you have to update `PATH` variable:  
+ Type `env` to search bar and click on "Edit environment variables for your account"
+ Click on Path field and click on "Edit..."
+ Click on white background, do not alter any previous record
+ Click "New" button on the right (left if you are RTL)
+ Put the new record: `X:\rust-1.89.0-x86_64-pc-windows-gnu\bin` and click "OK"

If you want to set up custom `CARGO_HOME`, because `cargo` will place its files in your user directory:
+ Select "New..." (We are still in "Environment variables" window)
+ Variable name field should be: `CARGO_HOME`
+ Variable value field should be: `X:\cargo` (chose a directory)
+ Click "OK" and "OK"  
You are ready now.

<hr/>

## Setting up Visual Studio Code

1. Get `rust-src` from official Rust repository.  
Open a Windows Command window and type command:
```
C:\Users\Rustlearner> curl -L https://static.rust-lang.org/dist/channel-rust-stable.toml | findstr /c:"rust-src" | findstr /c:.tar.
```
Note: if you selected `beta` or `nightly` substitude `stable` with your verb (i.e: `https://static.rust-lang.org/dist/channel-rust-beta.toml`)  
You will get something like this:
```
url = "https://static.rust-lang.org/dist/2025-08-20/rust-src-stable.tar.gz"
xz_url = "https://static.rust-lang.org/dist/2025-08-20/rust-src-stable.tar.xz"
```
Download any of these tarballs.

2. Open the source tarball with your archive manager.
3. Navigate to `rust-src\` directory
4. Decompress `lib` directory to `X:\rust-1.89.0-x86_64-pc-windows-gnu\`:
```
rust-src-1.89.0\rust-src\lib      ------>         X:\rust-1.89.0-x86_64-pc-windows-gnu
```
5. Create a new project directory in File Explorer and open it with Visual Studio Code.
6. Press Ctrl + &#96; if your Terminal is not visible.
7. Type there:
```
cargo init
```
8. Install official [rust-analyzer](https://marketplace.visualstudio.com/items?itemName=rust-lang.rust-analyzer) extension.

That's it!

Happy codding✍️ with :crab: Rust.

🥳🎉🎉🎉🎉

