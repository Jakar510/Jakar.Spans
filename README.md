# Jakar.Spans

Allocation-free span primitives for .NET 10: `ValueStringBuilder`, `ValueUtf8Builder`, `ValueSpanReader<T>` and `Sizes`. The package documentation is in [Jakar.Spans/README.md](./Jakar.Spans/README.md).

[Jakar.Json](https://github.com/Jakar510/Jakar.Json) and [Jakar.Extensions](https://github.com/Jakar510/Jakar.Extensions) build on this package.

## Build and test

```sh
dotnet test Jakar.Spans.slnx -c Release
dotnet pack Jakar.Spans/Jakar.Spans.csproj -c Release -o nupkg
```

## Versioning

Versions are **`<.NET major>.<library major>.<library minor>`**:

| Part | Meaning |
|---|---|
| .NET major | The .NET version the package targets (10 for .NET 10). |
| Library major | Breaking changes: removed or changed public API. |
| Library minor | New features and fixes that don't break existing code. |

A new package starts at `<.NET major>.1.0`, so Jakar.Spans started at 10.1.0.

## License

MIT. See [LICENSE.txt](./LICENSE.txt).
