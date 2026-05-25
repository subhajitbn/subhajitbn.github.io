---
date: 2026-05-25 17:00:00 +0530
---
# Testing return value of a mutating function in Zig

Consider the following `reverseArray` function. It mutates the array in-place, and returns the result. Of course, that's a rather redundant thing to do. But it represents a general class of functions that has side effects and a return value.

```zig
fn reverseArray(arr: []u32) []u32 { ... }
```

Now, we want to test it. The following code doesn't work, because the inline slice `&[_]u32{ 1, 2, 3 }` is read-only.

```zig
test "reverseArray: works" {
  try std.testing.expectEqualSlices(
    u32,
    &[_]u32{ 3, 2, 1 },
    reverseArray(&[_]u32{ 1, 2, 3 }), // Fails
  );
}
```

We need to make the input slice mutable. The next one works. This is the "stack approach".

```zig
test "reverseArray: works" {
  var mock_arr = [_]u32{ 1, 2, 3 };
  try std.testing.expectEqualSlices(
    u32,
    &[_]u32{ 3, 2, 1 },
    reverseArray(&mock_arr),
  );
}
```

However, `var mock_arr = [_]u32{ 1, 2, 3 }` makes stack allocation. And that might not be favorable in some cases. 
- We may need `var massive_mock_array = [_]u32{0} ** 10_000_000`, which will lead to a stack overflow.  
- The array may come from a text file containing a bunch of arrays, or a random number generator to do fuzz testing. In either case, the size of the array is not known at compile time. In Zig, stack array sizes must be known at comptime.

So, here comes the "heap approach" with the testing allocator.

```zig
test "reverseArray: works" {
  const mock_arr = try std.testing.allocator.dupe(u32, &[_]u32{ 1, 2, 3 });
  defer std.testing.allocator.free(mock_arr);

  try std.testing.expectEqualSlices(
    u32,
    &[_]u32{ 3, 2, 1 },
    reverseArray(mock_arr),
  );
}
```

In any case, having a function do both side effects and return something is not a good idea. It's better if a function does exactly one thing.
