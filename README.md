This is a GHC plugin that renders the Core generated by GHC
into JSON and also HTML, for easy inspection.  The JSON is machine
readable so it could be used by other tools, although at present the
format is not documented and unstable.

An easy way to use the plugin is to add a flag to your Cabal file. For
example, add the following to top-level of the Cabal file:

    flag dump-core
      description: Dump HTML for the core generated by GHC during compilation
      default:     False

Then, you can add something like this to your library or executable section:

    if flag(dump-core)
      build-depends: dump-core
      ghc-options: -fplugin=DumpCore -fplugin-opt DumpCore:core-html

The option to the plugin specifies the directory where files should be saved---
in this example, it is set to `core-html`.  The default is `dump-core`.



