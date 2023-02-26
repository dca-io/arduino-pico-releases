# arduino-pico-releases

# Publishing

1. Copy and extract existing distribution
```
$ curl https://github.com/earlephilhower/arduino-pico/releases/download/2.6.5/rp2040-2.6.5.zip > rp2040-2.6.5.zip
$ unzip rp2040-2.6.5.zip
```

2. C/O forked repo
```
$ clone https://github.com/dca-io/arduino-pico
$ git checkout pp128r0
```

3. Copy over custom files to distribution
```
$ cp -r arduino-pico/variants/pp128*  rp2040-2.6.5/variants
$ cp arduino-pico/board.txt rp2040-2.6.5/
```

4. Create package archive
```
$ rm rp2040-2.6.5.zip
$ zip -r rp2040-2.6.5.zip rp2040-2.6.5
```

5. Prepare package descriptor
```
$ cp arduino-pico/package_rp2040_index.template.json package_rp2040_index.json
# Gather size and SHA checksum of package archive
$ ls -l rp2040-2.6.5.zip
$ shasum -a 256 rp2040-2.6.5.zip
# Replace `size` and `checksum` properties in `package_rp2040_index.json`
```

6. Publish `package_rp2040_index.json` to release `global` in repo `dca-io/arduino-pico-releases`

7. Publish `package_rp2040_index.json` and `rp2040-2.6.5.zip` to release `2.6.5` in repo `dca-io/arduino-pico-releases`
