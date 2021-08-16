# parcel-build-hang-bug

This repo illustrates [an issue](https://github.com/parcel-bundler/parcel/issues/6473) with `parcel` `2.0.0-rc.0` where `parcel build` will fail to exit after completing.

## Repro steps

1. Clone the repo on a windows 10 machine. I've tested this with Windows 10 21H1, `19043.1165`
2. Run `yarn` to install dependencies
3. Run `yarn build`

### Result
The build completes but never exits. If you manually exit (by hitting `ctrl + c`), and then try running `yarn clean`, which tries to delete `dist` and `.parcel-cache`, you'll get an error `EBUSY: resource busy or locked: unlink C:\...\myproject\.parcel-cache\data.mdb`
