#Vulture

Vulture provides information about Parrot firmware files. It can list and extract files from a given firmware, along with other filesystem information such a partitionning and bootstrapping.

##Usage

```bash
./vulture -r <firmware> -o <output_dir> [-v] [-t]

optional arguments:
  -h, --help            show this help message and exit

I/O Options:
  Input and output data options.

  -r INPUT, --read INPUT
                        Parrot firmware file to read.
  -o OUTPUT, --output OUTPUT
                        Output directory into which files will be extracted
                        to.
  -v, --verbose			Display additional information about decompression
                        process.
  -t, --test            Do not extract files. Only list them and output JSON
						data about its contents.
```

Once executed, Vulture will analyze the given Parrot firmware and extract entries out of it. All the information found within the file will be written in JSON format in a file called "meta.json" in the given output directory. Unless the _-t_ argument is specified, all files within the firmware will be extracted to the output directory specified. Additionally, files in the bootloader entry and installation entry will be saved as "boot.bin" and "install.plf" in the root of the specified output directory.

##Examples

The example below will extract files from the 'nap_update.plf' file and extract all internal files to '/tmp/sky'.

```bash
.\vulture.py -r /home/resyst/targets/parrot/skycontroller/nap_update.plf -o /tmp/sky
```

##Notes

As of January 2017, Vulture was tested only on the Parrot SkyController 1.7.4 and Bebop2 4.0.3 firmware file. There is no guarantee that it will successfully extract contents from other firmware at this moment, but I'm confident it should do much of the work.

CRC checks are not conducted at this moment, as it is unclear how each CRC value is calculated. Additional work is being conducted on this. Feel free to assist if yo have more information.

Vulture was tested with the following firmwares:
- [SkyController  1.7.4](https://community.parrot.com/t5/Skycontroller/bd-p/Sky)
- [Parrot Bebop2 4.0.3](https://community.parrot.com/t5/Bebop-2/bd-p/Bebop2)

##Citation

This software is free to use and modify as needed in your project. If you do, please cite usage of this application in your code/papers and linking to my GitHub. Thank you!

```latex
@Misc{racicot17,
author =   {Jonathan Racicot},
title =    {Reversing the Parrot SkyController Firmware},
howpublished = {\url{http://wp.me/p852om-8Q}},
year = {2017}
}
```

##Further Reading

Racicot, J., Reversing the Parrot SkyController Firmware, Infected Packets, http://wp.me/p852om-8Q (accessed on 2017-01-09)
