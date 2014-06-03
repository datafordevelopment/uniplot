# histogram

Makes histograms.


# Usage

Pass `[]float64` values to `Hist`, along with the number of bins
you want:

```go
bins := 9
data := []float64{
    0.1,
    0.2, 0.21, 0.22, 0.22,
    0.3,
    0.4,
    0.5, 0.51, 0.52, 0.53, 0.54, 0.55, 0.56, 0.57, 0.58,
    0.6,
    // 0.7 is empty
    0.8,
    0.9,
    1.0,
}

hist := Hist(bins, data)
```

Then use `hist`:

```
hist.Count // total values in buckets
hist.Min   // size of smallest bucket
hist.Max   // size of biggest bucket
for _, bkt := range hist.Buckets {
    // bkt.Min, bin.Max, bkt.Count
}
```

You can use the `FPrint` utility to create this Unicode graph:

```
0.1-0.2  5%   ▉       [1/20]
0.2-0.3  25%  ██▉     [5/20]
0.3-0.4  0%   ▏       [0/20]
0.4-0.5  5%   ▉       [1/20]
0.5-0.6  50%  █████▏  [10/20]
0.6-0.7  0%   ▏       [0/20]
0.7-0.8  0%   ▏       [0/20]
0.8-0.9  5%   ▉       [1/20]
0.9-1    10%  █▏      [2/20]
```

Like this:
```go
data := []float64{
    0.1,
    0.2, 0.21, 0.22, 0.22,
    0.3,
    0.4,
    0.5, 0.51, 0.52, 0.53, 0.54, 0.55, 0.56, 0.57, 0.58,
    0.6,
    // 0.7 is empty
    0.8,
    0.9,
    1.0,
}

bins := 9
hist := Hist(bins, data)

maxWidth := 5
err := FPrint(os.Stdout, hist, Linear(maxWidth))
```

You can pass your own `Scale` func if you want a `Log` scale instead of `Linear`.

# Docs?

[Godocs](http://godoc.org/github.com/aybabtme/histogram)!

# License

MIT license.
