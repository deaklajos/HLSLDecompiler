## HLSLDecompiler

Translate dxbc to hlsl source code. You can use it alone, or as a renderdoc shader processing tool to decompile shader. Although the decompiled result looks very like the disassembly, you can edit the decompiled source code and refresh to see the change in Renderdoc. It's very useful while learning and analyzing rendering techniques in games if you don't have source code.

### How to integrate into renderdoc

1. Put `hlsl_decompiler_wrapper.bat` and `cmd_Decompiler.exe` in the same directory
2. Renderdoc -> Tools -> Settings -> Shader Viewer -> Add
    | Field | Value |
    |------|:--------------:|
    | Name | HLSLDecompiler |
    | Tool Type | Custom Tool |
    | Executable | Set absolute path of `hlsl_decompiler_wrapper.bat` |
    | Command Line | {input_file} |
    | Input/Output | DXBC/HLSL |

3. Renderdoc -> Pipeline State View -> Choose Any Shader Stage -> Edit -> Decompile with ${Name}
4. Modify shader as you wish, and click Refresh button to see the change

deaklajos: Forked the most uptodate fork of HLSLDecompiler.
I'm experimenting with shader model 5.1 which is not currently supported.
Mainly doing this for Xenia shader recompilation.
Currently the shaders are generated straight to dxbc bytecode. It might worth it to turn the dxbc to hlsl then compile to take advantage of the optimizer. The driver might do the same optimization steps so this might be uneffective.
Will try it and see.
Could recompile shaders which are run mostly with the same constant data.
Would also be usefull for shader debuging/editing in RenderDoc.
TODO: Any real bugfix should be merged back to the original repo: https://github.com/bo3b/3Dmigoto.
