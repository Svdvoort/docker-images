# Elastix Docker

This docker image provides the `transformix` command from [elastix](https://elastix.lumc.nl/) a toolbox for rigid and nonrigid registration of images.

Elastix is distributed under [an Apache 2.0 license](https://github.com/SuperElastix/elastix/blob/develop/LICENSE)

## Usage

Using this docker allows the direct execution of transformix. In the simplest form transformix can be run as:

```bash
docker run -u $UID:$GROUPS -v "<local_folder>:/transformix/" svdvoort/transformix:5.0.1 -out /transformix/ -tp /transformix/<transform_parameter_file>
```

This runs the 5.0.1 release of transformix. The `-u` and `-v` flags are needed to allow docker access to the local file system and set the correct file permissions. `<local_folder>` needs to be replaced by the folder on the local file system (the host system) on which the tranform parameter file is stored.

All flags and options used for transformix can be used by specifying them after `svdvoort/transformix:5.0.1` in the command. For example, to apply a transform to an image:

```bash
docker run -u $UID:$GROUPS -v "<local_folder>:/transformix/" svdvoort/transformix:5.0.1 -out /transformix/ -tp /transformix/<transform_parameter_file> -in /transformix/<moving_image_file>
```

Run

```bash
docker run svdvoort/transformix:5.0.1 -h
```

to see all command line options.

### Multiple input & output folders

The above command requires all files to be in the same local folder, and will als put the output in the same folder. This can be changed by allowing docker access to multiple folder:

```bash
docker run -u $UID:$GROUPS -v "<local_input_folder>:/transformix/" -v "<local_output_folder>:/output/" svdvoort/transformix:5.0.1 -out /output/ -tp /transformix/<transform_parameter_file> -in /transformix/<moving_image>
```

This will now read all the inputs from `<local_input_folder>` and will put outputs in `<local_output_folder>`. An arbitrary number of folders can be specified this way.


## See also

### Elastix

To register an image to obtain the transform parameters `elastix` is needed. See [the elastix docker](XXX) for instructions.

### Elastix-container

If you would like a base image containing elastix and transformix without running them directly, use the [elastix-container docker](XXX).

