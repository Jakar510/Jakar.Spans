# Jakar.Spans

Allocation-free span primitives. The types live in the `Jakar.Extensions` namespace. Jakar.Json and Jakar.Extensions both build on this package. Jakar.Extensions type-forwards `ValueStringBuilder` and `Sizes` here, so binaries compiled against an older Jakar.Extensions keep working.

The only dependency is `JetBrains.Annotations`, for its code-analysis attributes.

| Type | Purpose |
|---|---|
| `ValueStringBuilder` | A stack-only UTF-16 builder: starts from a caller buffer (`stackalloc char[256]`) or a pooled array, and formats values in place through `ISpanFormattable`. |
| `ValueUtf8Builder` | The UTF-8 counterpart: `Append("..."u8)`, UTF-16 text transcoded in place, values formatted through `IUtf8SpanFormattable`. |
| `ValueSpanReader<T>` | A forward cursor over a `ReadOnlySpan<T>` (`char`, `byte`, ...): `TryPeek`, `TryRead`, `TryReadExact`, `TryReadTo`, `SkipWhile`, and checkpoints with `Position` / `Rewind`. `Try*` members never throw and don't move on failure. |
| `Sizes` | Maximum formatted lengths per type, used to pre-size buffers. |

```csharp
using ValueUtf8Builder builder = new(stackalloc byte[256]);
builder.Append("{\"total\" : "u8).AppendUtf8Formattable(12.5m).Append((byte)'}');

ValueSpanReader<char> reader = new("key=value");
reader.TryReadTo('=', out ReadOnlySpan<char> key);   // "key"; reader.Remaining is "value"
```

Versions follow `<.NET major>.<library major>.<library minor>` (see the [repository README](https://github.com/Jakar510/Jakar.Spans#versioning)).
