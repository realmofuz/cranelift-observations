# IR
These are notes on how to store, read, and construct Cranelift IR.

## Types
Cranelift IR has a couple types:
- `i8`
- `i16`
- `i32`
- `i64`
- `i128`
- `f32`
- `f64`
- `r32`
- `r64`

You most likely recognize all but the last two - what is `r32` and `r64`? These are reference types, they represent a 32-bit pointer and a 64-bit pointer respectively. This difference is needed because some machines have 32bit memory addresses, while others have 64bit memory addresses.

### SIMD Vector Types
I saved these seperately because there's a lot of these.
`TODO: explain how vector types work, because they seem a bit weird`