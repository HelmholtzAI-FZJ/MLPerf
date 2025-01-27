# How To Run

This repo holds the code and configs for running on the JUWELS Booster as well as on HoreKa at KIT.
To run a training, simply use the `start_training_run.sh` script from within the `run_scripts` directory.
This will trigger the other scripts in this order: `start_**_training.sh` and `run_and_time.sh`, where `**`
is the training system (`jb` for JUWELS Booster and `horeka` for HoreKa).

Example usage:
```bash
./start_training_run --system booster --nodes 34 --time 01:00:00 --config "config_file_path"
```

# Repo Structure

This implementation is based on the implementation of NVIDIA, based on their containers. In our implementation,
we use Apptainer with an image that is almost identical to NVIDIA's image, except for installations of the packages
h5py and pmi, which we have added to the containers, and then converted to `.sif` files for Apptainer. We have copied
NVIDIA's Python code for the benchmark out of the container and adjusted it to our needs. This modified code is found
in the directory `image-src`.

The directory `utils` consists NVIDIA's utils for conversion, including the conversion of the data from individual `h5` files to numpy files.

In the directory, `hdf5_io` our conversion method to HDF5 is implemented. See below.

# HDF5 IO
We use HDF5 to store the input data. The conversion is implemented in `hdf5_io/convert_deepcam_to_hdf5.py`. In summary, this method creates
large `.h5` files for training and validation.


# Offical Repo

https://github.com/mlcommons/hpc/tree/main/deepcam
