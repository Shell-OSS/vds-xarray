# VDS Xarray Backend

An xarray backend for reading VDS (Voluum Data Store) files, commonly used in seismic data processing.

## Installation

Using uv:
```bash
uv pip install vdsxarray
```

Or for development:
```bash
git clone <repo-url>
cd vds-xarray-backend
uv pip install -e .
```

## Usage

```python
import xarray as xr

# Open a VDS file
ds = xr.open_dataset("path/to/your/file.vds", engine="vds")

# The dataset will contain seismic data with proper coordinates
print(ds)

# Access the amplitude data
amplitude = ds.Amplitude

# Data is lazily loaded and can be used with dask
print(amplitude.dims)  # ('sample', 'crossline', 'inline')
print(amplitude.coords)  # Shows coordinate ranges
```

## Features

- **Lazy loading**: Data is loaded on-demand using dask arrays
- **Proper coordinates**: Automatically extracts inline, crossline, and sample coordinates
- **Chunking**: Optimized chunk sizes for efficient processing
- **Metadata**: Includes coordinate ranges and source file information

## Requirements

- Python >=3.9, <3.12
- xarray >=2024.7.0
- openvds >=3.4.6
- ovds-utils >=0.3.1
- dask >=2024.8.0

## License

See LICENSE file.