# PublishAotCompressed

This is a NuGet package with an MSBuild target to compress results of [PublishAot](https://learn.microsoft.com/en-us/dotnet/core/deploying/native-aot/) with [UPX](https://upx.github.io/). Simply add a reference to this package and publish with `PublishAot` as usual. The result of AOT compilation will be compressed. UPX typically achieves 60% or more size savings.

UPX will in-memory decompress the program at launch. This is typically not observable.

A Hello World style program with `<EventSourceSupport>false</EventSourceSupport>`, `<UseSystemResourceKeys>true</UseSystemResourceKeys>`, and `<InvariantGlobalization>true</InvariantGlobalization>` (three [documented](https://docs.microsoft.com/en-us/dotnet/core/deploying/trimming/trimming-options?pivots=dotnet-6-0#trimming-framework-library-features) size savings options that pretty much everyone should enable) compressed with UPX is around 840 kB in size, fully self-contained.
