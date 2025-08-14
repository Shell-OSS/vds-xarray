# VDS Xarray Backend

[![PyPI version](https://badge.fury.io/py/vdsxarray.svg)](https://badge.fury.io/py/vdsxarray)
[![Python versions](https://img.shields.io/pypi/pyversions/vdsxarray.svg)](https://pypi.org/project/vdsxarray/)
[![License](https://img.shields.io/github/license/gavargas22/vds-xarray-backend.svg)](https://github.com/gavargas22/vds-xarray-backend/blob/main/LICENSE)

An xarray backend for reading VDS (Voluum Data Store) files, commonly used in seismic data processing and geophysical applications.

## Installation

Install from PyPI:
```bash
pip install vdsxarray
```

Using uv:
```bash
uv add vdsxarray
```

For development:
```bash
git clone https://github.com/gavargas22/vds-xarray-backend.git
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

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Built on top of the excellent [xarray](https://xarray.pydata.org/) library
- Uses [OpenVDS](https://osdu.pages.opengroup.org/platform/domain-data-mgmt-services/seismic/open-vds/) for VDS file access
- dask >=2024.8.0

## License

See LICENSE file.
