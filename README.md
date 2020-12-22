# ComponentLibWithXmlLinkerConfig
Sample of NET IL Configuration in Blazor Library 

I tried to replicate this same behavior: https://github.com/danroth27/ComponentLibWithXmlLinkerConfig but using .Net Core 5.0
I was able to run this sample locally (debug and release mode) but I'm not able run it after is deployed.

After VS reduce the assemblies sizes via Linker, I got:

# Unhandled exception rendering component: TypeInitialization_Type, System.Linq.Dynamic.Core.Parser.EnumerationsFromMscorlib
System.TypeInitializationException: TypeInitialization_Type, System.Linq.Dynamic.Core.Parser.EnumerationsFromMscorlib
 ---> System.IO.FileNotFoundException: 
IO_FileName_Name, System.Runtime
   at System.Reflection.Assembly.Load(AssemblyName assemblyRef, StackCrawlMark& stackMark, AssemblyLoadContext assemblyLoadContext)
   at System.Reflection.Assembly.Load(AssemblyName assemblyRef)
   at System.Linq.Dynamic.Core.Parser.EnumerationsFromMscorlib.AddEnumsFromAssembly(String assemblyName)
   at System.Linq.Dynamic.Core.Parser.EnumerationsFromMscorlib..cctor()
   Exception_EndOfInnerExceptionStack
   at System.Linq.Dynamic.Core.Parser.KeywordsHelper..ctor(ParsingConfig config)
   at System.Linq.Dynamic.Core.Parser.ExpressionParser..ctor(ParameterExpression[] parameters, String expression, Object[] values, ParsingConfig parsingConfig)
   at System.Linq.Dynamic.Core.DynamicExpressionParser.ParseLambda(Type delegateType, ParsingConfig parsingConfig, Boolean createParameterCtor, ParameterExpression[] parameters, Type resultType, String expression, Object[] values)
   at System.Linq.Dynamic.Core.DynamicExpressionParser.ParseLambda(ParsingConfig parsingConfig, Boolean createParameterCtor, ParameterExpression[] parameters, Type resultType, String expression, Object[] values)
   at System.Linq.Dynamic.Core.DynamicExpressionParser.ParseLambda(ParsingConfig parsingConfig, Boolean createParameterCtor, Type itType, Type resultType, String expression, Object[] values)
   at System.Linq.Dynamic.Core.DynamicQueryableExtensions.Where(IQueryable source, ParsingConfig config, String predicate, Object[] args)
   at System.Linq.Dynamic.Core.DynamicQueryableExtensions.Where[Person](IQueryable`1 source, ParsingConfig config, String predicate, Object[] args)
   at System.Linq.Dynamic.Core.DynamicQueryableExtensions.Where[Person](IQueryable`1 source, String predicate, Object[] args)
   at RazorClassLibrary1.Component1.OnClick()
   at Microsoft.AspNetCore.Components.EventCallbackWorkItem.InvokeAsync[Object](MulticastDelegate delegate, Object arg)
   at Microsoft.AspNetCore.Components.EventCallbackWorkItem.InvokeAsync(Object arg)
   at Microsoft.AspNetCore.Components.ComponentBase.Microsoft.AspNetCore.Components.IHandleEvent.HandleEventAsync(EventCallbackWorkItem callback, Object arg)
   at Microsoft.AspNetCore.Components.EventCallback.InvokeAsync(Object arg)
   at Microsoft.AspNetCore.Components.RenderTree.Renderer.DispatchEventAsync(UInt64 eventHandlerId, EventFieldInfo fieldInfo, EventArgs eventArgs)
d.printErr @ blazor.webassembly.js:1
d.preRun.push.window.Blazor._internal.dotNetCriticalError @ blazor.webassembly.js:1
w @ blazor.webassembly.js:1
_mono_wasm_invoke_js_blazor @ dotnet.5.0.0.js:1
do_icall @ dotnet.wasm:0x194e46
do_icall_wrapper @ dotnet.wasm:0x79df6
interp_exec_method @ dotnet.wasm:0x44ad0
interp_runtime_invoke @ dotnet.wasm:0x12efed
mono_jit_runtime_invoke @ dotnet.wasm:0x118e4d
do_runtime_invoke @ dotnet.wasm:0x79d3f
mono_runtime_invoke_checked @ dotnet.wasm:0xf65a
mono_runtime_try_invoke_array @ dotnet.wasm:0x10e81f
ves_icall_InternalInvoke @ dotnet.wasm:0xed48f
ves_icall_InternalInvoke_raw @ dotnet.wasm:0xecf54
do_icall @ dotnet.wasm:0x194dd3
do_icall_wrapper @ dotnet.wasm:0x79df6
interp_exec_method @ dotnet.wasm:0x44ad0
interp_runtime_invoke @ dotnet.wasm:0x12efed
mono_jit_runtime_invoke @ dotnet.wasm:0x118e4d
do_runtime_invoke @ dotnet.wasm:0x79d3f
mono_runtime_try_invoke @ dotnet.wasm:0x1297f
mono_runtime_invoke @ dotnet.wasm:0x10ec19
mono_wasm_invoke_method @ dotnet.wasm:0x108e40
Module._mono_wasm_invoke_method @ dotnet.5.0.0.js:1
call_method @ dotnet.5.0.0.js:1
(anonymous) @ dotnet.5.0.0.js:1
beginInvokeDotNetFromJS @ blazor.webassembly.js:1
h @ blazor.webassembly.js:1
e.invokeMethodAsync @ blazor.webassembly.js:1
(anonymous) @ blazor.webassembly.js:1
invokeWhenHeapUnlocked @ blazor.webassembly.js:1
(anonymous) @ blazor.webassembly.js:1
t.dispatchEvent @ blazor.webassembly.js:1
(anonymous) @ blazor.webassembly.js:1
(anonymous) @ blazor.webassembly.js:1
e.onGlobalEvent @ blazor.webassembly.js:1

# Steps:
- Clone repository
- Run solution in Visual Studio 2019 Preview (debug or release mode)
- Deploy the solution into IIS 
- Try to use Dynamic Linq Sample in order to get the error mentioned above

Show 6 more frames

