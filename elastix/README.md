# Elastix Docker

This docker image provides [elastix](https://elastix.lumc.nl/) a toolbox for rigid and nonrigid registration of images.

Elastix is distributed under [an Apache 2.0 license](https://github.com/SuperElastix/elastix/blob/develop/LICENSE)

## Usage

Using this docker allows the direct execution of elastix. In the simplest form elastix can be run as:

```bash
docker run -u $UID:$GROUPS -v "<local_folder>:/elastix/" svdvoort/elastix:5.0.1 -out /elastix/ -p /elastix/<parameter_file> -f /elastix/<fixed_image> -m /elastix/<moving_image>
```

This runs the 5.0.1 release of elastix. The `-u` and `-v` flags are needed to allow docker access to the local file system and set the correct file permissions. `<local_folder>` needs to be replaced by the folder on the local file system (the host system) on which the parameter file, the fixed image, and the moving image are stored.

All flags and options used for elastix can be used by specifying them after `svdvoort/elastix:5.0.1` in the command. For example, to use a fixed mask:

```bash
docker run -u $UID:$GROUPS -v "<local_folder>:/elastix/" svdvoort/elastix:5.0.1 -out /elastix/ -p /elastix/<parameter_file> -f /elastix/<fixed_image> -m /elastix/<moving_image> -fMask /elastix/<fixed_mask-file>
```

Run

```bash
docker run svdvoort/elastix:5.0.1 -h
```

to see all command line options.

### Multiple input & output folders

The above command requires all files to be in the same local folder, and will als put the output in the same folder. This can be changed by allowing docker access to multiple folder:

```bash
docker run -u $UID:$GROUPS -v "<local_input_folder>:/elastix/" -v "<local_output_folder>:/output/" svdvoort/elastix:5.0.1 -out /output/ -p /elastix/<parameter_file> -f /elastix/<fixed_image> -m /elastix/<moving_image>
```

This will now read all the inputs from `<local_input_folder>` and will put outputs in `<local_output_folder>`. An arbitrary number of folders can be specified this way.

## See also

### Transformix

To transform an image using the parameters obtained `transformix` is needed. See [the transformix docker](XXX) for instructions.

### Elastix-container

If you would like a base image containing elastix and transformix without running them directly, use the [elastix-container docker](XXX).
